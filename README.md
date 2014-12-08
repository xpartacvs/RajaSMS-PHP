RajaSMS-PHP
===================

Library PHP untuk layanan sms gateway dari <a href="http://raja-sms.com" target="_blank">RajaSMS</a>

Kebutuhan Sistem
================

<ul>
  <li>PHP >= 5.3</li>
  <li>cURL extension</li>
</ul>

Instalasi
=========

<ol>
  <li>Copy file <code>rajasms.class.php</code> ke direktori project PHP Anda.</li>
  <li>Load class RajaSMS: <code>include_once 'rajasms.class.php';</code></li>
  <li>Buat object RajaSMS dengan masukan nilai variabel yang Anda dapat dari akun RajaSMS:
    <ul>
      <li><code>$rajasms = new RajaSMS('USERNAME', 'PASSWORD', 'APIKEY');</code></li>
    </ul>
  </li>
</ol>

Daftar Fungsi
=============
<ul>
  <li><code>int get_credit()</code><br>Mengambil nilai saldo akun. Return FALSE jika gagal.</li>
  <li><code>string get_expire_date([string $format = 'Y-m-d H:i:s'])</code><br>Mengambil tanggal kedaluarsa akun. Return FALSE jika gagal.</li>
  <li><code>int get_expire_timestamp()</code><br>Mengambil nilai waktu kedaluarsa akun dalam format UNIX TIMESPAMP. Return FALSE jika gagal.</li>
  <li><code>string get_report(array $sms_result)</code><br>Mengambil laporan hasil kirim SMS dari nilai balik fungsi <code>send()</code>. Return FALSE jika gagal.</li>
  <li><code>array send([bool $is_masking = FALSE])</code><br>Mengirim SMS. Jika <code>$is_masking</code> bernilai TRUE maka nomor pengirim akan disamarkan. Return FALSE jika gagal.</li>
  <li><code>void set_number(string $nomor_ponsel [,bool $is_validate = FALSE])</code><br>Untuk assign nomor ponsel tujuan.</li>
  <li><code>void set_text(string $text)</code><br>Untuk assign isi SMS.</li>
  <li><code>void reset()</code><br>Menghapus nomor ponsel tujuan dan isi SMS.</li>
</ul>


Contoh Implementasi
===================

<ol>
  <li>
    Set nomor ponsel tujuan:
    <ul>
      <li><code>$rajasms->set_number('08xxxxxxxxxx');</code></li>
    <ul>
  </li>
  <li>
    Set isi SMS:
    <ul>
      <li><code>$rajasms->set_text('Isi SMS');</code></li>
    <ul>
  </li>
  <li>
    Kirim SMS:
    <ul>
      <li><code>$sms_result = $rajasms->send();</code></li>
    <ul>
  </li>
  <li>
    Mengambil status laporan SMS:
    <ul>
      <li><code>echo $rajasms->get_report($sms_result);</code></li>
    <ul>
  </li>
  <li>
    Menghapus nomor ponsel tujuan dan isi SMS:
    <ul>
      <li><code>echo $rajasms->reset();</code></li>
    <ul>
  </li>
  <li>
    Cek saldo:
    <ul>
      <li><code>echo $rajasms->get_credit();</code></li>
    <ul>
  </li>
  <li>
    Cek waktu kedaluarsa <i>(unix timestamp)</i>:
    <ul>
      <li><code>echo $rajasms->get_expire_timestamp();</code></li>
    <ul>
  </li>
  <li>
    Cek tanggal kedaluarsa:
    <ul>
      <li><code>echo $rajasms->get_expire_date('Y-m-d H:i:s');</code></li>
    <ul>
  </li>
</ol>
