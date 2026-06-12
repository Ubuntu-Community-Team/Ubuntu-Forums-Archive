---
title: "Trouble getting DVD to read in 12.04 beta"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by geovino on 2012-03-17
I've installed 12.04 beta 64 bit and did updates and install ubuntu-restricted-extras and DVDs still will not play. what else is needed to play DVDs? 

I've used Ubuntu for many years and haven't had this problem, unless its a bug in this beta version.

Any ideas?

---

### Post by kansasnoob on 2012-03-17
> **geovino said:**
> I've installed 12.04 beta 64 bit and did updates and install ubuntu-restricted-extras and DVDs still will not play. what else is needed to play DVDs? 

I've used Ubuntu for many years and haven't had this problem, unless its a bug in this beta version.

Any ideas?

I don't think Medibuntu is ready for Precise yet so you might try this:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Remember, this is a dev release so some things won't work yet, it should not be used as your only OS!

---

### Post by geovino on 2012-03-17
> **kansasnoob said:**
> I don't think Medibuntu is ready for Precise yet so you might try this:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Remember, this is a dev release so some things won't work yet, it should not be used as your only OS!

I even tried to install libdvdcss2 and it says "has no installation candidate" 

I'll wait until the final comes out April 26 and reinstall then. Thanks.

---

### Post by mc4man on 2012-03-17
> **geovino said:**
> I even tried to install libdvdcss2 and it says "has no installation candidate" 


If libdvdread4 is installed then this should work fine
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by grahammechanical on 2012-03-17
I recently ran a 12.04 test suite that included playing a DVD.

At first I could not get a DVD to play. I installed Ubuntu Restricted Extras because was running a default Beta 1. And I was able to play the DVD.

What is happening when you insert the DVD?

We are supposed to get an ask what to do box. From there we select Movie Player (Totum) then the movie player should load with the movie ready to play.

I noticed that to get my DVD movie to play I had to click a menu on the screen. That may have just been something to do with my DVDs.

But clicking the normal play buttons did not work until I clicked a menu item on screen.

So, tells us what you get when you put the DVD in the drive.

Regards.

---

### Post by geovino on 2012-03-17
gave another try and ran:

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)

sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

from: [http://ubuntuforums.org/showthread.php?t=1737727](http://ubuntuforums.org/showthread.php?t=1737727)

VLC is working now. :)

---

