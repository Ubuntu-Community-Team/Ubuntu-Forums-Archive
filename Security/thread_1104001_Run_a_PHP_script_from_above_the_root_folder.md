---
title: "Run a PHP script from above the root folder"
date: 2009-03-23
forum: Security
---

### Post by adman4054 on 2009-03-23
I have searched the forums for an answer, but I'm not sure if I'm asking the right question. I'm running a LAMP server, Ubuntu 8.04 as a webserver. I want to place a PHP script above the web accessible folder. What is the most secure way to do this? I have created a folder abouve the root, but it doesnt work. Permissions? Access? Sorry, I'm about 6 months into my first server outside of Windows.
Thanks!

---

### Post by Bachstelze on 2009-03-23
> **adman4054 said:**
> I want to place a PHP script above the web accessible folder.

What are you trying to achieve thus?

---

### Post by adman4054 on 2009-03-23
> **HymnToLife said:**
> What are you trying to achieve thus?

I am trying to access a folder outside of the root directory.
I have placed a directory there called PDFsubscribe.  It contains an image with the path xxxxx/test/Page-004.png
I am working on a php script in the xxxxx.net directory, but I can't seem to access this image.
The script is at
[http://www.xxxxx.net/xxxxx/subscription/testReadRoot.php](http://www.xxxxx.net/xxxxx/subscription/testReadRoot.php)
The img src I'm using is
<img src="/home/xxxxx/PDFsubscribe/xxxxx/test/Page-004.png">
but I just can't get the image to show up.

---

### Post by rendon on 2009-03-23
I believe you mean that you want to put a PHP script somewhere outside of the public web accessible folder, and then somehow call it from the web accessible location for the web-user...?

I used to put all of my scripts somewhere like:

/var/db/scripts/

and then from the web accessible place you could call the script from PHP like this:

```

<?PHP

include "/var/db/scripts/myscript.php"

?>

```

Permissions and ownership will probably only matter if your PHP script is trying to write files or make directories...

You can store your scripts anywhere on the file system as long as you include it from the correct path.

---

### Post by Bachstelze on 2009-03-23
> **adman4054 said:**
> I am trying to access a folder outside of the root directory.
I have placed a directory there called PDFsubscribe.  It contains an image with the path xxxxx/test/Page-004.png
I am working on a php script in the xxxxx.net directory, but I can't seem to access this image.
The script is at
[http://www.xxxxx.net/xxxxx/subscription/testReadRoot.php](http://www.xxxxx.net/xxxxx/subscription/testReadRoot.php)
The img src I'm using is
<img src="/home/xxxxx/PDFsubscribe/xxxxx/test/Page-004.png">
but I just can't get the image to show up.

The easiest way to do this is to setup an Apache alias:

```
Alias /PDFsubscribe /home/xxxxx/PDFsubscribe
```

now you can do

```
<img src="/PDFsubscribe/xxxxx/test/Page-004.png" />
```

---

### Post by rendon on 2009-03-23
> **adman4054 said:**
> 
I am working on a php script in the xxxxx.net directory, but I can't seem to access this image.


You won't be able to access the image directly this way, the easiest way to do this is to temporarily copy the image to the current directory.

Another way is to make a PHP script that directly posts the image as a link, something along these lines:

```


<?php
header("Content-Type: image/jpeg");
header("Content-Disposition: attachment; filename=file.jpg");
?>


```

To make that work you'll have to learn a little about the GD library.  This link explains a little if you scroll down:

[http://www.boutell.com/newfaq/creating/emitimage.html](http://www.boutell.com/newfaq/creating/emitimage.html)

google keywords: php gd image header content-type

---

### Post by gregor171 on 2009-03-29
- Using php for showing images might not be a good idea for performance reason. 
- image folder should be visible from www either you make alias:

File: /etc/apache2/conf.d/alias
[HTML]Alias /images     /{...}/images
<Directory /{...}/images>
        Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all
</Directory>[/HTML]

or you make link in wwwroot folder:
ln -sf /{...}/images images

- putting scripts to place outside wwwroot is a good practice!

I'd usually make folders like:
/myweb/mydomain/wwwroot
/myweb/mydomain/inc
scripts could be inside wwwroot or somewhere else under mydomain folder:
[HTML]include_once "../inc/myhiddenscript.php";[/HTML]
Then you have to set new root in apache. Either domain or apache based...

---

