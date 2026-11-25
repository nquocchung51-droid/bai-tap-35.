# Bài tập 35 - Danh sách sản phẩm

## Công nghệ
- HTML5: cấu trúc trang.
- CSS3: giao diện responsive bằng CSS Grid và Flexbox.
- JavaScript: mảng dữ liệu, hiển thị sản phẩm và tìm kiếm.

## Chạy trên máy
Mở trực tiếp `index.html` bằng trình duyệt. Không cần cài đặt thư viện hoặc chạy lệnh build.

## Đưa lên Netlify
1. Đưa toàn bộ nội dung thư mục `bai-tap-35` lên một GitHub repository.
2. Đăng nhập https://app.netlify.com và chọn **Add new site → Import an existing project**.
3. Kết nối GitHub và chọn repository vừa tạo.
4. Build command: để trống.
5. Publish directory: `.` (thư mục gốc chứa `index.html`).
6. Chọn Deploy site. Sau khi deploy, đặt site ở chế độ public và mở URL Netlify để kiểm tra.

## Giải thích tư duy và xử lý an toàn
- Dữ liệu sản phẩm nằm trong mảng `products`, sau đó dùng `filter()` để lọc theo tên.
- `trim()` bỏ khoảng trắng ở đầu/cuối từ khóa; `toLocaleLowerCase("vi")` giúp tìm kiếm không phân biệt chữ hoa và chữ thường.
- `includes()` kiểm tra tên sản phẩm có chứa từ khóa hay không.
- Không ghép input người dùng vào `innerHTML`. Nội dung được đưa vào DOM bằng `textContent`, nên chuỗi như `<img onerror=...>` được hiển thị như văn bản thay vì thực thi HTML/JavaScript. Đây là cách giảm nguy cơ HTML Injection/XSS.
- `replaceChildren()` xóa kết quả cũ; `DocumentFragment` gom các thẻ trước khi thêm vào trang, giảm số lần cập nhật DOM.
- Với danh sách nhỏ trong bài tập, lọc trực tiếp bằng `filter()` là đủ đơn giản và nhanh. Nếu dữ liệu rất lớn, có thể cân nhắc tìm kiếm phía máy chủ, lập chỉ mục hoặc debounce khi nhập.

## Kiểm thử
- Nhập `intel`, `INTEL` hoặc `Intel`: đều tìm được CPU Intel.
- Nhập `ssd`: tìm được SSD Samsung.
- Nhập một từ không tồn tại: xuất hiện thông báo không tìm thấy.
- Để trống ô tìm kiếm: hiển thị lại toàn bộ sản phẩm.
