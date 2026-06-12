---
title: "Browser very slow?"
date: 2016-07-26
forum: The Cafe
---

### Post by KayeNg on 2016-07-26
Computer X has 3gb RAM.  Internet connection is USB tethering via cellphone which is connected to wifi.  When I try to do a certain task in Facebook, the browser, whether Chromium or Firefox, becomes very slow.

Computer Y has 1gb RAM.  Internet connection is linksys usb wifi adapter (using ndiswrapper).  Same task in same browser, browser doesn't become slow.

What's the problem?

Both computers run Lubuntu 14.04

---

### Post by mastablasta on 2016-07-26
one is direct link ot router the other one over a phone with who knows what kind of protocols in between.

ram doesn't have much to do with nework speed.

---

### Post by yoshii on 2016-07-26
i think you are overstressing the hardware.  

try looking up web browser speed optimizations and use firefox addons that block ads and other unneeded metadata.  also disable the PDF reading functions of firefox, etc.  this type of stuff can speed it up a little.  also there are some tweaks that can change the network data flows.  And turn on the web browser disk cache and make it large, like say 1024 MB.  And have it not delete during shutdown.  

also, you could disable file access time logging in fstab with "noatime"  research that.  it's hard to explain.

---

### Post by shantiq on 2016-07-27
Tips on speeding up ...   CERTAINLY look at &#10114;  I leave the other info for reference





Now I did 3 things

&#10112;  loaded my distro to an external SSD in a caddy
&#10113;  installed LXDE   sudo apt install lxde
I run LXDE for the last two years after I was about to get rid of my 2005 machine; Unity often chokes it If you are running a machine more than 2 or 3 years old
***&#10114;  got rid of "slow/heavy" browsers   i now use Palemoon [excellent and fast]   also Otter-browser***


And a 2005 machine runs like a well-groomed and oiled cat 

Here are some how-tos  >>

&#9679; SSD distro install > [https://ubuntuforums.org/showthread.php?t=2265824](https://ubuntuforums.org/showthread.php?t=2265824)
&#9679; LXDE tips >  [https://ubuntuforums.org/showthread.php?t=2185566](https://ubuntuforums.org/showthread.php?t=2185566)
&#9679; Palemoon > [http://linux.palemoon.org/](http://linux.palemoon.org/)

---

