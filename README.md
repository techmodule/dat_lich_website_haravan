# dat_lich_website_haravan

Hướng dẫn cấu hình đặt lịch website haravan

## I. Cài đặt:

### 1.1 Truy cập: https://admin.booking-app.vn/

### 1.2 Đăng nhập bằng tài khoản haravan của chủ shop, sau đấy cài đặt ứng dụng.

## II. Thiết lập:

### 2.1: Thiết lập theme:

#### 2.1.1: Tạo cài đặt thiết lập và kết nối ứng dụng:

- Vào website haravan
- Vào giao diện, chọn chỉnh sửa code, tìm config/settings_schema.json: Thêm đoạn code

```json
{
  "name": "Thiết lập đặt lịch",
  "settings": [
    {
      "type": "header",
      "content": "Cấu hình trang đặt lịch"
    },
    {
      "type": "text",
      "id": "booking_token",
      "label": "Mã bảo mật trang đặt lịch"
    },
    {
      "type": "text",
      "id": "booking_service_welcome",
      "label": "Lời chào mừng đặt lịch"
    },
    {
      "type": "text",
      "id": "booking_service_title",
      "label": "Tiêu đề trang đặt lịch"
    },
    {
      "type": "text",
      "id": "booking_service_guide",
      "label": "Hướng dẫn khách đặt lịch"
    }
  ]
},
```

- Tại config.settings.html thêm đoạn code vào cuối trang:

```html
<!-- End: 10. Trang cấu hình đặt lịch-->
<fieldset class="test">
    <legend>11. Cấu hình đặt lịch</legend>
    <div id="booking-settings" class="setnd col-sm-12">
        <div class="col-sm-12">
            <fieldset>
                <legend>1. Thiết lập kết nối</legend>
                <table>
                    <tr>
                        <td>
                            <label>Mã token kết nối ứng dụng</label>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <input type="text" name="booking_token" value=""/>
                        </td>

                        <td>
                            <a href="https://admin.booking-app.vn/haravan_shop.html" target="_blank">Lấy mã bảo mật
                                (token)</a>
                        </td>

                    </tr>


                </table>
            </fieldset>
            <fieldset>
                <legend>2. Thiết lập hiển thị</legend>
                <table>

                    <tr>
                        <td>
                            <label>Tiêu đề trang đặt lịch</label>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <input type="text" name="booking_service_title" value=""/>
                        </td>

                    </tr>
                    <tr>
                        <td>
                            <label>Câu chào mừng khách hàng tới đặt lịch</label>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <input type="text" name="booking_service_welcome" value=""/>
                        </td>

                    </tr>
                    <tr>
                        <td>
                            <label>Nội dung hướng dẫn khách đặt lịch</label>
                        </td>
                    </tr>
                    <tr>
                        <td>
                            <input type="text" name="booking_service_guide" value=""/>
                        </td>

                    </tr>


                </table>
            </fieldset>
        </div>
    </div>
</fieldset>
```

- Đã hoàn thành bước thiết lập cho theme.
- Tại link sau, copy "Mã bảo mật kết nối đặt lịch trên website": https://admin.booking-app.vn/haravan_shop.html
- Vào thiết lập theme, paste đoạn token vào Cấu hình đặt lịch/Thiểt lập kết nối/Mã kết nối, sau đấy bấm lưu.

#### 2.2 Thiết lập giao diện hiển thị.

##### 2.2.1 Tạo Snippets:

- Vào giao diện/ chỉnh sủa code, tại thư mục Snippets tạo các file sau.
  booking_grid_css.liquid

```html

<style>
    .hotline {
        border: none;
        color: #333333;
        padding: 1px 5px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 13px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .hotline_active, .hotline:hover {
        background-color: #FFFF00;
        border: none;
        color: #333333;
        padding: 5px 15px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .btn_loccation {
        background-color: #4CAF50;
        border: none;
        color: white;
        padding: 1px 5px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 13px;
        margin: 4px 2px;
        cursor: pointer;
        width: 50%;
    }

    /* Style the active class (and buttons on mouse-over) */
    .btn_loccation_active, .btn_loccation:hover {
        background-color: #FFFF00;
        border: none;
        color: #333333;
        padding: 5px 10px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 15px;
        margin: 4px 2px;
        cursor: pointer;
    }


    .btn_free_time {
        background-color: #4CAF50;
        width: 18%;
        border: none;
        color: white;
        padding: 1px 2px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    /* Style the active class (and buttons on mouse-over) */
    .free_time_active, .btn_free_time:hover {
        background-color: #FFFF00;
        border: none;
        color: #333333;
        padding: 2px 5px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .btn_date {
        background-color: #4CAF50;
        width: 18%;
        border: none;
        color: white;
        padding: 1px 2px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 10px;
        margin: 4px 2px;
        cursor: pointer;
    }

    /* Style the active class (and buttons on mouse-over) btn_date date_active*/
    .btn_date_active, .btn_date:hover {
        background-color: #FFFF00;
        border: none;
        color: #333333;
        padding: 2px 5px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 11px;
        margin: 4px 2px;
        cursor: pointer;
    }

    /* Clear floats after the columns */
    .btnRow:after {
        content: "";
        display: table;
        clear: both;
    }

    .service_header {
        background-color: #333333;
        width: 100%;
        border-bottom: 1px solid #666;
        color: white;
        text-align: left;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        cursor: pointer;
        padding-left: 5px;
    }

    /* Style the active class (and buttons on mouse-over) */
    .btn_wrap {

        width: 30%;
        padding: 1px 2px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .btn_variant {
        background-color: #4CAF50;
        width: 30%;
        border: none;
        color: white;
        padding: 1px 2px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    /* Style the active class (and buttons on mouse-over) */
    .variant_active, .btn_variant:hover {
        background-color: #FFFF00;
        border: none;
        color: #333333;
        padding: 5px 15px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .card {
        width: 19%;
        border: none;
        color: white;
        padding: 1px 2px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .price {
        color: grey;
        font-size: 22px;
    }

    .card button {
        border: none;
        outline: 0;
        padding: 12px;
        color: white;
        background-color: #000;
        text-align: center;
        cursor: pointer;
        width: 90%;
        font-size: 18px;
    }

    .card button:hover {
        opacity: 0.7;
    }

    .cardMobile {
        width: 45%;
        border: none;
        color: white;
        padding: 1px 2px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .price {
        color: grey;
        font-size: 22px;
    }

    .cardMobile button {
        border: none;
        outline: 0;
        padding: 12px;
        color: white;
        background-color: #000;
        text-align: center;
        cursor: pointer;
        width: 90%;
        font-size: 18px;
    }

    .cardMobile button:hover {
        opacity: 0.7;
    }

    .btn_book {
        background-color: #4CAF50;
        width: 30%;
        border: none;
        color: white;
        padding: 1px 2px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    /* Style the active class (and buttons on mouse-over) */
    .btn_book_active, .btn_book:hover {
        background-color: #666;
        border: none;
        color: white;
        padding: 2px 5px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }

    .note {
        width: 100%;
        height: 100px;
    }

</style>
<style>
    /*the container must be positioned relative:*/
    .location-select {
        position: relative;
        font-family: Arial;
    }

    .location-select select {
        display: none; /*hide original SELECT element:*/
    }

    .select-selected {
        background-color: DodgerBlue;
    }

    /*style the arrow inside the select element:*/
    .select-selected:after {
        position: absolute;
        content: "";
        top: 14px;
        right: 10px;
        width: 0;
        height: 0;
        border: 6px solid transparent;
        border-color: #fff transparent transparent transparent;
    }

    /*point the arrow upwards when the select box is open (active):*/
    .select-selected.select-arrow-active:after {
        border-color: transparent transparent #fff transparent;
        top: 7px;
    }

    /*style the items (options), including the selected item:*/
    .select-items div, .select-selected {
        color: #ffffff;
        padding: 8px 16px;
        border: 1px solid transparent;
        border-color: transparent transparent rgba(0, 0, 0, 0.1) transparent;
        cursor: pointer;
        user-select: none;
    }

    /*style items (options):*/
    .select-items {
        position: absolute;
        background-color: DodgerBlue;
        top: 100%;
        left: 0;
        right: 0;
        z-index: 99;
    }

    /*hide the items when the select box is closed:*/
    .select-hide {
        display: none;
    }

    .select-items div:hover, .same-as-selected {
        background-color: rgba(0, 0, 0, 0.1);
    }
</style>
```

booking_select_css.liquid

````html

<style>
    /*the container must be positioned relative:*/
    .location-select {
        position: relative;
        font-family: Arial;
    }

    .location-select select {
        display: none; /*hide original SELECT element:*/
    }

    .location-select-selected {
        background-color: DodgerBlue;
    }

    /*style the arrow inside the select element:*/
    .location-select-selected:after {
        position: absolute;
        content: "";
        top: 14px;
        right: 10px;
        width: 0;
        height: 0;
        border: 6px solid transparent;
        border-color: #fff transparent transparent transparent;
    }

    /*point the arrow upwards when the select box is open (active):*/
    .location-select-selected.location-select-arrow-active:after {
        border-color: transparent transparent #fff transparent;
        top: 7px;
    }

    /*style the items (options), including the selected item:*/
    .location-select-items div, .location-select-selected {
        color: #ffffff;
        padding: 8px 16px;
        border: 1px solid transparent;
        border-color: transparent transparent rgba(0, 0, 0, 0.1) transparent;
        cursor: pointer;
        user-select: none;
    }

    /*style items (options):*/
    .location-select-items {
        position: absolute;
        background-color: DodgerBlue;
        top: 100%;
        left: 0;
        right: 0;
        z-index: 99;
    }

    /*hide the items when the select box is closed:*/
    .location-select-hide {
        display: none;
    }

    .location-select-items div:hover, .same-as-selected {
        background-color: rgba(0, 0, 0, 0.1);
    }

    /*the container must be positioned relative:*/
    .free-time-select {
        position: relative;
        font-family: Arial;
    }

    .free-time-select select {
        display: none; /*hide original SELECT element:*/
    }

    .free-time-select-selected {
        background-color: DodgerBlue;
    }

    /*style the arrow inside the select element:*/
    .free-time-select-selected:after {
        position: absolute;
        content: "";
        top: 14px;
        right: 10px;
        width: 0;
        height: 0;
        border: 6px solid transparent;
        border-color: #fff transparent transparent transparent;
    }

    /*point the arrow upwards when the select box is open (active):*/
    .free-time-select-selected.free-time-select-arrow-active:after {
        border-color: transparent transparent #fff transparent;
        top: 7px;
    }

    /*style the items (options), including the selected item:*/
    .free-time-select-items div, .free-time-select-selected {
        color: #ffffff;
        padding: 8px 16px;
        border: 1px solid transparent;
        border-color: transparent transparent rgba(0, 0, 0, 0.1) transparent;
        cursor: pointer;
        user-select: none;
    }

    /*style items (options):*/
    .free-time-select-items {
        position: absolute;
        background-color: DodgerBlue;
        top: 100%;
        left: 0;
        right: 0;
        z-index: 99;
    }

    /*hide the items when the select box is closed:*/
    .free-time-select-hide {
        display: none;
    }

    .free-time-select-items div:hover, .same-as-selected {
        background-color: rgba(0, 0, 0, 0.1);
    }
</style>

````

booking_grid_js.liquid

```html

<script>
    function makeListByItemPerRow(itemList, itemPerRow) {
        let list_len = 100;
        if (itemList.isArray) {
            list_len = itemList.length;
        }
        var _mod = list_len % itemPerRow;
        var maxlength = (list_len - (list_len % itemPerRow));
        if (_mod > 0) {
            maxlength = maxlength + 1;
        }
        var newlist = [];
        for (var i = 0; i < maxlength; i++) {
            var start = i * itemPerRow;
            var end = (i + 1) * itemPerRow;
            if (end > maxlength) {
                end = itemList.length;
            }
            let element = itemList.slice(start, end);
            if (element.length > 0) {
                newlist.push(element);
            }

        }
        return newlist;
    }

    function clickFreeTime(i) {
        let id_name = "free_time_item_" + i;
        var click_button = document.getElementById(id_name);
        //console.log(click_button);
        var current = document.getElementsByClassName("free_time_active");
        current[0].className = current[0].className.replace(" free_time_active", "");
        click_button.className += " free_time_active";
        //alert(i);

    }

    function renderDate(date_to_change) {
        let yourDate = new Date(date_to_change)
        return yourDate.toISOString().split('T')[0]
    }

    function makeDateList() {
        var date_render = '<div class="btnRow">';
        for (var i = 0; i < 10; i++) {
            date = new Date();
            date.setDate(date.getDate() + i);
            var string_date = renderDate(date);
            var date_element = '<button value="' + string_date + '" onclick="clickDate(' + i + ')" id="date_' + i + '"class="btn_date" >' + string_date + '</button>';
            if (i === 0) {
                date_element = '<button value="' + string_date + '" onclick="clickDate(' + i + ')" id="date_' + i + '"class="btn_date btn_date_active" >' + string_date + '</button>';
            }
            date_render = date_render + date_element;
        }
        date_render = date_render + '</div>'
        document.getElementById("date").innerHTML = date_render;
    }

    async function clickDate(date_id) {
        document.getElementById("free_time_render").innerHTML = '<h3>Đang tải dữ liệu</h3>';
        let id_date = "date_" + date_id;
        var date_click_button = document.getElementById(id_date);
        //console.log(date_click_button);
        var date_current = document.getElementsByClassName("btn_date_active");
        date_current[0].className = date_current[0].className.replace(" btn_date_active", "");
        date_click_button.className += " btn_date_active";
        await VariantFreeTime();
    }

    function formatDate(date) {
        var d = new Date(date),
                month = '' + (d.getMonth() + 1),
                day = '' + d.getDate(),
                year = d.getFullYear();

        if (month.length < 2)
            month = '0' + month;
        if (day.length < 2)
            day = '0' + day;

        return [year, month, day].join('-');
    }

    async function VariantFreeTime() {
        var free_time_render = '<h2>Đang tải dữ liệu</h2>';
        document.getElementById("free_time_render").innerHTML = free_time_render;
        let dates = document.getElementById("date");
        var date = dates.getElementsByClassName("btn_date_active")[0].value;
        var str_date = formatDate(date);
        //alert(str_date);
        var variant_id = $('#product-select').val()
        var new_url = "https://admin.booking-app.vn/api/haravan/variant.json";
        var token = "{{settings.booking_token}}";
        let new_free_time_url = new_url + '?variant_id=' + variant_id + '&date=' + str_date;
        //alert(new_free_time_url);
        var otpions = {
            method: "GET",
            mode: 'cors', // no-cors, *cors, same-origin
            cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
            credentials: 'same-origin', // include, *same-origin, omit
            headers: {
                Authorization: "Bearer " + token,
                'Content-Type': 'application/json',
                "Access-Control-Allow-Origin": "*",
            }
        }
        let response = await fetch(new_free_time_url, otpions);
        free_time_render = '<h2>Bắt đầu hiển thị thời gian rảnh</h2>';
        document.getElementById("free_time_render").innerHTML = free_time_render;
        let repsone_json = await response.json();
        //alert("True")
        if (repsone_json.status) {
            //alert("True")
            free_time_render = '';
            document.getElementById("free_time_render").innerHTML = free_time_render;
            let data = repsone_json.data;
            if (data !== null && typeof data.free_time !== "undefined" && data.free_time !== null) {
                let free_time = data.free_time;
                if (free_time.length === 0) {
                    free_time_render = '<h2>Ngày này đã kín lịch, vui lòng chọn ngày khác</h2>'
                } else {
                    //console.log(free_time);
                    var free_time_grid = makeListByItemPerRow(free_time, 5);
                    let i = 0
                    for (var free_time_row of free_time_grid) {
                        var free_time_row_render = '<div class="btnRow">';
                        for (var item of free_time_row) {
                            var time_hour = item.substring(11, 16);

                            var free_time_element = '<button value="' + item + '" onclick="clickFreeTime(' + i + ')" id="free_time_item_' + i + '"class="btn_free_time" >' + time_hour + '</button>';
                            if (i === 0) {

                                free_time_element = '<button value="' + item + '" onclick="clickFreeTime(' + i + ')" id="free_time_item_' + i + '"class="btn_free_time free_time_active" >' + time_hour + '</button>';
                            }
                            free_time_row_render = free_time_row_render + free_time_element;
                            i = i + 1;
                        }
                        i = i + 1;
                        free_time_row_render = free_time_row_render + '</div>'
                        free_time_render = free_time_render + free_time_row_render;

                    }
                }

            } else {
                free_time_render = '<h2>Chi nhánh chưa thiết lập đặt  lịch</h2>'
            }

            document.getElementById("free_time_render").innerHTML = free_time_render;
        } else {
            alert(response.message);
        }
        return repsone_json;
    }

    function formToJson(formData) {
        var object = {};
        formData.forEach((value, key) => {
            // Reflect.has in favor of: object.hasOwnProperty(key)
            if (!Reflect.has(object, key)) {
                object[key] = value;
                return;
            }
            if (!Array.isArray(object[key])) {
                object[key] = [object[key]];
            }
            object[key].push(value);
        });
        return object;
    }

    async function BookNow() {
        //alert(variant_id);
        let book_url = "https://admin.booking-app.vn/api/haravan/book.json"
        let phone = document.getElementById("phone").value;
        let email = document.getElementById("email").value;
        let last_name = document.getElementById("last_name").value;
        if (phone === null || phone.length < 10 || last_name === "") {
            if (phone === null || phone.length < 10) {
                alert("Vui lòng nhập số điện thoại");
            } else {
                alert("Vui lòng nhập tên bạn");
            }
            window.scrollTo({top: 0, behavior: 'smooth'});
        } else {
            //document.getElementById(button_id).innerHTML = '<h6>Đang đặt lịch</h6>';
            let free_times = free_time_render.getElementsByClassName("free_time_active");
            let start_time = null;
            if (free_times.length === 0) {
                alert("Ngày bạn chọn đã kín hoặc khóa lịch!\nVui lòng chọn ngày khác");
                window.scrollTo({top: 0, behavior: 'smooth'});
            } else {
                start_time = free_time_render.getElementsByClassName("free_time_active")[0].value;
                //bookingAppForm
                let bookingAppPostForm = new FormData(bookingAppForm);
                var variant_id = $('#product-select').val();
                let data = formToJson(bookingAppPostForm);
                data.variant_id = variant_id;
                data.start_time = start_time;
                var token = "{{settings.booking_token}}";
                //var token = "IZFSTFGTHTFRFL35ZNYIY2UJ22TYVOVW94O3P1KPVDT4MP5AHB1G5TBQULXI4AWN";
                var otpions = {
                    method: "POST",
                    mode: 'cors', // no-cors, *cors, same-origin
                    cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
                    credentials: 'same-origin', // include, *same-origin, omit
                    headers: {
                        Authorization: "Bearer " + token,
                        'Content-Type': 'application/json',
                        "Access-Control-Allow-Origin": "*",
                    },
                    body: JSON.stringify(data),
                }
                let book_button_render = '<h3>Đang đặt lịch</h3>';
                document.getElementById("book_button_render").innerHTML = book_button_render;
                await fetch(book_url, otpions)
                        .then(response => response.json())
                        .then(result => {
                            //alert(result.message);

                            if (result.status === true) {
                                book_button_render = '<h3>ĐẶT LỊCH THÀNH CÔNG</h3><button class="add-to-cartProduct button dark btn-addtocart addtocart-modal" type="button" id="book-now name="add" onclick="BookNow()">Đặt thêm lịch khác</button>';

                                //alert("Đặt lịch thành công");
                            } else {
                                //alert("Đặt  lịch thất bại");
                                book_button_render = '<h3>Đặt lịch THẤT BẠI, tải lại trang nếu muốn đặt lịch khác</h3>';
                            }
                            document.getElementById("book_button_render").innerHTML = book_button_render;
                            VariantFreeTime();
                            console.log('Success:', result);
                        })
                        .catch(error => {
                            book_button_render = '<h3>Đặt lịch THẤT BẠI, tải lại trang nếu muốn đặt lịch khác</h3>';
                            document.getElementById("book_button_render").innerHTML = book_button_render;
                            VariantFreeTime();
                            alert("Xảy ra lỗi khi đặt lịch, vui lòng liên hệ shop để đặt" + error.toString());
                            window.scrollTo({top: 0, behavior: 'smooth'});

                        });
            }
        }

    }

    window.onload = async function () {
        document.getElementById("free_time_render").innerHTML = '<h3>Đang tải dữ liệu</h3>';
        await makeDateList();
        await VariantFreeTime();
    };

</script>
```

booking_select_js.liquid

```html

<script>

    $(document).ready(function () {
        var now = new Date();

        var day = ("0" + now.getDate()).slice(-2);
        var month = ("0" + (now.getMonth() + 1)).slice(-2);

        var today = now.getFullYear() + "-" + (month) + "-" + (day);


        $('#booking_date_string').val(today);
    });

    async function onChangeDate() {
        await VariantFreeTime()
    }

</script>
<script>
    function formToJson(formData) {
        var object = {};
        formData.forEach((value, key) => {
            // Reflect.has in favor of: object.hasOwnProperty(key)
            if (!Reflect.has(object, key)) {
                object[key] = value;
                return;
            }
            if (!Array.isArray(object[key])) {
                object[key] = [object[key]];
            }
            object[key].push(value);
        });
        return object;
    }

    async function TestBook() {
        var start_time = document.getElementById('booking_free_time').value;
        //let start_time = $('#booking_free_time').val();

        let booking_date_string = $('#booking_date_string').val();
        start_time = booking_date_string + " " + start_time;
        alert(start_time);
    }

    async function BookNow() {
        //alert(variant_id);
        let book_url = "https://admin.booking-app.vn/api/haravan/book.json"
        let phone = document.getElementById("phone").value;
        let email = document.getElementById("email").value;
        let last_name = document.getElementById("last_name").value;
        if (phone === null || phone.length < 10 || last_name === "") {
            if (phone === null || phone.length < 10) {
                alert("Vui lòng nhập số điện thoại");
            } else {
                alert("Vui lòng nhập tên bạn");
            }
            window.scrollTo({top: 0, behavior: 'smooth'});
        } else {
            //document.getElementById(button_id).innerHTML = '<h6>Đang đặt lịch</h6>';
            //let free_times = free_time_render.getElementsByClassName("free_time_active");
            let start_time = $('#booking_free_time').val()
            let booking_date_string = $('#booking_date_string').val();
            start_time = booking_date_string + " " + start_time;
            if (start_time === 0 || start_time == "0") {
                alert(start_time);
            } else {
                //bookingAppForm
                let bookingAppPostForm = new FormData(bookingAppForm);
                //var variant_id = $('#product-select').val();
                //var date = document.getElementById("booking_date_string").value;
                var variant_id = $('#booking_location').val()
                let data = formToJson(bookingAppPostForm);
                data.variant_id = variant_id;
                data.start_time = start_time;
                var token = "{{ settings.booking_token }}";
                //var token = "IZFSTFGTHTFRFL35ZNYIY2UJ22TYVOVW94O3P1KPVDT4MP5AHB1G5TBQULXI4AWN";
                var otpions = {
                    method: "POST",
                    mode: 'cors', // no-cors, *cors, same-origin
                    cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
                    credentials: 'same-origin', // include, *same-origin, omit
                    headers: {
                        Authorization: "Bearer " + token,
                        'Content-Type': 'application/json',
                        "Access-Control-Allow-Origin": "*",
                    },
                    body: JSON.stringify(data),
                }
                let book_button_render = '<h3>Đang đặt lịch</h3>';
                document.getElementById("book_button_render").innerHTML = book_button_render;
                await fetch(book_url, otpions)
                        .then(response => response.json())
                        .then(result => {
                            //alert(result.message);

                            if (result.status === true) {
                                book_button_render = '<h3>ĐẶT LỊCH THÀNH CÔNG</h3><button class="add-to-cartProduct button dark btn-addtocart addtocart-modal" type="button" id="book-now name="add" onclick="BookNow()">Đặt thêm lịch khác</button>';

                                //alert("Đặt lịch thành công");
                            } else {
                                //alert("Đặt  lịch thất bại");
                                book_button_render = '<h3>Đặt lịch THẤT BẠI, tải lại trang nếu muốn đặt lịch khác</h3>';
                            }
                            document.getElementById("book_button_render").innerHTML = book_button_render;
                            VariantFreeTime();
                            console.log('Success:', result);
                        })
                        .catch(error => {
                            book_button_render = '<h3>Đặt lịch THẤT BẠI, tải lại trang nếu muốn đặt lịch khác</h3>';
                            document.getElementById("book_button_render").innerHTML = book_button_render;
                            VariantFreeTime();
                            alert("Xảy ra lỗi khi đặt lịch, vui lòng liên hệ shop để đặt" + error.toString());
                            window.scrollTo({top: 0, behavior: 'smooth'});

                        });
            }
        }

    }

    async function VariantFreeTime() {
        let repsone_json;
        var free_time_status = "<h6>Đang tải dữ liệu</h6>";
        document.getElementById("free_time_status").innerHTML = free_time_status;
        var booking_free_time = '<option value="0">Tải dữ liệu</option>';
        document.getElementById("booking_free_time").innerHTML = booking_free_time;
        var date = document.getElementById("booking_date_string").value;
        //alert(str_date);
        var variant_id = $('#booking_location').val()
        if (variant_id === 0 || variant_id === "0") {
            booking_free_time = '<option value="0">Chưa chọn chi nhánh</option>';
            document.getElementById("booking_free_time").innerHTML = booking_free_time
        } else {
            var token = "{{ settings.booking_token }}";
            //alert(token);
            var new_url = "https://admin.booking-app.vn/api/haravan/variant.json";
            //var token = "IZFSTFGTHTFRFL35ZNYIY2UJ22TYVOVW94O3P1KPVDT4MP5AHB1G5TBQULXI4AWN";
            let new_free_time_url = new_url + '?variant_id=' + variant_id + '&date=' + date;
            //alert(new_free_time_url);
            var otpions = {
                method: "GET",
                mode: 'cors', // no-cors, *cors, same-origin
                cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached

                headers: {
                    Authorization: "Bearer " + token,
                    'Content-Type': 'application/json',
                }
            }
            let response = await fetch(new_free_time_url, otpions);
            repsone_json = await response.json();
            //alert("True")
            if (repsone_json.status) {
                free_time_status = "<h6>Lấy dữ liệu thành công</h6>";
                document.getElementById("free_time_status").innerHTML = free_time_status;
                let data = repsone_json.data;
                if (data !== null && typeof data.free_time !== "undefined" && data.free_time !== null) {
                    free_time_status = "<h6>Có thời gian rảnh</h6>";
                    document.getElementById("free_time_status").innerHTML = free_time_status;
                    let free_time = data.free_time;
                    if (free_time.length === 0) {
                        free_time_status = "<h3>Kín lịch ngày này</h3>";
                        document.getElementById("free_time_status").innerHTML = free_time_status;
                        booking_free_time = '<option value="0">Kín lịch ngày này</option>';
                        document.getElementById("booking_free_time").innerHTML = booking_free_time;
                    } else {
                        booking_free_time = '<option value="0">Chọn thời gian</option>';
                        for (var item of free_time) {
                            booking_free_time += "<option value=" + item.substring(11, 16) + ">" + item.substring(11, 16) + "</option>";
                            //option = '<option value="' + item + '">' + item + '</option>\n';
                            //booking_free_time = booking_free_time + option;
                        }
                        console.log(booking_free_time);
                        document.getElementById("booking_free_time").innerHTML = booking_free_time;
                    }
                } else {
                    booking_free_time = '<option value="0">Chi nhánh không thiết lập đặt lịch</option>';
                    document.getElementById("booking_free_time").innerHTML = booking_free_time;
                }


            } else {
                free_time_status = "<h3>Lỗi kết nối server</h3>";
                document.getElementById("free_time_status").innerHTML = free_time_status;
                booking_free_time = '<option value="0">Lỗi kết nối server</option>';
                document.getElementById("booking_free_time").innerHTML = booking_free_time;
            }
        }
        return repsone_json;
    }


</script>
```

booking_render_grid.liquid
```html
{% include 'booking_grid_js' %}
{% include 'booking_grid_css' %}
<div class="customize-product-slider clearfix">
    <h1 itemprop="name">Hiển thị kiểu click</h1>
    <div class="pro-brand">
        <span class="title">Chọn ngày đặt lịch</span>
    </div>
    <div id="date" class="pro-short-desc">

    </div>
    <div class="pro-content-head clearfix">
        <div class="pro-brand">
            <span class="title">Chọn giờ bắt đầu:</span>
        </div>
    </div>

    <div id="free_time_render">

    </div>
</div>
<div class="contact-form">
    <form id="bookingAppForm">
        <div id="book_sucess"></div>
        <div class="title-bl">
            <h2>Thông tin của bạn</h2>
        </div>
        <div id="customer_infomations">
            <div class="row">
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input required type="text" id="first_name"
                               name="first_name" placeholder="Họ">
                    </div>
                </div>
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input required type="text" id="last_name"
                               name="last_name" placeholder="Tên">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input required type="phone" id="phone" name="phone"
                               placeholder="Di động">


                    </div>
                </div>
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input type="email" id="email" name="email"
                               placeholder="Nhập email">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-sm-12 col-xs-12">
                    <div class="input-group">
                        <div class="pro-price clearfix">
                            <input height="120" class="note" type="text" id="note"
                                   name="note"
                                   placeholder="Ghi chú nếu cần thiết"></div>
                        <h6>
                            Kéo xuống và bấm vào từng dịch vụ bạn muốn đặt lịch
                        </h6>
                        <div id="book_button_render">
                            <button type="button" id="book-now"
                                    {% unless product.available %}disabled{% endunless %}
                                    class="{% unless product.available %}disabled{% endunless %} add-to-cartProduct button dark btn-addtocart addtocart-modal {{ className }}"
                                    name="add" onclick="BookNow()">Đặt ngay
                            </button>
                        </div>

                    </div>
                </div>

            </div>
    </form>
</div>
</div>
```
booking_render_select.liquid
```html
{% include 'booking_select_css' %}
{% include 'booking_select_js' %}
<div class="customize-product-slider clearfix">
    {% if settings.booking_service_title!='' %}
        {{ settings.booking_service_title }}
    {% else %}
        <h1 itemprop="name">CHÀO MỪNG TỚI {{ shop.name }}</h1>
    {% endif %}

    <div class="pro-brand">
        {% if settings.booking_service_welcome!='' %}
            {{ settings.booking_service_welcome }}
        {% else %}
            <span class="title">HÃY ĐẶT LỊCH TRƯỚC</span>
        {% endif %}

        <div id="free_time_status"></div>
    </div>
    <div class="row">
    <div class="contact-form">
        <div class="col-sm-4 col-xs-12">
            <h5>Chi nhánh</h5>
            <div id="booking_location_select"  class="btn">
                <select id="booking_location"  onchange="if (this.selectedIndex) VariantFreeTime();">
                    <option value="0">Chọn chi nhánh</option>
                    {% for item in product.variants %}
                        <option value="{{ item.id }}">{{ item.option1 }}</option>
                    {% endfor %}
                </select>
            </div>
        </div>
        <div class="col-sm-4 col-xs-12">
            <h5>Ngày</h5>
            <div  class="btn">
                <input onchange="onChangeDate(event);" type="date"
                       id="booking_date_string" name="booking_date_string"/>
            </div>
        </div>
        <div class="col-sm-4 col-xs-12">
            <h5>Thời gian rảnh</h5>
            <div id="free_time_select" class="btn">
                <select id="booking_free_time" onchange="TestBook()">
                    <option value="0">Chọn thời gian</option>
                </select>

            </div>
        </div>

    </div>
    </div>
</div>
<div class="contact-form">
    <form id="bookingAppForm">
        <div id="book_sucess"></div>
        <div class="title-bl">
            <h2>Thông tin của bạn</h2>
        </div>
        <div id="customer_infomations">
            <div class="row">
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input required type="text" id="first_name"
                               name="first_name" placeholder="Họ">
                    </div>
                </div>
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input required type="text" id="last_name"
                               name="last_name" placeholder="Tên">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input required type="phone" id="phone" name="phone"
                               placeholder="Di động">


                    </div>
                </div>
                <div class="col-sm-6 col-xs-12">
                    <div class="input-group">
                        <input type="email" id="email" name="email"
                               placeholder="Nhập email">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-sm-12 col-xs-12">
                    <div class="input-group">
                        <div class="pro-price clearfix">
                            <input height="120" class="note" type="text" id="note"
                                   name="note"
                                   placeholder="Ghi chú nếu cần thiết"></div>
                        {% if settings.booking_service_guide!='' %}
                            {{ settings.booking_service_guide }}
                        {% else %}
                            <h6>
                                Kéo xuống và bấm vào từng dịch vụ bạn muốn đặt lịch
                            </h6>
                        {% endif %}

                        <div id="book_button_render">
                            <button type="button" id="book-now"
                                    {% unless product.available %}disabled{% endunless %}
                                    class="{% unless product.available %}disabled{% endunless %} add-to-cartProduct button dark btn-addtocart addtocart-modal {{ className }}"
                                    name="add" onclick="BookNow()">Đặt ngay
                            </button>
                        </div>

                    </div>
                </div>

            </div>
    </form>
</div>
</div>
```
##### 2.2.1 Tạo Giao diện:
- Vào giao diện/ chỉnh sủa code, tại thư mục Giao diện tạo các file sau bằng cách copy product.liqid
product.booking-grid.liquid. Sau đấy copy đoạn code này vào vị trí cần hiển thị.
```html
{% include "booking_render_grid"%}
```
product.booking-select.liquid. Sau đấy copy đoạn code này vào vị trí cần hiển thị.
```html
{% include "booking_render_select"%}
```
