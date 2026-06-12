---
title: "[PHP] ImageTTF"
date: 2006-12-24
forum: Server Platforms
---

### Post by Choxo on 2006-12-24
Hi all,
I'm running php with the gd library enabled.
This is what phpinfo() spits out about gd:
```

 GD Support 	                  enabled
GD Version 	                  2.0 or higher
FreeType Support 	   enabled
FreeType Linkage 	   with freetype
FreeType Version 	    2.2.1
T1Lib Support 	               enabled
GIF Read Support 	   enabled
GIF Create Support 	  enabled
JPG Support 	                enabled
PNG Support 	              enabled
WBMP Support 	           enabled

```

But I can't get imageTTF(); make work properly.
This snipllets works:
```

<?php
header("content-type: image/png");
$image = ImageCreate(150, 50);
$achtergrond = ImageColorAllocate($image, 255, 255, 255);
$grootte = 5;
$kleur = ImageColorAllocate($image, 0, 0, 0);
ImageString($image, $grootte, 5, 25, $_GET['tekst'], $kleur);
ImagePng($image);
ImageDestroy($image);
?> 

```

But this one doesn't:
```

<?php
header("Content-type: image/jpeg");
$font = "pixel.ttf";
$text = "test";
$im = ImageCreate(100, 100);
$zwart = ImageColorAllocate($im, 0, 0, 0); 
$wit = ImageColorAllocate($im, 255, 255, 255); 
ImageTTFText($im, 20, 0, 10, 10, $wit, $font , $text); 
Imagejpeg($im); 
ImageDestroy($im);
?>

```
And pixel.ttf is located in the same folder als the php file...

It just gives this : 'http://localhost/gd/link2.php' as output.

Can Anybody help me?

Thanks a lot,

---

### Post by tturrisi on 2006-12-24
[http://us3.php.net/imagecreate](http://us3.php.net/imagecreate)

---

### Post by Choxo on 2006-12-25
Thanks,
But I didn't find the answer there?


[SIZE="1"](I already have been searching on php.net etc...)[/SIZE]

---

### Post by frankos44 on 2008-04-02
I got exactly the same problem here.

My installation method was:

$ sudo apt-get install php5-gd

Firstly I thought the reason was perhaps the font not existing on the server so I  tried  on my desktop still no success. If you find out please let me know. Thanks

---

### Post by frankos44 on 2008-04-02
I did some work on this. The answer is simple, the font must exist and the PHP page be allowed access to it. 

For testing purposes I copied "arial.ttf" into the same folder where the PHP file lives and off it went.

---

