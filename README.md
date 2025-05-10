# ARİVA Geçici E-posta Aracı

![ARİVA Banner](https://img.shields.io/badge/ARİVA-Ge%C3%A7ici_E--posta_Arac%C4%B1-blueviolet)
[![Lisans: MIT](https://img.shields.io/badge/Lisans-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**ARİVA Geçici E-posta Aracı**, geçici e-posta adresleri oluşturmak ve bu adreslere gönderilen doğrulama kodlarını otomatik olarak almak için geliştirilmiş Python tabanlı bir komut satırı aracıdır. `tempmailorg1` RapidAPI ile çalışır ve test, otomasyon veya geçici e-posta gerektiren senaryolar için idealdir.

📢 **Güncellemeler ve destek için Telegram kanalımıza katılın**: [t.me/arivatools](https://t.me/arivatools)

## Özellikler
- Birden fazla domaine sahip rastgele geçici e-posta adresleri oluşturur.
- Gelen e-postaları tarar ve 4-8 karakterlik doğrulama kodlarını çeker.
- Renkli ve kullanıcı dostu CLI arayüzü, tarama sırasında dönen animasyon ile.
- Hata yönetimi ve hata ayıklama için günlük kaydı.
- Termux, Kali Linux ve standart Linux/Windows ortamlarını destekler.

## Gereksinimler
- **Python 3.8+** (3.11 veya 3.12 önerilir).
- [RapidAPI](https://rapidapi.com) üzerinden alınmış geçerli bir **RapidAPI anahtarı**.
- İnternet bağlantısı (API istekleri için).

## Kurulum

### 1. Depoyu Klonlayın
Depoyu yerel makinenize klonlayın:
```bash
git clone https://github.com/siberdunyaniz/arivaeposta.git
cd arivaeposta
```

### 2. Bağımlılıkları Yükleyin
Gerekli Python kütüphanelerini `pip` ile yükleyin:
```bash
pip install requests pystyle fake_useragent tenacity
```

#### Ortama Özel Talimatlar
- **Termux (Android)**:
  1. Termux’u [F-Droid](https://f-droid.org) veya Play Store’dan yükleyin.
  2. Termux’u güncelleyin ve Python’u kurun:
     ```bash
     pkg update && pkg upgrade
     pkg install python
     ```
  3. `pip` ve bağımlılıkları yükleyin:
     ```bash
     pip install requests pystyle fake_useragent tenacity
     ```
  4. `git`’in yüklü olduğundan emin olun:
     ```bash
     pkg install git
     ```

- **Kali Linux**:
  1. Sistemi güncelleyin:
     ```bash
     sudo apt update && sudo apt upgrade
     ```
  2. Python ve `pip`’i yükleyin:
     ```bash
     sudo apt install python3 python3-pip
     ```
  3. `git`’i yükleyin (zaten yüklü değilse):
     ```bash
     sudo apt install git
     ```
  4. Bağımlılıkları yükleyin:
     ```bash
     pip3 install requests pystyle fake_useragent tenacity
     ```

- **Genel Linux (ör. Ubuntu, Debian)**:
  1. Python ve `pip`’i yükleyin:
     ```bash
     sudo apt update
     sudo apt install python3 python3-pip git
     ```
  2. Bağımlılıkları yükleyin:
     ```bash
     pip3 install requests pystyle fake_useragent tenacity
     ```

- **Windows**:
  1. Python’u [python.org](https://www.python.org/downloads/) adresinden yükleyin (`pip`’in dahil olduğundan emin olun).
  2. `git`’i [git-scm.com](https://git-scm.com/download/win) adresinden yükleyin.
  3. Komut İstemi veya PowerShell’de bağımlılıkları yükleyin:
     ```bash
     pip install requests pystyle fake_useragent tenacity
     ```

### 3. RapidAPI Anahtarını Ayarlayın
1. [RapidAPI](https://rapidapi.com) sitesine kaydolun ve `tempmailorg1` API’sine abone olun.
2. RapidAPI kontrol panelinden API anahtarınızı kopyalayın.
3. Anahtarı çevre değişkeni olarak ayarlayın:
   - **Linux/Termux/Kali**:
     ```bash
     export RAPIDAPI_KEY='sizin-rapidapi-anahtariniz'
     ```
     Kalıcı yapmak için `~/.bashrc` veya `~/.zshrc`’ye ekleyin:
     ```bash
     echo "export RAPIDAPI_KEY='sizin-rapidapi-anahtariniz'" >> ~/.bashrc
     source ~/.bashrc
     ```
   - **Windows (Komut İstemi)**:
     ```cmd
     set RAPIDAPI_KEY=sizin-rapidapi-anahtariniz
     ```
     Kalıcı ayar için Windows Ayarları’ndan Sistem Çevre Değişkenleri’ne ekleyin.
   - **Windows (PowerShell)**:
     ```powershell
     $env:RAPIDAPI_KEY = "sizin-rapidapi-anahtariniz"
     ```
     Kalıcı yapmak için PowerShell profiline ekleyin:
     ```powershell
     echo '$env:RAPIDAPI_KEY = "sizin-rapidapi-anahtariniz"' >> $PROFILE
     ```

## Kullanım
1. Scripti çalıştırın:
   ```bash
   python3 arivaeposta.py
   ```
2. Araç, bir banner gösterir ve destek için [t.me/arivatools](https://t.me/arivatools) kanalına yönlendirir.
3. Menüden bir seçenek seçin:
   - **1. Yeni E-posta Oluştur ve Kod Al**: Yeni bir geçici e-posta oluşturur ve doğrulama kodlarını tarar.
   - **2. Çıkış**: Aracı kapatır.
4. Kod alındığında, kod ve detaylar (konu, gönderici, tarih) görüntülenir.

### Örnek Çıktı
```
[*] ARİVA Geçici E-posta Aracı başlatıldı.
============================================================
[*] Aktif E-posta: Yok
============================================================
1. Yeni E-posta Oluştur ve Kod Al
2. Çıkış
============================================================
[?] Seçim (1/2): 1
[*] Oluşturulan E-posta: x7b4k9m2p8q@tmails.net
[*] Doğrulama kodu bekleniyor...
[+] Doğrulama Kodu: 483920
  Konu: Doğrulama Kodu
  Gönderen: noreply@example.com
  Tarih: 2025-05-10T11:20:00Z
------------------------------------------------------------
```

## Sorun Giderme
- **IndentationError**: Scriptin 4 boşluklu girinti kullandığından emin olun. VS Code’da `Girintiyi Boşluklara Dönüştür` seçeneğini kullanın (Ctrl+Shift+P).
- **ModuleNotFoundError**: Tüm bağımlılıkların yüklü olduğunu kontrol edin (`pip show requests pystyle fake_useragent tenacity`).
- **RapidAPI Anahtarı Hatası**: `RAPIDAPI_KEY` çevre değişkeninin ayarlı olduğunu doğrulayın (Linux’ta `echo $RAPIDAPI_KEY`, Windows’ta `echo %RAPIDAPI_KEY%`).
- **API İstek Hataları**: İnternet bağlantınızı kontrol edin ve RapidAPI kotanızı doğrulayın. `tempmailorg1` API’sinin aktif olduğundan emin olun.
- **Günlükler**: Hata detayları için script dizinindeki `ariva_tool.log` dosyasını kontrol edin.

## Katkıda Bulunma
1. Depoyu forklayın.
2. Yeni bir dal oluşturun: `git checkout -b ozellik-adi`.
3. Değişikliklerinizi yapın ve kaydedin: `git commit -m "Yeni özellik eklendi"`.
4. Foruğunuza itin: `git push origin ozellik-adi`.
5. [GitHub](https://github.com/siberdunyaniz/arivaeposta) üzerinde bir Pull Request açın.

## Lisans
Bu proje MIT Lisansı altında lisanslanmıştır. Detaylar için [LICENSE](LICENSE) dosyasına bakın.

## Destek
Sorular, öneriler veya güncellemeler için:
- Telegram kanalımıza katılın: [t.me/arivatools](https://t.me/arivatools)
- [GitHub](https://github.com/siberdunyaniz/arivaeposta/issues) üzerinde bir sorun açın

---

*[siberdunyaniz](https://github.com/siberdunyaniz) tarafından 💻 ile geliştirildi*