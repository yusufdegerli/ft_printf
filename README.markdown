# ft_printf

## Proje Hakkında
**ft_printf**, 42 Network müfredatında yer alan bir C programlama projesidir. Bu proje, standart C kütüphanesi fonksiyonu olan `printf`'in işlevselliğini taklit eden bir `ft_printf` fonksiyonu geliştirmeyi amaçlar. Proje, değişken argümanlar (variadic arguments) ile çalışmayı, string formatlamayı ve hafıza yönetimini öğrenmek için tasarlanmıştır. Kendi `ft_printf` fonksiyonumu yazarak, C programlama dilinde modüler kod yazımı, hata yönetimi ve algoritmik düşünme becerilerimi geliştirdim.

## Özellikler
`ft_printf` fonksiyonu, aşağıdaki format belirteçlerini ve bayrakları destekler:

### Zorunlu Kısım
- **Format Belirteçleri**:
  - `%c`: Tek bir karakter yazdırır.
  - `%s`: Bir string yazdırır.
  - `%d` / `%i`: İşaretli tamsayı yazdırır.
  - `%u`: İşaretsiz tamsayı yazdırır.
  - `%x` / `%X`: Onaltılık sayı yazdırır (küçük/büyük harf).
  - `%p`: Bir pointer adresini onaltılık formatta yazdırır.
  - `%%`: Yüzde işareti yazdırır.
- **Bayraklar**:
  - `-`: Sola hizalama.
  - `0`: Sıfır dolgusu.
  - `.`: Hassasiyet (precision) belirteci.
  - `*`: Genişlik veya hassasiyet için dinamik değer.
- **Dönüş Değeri**: Yazdırılan toplam karakter sayısını döndürür.

### Bonus Kısım (Opsiyonel)
- Ek bayraklar: `#` (alternatif format, örneğin `0x` öneki), `+` (pozitif sayılar için işaret), boşluk (space).
- Ek format belirteçleri: `%f` (kayan noktalı sayı), `%n` (yazdırılan karakter sayısını bir pointer'a kaydeder).
- Diğer: Uzunluk belirteçleri (`hh`, `h`, `l`, `ll`).

## Kurulum ve Kullanım

### Gereksinimler
- C derleyicisi (gcc veya clang önerilir).
- POSIX uyumlu bir işletim sistemi (Linux, macOS veya WSL).
- `make` komutu (Makefile ile derleme için).

### Kurulum
1. Repoyu klonlayın:
   ```bash
   git clone https://github.com/yusufdegerli/ft_printf.git
   cd ft_printf
   ```
2. Projeyi derleyin:
   ```bash
   make
   ```
   Bu komut, `libftprintf.a` statik kütüphanesini oluşturur.

3. Kendi test dosyanızı oluşturmak için:
   - Örnek bir `main.c` dosyası oluşturun:
     ```c
     #include "ft_printf.h"
     int main(void)
     {
         ft_printf("Merhaba, %s! Sayı: %d\n", "Dünya", 42);
         return (0);
     }
     ```
   - Derleyin ve çalıştırın:
     ```bash
     make
     ./a.out
     ```

### Makefile Komutları
- `make`: Kütüphaneyi derler (`libftprintf.a`).
- `make clean`: Ara dosyaları siler.
- `make fclean`: Ara dosyaları ve kütüphaneyi siler.
- `make re`: Her şeyi siler ve yeniden derler.
- `make bonus`: Bonus özellikleri derler (eğer implemente edildiysa).

## Test Etme
Projenizi test etmek için aşağıdaki açık kaynak test araçlarını kullanabilirsiniz:
- [gavinfielder/pft](https://github.com/gavinfielder/pft): Temel birim testleri.
- [Mazoise/42TESTERS-PRINTF](https://github.com/Mazoise/42TESTERS-PRINTF): Bayrak kombinasyonları için testler.
- [cacharle/ft_printf_test](https://github.com/cacharle/ft_printf_test): Rastgele test senaryoları.

Test araçlarını kullanmak için:
1. Test reposunu klonlayın.
2. Test talimatlarını takip ederek `ft_printf` kütüphanenizi entegre edin.
3. Testleri çalıştırın ve çıktıları kontrol edin.

## Kod Yapısı
Proje, modüler bir yaklaşımla yazılmıştır:
- **ft_printf.c**: Ana fonksiyon ve format string işleme mantığı.
- **ft_utils.c**: Yardımcı fonksiyonlar (örneğin, string veya sayı işleme).
- **ft_flags.c**: Bayrak ve format belirteçlerini işleyen fonksiyonlar.
- **libft/**: Libft kütüphanesi (string ve hafıza yönetimi için).

### Örnek Kullanım
```c
#include "ft_printf.h"

int main(void)
{
    int count;
    count = ft_printf("Merhaba, %s! Sayı: %-10d Hex: %x\n", "42", 42, 42);
    ft_printf("Yazdırılan karakter sayısı: %d\n", count);
    return (0);
}
```

**Çıktı**:
```
Merhaba, 42! Sayı: 42        Hex: 2a
Yazdırılan karakter sayısı: 35
```

## Öğrenilenler
Bu proje sayesinde aşağıdaki becerileri geliştirdim:
- **C Programlama**: Değişken argümanlar (`va_list`), string manipülasyonu ve formatlama.
- **Hafıza Yönetimi**: Dinamik bellek tahsisi ve sızıntı önleme.
- **Modüler Kod**: Okunabilir, yeniden kullanılabilir ve bakımı kolay kod yazımı.
- **Hata Ayıklama**: Edge case'ler (örneğin, null pointer'lar, en büyük negatif sayılar) için test ve düzeltme.
- **Algoritmik Düşünme**: Format string'ini ayrıştırma ve bayrak kombinasyonlarını işleme.

## Katkıda Bulunma
Eğer bu projeye katkıda bulunmak isterseniz:
1. Repoyu fork edin.
2. Yeni bir dal (branch) oluşturun: `git checkout -b feature/yeni-ozellik`.
3. Değişikliklerinizi yapın ve commit edin: `git commit -m "Yeni özellik eklendi"`.
4. Dalınızı push edin: `git push origin feature/yeni-ozellik`.
5. Bir Pull Request açın.

## Lisans
Bu proje, [MIT Lisansı](LICENSE) altında lisanslanmıştır.

**Not**: Bu README, 42 Network'ün ft_printf projesi için hazırlanmıştır. Projenizi 42 kurallarına uygun şekilde teslim ediyorsanız, lütfen 42'nin GitHub paylaşım politikalarını kontrol edin.
