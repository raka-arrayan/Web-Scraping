# Web Scraping - CSS Knowledge

## Convert to CSS

* CSS (Cascading Style Sheets) adalah bahasa yang digunakan untuk mengatur tampilan atau desain dari halaman web yang dibuat dengan HTML.

| XPath | CSS | Ex. XPath | Ex. CSS |
| :--- | :--- | :--- | :--- |
| / | > (kecuali 1st char) | /html/body/div | html > body > div |
| // | blank (kecuali 1st char) | //div/h3//p | div > h3 p |
| [N] | :nth-of-type(N) | //div/p[1] | div > p:nth-of-type(1) |

---

## Seleksi Elemen & Atribut

* **Memanggil class dengan tanda "."**
  Contoh: `p.class-5` (mengambil semua paragraph dengan elemen **class-5**)

* **Apabila data berupa attribute dengan ":"**

| XPath | CSS | Ex. XPath | Ex. CSS |
| :--- | :--- | :--- | :--- |
| /@attr-name | ::attr(attr-name) | //div[@id="uid"]/a/@href | div#uid > a::attr(href) |

* **Apabila mau mengambil data berupa text**

| XPath | CSS | Ex. XPath | Ex. CSS |
| :--- | :--- | :--- | :--- |
| /text() | ::text | //div[@id="example-s"]/text() | div#example-s::text |

---

## Contoh Implementasi

**URL:** [https://books.toscrape.com/](https://books.toscrape.com/)

![image](https://hackmd.io/_uploads/Sy0rkyFIZe.png)

```python
data = {
    "judul": book.css("h3 a::attr(title)").get(),
    "harga": book.css("div.product_price p.price_color::text").get(),
    "rating": book.css("p.star-rating::attr(class)").get().split()[1]
}

![image](https://hackmd.io/_uploads/Sy0rkyFIZe.png)

URL : https://books.toscrape.com/

```py
data = {
            "judul": book.css("h3 a::attr(title)").get(),
            "harga": book.css("div.product_price p.price_color::text").get(),
            "rating": book.css("p.star-rating::attr(class)").get().split()[1]
        }
```

Penjelasan

```py
book.css("h3 a::attr(title)").get()
```
```
book → merepresentasikan satu <article class="product_pod">

h3 a → memilih tag <a> di dalam <h3>

::attr(title) → mengambil atribut title

.get() → mengambil satu nilai pertama
Hasil: "A Light in the Attic"
```

```py
book.css("div.product_price p.price_color::text").get()
```

```
div.product_price → container harga

p.price_color → elemen <p> yang menyimpan harga

::text → mengambil teks di dalam elemen
Hasil: "£51.77"
```

```py
book.css("p.star-rating::attr(class)").get().split()[1]
```

```
p.star-rating → elemen rating

::attr(class) → mengambil seluruh nilai class
(contoh: "star-rating Three")

.split()[1] → mengambil kata kedua sebagai rating
Hasil: "Three"
```











