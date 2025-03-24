#  def url_olustur_v2():
    gazeteler = input("Gazete isimlerini aralarına virgül koyarak yazın: ").split(",")
    kategoriler = input("Kategorileri aralarına virgül koyarak yazın: ").split(",")
    tarihler = input("Tarihleri (GG-AA-YYYY) formatında virgül ile ayırarak yazın: ").split(",")

    dosya_adi = "olusan_url.txt"

    with open(dosya_adi, "w") as dosya:
        for gazete in gazeteler:
            gazete_adi = gazete.strip().lower()  # Küçük harfe çevir ve boşlukları temizle
            base_url = f"https://{gazete_adi}.com.tr"

            for kategori in kategoriler:
                kategori_adi = kategori.strip().replace(" ", "-")  # Boşlukları tireyle değiştir

                for tarih in tarihler:
                    tarih_kod = tarih.strip().replace("-", "/")  # Tarih formatını düzenle
                    url = f"{base_url}/{kategori_adi}/{tarih_kod}"
                    dosya.write(url + "\n")
