# HCM-KS26-CNTT1_NhapMonCNTT_Session18_BTVN4
# BÀI 4 – SESSION 18: SỰ CỐ XUNG ĐỘT PHIÊN ĐĂNG NHẬP TRÊN TRÌNH DUYỆT

**Họ và tên:** Phạm Thành Đạo  
**Lớp:** HCM-KS26-CNTT1  
**Môn học:** Nhập môn CNTT  
**Chủ đề:** Quản lý Browser Profile và khắc phục Session Conflict

---

# PHẦN 1. PHÂN TÍCH

## 1. Nguyên nhân xảy ra xung đột phiên đăng nhập (Session Conflict)

Trong quá trình làm việc, quản trị viên điều phối cần sử dụng đồng thời ba loại tài khoản:

- Personal: Tài khoản cá nhân phục vụ nhu cầu riêng.
- Work: Tài khoản quản trị hệ thống GreenLog và công việc doanh nghiệp.
- Sandbox: Tài khoản kiểm thử phục vụ thử nghiệm hệ thống.

Nếu sử dụng chung một cửa sổ trình duyệt, các tài khoản có thể xảy ra xung đột do dùng chung Cookie, Session và dữ liệu đăng nhập.

Ví dụ:

Khi quản trị viên đăng nhập tài khoản GreenLog, sau đó chuyển sang đăng nhập tài khoản Sandbox trên cùng một trang web, phiên đăng nhập trước đó có thể bị thay thế. Điều này khiến người dùng bị đăng xuất hoặc thực hiện nhầm thao tác trên tài khoản khác.

Ngoài ra, việc sử dụng chung trình duyệt còn có nguy cơ để lộ lịch sử duyệt web, mật khẩu đã lưu và thông tin cá nhân khi trình chiếu màn hình.

**Giải pháp:** Sử dụng mô hình 3 Browser Profile độc lập gồm Personal, Work và Sandbox.

## 2. So sánh Incognito Mode và Dedicated Profile

| Tiêu chí | Incognito Mode | Dedicated Profile |
|---|---|---|
| Mục đích | Duyệt web tạm thời, hạn chế lưu dữ liệu cục bộ sau khi đóng phiên | Quản lý một môi trường làm việc riêng biệt |
| Cookie và Session | Lưu tạm trong phiên ẩn danh, bị xóa khi đóng toàn bộ cửa sổ ẩn danh | Được lưu riêng cho từng Profile và có thể duy trì sau khi đóng trình duyệt |
| Lịch sử duyệt web | Không lưu lịch sử thông thường vào trình duyệt sau khi đóng phiên | Lưu lịch sử riêng biệt |
| Mật khẩu | Không tự động lưu mật khẩu mới theo cách thông thường | Có thể lưu mật khẩu riêng |
| Bookmark | Không phải môi trường quản lý Bookmark lâu dài | Có thể tạo và quản lý Bookmark độc lập |
| Tiện ích mở rộng | Thường bị tắt mặc định, có thể bật theo quyền cho phép | Có thể cài đặt và quản lý riêng |
| Đồng bộ hóa | Không phải môi trường đồng bộ Profile thông thường | Có thể đồng bộ Bookmark và cài đặt qua tài khoản trình duyệt |
| Tính phù hợp | Phù hợp cho nhu cầu truy cập tạm thời | Phù hợp quản lý nhiều tài khoản lâu dài |

**Nhận xét:**

Incognito Mode chỉ giúp hạn chế lưu lại dữ liệu duyệt web trên thiết bị sau khi đóng phiên. Nó không tạo ra một môi trường quản lý công việc lâu dài và không giúp phân chia tài khoản một cách thuận tiện.

Dedicated Profile tạo ra các không gian trình duyệt riêng biệt, mỗi Profile có Cookie, lịch sử, Bookmark, tiện ích mở rộng và thông tin đăng nhập riêng.

Vì vậy, Dedicated Profile là giải pháp phù hợp hơn để quản lý đồng thời tài khoản cá nhân, công việc và kiểm thử.

---

# PHẦN 2. TRIỂN KHAI

## 3. Thiết lập mô hình 3 Profile độc lập

Sử dụng trình duyệt Google Chrome để triển khai.

### 3.1. Tạo Profile Personal

**Mục đích:** Phục vụ các hoạt động cá nhân và bảo vệ thông tin riêng tư.

Các bước thực hiện:

1. Mở Google Chrome.
2. Nhấn biểu tượng Profile ở góc trên bên phải.
3. Chọn Add Chrome profile hoặc Add.
4. Chọn tạo Profile mới.
5. Đặt tên là Personal.
6. Chọn màu nhận diện riêng.
7. Đăng nhập tài khoản cá nhân nếu cần đồng bộ dữ liệu.

Cấu hình đề xuất:

- Lưu Bookmark cá nhân.
- Lưu lịch sử duyệt web cá nhân.
- Quản lý tài khoản Gmail và Facebook cá nhân.
- Không sử dụng Profile này khi trình chiếu công việc.

### 3.2. Tạo Profile Work

**Mục đích:** Quản lý công việc và tài khoản doanh nghiệp.

Các bước thực hiện:

1. Nhấn biểu tượng Profile trên Chrome.
2. Chọn Add.
3. Tạo Profile mới với tên Work.
4. Chọn màu nhận diện khác Personal.
5. Đăng nhập tài khoản phục vụ công việc nếu cần.

Cấu hình đề xuất:

- Đăng nhập hệ thống GreenLog.
- Quản lý GitHub.
- Truy cập Canvas LMS và Portal công ty.
- Chỉ cài đặt các tiện ích phục vụ công việc.
- Không lưu mật khẩu hoặc tài khoản cá nhân trong Profile này.

### 3.3. Tạo Profile Sandbox

**Mục đích:** Phục vụ kiểm thử và thử nghiệm hệ thống.

Các bước thực hiện:

1. Mở trình quản lý Profile của Chrome.
2. Chọn Add để tạo Profile mới.
3. Đặt tên Sandbox.
4. Chọn màu nhận diện riêng.
5. Sử dụng tài khoản thử nghiệm để đăng nhập.

Cấu hình đề xuất:

- Chỉ sử dụng tài khoản kiểm thử.
- Truy cập môi trường thử nghiệm.
- Kiểm tra giao diện và chức năng hệ thống.
- Không sử dụng tài khoản quản trị thật.
- Không lưu thông tin nhạy cảm hoặc mật khẩu sản xuất.

### 3.4. Nguyên tắc cách ly dữ liệu giữa các Profile

| Loại dữ liệu | Personal | Work | Sandbox |
|---|---|---|---|
| Tài khoản cá nhân | Có | Không | Không |
| Tài khoản GreenLog | Không | Có | Không |
| Tài khoản GitHub công việc | Không | Có | Không |
| Tài khoản kiểm thử | Không | Không | Có |
| Lịch sử duyệt web | Riêng | Riêng | Riêng |
| Cookie và Session | Riêng | Riêng | Riêng |
| Bookmark | Riêng | Riêng | Riêng |

**Kết quả mong đợi:**

Ba Profile hoạt động độc lập, không sử dụng chung Cookie và Session. Khi đăng nhập tài khoản GreenLog trong Profile Work, tài khoản cá nhân trong Profile Personal không bị thay thế.

Đồng thời, khi trình chiếu màn hình, quản trị viên chỉ mở Profile Work để tránh hiển thị thông tin cá nhân.

Lưu ý: Việc tách Profile giúp cách ly dữ liệu trình duyệt, nhưng không thay thế bảo mật ở cấp hệ điều hành. Cần bảo vệ máy tính bằng tài khoản người dùng riêng, khóa màn hình và không chia sẻ quyền truy cập trái phép.

## 4. Xây dựng cấu trúc cây thư mục Bookmark khoa học

Để tối ưu thời gian truy cập, cần tổ chức Bookmark theo từng nhóm công việc.

### 4.1. Cấu trúc Bookmark đề xuất

**Profile Personal**

- Học tập cá nhân
- Mạng xã hội
- Giải trí
- Email cá nhân
- Tài liệu tham khảo

**Profile Work**

- Công cụ quản trị
  - GreenLog
  - GitHub Enterprise
  - Dashboard quản trị
- Hệ thống học tập
  - Canvas LMS
  - Portal công ty
- Công cụ làm việc
  - Google Drive
  - Google Docs
  - Email công việc
- Tài liệu kỹ thuật
  - GitHub Docs
  - Tài liệu API
  - Tài liệu nội bộ

**Profile Sandbox**

- Môi trường kiểm thử
  - Sandbox Dashboard
  - Test API
  - Test Website
- Công cụ phát triển
  - Chrome DevTools
  - GitHub Test Repository
  - Công cụ kiểm tra giao diện
- Tài liệu thử nghiệm
  - Test Cases
  - Bug Reports
  - Test Documentation

### 4.2. Các bước tạo thư mục Bookmark

1. Mở Profile cần tổ chức Bookmark.
2. Nhấn tổ hợp phím Command + Shift + O trên macOS để mở Trình quản lý dấu trang.
3. Chọn biểu tượng ba chấm hoặc nhấn chuột phải vào khu vực Bookmark.
4. Chọn Add new folder.
5. Đặt tên thư mục theo nhóm công việc.
6. Tạo các thư mục con để phân loại chi tiết.
7. Kéo các trang web thường xuyên sử dụng vào đúng thư mục.

**Lợi ích:**

- Giảm thời gian tìm kiếm trang web.
- Tránh nhầm lẫn giữa tài khoản cá nhân và công việc.
- Quản lý tài liệu khoa học hơn.
- Tăng hiệu quả làm việc và giảm thao tác không cần thiết.

## 5. Quy trình đồng bộ hóa Cloud Sync để bảo vệ Bookmark khi đổi máy tính

Cloud Sync là cơ chế đồng bộ dữ liệu trình duyệt thông qua tài khoản đám mây, giúp người dùng có thể khôi phục Bookmark và một số cài đặt khi chuyển sang máy tính khác.

**Các bước thực hiện trên Google Chrome:**

**Bước 1: Đăng nhập tài khoản Google**

- Mở Chrome bằng Profile cần đồng bộ.
- Chọn biểu tượng Profile.
- Đăng nhập tài khoản Google tương ứng.
- Bật tính năng đồng bộ hóa.

**Bước 2: Thiết lập dữ liệu cần đồng bộ**

- Mở Settings.
- Chọn You and Google hoặc mục Sync and Google services tùy phiên bản.
- Kiểm tra mục quản lý dữ liệu đồng bộ.
- Bật đồng bộ Bookmarks.
- Chỉ bật đồng bộ mật khẩu, lịch sử và dữ liệu khác khi thực sự cần thiết.

**Bước 3: Kiểm tra đồng bộ**

- Tạo thử một Bookmark mới.
- Đợi trình duyệt hoàn tất đồng bộ.
- Kiểm tra Bookmark xuất hiện trên thiết bị khác đã đăng nhập đúng tài khoản và bật Sync.

**Bước 4: Khôi phục khi đổi máy tính**

- Cài đặt Google Chrome trên máy tính mới.
- Tạo Profile tương ứng.
- Đăng nhập đúng tài khoản Google đã sử dụng trước đó.
- Bật đồng bộ hóa.
- Chờ dữ liệu Bookmark được tải xuống.
- Kiểm tra lại cấu trúc thư mục.

**Lưu ý bảo mật:**

Không sử dụng chung một tài khoản đồng bộ cho cả Personal, Work và Sandbox nếu điều đó khiến dữ liệu bị trộn lẫn.

Đặc biệt, với Profile Work, cần tuân thủ chính sách đồng bộ dữ liệu của doanh nghiệp. Không đồng bộ mật khẩu hoặc thông tin nội bộ lên tài khoản cá nhân khi chưa được cho phép.

---

# PHẦN 3. KIỂM THỬ

## 6. Quy tắc sử dụng Guest Profile trên máy tính công cộng

Trong trường hợp phải sử dụng máy tính công cộng tại thư viện, phòng máy hoặc quầy dịch vụ, cần sử dụng Guest Profile để hạn chế lưu lại thông tin cá nhân trên thiết bị.

**Các quy tắc thực hiện:**

**1. Sử dụng chế độ Guest**

- Mở trình duyệt Chrome.
- Chọn biểu tượng Profile.
- Chọn Guest.
- Không đăng nhập tài khoản Google để đồng bộ dữ liệu cá nhân.

**2. Không lưu mật khẩu**

- Không chọn Save Password khi trình duyệt hỏi lưu mật khẩu.
- Không lưu thông tin đăng nhập trên máy tính công cộng.
- Không sử dụng tính năng tự động điền thông tin nhạy cảm.

**3. Hạn chế truy cập tài khoản quan trọng**

- Không truy cập tài khoản ngân hàng hoặc hệ thống quản trị quan trọng nếu không cần thiết.
- Không sử dụng máy tính công cộng để thực hiện giao dịch nhạy cảm.
- Không tải xuống tài liệu chứa thông tin cá nhân nếu không cần thiết.

**4. Đăng xuất sau khi sử dụng**

- Đăng xuất khỏi tất cả website đã truy cập.
- Đóng toàn bộ cửa sổ Guest.
- Không để lại tệp tải xuống hoặc dữ liệu cá nhân trên máy tính.

**5. Kiểm tra bảo mật sau khi sử dụng**

Nếu đã đăng nhập tài khoản quan trọng trên máy tính không đáng tin cậy, cần kiểm tra các phiên đăng nhập từ thiết bị khác và thu hồi những phiên bất thường.

**Lưu ý:** Guest Profile giúp không lưu lịch sử duyệt web và dữ liệu phiên sau khi kết thúc phiên Guest thông thường, nhưng không đảm bảo chống lại phần mềm giám sát, mã độc hoặc keylogger được cài trên máy tính công cộng.

## 7. Bảng kiểm thử và đánh giá kết quả

| STT | Trường hợp kiểm thử | Kết quả mong đợi |
|---|---|---|
| 1 | Đăng nhập tài khoản cá nhân trong Personal | Hoạt động bình thường |
| 2 | Đăng nhập GreenLog trong Work | Không ảnh hưởng Personal |
| 3 | Đăng nhập tài khoản Sandbox | Không ghi đè Session của Work |
| 4 | Mở Bookmark trong Work | Truy cập đúng các công cụ công việc |
| 5 | Đồng bộ Bookmark sang máy tính khác | Bookmark được khôi phục |
| 6 | Sử dụng Guest trên máy tính công cộng | Không lưu dữ liệu phiên sau khi đóng Guest |
| 7 | Trình chiếu màn hình bằng Work | Không hiển thị lịch sử và mật khẩu của Personal |

**Đánh giá:** Nếu tất cả trường hợp kiểm thử đạt kết quả mong đợi, mô hình 3 Profile đáp ứng yêu cầu phân tách môi trường làm việc, giảm xung đột phiên đăng nhập và hạn chế nguy cơ lộ thông tin cá nhân khi trình chiếu.

---

# 8. KẾT LUẬN

Qua bài tập, em hiểu được nguyên nhân xảy ra xung đột phiên đăng nhập khi sử dụng nhiều tài khoản trên cùng một trình duyệt.

Việc sử dụng chung một Profile có thể dẫn đến tình trạng ghi đè Cookie, Session và nhầm lẫn tài khoản. Để khắc phục, cần xây dựng các Profile độc lập gồm Personal, Work và Sandbox.

Bên cạnh đó, việc tổ chức Bookmark theo thư mục khoa học và sử dụng Cloud Sync giúp nâng cao hiệu quả làm việc, tiết kiệm thời gian khi truy cập các hệ thống thường xuyên sử dụng.

Đối với máy tính công cộng, Guest Profile là một giải pháp phù hợp để hạn chế lưu lại dữ liệu duyệt web, tuy nhiên người dùng vẫn cần chủ động bảo vệ tài khoản và tránh thực hiện các thao tác nhạy cảm trên thiết bị không đáng tin cậy.

**Bài học rút ra:** Phân tách Profile trình duyệt là một phương pháp đơn giản nhưng hiệu quả để quản lý nhiều tài khoản, hạn chế xung đột phiên đăng nhập và bảo vệ dữ liệu cá nhân trong môi trường làm việc số.

---

# 9. CẤU TRÚC REPOSITORY GITHUB

**Tên Repository đề xuất:**

`HCM-KS26-CNTT1_NhapMonCNTT_Session18_Ex04`

```text
HCM-KS26-CNTT1_NhapMonCNTT_Session18_Ex04/
│
├── README.md
│
├── docs/
│   ├── Phan-tich-Session-Conflict.md
│   ├── Trien-khai-3-Profile.md
│   ├── Cau-truc-Bookmark.md
│   └── Quy-tac-Guest-Profile.md
│
└── evidence/
    ├── profile-personal.png
    ├── profile-work.png
    ├── profile-sandbox.png
    └── bookmark-structure.png
```

**Nội dung README.md:**

```markdown
# SESSION 18 - EXERCISE 04
## SỰ CỐ XUNG ĐỘT PHIÊN ĐĂNG NHẬP TRÊN TRÌNH DUYỆT

- Họ và tên: Phạm Thành Đạo
- Lớp: HCM-KS26-CNTT1
- Môn học: Nhập môn CNTT

## 1. Mục tiêu
Khắc phục xung đột phiên đăng nhập bằng cách
phân tách Browser Profile.

## 2. Nội dung
- Phân tích Incognito và Dedicated Profile.
- Thiết lập 3 Profile độc lập.
- Tổ chức Bookmark theo thư mục.
- Triển khai Cloud Sync.
- Đề xuất quy tắc sử dụng Guest Profile.

## 3. Kết quả
Phân tách môi trường cá nhân, công việc và kiểm thử,
hạn chế nhầm lẫn tài khoản và rò rỉ dữ liệu.

## 4. Minh chứng
Xem thư mục evidence/.
```

