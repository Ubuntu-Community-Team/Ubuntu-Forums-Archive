---
title: "GUI problem"
date: 2010-02-05
forum: Server Platforms
---

### Post by rwslippey on 2010-02-05
Hello all,

I wouldnt completly call myself a noobie to ubuntu (set up a few servers before) and now I feel like a complete idiot...

I decided early this morning that I might want to try and put a gui on my ubuntu server installation went fine however now I'm staring at a blank screen. 

ubuntu boots goes to screen similar to desktop (loading with the mouse cursor) and then blank... occationaly it'll load a partial username box... but more offten than not it loads a completly blank screen and the caps lock and scroll lock lights on the keyboard are both blinking consistantly...

This ones got me thrown for a loop

Hope someone can help.. Thanks

Rob

---

### Post by rwslippey on 2010-02-05
Ok again I feel retarted... not exactly sure what the reason for a gui on server was... guess it's because my desk was useless... anyways ... I was able to fix my problem... for future issues  reboot your system and watch for the command on the screen saying starting gnome desktop manager or similar...

press   cntrl   alt F1 quickly ... this should brign you back to a command to remove what ever it is you've installed 

example   sudo apt-get remove   inplace of sudo apt-get install

you may have to run sudo apt-get --purge


goodluck   ... and I think I'm sticking with command lines

---

