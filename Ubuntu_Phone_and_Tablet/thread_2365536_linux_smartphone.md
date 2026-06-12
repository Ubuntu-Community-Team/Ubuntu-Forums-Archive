---
title: "linux smartphone?"
date: 2017-07-07
forum: Ubuntu Phone and Tablet
---

### Post by chicoperico2 on 2017-07-07
good day to all!


recently my Aquaris E5 ubuntu phone completely lost all functionality -   i could make it to the fastboot screen, then everything went black.

since i bought it late 2015 Aquaris seems to have given up on linux smartphones. looking at the forum threads, it seems they were not the only ones.


what do the erudite on this list recommend?
- buying a new one -    are there any available at all?
- installing a linux on an android device?
(i am quite experienced with linux on desktops, have flashed cyanogenmod onto an android device once.)
in this case, which device would you recommend?


thank you!

Rainer
Malmö
Sweden

---

### Post by monkeybrain20122 on 2017-07-07
Canonical has discontinued Ubuntu phone and convergence. But the developers from UBports have forked the project to continue its development. Looks like your device is supported. [https://devices.ubports.com/#/vegetahd](https://devices.ubports.com/#/vegetahd)

---

### Post by chicoperico2 on 2017-07-09
thank you for answering!


BUT:  i do not have the device any more -    it simply would not boot into anything any more, got stuck at the fastboot screen.

now -   i should prefer buying a preinstalled system.  i like working with computers and linux in particular, but i have a busy life, with work and children. are there any linux phones available on the market?

and if not, which phone and operating system variant would you recommend? the ones listed on ubports as the core devices?


best regards,
Rainer

---

### Post by wgarcia on 2017-07-09
I bought a used Nexus 5, but as new, about a month ago and flashed uBports on it. The flashing procedure for this phone is quite easy. I'm using it as my main phone without any problem, everything works as expected.  This phone will get the upgrade to UT 16.04 in the coming months, according to the uBports developers.

---

### Post by wildmanne39 on 2017-07-10
This is an English speaking forum please post in English only.

Thanks

---

### Post by chicoperico2 on 2017-07-13
thank you, WGarcia!

i bought a nexus 5. 
i got magic-device-tool via git.
i am using ubuntu 16.04.
after a few unlucky tries, i found i had to unlock the phone, i did so, i also activated usb-debugging.

the script ran a bit farther, a ubport menu appeared on the phone, offering to install ubuntu zip or from an image, those options led to empty folders.

i insert the bash output of what happens on my ubuntu machine, when i start launcher.sh from the magic-device-tools folder.


what is going wrong????


best regards,
Rainer



Created filesystem with 11/838832 inodes and 93654/3351034 blocks
erasing 'userdata'...
OKAY [  8.712s]
sending 'userdata' (137318 KB)...
OKAY [  9.411s]
writing 'userdata'...
OKAY [  9.142s]
finished. total time: 27.265s
rebooting into bootloader...
OKAY [  0.127s]
finished. total time: 0.178s

2017/07/13 17:09:20 Device is |hammerhead|
2017/07/13 17:09:20 Flashing version 42 from ubports-touch/legacy channel and server [http://system-image.ubports.com](http://system-image.ubports.com) to device hammerhead
2017/07/13 17:09:51 Start pushing /home/chico/.cache/ubuntuimages/pool/ubports-d50c18b27590af5734a826c4f7857d8909b0e0f902d21af142a780620c8eb58b.tar.xz to device
2017/07/13 17:09:51 Start pushing /home/chico/.cache/ubuntuimages/ubports-touch/15.04/stable/hammerhead/version-1.tar.xz to device
2017/07/13 17:09:51 Start pushing /home/chico/.cache/ubuntuimages/pool/keyring-4c4e7ef380ebcfa2c31084efa199138e93bfed8fc58aa3eb06bdf75a78af9b57.tar.xz to device
2017/07/13 17:09:51 Start pushing /home/chico/.cache/ubuntuimages/gpg/image-signing.tar.xz to device
2017/07/13 17:09:51 Start pushing /home/chico/.cache/ubuntuimages/gpg/image-master.tar.xz to device
2017/07/13 17:09:51 Start pushing /home/chico/.cache/ubuntuimages/pool/device-728a726a0e9a9983dc3b3b5279ab12759b3e15d33a657dd4b9253b3aa27858c1.tar.xz to device
2017/07/13 17:09:51 Done pushing /home/chico/.cache/ubuntuimages/pool/keyring-4c4e7ef380ebcfa2c31084efa199138e93bfed8fc58aa3eb06bdf75a78af9b57.tar.xz to device
2017/07/13 17:09:51 Done pushing /home/chico/.cache/ubuntuimages/gpg/image-signing.tar.xz to device
2017/07/13 17:09:51 Done pushing /home/chico/.cache/ubuntuimages/ubports-touch/15.04/stable/hammerhead/version-1.tar.xz to device
2017/07/13 17:09:51 Done pushing /home/chico/.cache/ubuntuimages/gpg/image-master.tar.xz to device
2017/07/13 17:10:09 Done pushing /home/chico/.cache/ubuntuimages/pool/device-728a726a0e9a9983dc3b3b5279ab12759b3e15d33a657dd4b9253b3aa27858c1.tar.xz to device
2017/07/13 17:10:51 error pushing: 

Move to your device to finish the setup.

Cleaning up..

Exiting script. Bye Bye

---

### Post by chicoperico2 on 2017-07-13
hello all  -   i found the solution on the french ubuntouch forum.
running launcher.sh without sudo does the trick!

---

### Post by wgarcia on 2017-07-15
Great @chicoperico2 that  you could install it. 

Another good place to get advise is the magic-device-tool Telegram group:
[https://t.me/joinchat/AAAAAAiC4TTYHRddjUbpXg](https://t.me/joinchat/AAAAAAiC4TTYHRddjUbpXg)

---

### Post by Ignorance Isnt Bliss on 2017-08-19
Hi sorry if this is the wrong place for this question. 
I have a Mezui MX4 running Ubuntu 15.04. I have recently noticed none of the apps update and every time I check for updates, it says it is up to date on the day of the check prior to the update check being completed. This is not how it used to operate. I am also unable to mount my phone on a Windows 10, Windows 7 and Ubuntu 16.04 computer. 
The question is, is this all because Ubuntu Touch has been discontinued or have I changed my settings some how. A supplementary question is do I have to reinstall Ubuntu Touch to benefit from uBports continuing development?

---

### Post by wgarcia on 2017-08-22
On the first question: Since Canonical does not support Ubuntu Touch any more, and the App Store will be closed soon, it is normal that you don't get updates. On the problem of mounting the phone, it is hard to say. On the question of moving to uBports, yes, you have to reinstall Ubuntu Touch, but there are some tools to save some of your data like contacts, messages and some settings (unfortunately wifi passports have to be reentered and applications have to be reinstalled). If you move to uBports you can get some support from the community to try to solve the problem of mounting.

---

