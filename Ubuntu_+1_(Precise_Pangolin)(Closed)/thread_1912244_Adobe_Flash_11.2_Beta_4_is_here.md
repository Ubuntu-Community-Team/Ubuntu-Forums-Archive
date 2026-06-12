---
title: "Adobe Flash 11.2 Beta 4 is here"
date: 2012-01-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-01-20
Beta 3 still crashes far too often for my liking. Hope Beta 4 is an improvement.

[http://labs.adobe.com/downloads/flashplayer11-2.html](http://labs.adobe.com/downloads/flashplayer11-2.html)

---

### Post by effenberg0x0 on 2012-01-20
I gave up, won't even try it. I bet the super-fresh-hot new feature is that it will not only use all the available CPU but also kill other PIDs and take all of the resources to it. The roadmap is likely to include code that, in the near future, will also slow/stop your cooler while using 100% of the CPU, hopefully causing true financial damage to users. Not a promise yet, but it looks like they're working hard on it.

---

### Post by portis on 2012-01-20
Just tried it. Disappointed.

With EnableLinuxHWVideoDecode=1, it crashes a lot;
with EnableLinuxHWVideoDecode=0, all human faces turn into blue!!!

> **paul_in_london said:**
> Beta 3 still crashes far too often for my liking. Hope Beta 4 is an improvement.

[http://labs.adobe.com/downloads/flashplayer11-2.html](http://labs.adobe.com/downloads/flashplayer11-2.html)

---

### Post by philinux on 2012-01-20
> **portis said:**
> Just tried it. Disappointed.

With EnableLinuxHWVideoDecode=1, it crashes a lot;
with EnableLinuxHWVideoDecode=0, all human faces turn into blue!!!

+1 back to the stable version.

---

### Post by Sworddragon on 2012-01-20
> **portis said:**
> With EnableLinuxHWVideoDecode=1, it crashes a lot;

Even on the stable version there are problems with this. If I try to fast-forward a video sometimes the frame is freezing but the video is still playing (I'm even hearing sound). If I replay the video it is freezing on the first frame.

---

### Post by paul_in_london on 2012-01-21
Well I've been using 11.2 Beta 4 since last night and it still seems very buggy to me. Maybe a slight improvement on Beta 3, but not by much IMHO. Mostly refreshing the page is enough to recover from a crash, but last night I got one of those really annoying crashes I'd seen all too often with Beta 3. Firefox froze completely, I had to force quit and then manually kill the flash plugin process. When I restarted FF all of my (many) tabs were gone. Luckily I had a recent backup of sessionstore.js. Touch wood, that hasn't happened again today so far.

EDIT: this is 64 bit btw.

---

### Post by paul_in_london on 2012-01-21
It's been driving me crazy again [tonight and today] so I've now installed Session Manager (the FF add-on). I wish I'd done that long ago actually.

Session Manager shows me I'm using 186 tabs. Is that a lot? :lolflag:

---

### Post by kevpan815 on 2012-01-22
How do you install that package on Ubuntu? So far in the read me I found instructions only for installing it on .RPM systems like Red Hat Fedora.

---

### Post by effenberg0x0 on 2012-01-22
> **paul_in_london said:**
> It's been driving me crazy again [tonight and today] so I've now installed Session Manager (the FF add-on). I wish I'd done that long ago actually.

Session Manager shows me I'm using 186 tabs. Is that a lot? :lolflag:
Hey Paul, 
I might give it a try as you mention a little more stability. I got really mad about some browser crashes with latest versions (like latest all versions) and was not using it at all anymore. 
Now, 186 tabs? Meh, it's OK, everyone does that :)

Regards,
EFfenberg

---

### Post by paul_in_london on 2012-01-22
> **kevpan815 said:**
> How do you install that package on Ubuntu? So far in the read me I found instructions only for installing it on .RPM systems like Red Hat Fedora.

Taking the 64 bit version as an example, download flashplayer11-2_p4_install_lin_64_011912.tar.gz and then (assuming it's in ~/Downloads):

```
cd /usr/lib/adobe-flashplugin/
sudo mv ~/Downloads/flashplayer11-2_p4_install_lin_64_011912.tar.gz .
sudo tar -zxvf flashplayer11-2_p4_install_lin_64_011912.tar.gz
```

---

### Post by paul_in_london on 2012-01-22
> **effenberg0x0 said:**
> Hey Paul, 
I might give it a try as you mention a little more stability. I got really mad about some browser crashes with latest versions (like latest all versions) and was not using it at all anymore. 
Now, 186 tabs? Meh, it's OK, everyone does that :)

Regards,
EFfenberg

Hi effenberg0x0,

Give it a go. :lolflag:

The Bar Tab add-on is a great help in FF when you have lots of tabs open.

Session Manager is handy too (makes it less painful when flash trashes your session).

Regards,

Paul

---

