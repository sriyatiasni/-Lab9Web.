# -Lab9Web.
## Nama : Sriyati Asni
## NIM : 311910697
## Kelas : TI.19.A2
## Langkah-langkah praktikum
## Langkah 1
## Jalankan XAMPP dan akses http://localhost/phpmyadmin/ untuk membuat database.
![xampp](https://user-images.githubusercontent.com/56379905/121054365-78eaee80-c7e6-11eb-92fa-db0297411e52.png)
## LANGKAH 2
## Buat file lab9_php_modular pada root directory web server (d:\xampp\htdocs)
![folder1](https://user-images.githubusercontent.com/56379905/121054641-c23b3e00-c7e6-11eb-8f1c-a161a5d29fd8.png)
## LANGKAH 3
## Buat file baru dengan nama header.php pada folder (d:\xampp\htdocs\lab9_php_modular)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/stylesheet" media="screen" />
</head>
<body>
    <div class="container">
        <header>
            <h1>Modularisasi Menggunakan Require</h1>
        </header>
        <nav>
        <a href="home.php">Home</a>
        <a href="about.php">Tentang</a>
        <a href="kontak.php">Kontak</a>
        </nav>

## LANGKAH 4
## Buat file baru dengan nama footer.php pada folder (d:\xampp\htdocs\lab9_php_modular)
      <footer>
            <p>&copy; 2021, Informatika, Universitas Pelita Bangsa</p>
        </footer>
    </div>
</body>
</html>
![2](https://user-images.githubusercontent.com/56379905/121066482-257f9d00-c7f4-11eb-8013-6adf27a4b457.png)


## LANGKAH 5
## Buat file baru dengan nama home.php pada folder (d:\xampp\htdocs\lab9_php_modular)
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman Home</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
![3 3](https://user-images.githubusercontent.com/56379905/121055778-c451cc80-c7e7-11eb-8def-0f0e2958cfa8.png)
## LANGKAH 6
## Buat file baru dengan nama about.php pada folder (d:\xampp\htdocs\lab9_php_modular)
<?php require('header.php'); ?>

<div class="content">
    <h2>Ini Halaman About</h2>
    <p>Ini adalah bagian content dari halaman.</p>
</div>

<?php require('footer.php'); ?>
![4 4](https://user-images.githubusercontent.com/56379905/121056069-0549e100-c7e8-11eb-8c22-56604cd30900.png)
## HASIL
![5 5](https://user-images.githubusercontent.com/56379905/121056348-4e019a00-c7e8-11eb-97ab-436ee40eafab.png)
## About
![6 6](https://user-images.githubusercontent.com/56379905/121056642-98831680-c7e8-11eb-9279-8248047cc3af.png)
## TUGAS
## Implementasikan konsep modularisasi pada kode program praktikum 8 tentang database, sehingga setiap halamannya memiliki template tampilan yang sama.
## LANGKAH 1
## Buat file lab9_tugas pada root directory web server (d:\xampp\htdocs)
![tgs1](https://user-images.githubusercontent.com/56379905/121057090-1ba46c80-c7e9-11eb-8d53-4d9c31eee852.png)
## LANGKAH 2
## Buat file baru dengan nama koneksi.php pada folder (d:\xampp\htdocs\lab9_tugas)
<?php
$host = "localhost";
$user = "root";
$pass = "";
$db = "latihan1";
$conn = mysqli_connect($host, $user, $pass, $db);

if ($conn == false)
{
    echo "Koneksi ke server gagal.";
    die();
} #else echo "Koneksi berhasil";
?>
![koneksi ss 1](https://user-images.githubusercontent.com/56379905/121058069-257a9f80-c7ea-11eb-91ed-c896e5699bd6.png)
## LANGKAH 3
## Buat file baru dengan nama header.php pada folder (d:\xampp\htdocs\lab9_tugas)

<?php
include("koneksi.php");

// query untuk menampilkan data
$sql = 'SELECT * FROM data_barang';
$result = mysqli_query($conn, $sql);
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contoh Modularisasi</title>
    <link href="style.css" rel="stylesheet" type="text/css" />
</head>
<body>
    <div id="container">
        <header>
            <h1>Database</h1>
        </header>
        <nav>
            <a href="home.php">Home</a>
            <a href="tambah.php">Tambah Barang</a>
        </nav>
      ![header ss1](https://user-images.githubusercontent.com/56379905/121058567-aafe4f80-c7ea-11eb-9c88-2c2981db9840.png)
## LANGKAH 4
## Buat file baru dengan nama footer.php pada folder (d:\xampp\htdocs\lab9_tugas)
      
        <footer>
            <p>&copy; 2021, Veno Setyoaji Wiratama, 3111910363, TI.19.A.2</p>
        </footer>
    </div>
</body>
</html>
![ss footer1](https://user-images.githubusercontent.com/56379905/121058906-13e5c780-c7eb-11eb-8e36-340c7a4e8274.png)
## LANGKAH 5
## Buat file baru dengan nama home.php pada folder (d:\xampp\htdocs\lab9_tugas)
<?php require('header.php'); ?>

<div class="content">
    <h1>Data Barang</h1>
    <div class="main">
        <table>
        <tr>
            <th>Gambar</th>
            <th>Nama Barang</th>
            <th>Katagori</th>
            <th>Harga Jual</th>
            <th>Harga Beli</th>
            <th>Stok</th>
            <th>Aksi</th>
        </tr>
        <?php if($result): ?>
        <?php while($row = mysqli_fetch_array($result)): ?>
        <tr>
            <td><img src="gambar/<?= $row['gambar'];?>" alt="<?=$row['nama'];?>"></td>
            <td><?= $row['nama'];?></td>
            <td><?= $row['kategori'];?></td>
            <td><?= $row['harga_jual'];?></td>
            <td><?= $row['harga_beli'];?></td>
            <td><?= $row['stok'];?></td>
            <td>
                <a href="ubah.php?id=<?= $row['id_barang'];?>">Ubah</a>
                <a href="hapus.php?id=<?= $row['id_barang'];?>">Hapus</a> 
            </td>
        </tr>
        <?php endwhile; else: ?>
        <tr>
            <td colspan="7">Belum ada data</td>
        </tr>
        <?php endif; ?>
        </table>
    </div>
</div>

<?php require('footer.php'); ?>
![ss home 1 1](https://user-images.githubusercontent.com/56379905/121059299-85257a80-c7eb-11eb-9e02-341d347a1650.png)
## LANGKAH 6
## Buat file baru dengan nama tambah.php pada folder (d:\xampp\htdocs\lab9_tugas)
<?php
error_reporting(E_ALL);
include_once 'koneksi.php';

if (isset($_POST['submit']))
{
    $nama = $_POST['nama'];
    $kategori = $_POST['kategori'];
    $harga_jual = $_POST['harga_jual'];
    $harga_beli = $_POST['harga_beli'];
    $stok = $_POST['stok'];
    $file_gambar = $_FILES['file_gambar'];
    $gambar = null;

    if ($file_gambar['error'] == 0)
    {
        $filename = str_replace(' ', '_',$file_gambar['name']);
        $destination = dirname(__FILE__) .'/gambar/' . $filename;
        if(move_uploaded_file($file_gambar['tmp_name'], $destination))
        {
            $gambar = 'gambar/' . $filename;;
        }
    }
    
    $sql = 'INSERT INTO data_barang (nama, kategori, harga_jual, harga_beli, stok, gambar) ';
    $sql .= "VALUE ('{$nama}', '{$kategori}','{$harga_jual}','{$harga_beli}', '{$stok}', '{$gambar}')";
    $result = mysqli_query($conn, $sql);
    header('location: home.php');
}
?>

<?php require('header.php'); ?>

<div class="content">
    <h1>Tambah Barang</h1>
    <div class="main">
        <form method="post" action="tambah.php" enctype="multipart/form-data">
            <div class="input">
                <label>Nama Barang</label>
                <input type="text" name="nama" style="margin-left: 20px;" />
            </div>
            <div class="input">
                <label>Kategori</label>
                <select name="kategori" style="margin-left: 58px;" >
                    <option value="Komputer">Komputer</option>
                    <option value="Elektronik">Elektronik</option>
                    <option value="Hand Phone">Hand Phone</option>
                </select>
            </div>
            <div class="input">
                <label>Harga Jual</label>
                <input type="text" name="harga_jual" style="margin-left: 40px;" />
            </div>
            <div class="input">
                <label>Harga Beli</label>
                <input type="text" name="harga_beli" style="margin-left: 43px;" />
            </div>
            <div class="input">
                <label>Stok</label>
                <input type="text" name="stok" style="margin-left: 85px;" />
            </div>
            <div class="input">
                <label>File Gambar</label>
                <input type="file" name="file_gambar" />
            </div>
            <div class="submit">
                <input type="submit" name="submit" value="Simpan" />
            </div>
        </form>
    </div>
</div>

<?php require('footer.php'); ?>
![ss tambah 1 1](https://user-images.githubusercontent.com/56379905/121064476-d9335d80-c7f1-11eb-9544-bd364cd68280.png)
![ss tambah 2 2](https://user-images.githubusercontent.com/56379905/121064490-dcc6e480-c7f1-11eb-96d1-83c94485410c.png)
![ss tambah 3 3](https://user-images.githubusercontent.com/56379905/121064510-e2bcc580-c7f1-11eb-9d35-9ea8ffd18566.png)

## LANGKAH 7
## Buat file baru dengan nama ubah.php pada folder (d:\xampp\htdocs\lab9_tugas)
<?php
error_reporting(E_ALL);
include_once 'koneksi.php';

if (isset($_POST['submit']))
{
    $id = $_POST['id'];
    $nama = $_POST['nama'];
    $kategori = $_POST['kategori'];
    $harga_jual = $_POST['harga_jual'];
    $harga_beli = $_POST['harga_beli'];
    $stok = $_POST['stok'];
    $file_gambar = $_FILES['file_gambar'];
    $gambar = null;

    if ($file_gambar['error'] == 0)
    {
        $filename = str_replace(' ', '_', $file_gambar['name']);
        $destination = dirname(__FILE__) . '/gambar/' . $filename;
        if (move_uploaded_file($file_gambar['tmp_name'], $destination))
        {
           $gambar = 'gambar/' . $filename;;
        }
    }

    $sql = 'UPDATE data_barang SET ';
    $sql .= "nama = '{$nama}', kategori = '{$kategori}', ";
    $sql .= "harga_jual = '{$harga_jual}', harga_beli = '{$harga_beli}', stok = '{$stok}' ";
    if (!empty($gambar))
        $sql .= ", gambar = '{$gambar}' ";
    $sql .= "WHERE id_barang = '{$id}'";
    $result = mysqli_query($conn, $sql);

    header('location: home.php');
    }

    $id = $_GET['id'];
    $sql = "SELECT * FROM data_barang WHERE id_barang = '{$id}'";
    $result = mysqli_query($conn, $sql);
    if (!$result) die('Error: Data tidak tersedia');
    $data = mysqli_fetch_array($result);

    function is_select($var, $val) {
        if ($var == $val) return 'selected="selected"';
        return false;
}
?>
<?php require('header.php'); ?>

<div class="content">
    <h1>Ubah Barang</h1>
    <div class="main">
        <form method="post" action="ubah.php" enctype="multipart/form-data">
            <div class="input">
                <label>Nama Barang</label>
                <input type="text" name="nama" value="<?php echo $data['nama'];?>" style="margin-left: 20px;"/>
            </div>
            <div class="input">
                <label>Kategori</label>
                <select name="kategori" style="margin-left: 58px;">
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Komputer">Komputer</option>
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Elektronik">Elektronik</option>
                    <option <?php echo is_select ('Komputer', $data['kategori']);?> value="Hand Phone">Hand Phone</option>
                </select>
            </div>
            <div class="input">
                <label>Harga Jual</label>
                <input type="text" name="harga_jual" value="<?php echo $data['harga_jual'];?>" style="margin-left: 40px;"/>
            </div>
            <div class="input">
                <label>Harga Beli</label>
                <input type="text" name="harga_beli" value="<?php echo $data['harga_beli'];?>" style="margin-left: 43px;"/>
            </div>
            <div class="input">
                <label>Stok</label>
                <input type="text" name="stok" value="<?php echo $data['stok'];?>" style="margin-left: 85px;"/>
            </div>
            <div class="input">
                <label>File Gambar</label>
                <input type="file" name="file_gambar" />
            </div>
            <div class="submit">
                 <input type="hidden" name="id" value="<?php echo $data['id_barang'];?>" />
                 <input type="submit" name="submit" value="Simpan" />
            </div>
        </form>
    </div>
</div>

<?php require('footer.php'); ?>
![ss ubah 1 1](https://user-images.githubusercontent.com/56379905/121064779-30d1c900-c7f2-11eb-94f0-10246ec66b6c.png)
![ss ubah 2 2](https://user-images.githubusercontent.com/56379905/121064792-34655000-c7f2-11eb-89b4-10d572f23031.png)
![ss ubah 3 3](https://user-images.githubusercontent.com/56379905/121064811-3b8c5e00-c7f2-11eb-8daf-600f677306e2.png)

## LANGKAH 8
## Buat file baru dengan nama hapus.php pada folder (d:\xampp\htdocs\lab9_tugas)
<?php
include_once 'koneksi.php';
$id = $_GET['id'];
$sql = "DELETE FROM data_barang WHERE id_barang = '{$id}'";
$result = mysqli_query($conn, $sql);
header('location: home.php');
?>
![ss hapus 1](https://user-images.githubusercontent.com/56379905/121064951-68d90c00-c7f2-11eb-83a3-eb977ebb6bee.png)

## LANGKAH 9
## Buat file baru dengan nama style.css pada folder (d:\xampp\htdocs\lab9_tugas) agar mempercantik tampilannya.
/* import google font */
@import
url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,600;0,700;0,800;1,300;1,400;1,600;1,700;1,800&display=swap');
@import
url('https://fonts.googleapis.com/css2?family=Open+Sans+Condensed:ital,wght@0,300;0,700;1,300&display=swap');

/* Reset CSS */
* {
    margin: 0;
    padding: 0;
}
body {
    line-height:1;
    font-size:100%;
    font-family:'Open Sans', sans-serif;
    color:#5a5a5a;
}
#container {
    width: 980px;
    margin: 0 auto;
    box-shadow: 0 0 1em #cccccc;
}

/* header */
header {
    padding: 20px;
}
header h1 {
    margin: 20px 10px;
    color: #b5b5b5;
}

/* navigasi */
nav {
    display: block;
    background-color: #1f5faa;
}
nav a {
    padding: 15px 30px;
    display: inline-block;
    color: #ffffff;
    font-size: 14px;
    text-decoration: none;
    font-weight: bold;
}
nav a.active,
nav a:hover {
    background-color: #2b83ea;
}

/* Content Panel */
.content {
    background-color: #e4e4e5;
    padding: 50px 20px;
    margin-bottom: 20px;
}
.content h1 {
    margin-bottom: 20px;
    font-size: 35px;
}
.content p {
    margin-bottom: 20px;
    font-size: 18px;
    line-height: 25px;
}

/* footer */
footer {
    clear:both;
    background-color:#1d1d1d;
    padding:20px;
    color:#eee;
}

/* tabel */
body{
    font-family: sans-serif;
}
table{
    border-collapse: collapse;
}
th, td{
    border: 1px solid black;
    font-size: 16px;
    padding: 7px 9px;
}
table th {
    background:#1f5faa;
    color:#DCDCDC;
    font-weight:bold;
    font-size:14px;
}
table tr:nth-child(even) {
    background:#F0F8FF;
}

/* Tambah Barang */
.input{
    padding: 5px;
}
![ss style css 1 1](https://user-images.githubusercontent.com/56379905/121065317-d38a4780-c7f2-11eb-9e32-4c514e4cb5d9.png)
![ss style css 2 2](https://user-images.githubusercontent.com/56379905/121065326-d6853800-c7f2-11eb-9bd6-341b8133c64c.png)
![ss style css 3 3](https://user-images.githubusercontent.com/56379905/121065354-dd13af80-c7f2-11eb-8c6c-253d1e6ebdea.png)

## Hasil
## Tampilan Home
![ss 1 tgs 1](https://user-images.githubusercontent.com/56379905/121065425-f4529d00-c7f2-11eb-914f-73ed393fe9a0.png)
## Tampilan Tambah Barang
![tmbh brg](https://user-images.githubusercontent.com/56379905/121065486-02a0b900-c7f3-11eb-8960-2451a0f6d824.png)
## Tampilan Ubah Barang
![ubah brg](https://user-images.githubusercontent.com/56379905/121065525-0fbda800-c7f3-11eb-9cec-7eb5e31badf5.png)






       
          
    

      
      








      
