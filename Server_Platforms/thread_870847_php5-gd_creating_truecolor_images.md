---
title: "php5-gd creating truecolor images"
date: 2008-07-26
forum: Server Platforms
---

### Post by janlazar2 on 2008-07-26
web server instalation and configuration

This line is NOT working imagettftext($im, 15, 0, 10, 20, $black, $font, $text);
-----------------------------------------------------------------------------

on new instalation ubuntu 7.10 I installed:

*************************************************************************
su									
apt-get update
apt-get install apache2
apt-get install php5
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
/etc/init.d/apache2 restart
cp /var/www/apache2-default/index.html /var/www/index.php
apt-get install mysql-server
apt-get install mysql-admin
apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
/etc/php5/apache2/php.ini	-	extension=mysql.so
/etc/init.d/apache2 restart
ln -s /usr/share/phpmyadmin/
apt-get install php5-gd
/etc/php5/conf.d/gd.ini		-	extension=gd.so
/etc/init.d/apache2 restart						
*************************************************************************

apache2, php5, mysql, phpmyadmin, php5-gd is working

php5-gd is working but
problem is I can't create images using imagettftext($im, 15, 0, 10, 20, $black, $font, $text); function.
file image.php is working
file image2.php is NOT working
-----------------------------------------------------------
if I install LAMPP files image.php and image2.php are working fine
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)
-----------------------------------------------------------

Any ideas for solution?
Thank you very much

Appendix 1: I'm trying and I realized that just lines 
            imagettftext($im, 15, 0, 10, 20, $black, $font, $text);
            imagettftext($im, 15, 0, 10, 20, $black, $font, $text);
            in image2.php are NOT working.

                           Jan


-------------------------------------------------------------------------
FILES
-------------------------------------------------------------------------
file image.php is working:
--------------------------
<?php
header("Content-type: image/gif");
list($width, $height, $type, $attr) = getimagesize("img/apache_pb22_ani.gif");
$im = imagecreatefromgif ( "img/apache_pb22_ani.gif" );
	$text_color = imagecolorallocate($im, 0, 0, 0);
	$line_colour = imagecolorallocate( $im, 255, 0, 0 );
imagestring($im, 2, 5, 5,  "Obrazok vygenerovany s PHP 5.2.6", $text_color);
imageline( $im, 0, 0, $width, $height, $line_colour );
imagesetthickness ( $im, 10 );
imagegif($im);
imagedestroy($im);
?>


file image2.php is NOT working:
-------------------------------
<?php
$prem='JANO';
$dlzka=100;
header("Content-type: image/png");
$im = imagecreatetruecolor($dlzka, 30);
$white = imagecolorallocate($im, 255, 255, 255);
$grey = imagecolorallocate($im, 128, 128, 128);
$black = imagecolorallocate($im, 0, 0, 0);
imagefilledrectangle($im, 0, 0, $dlzka-1, 29, $white);
$text = $prem;
$font = 'RAVIE.TTF';
imagettftext($im, 15, 0, 11, 21, $grey, $font, $text);// This two lines are not working
imagettftext($im, 15, 0, 10, 20, $black, $font, $text);// Without them it works OK
imagepng($im);
imagedestroy($im);
?>

---

### Post by janlazar2 on 2008-07-26
I changed the line $font = 'RAVIE.TTF'; to $font = './RAVIE.TTF';

and IT'S WORKING

see ya

---

