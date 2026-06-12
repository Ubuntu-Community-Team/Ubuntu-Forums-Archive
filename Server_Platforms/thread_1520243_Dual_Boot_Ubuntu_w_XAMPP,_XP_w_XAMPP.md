---
title: "Dual Boot: Ubuntu w/ XAMPP, XP w/ XAMPP"
date: 2010-06-29
forum: Server Platforms
---

### Post by grpace on 2010-06-29
Hi all !
I've recently been 'migrating' to Ubuntu and absolutely LOVE IT!!!
However, I have a question concerning Apache 2 on Ubuntu.

I have XP and Ubuntu on separate drives (Ubuntu on the first).
I have XAMPP installed on both systems.

Most of my site development lives on the XP drive.
I know I could copy all the folders, etc. to the Ubuntu drive, but it seems to me that may be a waste of drive space, not to mention having to keep both mirrored with each other.

The question:

Is is possible to set the Apache config file in Ubuntu to recognize the site folder on the XP drive and use it... Instead of having to mirror it on the Ubuntu drive ?

Thanks for any suggestions !

grpace

---

### Post by Protocol Distortion on 2010-06-29
What you need to do is be able to mount the windows drive on start up, using fstab.  Then change the settings of XAMPP to load the windows drive folder with the web files in it. I do not know how to edit xampp but in apache  the config file is located at "/etc/apache2/apache2.conf",    or you can create a symbolic link that way when the xampp  loads /var/www it would atomaticly load the folder on the windows drive also.

---

### Post by okplayer02 on 2010-06-29
I dont know just seems like it be easier in the long run to just configure XAMPP on your ubuntu and sure you can copy the apache2 config file from windows to ubuntu and compare the two and make the changes necessary on the ubuntu file.

---

### Post by grpace on 2010-06-29
Thank you folks for the reply !

1st off... As I stated...  I'm a newbie on Ubuntu.

What is fstab ?
How does it work ?
In simple terms, please.

I can understand mounting the XP drive first.

The main question is:

How to get Apache to recognize /dev/sd0 or /dev/sd1, etc ?

grpace

---

### Post by okplayer02 on 2010-06-29
its easier that you copy config files over to ubuntu it can be with usb stick or mount the windows partition in linux. then just make the changes to your apache installation in ubuntu and go from there. no need for linking and this other things. Do you know how to configure apache correct? the options should be just about the same in Windows compared to Ubuntu. Dont make it too hard or complicated for yourself.

---

### Post by Protocol Distortion on 2010-06-29
fstab is a file that lets linux knows what drives to mount in what folders,  for example 
/media/windows is the folder in which we could mount windows into, you will first have to create the folder. by using the command mkdir /media/windows if you might need to do sudo I can not rememebr 

then edit fstab and put this line of code in
   the drive          folder to mount the drive to
       \/                    \/
[B]/dev/sdax /media/windows ntfs defaults 0 0

[/B]where /dev/sdax is which partition that windows is on which would probally be sda1 (i could be wrongbeen awhile) since it was the original OS.  
 
then in apache you do not need to config it to read any thing in /dev/sda1 or 0 you just need to edit the line  
[FONT=Courier New]DocumentRoot /var/www[/FONT]
[FONT=Courier New]to[/FONT]
[FONT=Courier New]DocumentRoot /media/windows/xxx/xxx/xxx
where the xxx/xxx/xx/xx is the path to the folder that contains the html files or php or what ever you want served


any one that is reading this if I got something wrong then please reply and make the corrections [/FONT]

---

### Post by Protocol Distortion on 2010-06-29
> **Protocol Distortion said:**
> fstab is a file that lets linux knows what drives to 
then edit fstab and put this line of code in
the drive folder to mount the drive to
\/ \/
[FONT=Courier New]and make the corrections [/FONT]
  ingore that lol the formating got messed up,   but /dev/sdax is the drive and x is the partition number I am pretty sure you can tell which partition is which,   /media/windows is the folder that you can mount it to. you can change the name.

---

### Post by grpace on 2010-07-17
Thanks for all the information, folks !

I'll dig into this and see what I can destroy. :)

Thanks, again.
grpace

---

### Post by grpace on 2010-07-17
Just a second thought...

XAMPP comes complete with Apache2, MySQL, PHP, phpMyAdmin, and Perl.
It also installs in its own location.
I have also learned, through X-Chat, Ubuntu doesn't support XAMPP.

If Drupal installed its dependencies (Apache, MySQL) then that would mean I have 2 installations of each of them... One for XAMPP and one for Drupal... in different locations.

Considering this...

Wouldn't the best likely route... To start with... Would be to ditch XAMPP and its folder/directory, then add-on PHP, phpMyAdmin, Perl to what is considered the *nix standard... And then start from there ?

grpace

---

### Post by annavlad on 2010-08-03
try this [http://www.edonline.ro/mod/resource/view.php?id=69](http://www.edonline.ro/mod/resource/view.php?id=69)

---

### Post by tallthom on 2010-10-02
Just posted this:  [http://it.nikino.net/?p=1](http://it.nikino.net/?p=1)

Booting XP and Ubuntu with XAMPP.

---

