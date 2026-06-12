---
title: "Folders immediately close/Infinite &quot;starting file manager&quot;"
date: 2011-01-20
forum: Ubuntu One (CLOSED)
---

### Post by LandArch13 on 2011-01-20
Absolute noob here, so go easy on me. 

Not sure where to post  this, I am runing 10.04 LTS, 64 bit and things have been great,  until..... I activated a Ubuntu One account and once I did, my Ubuntu  One folder would immediately close upon opening and my downloads folder  would immediately close upon opening. I delt with it, no big deal. So I  decided that I need to get my crap off the Ubuntu One account so I  downloaded them all from the website onto my desktop. Now none of my  folders immediately close upon opening and ever couple seconds my  desktop flashes and a windows quickly opens and closes stating "starting  file manager". 

I found a couple of posts the looked like fixes,  but nothing has worked. clicked off show_desktop in gconf-editor which  stops the "starting file manager", but does not stop the folder from  immediately closing. I also found this, [http://ubuntuforums.org/showthread.php?t=1603149](http://ubuntuforums.org/showthread.php?t=1603149),  but I don't know hoe to apply the patch nor if I should. I have tried  some other things, but I cant find the threads again to provide. I  believe one was the killall Nautilus then apply Linux Essentials, which I  don't think even ran at all.

Any advice in layman's terms would be greatly appreciated.

---

### Post by LandArch13 on 2011-01-21
I finally came across a fix. I removed Ubuntu One completely form my  system then changed the default file manager to Thunar, as described [here]("https://help.ubuntu.com/community/DefaultFileManager"), rebooted and changed back to Nautilus. So far so good, but I am thinking of reinstalling Ubuntu One to see what happens.

---

### Post by altor on 2011-01-22
> **LandArch13 said:**
> I finally came across a fix. I removed Ubuntu One completely form my  system then changed the default file manager to Thunar, as described [here]("https://help.ubuntu.com/community/DefaultFileManager"), rebooted and changed back to Nautilus. So far so good, but I am thinking of reinstalling Ubuntu One to see what happens.

I solved the same problem just removing U1 (reinstalling again infinite file manager).
Do someone knows if there is already a bug open?
And how is it possible to open such a bug?
Thanks

---

