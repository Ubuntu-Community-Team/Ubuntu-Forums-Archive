---
title: "stopmotion crashes when importing webcam image"
date: 2010-03-07
forum: Ubuntu Studio
---

### Post by scbell on 2010-03-07
Hi Folks,

Stopmotion dies every time I try to take a picture with my webcam.

Running in terminal it gives:

*** glibc detected *** stopmotion: free(): invalid next size (fast): 0x0000000002634420 *** 
and prints out a backtrace then memory map. 

My stopmotion video import settings:

pre-poll command: fswebcam -d V4L2:$VIDEODEVICE -i 0 -r 640x480 $IMAGEFILE

start deamon: blank

stop deamon: blank

I can see the output of the webcam in stopmotion, and import images created using the exact same command as above, but when I try to use stopmotion to save the image it crashes.

I have also tried using motion as suggested in [http://ubuntuforums.org/archive/index.php/t-956338.html](http://ubuntuforums.org/archive/index.php/t-956338.html). But I still get the same issues.

Any help would be great!

Thanks,
Simon

---

