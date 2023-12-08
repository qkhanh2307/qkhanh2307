- 👋 Hi, I’m @qkhanh2307
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
qkhanh2307/qkhanh2307 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
// src/App.tsx
import React, { useState } from
 
"react";
import { BrowserRouter, Routes, Route } from
 
"react-router-dom";
import Header from
 
"./components/Header";
import Main from
 
"./components/Main";
import Footer from
 
"./components/Footer";

const App = () => {
  const [news, setNews] = useState([]);

  const fetchNews = async () => {
    const response = await fetch("https://api.example.com/news");
    const data = await response.json();
    setNews(data.news);
  };

  useEffect(() => {
    fetchNews();
  }, []);

  return (
    <BrowserRouter>
      <Header />
      <main>
        <Routes>
          <Route path="/" element={<Main news={news} />} />
        </Routes>
      </main>
      <Footer />
    </BrowserRouter>
  );
};

export default App;
Vui lòng thận trọng khi sử dụng mã. Tìm hiểu thêm
Mô tả:

Tệp App.tsx là tệp khởi tạo của ứng dụng. Nó sử dụng useState() để lưu trữ danh sách tin tức và fetch() để lấy danh sách tin tức từ API.

Tệp components/Header.tsx:

Tệp Header.tsx tạo ra một thanh tiêu đề cho ứng dụng.

TypeScript
// src/components/Header.tsx
import React from "react";

const Header = () => {
  return (
    <header>
      <h1>Trang tin tức cơ bản</h1>
    </header>
  );
};

export default Header;
Vui lòng thận trọng khi sử dụng mã. Tìm hiểu thêm
Tệp components/Main.tsx:

Tệp Main.tsx tạo ra phần nội dung chính của ứng dụng. Nó chứa danh sách tin tức và một nút để xem chi tiết tin tức.

TypeScript
// src/components/Main.tsx
import React, { useState } from "react";
import { Link } from "react-router-dom";
import NewsCard from "./components/NewsCard";

const Main = ({ news }) => {
  const [selectedNews, setSelectedNews] = useState(null);

  return (
    <div>
      <h2>Danh sách tin tức</h2>
      <ul>
        {news.map((newsItem) => (
          <li key={newsItem.id}>
            <Link to={`/news/${newsItem.id}`}>
              <NewsCard news={newsItem} />
            </Link>
          </li>
        ))}
      </ul>
      {selectedNews && (
        <div>
          <h2>Chi tiết tin tức</h2>
          <p>{selectedNews.title}</p>
          <p>{selectedNews.content}</p>
        </div>
      )}
    </div>
  );
};

export default Main
 <ul>
        {news.map((newsItem) => (
          <li key={newsItem.id}>
            <Link to={`/news/${newsItem.id}`}>
              <NewsCard news={newsItem} />
            </Link>
          </li>
        ))}
      </ul>
