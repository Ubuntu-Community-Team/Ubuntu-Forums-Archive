---
title: "sanner under wine? usb...."
date: 2009-01-20
forum: Wine
---

### Post by jarbo on 2009-01-20
I am trying to get my epson300 to work, until now the program vuescan just recognizes it, but does not adress it properly. This was until some hours ago. I installed Wine into the /home/user folder and here comes my question:
Can I plug in a USB-device and use the so called oem-software, just the way you do it with windows...by just installing this software and make it run? In Wine? :KS

---

### Post by hikaricore on 2009-01-20
I'm sorry to say, you're not going to be able to use any provided scanner drivers or software with WINE properly.

You'll have to likely make due with how it works under Linux.

---

### Post by donkyhotay on 2009-01-20
Try using the scanner with sane. The xsane client is installed by default and it recognizes my epson rx500 scanner 'out of the box'.

---

### Post by jarbo on 2009-01-22
Well it works, you can use the hint here 
[http://ubuntuforums.org/showthread.php?t=1000341&highlight=scanner+intrepid](http://ubuntuforums.org/showthread.php?t=1000341&highlight=scanner+intrepid)
and after this you have to find the file of .gscan2pdf where you have to change in line 55,64 and 65 the vendor_ID from the orignial value to 006:005 (the original value is 006:003, but this does not work), save the file in the folder as before. Then you find the file .so_sane_state and there you change the value to 006:005 as well. After that, iscan works! And it works well. You may got to change from former repository list the libltdl3 or put it in again.....when colliding with libltdl7 it is due to pulse. Take out pulse for a while....and add in the repo list sane and libsane......this should work for ISCAN. Furhtermore I'd say the program xsane it is quite a disappointment for colour-scans.

---

