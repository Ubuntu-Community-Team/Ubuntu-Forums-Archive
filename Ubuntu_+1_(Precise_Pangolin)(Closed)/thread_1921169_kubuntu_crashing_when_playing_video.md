---
title: "kubuntu crashing when playing video"
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lefuuuu on 2012-02-06
everytime I try to play an avi in any media player it logs me out.I've never experienced anything like it. Is anyone else experiencing this?

---

### Post by redcylon on 2012-02-06
> **lefuuuu said:**
> everytime I try to play an avi in any media player it logs me out.I've never experienced anything like it. Is anyone else experiencing this?

It did happened to me after I upgraded to proprieatary/close ATI driver. Revert to original driver and able to play videos again.

---

### Post by lefuuuu on 2012-02-06
> It did happened to me after I upgraded to proprieatary/close ATI driver. Revert to original driver and able to play videos again.

Thanks, that fixed it for me.

---

### Post by slayner117 on 2012-02-07
I understand it's in the alpha, and there are still plenty of bugs, it's not urgent I was just curious if there was a simple fix. Basically what's happening is whenever I try to play a video with VLC it will play for roughly 2 seconds, crash, and log me out. 

It also does this with the default video player, please forgive me for not remembering the name. I have never had an issue with this, and I don't know if it matters, but my videos are on a different Hard Drive. 

thank you in advance.

---

### Post by P-I H on 2012-02-08
Their is already a thread about this.
[http://ubuntuforums.org/showthread.php?t=1921169](http://ubuntuforums.org/showthread.php?t=1921169)
You get the crash when you use the proprietary drivers. I have this proglem now with a Radeon 5450 card and some weeks back when I used an Nvidia GTS250 card. Ithink it is the new xserver and the proprietary drivers that don't like each other. If you have an AMD card the Gallium driver works fine.

---

### Post by slayner117 on 2012-02-08
Actually, How do I get the Gallium Driver? I have an ATI 6950

---

### Post by P-I H on 2012-02-08
Thats the open driver provided in the standard installation.

In case you have used **Additional drivers** to install fglrx, you just need to use it to uninstall the FGLRX graphic driver.

In case it is installed in some other way it might work to follow the instructions about **Removing Catalyst/fglrx** on this page
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

The instruction relates to Oneiric and I do not know if it will work for Precise. In my case I have used **Additional Drivers** both to install and uninstall.

---

### Post by slayner117 on 2012-02-08
Works perfectly thank you.

---

### Post by nardusg on 2012-02-15
Issues playing video with latest catalyst drivers:

[http://ati.cchtml.com/show_bug.cgi?id=337#c7](http://ati.cchtml.com/show_bug.cgi?id=337#c7)

Not a solution but a workaround; add the following snippet to your
/etc/X11/xorg.conf, that way the crashy code won't be executed:

Section "Extensions"
       Option "XVideo" "Disable"
EndSection

---

### Post by nardusg on 2012-02-15
Issues playing video with latest catalyst drivers:

[http://ati.cchtml.com/show_bug.cgi?id=337#c7](http://ati.cchtml.com/show_bug.cgi?id=337#c7)

Not a solution but a workaround; add the following snippet to your
/etc/X11/xorg.conf, that way the crashy code won't be executed:

Section "Extensions"
       Option "XVideo" "Disable"
EndSection

---

### Post by cariboo on 2012-02-15
Merged two threads on the same subject.

---

### Post by rrinjapan on 2012-02-23
Thanks for this!

---

