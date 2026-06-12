---
title: "Apache / php and gdlib ??"
date: 2006-09-25
forum: Server Platforms
---

### Post by _jB on 2006-09-25
Hello.
Anyone know howto get gdlib up and running ?

1) I removed apache (apt-get removed). Apparently i had both apache and apache2 installed.
2) Installed apache (2.2.2)
```
./configure --enable-so --with-mysql --enable-rewrite
make clean
make
make install
```
3) Installed php (4.4.2) (from [this guide]("http://wiki.c3w.org/index.php?Compiling%20PHP"))
```
./configure --with-mysql --with-gd=../php_stuff/gd-1.8.4 --with-png-dir=../php_stuff/libpng-1.2.12 --with-tiff-dir=../php_stuff/tiff-3.8.2 --with-zlib-dir=../php_stuff/zlib-1.2.3 --with-jpeg-dir=../php_stuff/jpeg-6b/ --with-truecolor --with-gif-dir=../php_stuff/libungif-4.1.4 --enable-ftp --enable-calendar --with-freetype-dir=../php_stuff/freetype-2.1.10
```
Apache works fine and so does php, but I have NO gdlib what-so-ever :-k 

***What have I forgotten*** **??**

[SIZE="1"][FONT="Verdana"]Please let me know if I need to post some files/.conf's here :)[/FONT][/SIZE]

---

### Post by spp on 2006-09-26
Installing the php4-gd or php5-gd from the repos does not work for you?

Not dissuading you from the manual compile route but that compile statement looks like it compiles a CLI binary only as I do not see an --with-apxs2 statement in there. Hell, my configure line wraps about 5 times :)

```

'./configure' '--host=i386-redhat-linux' '--build=i386-redhat-linux' '--target=i386-redhat-linux-gnu' '--program-prefix=' '--prefix=/usr' '--exec-prefix=/usr' '--bindir=/usr/bin' '--sbindir=/usr/sbin' '--sysconfdir=/etc' '--datadir=/usr/share' '--includedir=/usr/include' '--libdir=/usr/lib' '--libexecdir=/usr/libexec' '--localstatedir=/var' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--with-config-file-path=/etc' '--with-config-file-scan-dir=/etc/php.d' '--enable-force-cgi-redirect' '--disable-debug' '--enable-pic' '--enable-inline-optimization' '--with-bz2' '--with-curl' '--with-exec-dir=/usr/bin' '--with-freetype-dir=/usr' '--with-png-dir=/usr' '--with-gd' '--enable-gd-native-ttf' '--with-gettext' '--with-ncurses' '--with-gmp' '--with-iconv' '--with-jpeg-dir=/usr' '--with-openssl' '--with-png' '--with-pspell' '--with-xml' '--with-expat-dir=/usr' '--with-dom=shared,/usr' '--with-dom-xslt=/usr' '--with-dom-exslt=/usr' '--with-xmlrpc=shared' '--with-zlib' '--with-layout=GNU' '--enable-bcmath' '--enable-exif' '--enable-sockets' '--enable-track-vars' '--enable-trans-sid' '--with-oci8' '--with-imap=shared' '--with-imap-ssl' '--with-kerberos' '--with-ldap=shared' '--with-mysql' '--with-pgsql=shared' '--with-snmp=shared,/usr' '--with-snmp=shared' '--enable-ucd-snmp-hack' '--enable-bcmath' '--enable-calendar' '--enable-mcal' '--enable-mbstring' '--enable-mbstr-enc-trans' '--enable-mbregex' '--with-sybase=/usr/include' '--with-apxs2=/usr/sbin/apxs'

```

Granted this is a RHEL3 development box but you may need a few more options to get a useful compile.

I think what is happening is you are using your existing php compile and your new one is not going anywhere.


SP

---

### Post by _jB on 2006-09-26
nope, apg-get php4-gd dosen't do anything for me (or for php :P).
I'll give it a go with the **--with-apxs2** enabled, don't quite know why I haven't tried that yet ;) ](*,)

------
update;
Tried
```
# php med gdlib
./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql --with-gd=../php_stuff/gd-1.8.4 --with-png-dir=../php_stuff/libpng-1.2.12 --with-tiff-dir=../php_stuff/tiff-3.8.2 --with-zlib-dir=../php_stuff/zlib-1.2.3 --with-jpeg-dir=../php_stuff/jpeg-6b/ --with-truecolor --with-gif-dir=../php_stuff/libungif-4.1.4 --enable-ftp --enable-calendar --with-freetype-dir=../php_stuff/freetype-2.1.10
make clean
make
sudo make install
``` and that gave me **ZLib Support enabled**.

Now when I run **$orig = imagecreatefrompng($_FILES['file']['tmp_name']);** it "works", but **$image = imagecreatetruecolor($image_x, $image_y);** returns ***Fatal error**: Call to undefined function: imagecreatetruecolor() in ....* (no **gd** section @ phpinfo(); yet either)..

---

### Post by _jB on 2006-09-27
oki now gdlib is available @ phpinfo(); but ***imagecreatetruecolor()*** still failes. If I try ***imagecreate()*** instead ***ImageCopyResampled*** failes instead :(

A.t.m I'm using (found @ php.net) for testing.
[SIZE="3"][PHP]<?php
function easyResize($img_sourse, $save_to, $quality, $width, $str)
{
$size = GetImageSize($img_sourse);
   $im_in = ImageCreateFromJPEG($img_sourse);
  
   $new_height = ($width * $size[1]) / $size[0]; // Generate new height for image
   $im_out = imagecreatetruecolor($width, $new_height);
  
   ImageCopyResampled($im_out, $im_in, 0, 0, 0, 0, $width, $new_height, $size[0], $size[1]);
      
   #Find X & Y for note
   $X_var = ImageSX($im_out);
   $X_var = $X_var - 130;
   $Y_var = ImageSY($im_out);
   $Y_var = $Y_var - 25;

   #Color
   $white = ImageColorAllocate($im_out, 0, 0, 0);
  
   #Add note(simple: site address)
   ImageString($im_out,2,$X_var,$Y_var,$str,$white);

   ImageJPEG($im_out, $save_to, $quality); // Create image
   ImageDestroy($im_in);
   ImageDestroy($im_out);
}
easyResize("mario.jpg","mario_2.jpg","100","90",NULL);
?>[/PHP][/SIZE]

---

