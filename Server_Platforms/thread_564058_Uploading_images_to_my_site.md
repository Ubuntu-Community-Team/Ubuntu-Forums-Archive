---
title: "Uploading images to my site"
date: 2007-09-30
forum: Server Platforms
---

### Post by djknorr75 on 2007-09-30
Greetings all, I have just recently moved my website from my Windows computer to this one with Ubuntu, and everything was working great until I found that I could no longer upload images to it like I had in the past.  The path shown in the section below is the correct folder where it should store the images. 

```
Warning: move_uploaded_file(var/www/snapshots/images/slip_slide.jpg) [function.move-uploaded-file]: failed to open stream: No such file or directory in /var/www/snapshots/check_image.php on line 29

Warning: move_uploaded_file() [function.move-uploaded-file]: Unable to move '/tmp/php9Kd9U8' to 'var/www/snapshots/images/slip_slide.jpg' in /var/www/snapshots/check_image.php on line 29
An error occurred when attempting to load your picture. Please user your browser's 'back' button to try again.
```

At first, I thought this was probably just a simple permissions issue so I tinkered with the permissions on the 'snapshots' folder, but even after growing desperate and chmod 777 on it, I still get the same error.  I'm using PHP 5 as part of the LAMP install package.

TIA

---

### Post by djknorr75 on 2007-09-30
Please disregard this one...I meant to post in the 'Absolute Beginners' forum, and have now done so at [this page]("http://ubuntuforums.org/showthread.php?p=3453406#post3453406").

---

