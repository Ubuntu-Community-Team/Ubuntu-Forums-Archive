---
title: "testing unity7 on xubuntu"
date: 2017-09-18
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-09-18
Hi all,

Anyone on the U+1 team or in UDV that would like to test unity7 alongside xubuntu distribution please do so. That would mean you would have to download the ISO from the daily:  [http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

..and then do, in terminal

```

sudo apt-get install unity-session

```

There is one month left before this cycle (17.10) is released and I would appreciate any testing or input.

Regards..

---

### Post by ventrical on 2017-09-18
The unity dash will report 'recently used' whereas ubuntu-desktop install will not. I know there are zeigiest issues. Other wise we ave a beautifully working unity7 desktop with the snapiness of xubuntu :)

scootching around with mouse.... xubuntu much more friendlier to unity7 stack.

---

### Post by ventrical on 2017-09-18
Can't drag files (screenshots) from one directory to desktop. Desktop folder bounces files back.

---

### Post by Chanath on 2017-09-18
@ventrical

Installed fresh Xubuntu after so long. Earlier, it was just upgrading upwards. Xubuntu is so snappier, must think twice, before installing Unity alongside it. Too much time wasted on the slower Gnome desktop, default or not.

---

### Post by ventrical on 2017-09-18
> **Chanath said:**
> @ventrical

Installed fresh Xubuntu after so long. Earlier, it was just upgrading upwards. Xubuntu is so snappier, must think twice, before installing Unity alongside it. Too much time wasted on the slower Gnome desktop, default or not.

Yes .. it is very sleek and fast.

---

### Post by Chanath on 2017-09-19
> **ventrical said:**
> Yes .. it is very sleek and fast.

I decided against installing Unity alongside Xubuntu. 
Its a different thing to install Unity on Ubuntu Gnome (or default).

---

### Post by ventrical on 2017-09-19
> **Chanath said:**
> I decided against installing Unity alongside Xubuntu. 
Its a different thing to install Unity on Ubuntu Gnome (or default).

Yes.. xubuntu uses thunar FM . The other, nautilus plus other depends. There is some breakage here.

---

### Post by wgarcia on 2017-09-20
Just a constructive question: Are these tests (trying to install unity-session on Xubuntu or Lubuntu) relevant? I mean, if I try for instance to install lubuntu-desktop on Xubuntu I presume I will also cause breakage, but this doesn't mean lubuntu-desktop is not well maintained in the repos. If we want to help to keep unity-desktop well maintained in the repos, in my opinion the relevant test would be to install Ubuntu default (now with Gnome), and afterwards install unity-session and see it there are breakages, both in Gnome or in Unity.

---

### Post by ventrical on 2017-09-20
> **wgarcia said:**
> Just a constructive question: Are these tests (trying to install unity-session on Xubuntu or Lubuntu) relevant? I mean, if I try for instance to install lubuntu-desktop on Xubuntu I presume I will also cause breakage, but this doesn't mean lubuntu-desktop is not well maintained in the repos. If we want to help to keep unity-desktop well maintained in the repos, in my opinion the relevant test would be to install Ubuntu default (now with Gnome), and afterwards install unity-session and see it there are breakages, both in Gnome or in Unity.

@wgarcia,

Thank you for your thoughtful question.  I agree that we should keep testing default cases of unity7 on gnome as this is what the developers have requested of us to do. I have four separate boxes on a kvm with hard installed 17.10 gnome default plus with unity7 installs updated/upgraded everyday. I also test the current ISOs now and again and do fresh installs. So far - not much breakage but there are cases where there is some breakage (and perhaps some in the next couple of weeks).

One of the reasons I think it is relevant to test the other ubuntu flavors is that it allows me to compare some of the different breakages on those installs. It also has the dual purpose that I can test the ISO cases of lubuntu, xubuntu and the other flavors , when I have time, on the daily currents. I have 7 boxes in my Ubuntu shack and so  I have the extra hardware resources to do hard installs - so - perhaps it is not really  relevant to testing unity on default gnome and may not help in unity7 maintenance - as to why I created a separate thread  on this - but I just thought it would be interesting to do this experiment . 

  I hope this answers, in part,  some of your question.

Regards..

---

### Post by Chanath on 2017-09-20
Usually a Lubuntu or Xubuntu user will not install Gnome or Unity alongside it--its counter effective as both Lubuntu and Xubuntu are snappier. When you use PCmanFM or Thunar, you just don't want to use the new Nautilus, maybe the older Nautilus or a fork of it. In PCmanFM or Thunar, every configuration is in front of you.

That said, the best way to test Unity is to have it alone. I have one partition with Unity alone. And, it works without a problem. One may even learn to like Nautilus, but for day to day work, I use PCmanFM there. ([https://ubuntuforums.org/showthread.php?t=2367282](https://ubuntuforums.org/showthread.php?t=2367282))

I also have a Gnome alone partition, and both Gnome alone and Unity alone installs don't have ubuntu-...-desktop in them. So, a dist-upgrade won't trouble them (I hope). If unity-session is taken off the repos, it cannot be uninstalled from the laptop.

---

### Post by ventrical on 2017-09-20
@Chanath,

Just a reminder; I was requesting anyone who would like to:

> 
Hi all,

Anyone on the U+1 team or in UDV that would like to test unity7  alongside xubuntu distribution please do so. That would mean you would  have to download the ISO from the daily:  [http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)


I am not asking for the best way to test it in this thread. That is already taken care of in another thread.

[https://ubuntuforums.org/showthread.php?t=2363847](https://ubuntuforums.org/showthread.php?t=2363847)

Regards..

---

### Post by ventrical on 2017-09-20
> **wgarcia said:**
>  If we want to help to keep unity-desktop well maintained in the repos, in my opinion the relevant test would be to install Ubuntu default (now with Gnome), and afterwards install unity-session and see it there are breakages, both in Gnome or in Unity.

Reviewing this I will request Cariboo that this thread be closed.

Regards..

---

### Post by slickymaster on 2017-09-20
Closed per OP request.

---

