# Cài app vào điện thoại

Năm file trong thư mục này là một app hoàn chỉnh. Sau khi cài xong, điện thoại **không cần mạng** nữa — toàn bộ 1.900 từ nằm trong máy.

| File | Vai trò |
|---|---|
| `index.html` | Toàn bộ app + 1.900 từ |
| `manifest.webmanifest` | Khai báo tên, icon, chạy toàn màn hình |
| `sw.js` | Bộ nhớ đệm offline |
| `icon-192.png`, `icon-512.png` | Icon trên màn hình chính |

## Vì sao phải đưa lên mạng một lần

Trình duyệt chỉ cho phép cài app và chạy offline khi trang được phục vụ qua **HTTPS**. Mở file trực tiếp từ bộ nhớ điện thoại thì Chrome chặn cả lưu trữ lẫn offline — học xong đóng app là mất tiến độ.

Nên: đưa lên một lần, cài một lần, rồi ngắt mạng dùng mãi.

## Cách 1 — GitHub Pages (khuyến nghị, miễn phí)

1. Tạo tài khoản tại github.com nếu chưa có.
2. Bấm **New repository**, đặt tên `hsk`, chọn **Public**, bấm Create.
3. Trong repo mới, bấm **Add file → Upload files**, kéo cả 5 file vào, bấm **Commit changes**.
4. Vào tab **Settings → Pages**. Mục *Branch* chọn `main`, thư mục `/ (root)`, bấm **Save**.
5. Đợi 1–2 phút, GitHub hiện địa chỉ dạng `https://<tên-tài-khoản>.github.io/hsk/`.

## Cách 2 — Netlify Drop (nhanh hơn, không cần tài khoản)

Vào `app.netlify.com/drop`, kéo nguyên thư mục vào ô giữa trang. Vài giây sau nó cho một địa chỉ HTTPS dùng được ngay.

## Cài vào màn hình chính

**Android (Chrome):** mở địa chỉ trên, bấm menu ⋮ → **Cài đặt ứng dụng** hoặc **Thêm vào Màn hình chính**.

**iPhone (bắt buộc dùng Safari):** mở địa chỉ, bấm nút Chia sẻ → **Thêm vào MH chính**. Chrome trên iPhone không cài được.

Mở app từ icon vừa tạo, để nó chạy trọn một lượt (vào trang chính là đủ). Sau đó bật chế độ máy bay và mở lại — vẫn chạy bình thường là đã xong.

## Tiến độ giữa điện thoại và laptop

Hai bên lưu riêng, **không tự đồng bộ**. Chuyển tay bằng hai nút có sẵn trong app:

- Bên đang có tiến độ mới nhất: bấm **Sao lưu tiến độ** → tải về file `.json`
- Bên kia: bấm **Khôi phục từ file** → chọn file đó

Nên chọn một máy làm chính, máy kia chỉ dùng lúc rảnh, rồi chuyển một chiều. Chuyển qua chuyển lại hai chiều trong cùng một ngày sẽ ghi đè lẫn nhau.

## Khi cập nhật app

Nếu sau này thay `index.html` bằng bản mới, phải sửa `sw.js`: đổi `const CACHE = "hsk-v1"` thành `"hsk-v2"`. Không đổi thì điện thoại vẫn chạy bản cũ đã lưu trong bộ nhớ đệm.
