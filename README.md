# Flight-Analytics
# ✈️ Flight Analytics — Phân tích & Trực quan hóa Dữ liệu Hàng không  
_(Google Colab + Databricks + FastAPI + MongoDB + ngrok)_

## 🎯 Mục tiêu dự án  
Dự án này nhằm mô phỏng toàn bộ quy trình của một hệ thống dữ liệu hiện đại:  
- Thu thập & xử lý dữ liệu chuyến bay bằng **PySpark trên Databricks**  
- Tính toán các chỉ số vận hành (KPI) hãng hàng không  
- Lưu kết quả lên **MongoDB Atlas**  
- Xây dựng ứng dụng web + API với **FastAPI** cho việc truy xuất và trực quan hóa  
- Triển khai nhanh trên **Google Colab** với **ngrok** để demo  
---

## 🧠 Kỹ năng thể hiện  
- **Data Engineering**: Làm sạch, chuẩn hóa và tổng hợp dữ liệu lớn với PySpark  
- **API Development**: Thiết kế RESTful API chuẩn với FastAPI  
- **NoSQL Database**: Thiết kế và làm việc với MongoDB Atlas  
- **Cloud Integration**: Kết nối Databricks ↔ MongoDB, triển khai trên Colab/ngrok   
---
## 📦 Cấu trúc dự án  
flight_analytics/
│
├── main.ipynb # Notebook xử lý dữ liệu ( Databricks)
├── mainAPI # Ứng dụng FastAPI (UI + API) chạy trên colab

## ⚙️ Công nghệ & Tools  
- **Databricks / PySpark** — xử lý dữ liệu lớn  
- **MongoDB Atlas** — lưu trữ dữ liệu tổng hợp  
- **FastAPI + Uvicorn** — backend web + API  
- **Jinja2 Templates + Chart.js** — giao diện động & biểu đồ  
- **ngrok** — tạo public URL demo trên Colab  
- **Google Colab** — môi trường chạy nhanh và share dễ dàng  
---

## 🧮 Pipeline xử lý dữ liệu  
1. Đọc dữ liệu CSV (airlines, airports, flights)  
2. Làm sạch & chuẩn hóa: chuyển kiểu dữ liệu, fillna, thời gian từ HHMM → phút  
3. Tạo các cột mới: IS_DELAYED, DELAY_CATEGORY, PEAK_PERIOD, TIME_OF_DAY  
4. Join với bảng airlines & airports để enrich thông tin  
5. Tính KPI per-airline (tổng chuyến bay, tỷ lệ đúng giờ/hủy/chuyển hướng, độ trễ trung bình, top sân bay…)  
6. Chuyển kết quả sang định dạng document JSON và ghi vào MongoDB  
7. Ứng dụng FastAPI đọc dữ liệu từ MongoDB, hiển thị qua web UI & cung cấp API endpoints

---

## 💻 Hướng dẫn chạy dự án  
1. Tạo Notebook mới và upload `main.ipynb` trên databricks
2. chạy file Api trên colab
   ```bash
   !pip install fastapi uvicorn nest_asyncio pyngrok pymongo jinja2
   !ngrok config add-authtoken <YOUR_NGROK_TOKEN>
Cấu hình kết nối MongoDB trong main.ipynb (user, password, uri)

Chạy:
🌍 Ứng dụng chạy tại: https://xxxx.ngrok-free.app
Mở link để truy cập Dashboard hoặc test API

🔗 API Endpoints
Phương thức	Endpoint	Mô tả
GET	/api/airlines	Lấy danh sách tất cả hãng bay
GET	/api/airlines/{code}	Lấy thông tin chi tiết cho một hãng
POST	/api/airlines	Thêm mới một hãng bay
PUT	/api/airlines/{code}	Cập nhật dữ liệu hãng bay
DELETE	/api/airlines/{code}	Xóa hãng bay từ database

🎨 Giao diện Web Dashboard
Nhập mã hãng bay (VD: UA, DL, AA)

Hiển thị các chỉ số: tổng chuyến bay, tỷ lệ đúng giờ, độ trễ trung bình, top sân bay

Biểu đồ Top 10 sân bay khởi hành & điểm đến sử dụng Chart.js

Cập nhật thời gian (last_updated) hiển thị dưới cùng

❗ Lưu ý & Khắc phục lỗi thường gặp
ServerSelectionTimeoutError (MongoDB): Kiểm tra URI đúng, IP whitelist trên Atlas

Ngrok tunnel expired: đảm bảo token ngrok đã add đúng

ModuleNotFoundError: chạy đầy đủ các thư viện theo requirements.txt

Dữ liệu trống / null: kiểm tra bước làm sạch trong notebook Databricks

📈 Hướng phát triển tiếp theo
Thực hiện load dữ liệu incremental (Delta Lake)

Tạo Dashboard nâng cao bằng Streamlit hoặc Dash

Triển khai ứng dụng lên sản phẩm (Render / Railway / AWS Lambda)

Thêm authentication (JWT) cho API

Tích hợp CI/CD và test tự động cho pipeline

👤 Tác giả
Đinh Trọng Quỳnh
Data Engineer
📧 [dinhtrongquynh240@gmail.com]
🔗 [https://github.com/quynh1111 / https://www.linkedin.com/in/qu%E1%BB%B3nh-%C4%91inh-tr%E1%BB%8Dng-233b28319?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app]

