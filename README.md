# bsModal
Tạo Bootstrap Modal thật dễ dàng

## Cú pháp
Cú pháp để tạo Bootstrap Modal, cũng giống như định nghĩa hàm, gồm hai cách sau:
- Tạo modal vô danh, modal sẽ hiển thị ngay lập tức khi được tạo.
```js
bsModal(optional);
```
- Tạo modal với tên duy nhất, sẽ chỉ hiển thị khi được gọi. Có thể gọi lại ở nhiều nơi.
```js
bsModal(name, optional);
```
Các tham số
- name - *Tên của modal.*
- optional - *Một đối tượng định nghĩa các thành phần của modal.*
  - title - *Tiêu đề của modal.*
  - body - *Nội dụng HTML phần thân của modal.*
  - footer - *Nội dung HTML phần chân của modal.*
  - size - *Kích thước của modal, các giá trị có thể là:*
    - "sm" - *nhỏ*
    - "md" - *thường*
    - "lg" - *lớn*
    - number - *thiết lập chiều rộng theo px*
  - js - *Phương thức JavaScript tương tác với modal. Tham số thứ nhất (`scope`) là một biến dùng để chọn các thành phần trong modal, các tham số tiếp theo là các đối số truyền vào khi gọi modal với tên modal.*

## Sử dụng
Tạo modal với tiêu đề, nội dung là dòng chữ "Hello World!", với một nút OK ở phía dưới. Thêm class cho thẻ `p` với tên class bắt đầu bằng ký tự `$`. Các thẻ với class có tên bắt đầu bằng `$` có thể được chọn như một thuộc tính của biến `scope` trong phương thức `js`, và trả về một đối tượng jQuery.
```js
bsModal({
  title: "Thông báo",
  body: `<p class="$message">Hello World!</p>`,
  footer: `<button>OK</button>`,
  js(scope) {
    scope.message.html("Hello Universe!");
  }
});
```
Có thể tạo modal trên với một tên duy nhất, sau đó gọi theo cú pháp `bsModal.tenCuaModal()`. Khi gọi có thể truyền các đối số tương ứng với các tham số trong phương thức `js`, các tham số tiếp theo sau `scope`.
```js
bsModal("myModal", {
  title: "Thông báo",
  body: `<p class="$message">Hello World!</p>`,
  footer: `<button>OK</button>`,
  js(scope, text) {
    scope.message.html(text);
  }
});

bsModal.myModal("Hello Universe!");
```

## Tải về
**Phiên bản 1.00** (17/09/2017)
- [bsmodal.min.js](https://cdn.rawgit.com/tiencoffee/bsmodal/14bb386d/bsmodal.min.js)&emsp;&emsp;&emsp;—&emsp;&emsp;&emsp;2.38 KB

## Ví dụ khác
```js
bsModal({
  title: "Login",
  body: `
    <label>Username: </label>
    <input type="text" class="form-control $usr">
    <br>
    <label>Password: </label>
    <input type="password" class="form-control $pwd">
  `,
  footer: `
    <button class="btn btn-primary $btnLogin">Login</button>
  `,
  js($0) {
    $0.btnLogin.click(event => {
      if ($0.usr.val() === "") {
        bsModal.alert("Please enter your username!");
      }
      else if ($0.pwd.val() === "") {
        bsModal.alert("Please enter your password!");
      }
      else {
        // Login success...
      }
    });
  }
});
```
