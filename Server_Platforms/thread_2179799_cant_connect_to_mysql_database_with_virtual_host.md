---
title: "cant connect to mysql database with virtual host"
date: 2013-10-09
forum: Server Platforms
---

### Post by ally_bintang on 2013-10-09
hellow
 i've got some problem to displaying my data from database. Iam new to ubuntu so not sure are my connect script working with virtual host..:confused:
here my setting code:

   /etc/apache2/sites-available/enefka-event.com
 ```

<VirtualHost *:80>
        ServerAdmin webmaster@enefka-event.com
        ServerName enefka-event.com

        DocumentRoot /var/www/enefka-event.com/public_html
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/enefka-event.com/public_html>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

   /etc/hosts
```
127.0.0.1       localhost 127.0.1.2       enefka-event.com
```

it's working because i can access that file from my browser.
then i have my connect file at    /var/www/enefka-event.com/public_html/admin/koneksi.php
```
   
*<?php*
*$host = "enefka-event.com";*
 *$user = "admin";*
 *$pass = "xxxx";*
 *$dbnm = "enefka_db";*
 *$conn = mysql_connect ($host, $user, $pass);*
 *if ($conn) {*
 *    $open = mysql_select_db ($dbnm);*
 *    if (!$open) {*
 *        die ("database cannot open");*
 *    }*
 *} else {*
 *    die {"Server Mysql connot connect"};*
 *}*
*?>*
```

    then my kategori file at /var/www/enefka-event.com/public_html/admin/kategori.php
```

<?php
include "koneksi.php";
?>
<!DOCTYPE html>
<head></head>
<body>
...
<table class="bordered">
                <thead>
                    <tr>
                        ...
                    </tr>
                </thead>
                <tbody>
                 <?php     
                    $query = "SELECT id_kategori, keterangan FROM kategori ORDER BY id_kategori ";
                    $result = mysqli_query($query);
                    $no = 1;
                    while($row = mysql_fetch_row($result))
                    {
                 ?>    
                         <tr>
                            <?php
                            $id_kategori= $row[ 0];
                            $keterangan = $row[ 1];
                            ?>
                            <td><?php echo $id_kategori;?></td>
                            <td><?php echo $keterangan;?></td>
                         </tr>                        
                 <?php
                     $no++;                  
                     }              
                 ?>                       
                </tbody>                
            </table>
...
</body>
<footer></footer>
```

then this error log from apache2
```
   *[Thu Oct 10 10:07:28 2013] [error] [client 127.0.0.1] PHP Parse error:  syntax error, unexpected '"FROM kategori ORDER BY id_kat' (T_CONSTANT_ENCAPSED_STRING) in /var/www/enefka-event.com/public_html/admin/kategori.php on line 85, referer: http://enefka-event.com/admin/*
```

cant someone help me coz iam only got blank white page every time i access the "kategori.php" page, and sry if my english bad :oops:

---

### Post by Habitual on 2013-10-10
show us line 85 of kategori.php please.

---

### Post by ally_bintang on 2013-10-10
okay

```

           80     <tbody>
           81      <?php     
           82         $query = "SELECT id_kategori, keterangan
           83                 FROM kategori ORDER BY id_kategori ";
           84         $result = mysqli_query($query);
           85         $no = 1;
           86         while($row = mysql_fetch_row($result))
           87         {
           88      ?>    

```

---

### Post by SeijiSensei on 2013-10-10
>  unexpected '**"**FROM kategori ORDER BY **id_kat**'

The error shows an extraneous double quote before the FROM.  I don't see that in the text you showed.  There is also a reference to "id_kat" which isn't the same as "id_kategori".

---

### Post by ally_bintang on 2013-10-10
> **SeijiSensei said:**
> The error shows an extraneous double quote before the FROM.  I don't see that in the text you showed.  There is also a reference to "id_kat" which isn't the same as "id_kategori".

but php script in kategori.php only that i show u.. how come there was id_kat :confused: and my database for table kategori only have 2 row > id_kategori and keterangan.

here was completed script
```

<?php
include "koneksi.php";
?>

<!DOCTYPE html>
<html lang=en>
<head>
    <meta charset=UTF-8>
    <title>Enefka| admin area</title>
    <!--[if lt IE 9]><script src=http://html5shiv.googlecode.com/svn/trunk/html5.js></script><![endif]-->
    <link href=style-full.css rel=stylesheet />
    <!--[if lt IE 9]><link href=ie.css rel=stylesheet /><![endif]-->
    <link href='http://fonts.googleapis.com/css?family=Luckiest+Guy' rel='stylesheet' type='text/css'>        
</head>

<body>
<header> 
    <hgroup class="clearfix"> 
        <h1><a href="#"><span>ENEFKA</span>admin area</a></h1> 
        <h2>xxx</h2> 
    </hgroup>
    
        <form id="searchbox" action="">
            <input id="search" type="text" placeholder="Type here">
            <input id="submit" type="submit" value="Search">
        </form>
    
    <ul id="menu">
    <li><a href="home.html">Home</a></li>
    <li><a href="kategori.html">Kategori</a></li>
    <li>
        <a href="content.html">Content</a>
        <ul>
            <li><a href="news.html">News</a></li>
            <li><a href="event.html">Event</a></li>
            <li><a href="jadwal_kegiatan">Jadwal Kegiatan</a></li>
            <li><a href="informasi_event">Info Event</a></li>
        </ul>
    </li>
    <li>
        <a href="user.html">User</a>
        <ul>
            <li><a href="registrasi.html">Registrasi</a></li>
            <li><a href="member_list01.html">Member List</a></li>
            <li><a href="edit-profile.html">Edit Profile</a></li>            
        </ul>
    </li>
    <li>
        <a href="message.html">Message</a>
        <ul>
            <li><a href="comment.html">Comment Event</a></li>
            <li><a href="inbox.html">Inbox Member</a></li>
            <li><a href="contact_us.html">Contact Us</a></li>
        </ul>
    </li>
    <li>
        <a href="gallery.html">Gallery</a>
        <ul>
            <li><a href="picture.html">Picture Member</a></li>
            <li><a href="image.html">Image Event</a></li>
            <li><a href="video.html">Video</a></li>
        </ul>
    </li>
    <li><a href="logout.html">Logout</a></li>
    </ul>
</header>  

<div id="main" class="clearfix"> 
    <div id="content">
        <article>            
                <h1>KATEGORI</h1>
            <table class="bordered">
                <thead>
                    <tr>     
                        <th>Id</th>
                        <th>Keterangan</th>
                    </tr>
                </thead>
                <tbody>
                 <?php     
                    $query = "SELECT id_kategori, keterangan
                             FROM kategori ORDER BY id_kategori ";
                    $result = mysqli_query($query);
                    $no = 1;
                    while($row = mysql_fetch_row($result))
                    {
                 ?>    
                         <tr>
                            <?php
                            $id_kategori= $row[ 0];
                            $keterangan = $row[ 1];
                            ?>
                            <td><?php echo $id_kategori;?></td>
                            <td><?php echo $keterangan;?></td>
                         </tr>                        
                 <?php
                     $no++;                  
                     }              
                 ?>                       
                </tbody>                
            </table>
            <a class=button-table href="delete-kategori.php">Edit Data</a>
            <a class=button-table href="add-kategori.php">Add Data</a>
            <a class=button-table href="delete-kategori.php">Delete Data</a>                                   
        </article>
    </div>
</div>

<footer class="clearfix">
    <span class="white-red">Design and code by </span><a href="#">xxx</a>
</footer>

<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js"></script>

</body>
</html>

```

is there a way to check that error??

---

### Post by ally_bintang on 2013-10-13
woot !! stupid me.. it's all about extra "{" at koneksi.php :oops: i edit to become like this
```

<?php
$host = "enefka-event.com";
$user = "admin";
$pass = "xxxx";
$dbnm = "enefka_db";
$conn = mysql_connect ($host, $user, $pass);
if ($conn) {
    $buka = mysql_select_db ($dbnm);
    if (!$buka) {
        die ("database cannot open");
    }
} else {
    die ("Server Mysql not connect");
}
?>

```
and use simple table to check
```

<h2>Data</h2>
    <table border="1" width="500px">
      <th><td>Id</td><td>Keterangan</td></th> 
<?php 
require_once('koneksi.php');
$query1="select id_kategori, keterangan from kategori "; 
$result=mysql_query($query1) or die(mysql_error());
$no=1;
while($rows=mysql_fetch_object($result)){
      ?>
      <tr>
        <td><?php echo $no
        ?></td>
        <td><?php    echo $rows -> id_kategori;?></td>
        <td><?php    echo $rows -> keterangan;?></td>
      </tr>
      <?php
$no++;
}?>
    </table>

```

and it's working \\:D/ thx for everyone who was helping me :popcorn:here some snack

---

