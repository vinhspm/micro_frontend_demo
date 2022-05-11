
Hướng dẫn cài đặt

Trong demo này, chúng ta sẽ sử dụng Webpack 5, trong bản release mới nhất nó đã giới thiệu một advanced API là Module Federation. Điều này giúp chúng ta dễ dàng phát triển được Micro Frontend. Ngoài ra, chúng ta sẽ dùng Angular v11 (thời điểm này đang là RC) để tạo các app.

Chuẩn bị

Đầu tiên, chúng ta cần tạo một shell app bằng lệnh sau.

Sau khi tạo xong project, chúng ta sẽ tạo thêm 2 application nữa: 1 cho service1, 1 cho service2.

Ngoài ra, chúng ta cần dùng đến custom webpack config nên chúng ta cần install thêm một package là @angular-builders/custom-webpack.





Bật tính năng Module Federation

Đây là tính năng hỗ trợ build các module một cách độc lập. Để bật được tính năng này chúng ta cần sử dụng custom webpack như sau: ta tạo ra các file webpack config, sau đó thay thế builder mặc định ở trong angular.json.
Chúng ta tạo ra 2 files webpack.config.js và webpack.prod.config.js để sử dụng cho 2 môi trường là development và production. Sau đó chúng ta sẽ thay thế trong angular.json

Thay @angular-devkit/build-angular bằng @angular-builders/custom-webpack. 
Thêm config của webpack mà chúng ta vừa tạo
Config Shell
Chúng ta cần config shell như sau để bật Module Federation:
		
		
		Shell sẽ chạy ở port 5200, và chúng ta cần một unique name cho mỗi app. Ngoài ra, do shell sẽ trỏ đến 2 app remote, nên bạn sẽ thấy chúng ta config tương ứng cho 2 app remote luôn ở đây. Do đang dùng các micro app bằng Angular, nên chúng ta có thể share các phần code, như config phía trên, chúng ta đã share 3 packages. Giờ đây chúng ta có thể thêm config cho routing của shell để trỏ đến 2 micro app kia
		



		
Khởi chạy ứng dụng


Chạy cả 3 ứng dụng với 3 lệnh sau
 npm run start:shell
 npm run start:service1
 npm run start:service2


