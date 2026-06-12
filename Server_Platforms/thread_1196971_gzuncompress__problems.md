---
title: "gzuncompress  problems"
date: 2009-06-25
forum: Server Platforms
---

### Post by anthonyruk on 2009-06-25
Hi all,

I'm new to Ubuntu Server after using the Desktop Client for a while, I decided to setup a VPS using Ubuntu Server for a small project.

I have set the server up, however it seems that there is an issue with running Wordpress on it. Each Wordpress page returns the following:-

===

**Warning**:  gzuncompress() [[function.gzuncompress]("http://www.anthonyrobinson.info/wordpress/function.gzuncompress")]: data error in **/home/anthony-robinson-info/public_html/wordpress/wp-includes/http.php** on line **1792**

**Warning**:  gzinflate() [[function.gzinflate]("http://www.anthonyrobinson.info/wordpress/function.gzinflate")]: data error in **/home/anthony-robinson-info/public_html/wordpress/wp-includes/http.php** on line **1787**

**Warning**:  gzuncompress() [[function.gzuncompress]("http://www.anthonyrobinson.info/wordpress/function.gzuncompress")]: data error in **/home/anthony-robinson-info/public_html/wordpress/wp-includes/http.php** on line **1792**

**Warning**:  gzinflate() [[function.gzinflate]("http://www.anthonyrobinson.info/wordpress/function.gzinflate")]: data error in **/home/anthony-robinson-info/public_html/wordpress/wp-includes/http.php** on line **1787**

**Warning**:  gzuncompress() [[function.gzuncompress]("http://www.anthonyrobinson.info/wordpress/function.gzuncompress")]: data error in **/home/anthony-robinson-info/public_html/wordpress/wp-includes/http.php** on line **1792**

**Warning**:  gzinflate() [[function.gzinflate]("http://www.anthonyrobinson.info/wordpress/function.gzinflate")]: data error in **/home/anthony-robinson-info/public_html/wordpress/wp-includes/http.php** on line **1787**

**Fatal error**:  Cannot access empty property in **/home/anthony-robinson-info/public_html/wordpress/wp-includes/http.php** on line [B]1654
==

[/B]I have re-compled zlib into PHP 5, and phpinfo.php is showing that zlib extensions and compression are enabled yet the errors remain.

I'm really out of ideas and was wondering if anyone has come across this before?

My phpinfo.php is at [http://www.anthonyrobinson.info/phpinfo.php](http://www.anthonyrobinson.info/phpinfo.php)

Any help greatly appreciated.

Thanks.
Anthony.

---

### Post by anthonyruk on 2009-06-25
Fixed - Turns out this can be fixed by sudo apt-get install php-5 mcrypt.

---

