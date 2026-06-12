---
title: "uTorrent"
date: 2009-10-04
forum: Wine
---

### Post by Gyppie on 2009-10-04
Hi!

I installed utorrent by using wine in ubuntu 9.04. Does anybody know how to start utorrent at boot, so I dont hove to login to the desktop to start it manually when doing a reboot?


Gyppie

---

### Post by asdfoo on 2009-10-04
> **Gyppie said:**
> Hi!

I installed utorrent by using wine in ubuntu 9.04. Does anybody know how to start utorrent at boot, so I dont hove to login to the desktop to start it manually when doing a reboot?


Gyppie

Only if you set your desktop to login automatically without a password.

---

### Post by Drakebyte on 2009-10-04
System -> Administration -> Login Screen, you can turn on automatic login there.

After that you will need to go to:
System -> Preferences -> Start Up Applications

Being there, add a new entry:
> Name: uTorrent
Command: wine <path to utorrent>/utorrent.exe [i](probably: "wine /home/**your account name here**/.wine/dosdevices/c:/Program\ Files/uTorrent/utorrent.exe", or anything along these lines)
Description: Whatever you want here.

That should be all :)! Good luck, feel free to ask anything.
--D

---

### Post by tuxxy on 2009-10-04
Deluge is a good client also if you still have difficulty.

---

### Post by Enigmapond on 2009-10-04
I just wanted to say I used uTorrent before I switched to Ubuntu. I did as you have done and ran it in Wine...but it still wasn't like it was before. I highly recommend Deluge, as well. Very good client and if you forward the proper ports and such it will fly. It's not atypical for me to get 1+mb/s download speeds on very popular torrents...

Cheers!:)

---

### Post by Gyppie on 2009-10-05
Ok. Thanks. I will also check Deluge out too.....

Gyppie

---

### Post by Gyppie on 2009-10-05
Hi Again!

I just want to say thanks to you guys again who recomended Deluge. I fell in love at first run, most because of the web-ui.

Thanks again guys


Gyppie :guitar:

---

### Post by psablo on 2009-10-05
I use Transmission and have had no problems.
Do you guys think Deluge is better, and why?

---

### Post by Shmalignant on 2009-10-05
I like Transmission.

---

