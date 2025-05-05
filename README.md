# dart-oop
// Soal 1: Pewarisan dan Override
// Class induk Hewan
class Hewan {
  String nama;

  Hewan(this.nama); // Konstruktor untuk mengatur nama

  void suara() {
    print('$nama mengeluarkan suara.');
  }
}

// Class anak Kucing, turunan dari Hewan
class Kucing extends Hewan {
  String jenisBulu;

  // Konstruktor dengan nama dan jenisBulu
  Kucing(String nama, this.jenisBulu) : super(nama);

  // Override metode suara()
  @override
  void suara() {
    print('$nama mengeong.');
  }
}

// Fungsi contoh untuk objek Kucing
void contohKucing() {
  var kucing = Kucing('Mimi', 'Panjang');
  kucing.suara(); // Panggil metode suara()
  print('Jenis bulu: ${kucing.jenisBulu}');
}

// Soal 2: Enkapsulasi
class RekeningBank {
  double _saldo = 0; // Properti saldo dibuat private dengan _

  // Getter untuk melihat saldo (tidak bisa diubah langsung dari luar)
  double get saldo => _saldo;

  // Metode untuk setor uang
  void setor(double jumlah) {
    if (jumlah > 0) {
      _saldo += jumlah;
      print('Setor: Rp$jumlah');
    }
  }

  // Metode untuk tarik uang
  void tarik(double jumlah) {
    if (jumlah > 0 && jumlah <= _saldo) {
      _saldo -= jumlah;
      print('Tarik: Rp$jumlah');
    } else {
      print('Saldo tidak cukup.');
    }
  }
}

// Fungsi contoh untuk RekeningBank
void contohRekening() {
  var rekening = RekeningBank();
  rekening.setor(100000);      // Setor uang
  rekening.tarik(30000);       // Tarik sebagian
  rekening.tarik(80000);       // Coba tarik lebih dari saldo
  print('Saldo akhir: Rp${rekening.saldo}');
}

// Soal 3: Polimorfisme dengan Override
class BangunDatar {
  // Metode dasar yang bisa dioverride
  double hitungLuas() {
    return 0;
  }
}

// Class Persegi turunan dari BangunDatar
class Persegi extends BangunDatar {
  double sisi;

  Persegi(this.sisi);

  @override
  double hitungLuas() {
    return sisi * sisi; // Luas persegi = sisi × sisi
  }
}

// Class Segitiga turunan dari BangunDatar
class Segitiga extends BangunDatar {
  double alas;
  double tinggi;

  Segitiga(this.alas, this.tinggi);

  @override
  double hitungLuas() {
    return 0.5 * alas * tinggi; // Luas segitiga = ½ × alas × tinggi
  }
}

// Fungsi contoh untuk menghitung luas bangun datar
void contohBangunDatar() {
  var persegi = Persegi(4);
  var segitiga = Segitiga(6, 3);
  print('Luas persegi: ${persegi.hitungLuas()}');
  print('Luas segitiga: ${segitiga.hitungLuas()}');
}

// Soal 4: Abstract class
// Abstract class tidak bisa dibuat objek langsung
abstract class Bentuk {
  double hitungLuas(); // Metode abstrak (tanpa isi)
}

// Class Lingkaran implementasi dari abstract class Bentuk
class Lingkaran extends Bentuk {
  double jariJari;

  Lingkaran(this.jariJari);

  @override
  double hitungLuas() {
    return 3.14 * jariJari * jariJari; // Luas lingkaran = π × r²
  }
}

// Fungsi contoh untuk objek Lingkaran
void contohLingkaran() {
  var lingkaran = Lingkaran(7);
  print('Luas lingkaran: ${lingkaran.hitungLuas()}');
}

// Fungsi utama menjalankan semua contoh
void main() {
  print('--- Contoh Pewarisan ---');
  contohKucing();

  print('\n--- Contoh Enkapsulasi ---');
  contohRekening();

  print('\n--- Contoh Polimorfisme ---');
  contohBangunDatar();

  print('\n--- Contoh Abstract Class ---');
  contohLingkaran();
}
