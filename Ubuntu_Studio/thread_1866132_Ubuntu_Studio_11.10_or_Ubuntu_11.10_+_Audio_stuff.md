---
title: "Ubuntu Studio 11.10 or Ubuntu 11.10 + Audio stuff?"
date: 2011-10-21
forum: Ubuntu Studio
---

### Post by ShinHadoken on 2011-10-21
Hi, 

I've been meaning to install Ubuntu Studio on my laptop for some time now. Currently I'm running Ubuntu 11.04. I went to ubuntustudio.org and I could not find the latest 11.10 release. I was wondering, firstly, is it out there somewhere and I just haven't found it, and secondly, would I be better off installing Ubuntu Studio 11.10, or Ubuntu 11.10 with Ubuntu Studio stuff added on? 

PS: How exactly would I add that stuff on? I know in the old days you just went into Synaptic and found the Ubuntu Studio groups and installed them, and that would install like all of the audio apps, and all of the graphic apps, etc. How would I do that in the new Ubuntu Software Center?

Thanks a lot for your help/feedback!

---

### Post by jejeman on 2011-10-21
Now, as of ubuntustudio 11.10, it uses Xfce Desktop Environment. So instaling it on Ubuntu would probably make an Xfce session. I suggest in that scenario to install just the applications you need. Not ubuntustudio meta packages. 
To have another DE sesion is not a big deal, you don't need to use it. It all depends waht you need/like.

You can find the release here
[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/)

Exept the Xfce, new thing I could find in this release, on my brief inspection, is pulse jack sink, ladish.
So if you like to be able to play pulseaudio thru jack, have ladish sessions out of the box and everything else like in pervious versions,  go for clean install of ubuntustudio 11.10. But, you should first read the release notes:
[https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes](https://wiki.ubuntu.com/UbuntuStudio/11.10release_notes)

---

### Post by Totalchaos on 2011-10-22
the most efficient decision actually will be studio 10.04 + realtime kernel + backports

---

### Post by jejeman on 2011-10-22
Personally don't find the need for rt kernel on 10.04. The default preempt kernel does everything fine, so far.

---

