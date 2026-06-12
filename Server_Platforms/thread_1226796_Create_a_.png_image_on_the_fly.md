---
title: "Create a .png image on the fly"
date: 2009-07-29
forum: Server Platforms
---

### Post by DFHIII on 2009-07-29
I am trying to create a .png image in php and have it posted to a web page.  The php compiler can't find the ImageCreate function.  Where do I find and how do I add png image support?

Thanks,

Dan H.

---

### Post by t3r0 on 2009-07-30
> **DFHIII said:**
> I am trying to create a .png image in php and have it posted to a web page.  The php compiler can't find the ImageCreate function.  Where do I find and how do I add png image support?

Thanks,

Dan H.


Install ```
php5-gd
``` 

- Tero

---

### Post by DFHIII on 2009-07-30
I installed php-pg and ran a test page.  I got the same error:

Fatal error: Call to undefined function ImageCreate() in /var/www/progress_bar_test.php on line 21

There must be something else I am missing.

Dan H.

---

### Post by ade234uk on 2009-07-30
You need to 
sudo apt-get install php5-gd 
like the poster said above.

If this does not work, could there be an issue with your script?

---

### Post by DFHIII on 2009-07-30
I did install php5-gd using Synaptic.  That was a typo in my previous reply.  I checked and it is installed.

The test script is as follows:

<?php

/**********************
  Initial calculations for progress bar
***********************/

$question_count = 25;
$learning = 25;
$practice = 0;
$review = 0;

$width = 500;
$left = 50;
$right = 50;
$bar_height = 40;

$x = $left + 50;
$y = 50;
$height = $bar_height + 50;

$im = ImageCreate($width, $height);
$white = ImageColorAllocate($im, 255, 255, 255);
$blue = ImageColorAllocate($im, 0, 64, 128);
$red = ImageColorAllocate($im, 255, 255, 0);
$lime = ImageColorAllocate($im, 0, 0, 255);

$bg_color = $lime;
ImageFilledRectangle($im, 0, 0, $width, $height, $bg_color);

$learning_length = ($learning / $question_count) * 100;
$practice_length = ($practice / $question_count) * 100;
$review_length = ($reviews / $question_count) * 100;

// Draw progress bar
ImageFilledRectangle($im, $x, $y-2, $learning_length, $y + $bar_height, $red);
ImageFilledRectangle($im, $x + $learning_length, $y-2, $practice_length, $y + $bar_height, $white);
ImageFilledRectangle($im, $x + $learning_length + $practice_length, $y-2, $review_length, $y + $bar_height, $blue);

// Display progress bar
Header('Content-type: image/png');
ImagePng($im);

// Clean up
ImageDestroy($im);

?>

Your gnulinux website is a great resource.  After this problem is solved I am going to bring up GoogleEarth.

Dan H

---

### Post by ade234uk on 2009-07-30
Your missing a ) bracket on this line. Just copy and paste this line below and remove the old one.

$blue = ImageColorAllocate($im, 0, 64, 12);

I just installed this to my own webspace and it worked fine.
I got a blue rectangle and horizontal line.

=======================

I also just found this info on another site.
The GD has to be installed with your PHP installation or it has to be uncommented in php.ini

Depending which one is in the library:

;extension=php_gd.dll
or
extension=php_gd2.dll

---

### Post by DFHIII on 2009-07-30
I'm glad to hear it works, sorta.  Since I am using ubuntu I don't have any .dll files.  For some reason php is not finding the graphics library.  I am running Ubuntu Desktop 8.04.  Is there something in the server edition that I should have?

Any more ideas?

Dan H.

---

