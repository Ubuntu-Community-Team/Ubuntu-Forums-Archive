---
title: "Which Ubuntu to install"
date: 2012-02-10
forum: Ubuntu Studio
---

### Post by themuseman on 2012-02-10
I have XP on a desktop doing midi/digital audio, which is fine for now but want eventually to move to Ubuntu on this desktop ... the point is I have some familiarity with midi and digital audio, and I have installed Ubuntu on another desktop. 

I also have a EEE 1005HA netbook that I am not getting much use out of, so I'm thinking of installing Ubuntu on it and trying to get it set up to do some simple midi and digital audio, and have portability. The processing power is limited, Intel Atom N280, but I'm hoping to do some simple basic things to get experience with the Linux world of digital audio. I hope to get a USB midi/audio interface, but in the meantime I can get some of the software setup. 

So, here are my initial questions:

1. Should I install the standard version of Ubuntu or should I install Ubuntu Studio?
2. I'm thinking that, besides the support software, all I will need to install is Ardour. Will the netbook have enough power for this?
3. Any other comments or recommendations?

Thanks, 
Lare

---

### Post by sudodus on 2012-02-10
I am running Ubuntu Studio 11.04 (which has gnome desktop environment). The advantage is that the software is already installed, and it is possible to install it to get low latency selecting a suitable kernel. Otherwise it makes no big difference from the other flavours of Ubuntu.

I think you should try if the netbook has enough power. And Ubuntu Studio cannot be run live, so test that with another flavour for example vanilla Ubuntu or Xubuntu (and install Ardour temporarily to the live system).

---

### Post by Hylas de Niall on 2012-02-10
What put me off doing a similar thing is screen size, I doubt Ardour would be very easy to use on 1024x600, but Traverso fitted well enough

---

### Post by themuseman on 2012-02-11
Which Ubuntu to install is no longer a serious issue for me ... the ASUS netbook is as good as dead. Been having trouble with the keyboard (as many others have had) ... thought it was fixed ... problem just returned ... but in addition, the cmos battery is dead. Guess it will go on the parts shelf.

Lare

---

### Post by sgx on 2012-02-11
take it apart and replace the battery, perhaps a keyboard ribbon
connector is loose. Metal strips can be polished with a pencil erasure
to improve connections.  Take digital photos of each step, to insure
getting it back together.  netbook disasssembly: you're not alone!

[https://www.google.com/search?q=%22netbook+disassembly%22&hl=en&authuser=0&num=10&lr=&ft=i&cr=&safe=images](https://www.google.com/search?q=%22netbook+disassembly%22&hl=en&authuser=0&num=10&lr=&ft=i&cr=&safe=images)

---

### Post by CivilizationII on 2012-02-20
If you don't have any idea or any willing to get very basic knowledge to set up alsa (today, there is no more anything to do here) and jack, the best distro could be Ubuntu studio.

Otherwise, Ubuntu standard is much more reliable, and to my opinion much more suited to handle sound. You only need to know the names of the packages you will need to install, it is very likely you already know them.

---

### Post by Noobuntu Guy on 2012-02-21
Well,
 
I'm only one step ahead of you.  I just installed Ubuntu on my eeePC 1005HA this weekend.  I went with the standard ubuntu 11.10.  I haven't had any issues.  Everything seems to work "Out of the Box" and it's running a lot faster than the Windows XP SP3 that it was running in.  
 
I chose the standard distro over Lubuntu (the lightweight edition) because it seemed a bit more polished and my wife is the primary user of the netbook (She likes easy and refined interfaces like iOS).

---

### Post by roelforg on 2012-02-21
> **Noobuntu Guy said:**
> Well,
 
I'm only one step ahead of you.  I just installed Ubuntu on my eeePC 1005HA this weekend.  I went with the standard ubuntu 11.10.  I haven't had any issues.  Everything seems to work "Out of the Box" and it's running a lot faster than the Windows XP SP3 that it was running in.  
 
I chose the standard distro over Lubuntu (the lightweight edition) because it seemed a bit more polished and my wife is the primary user of the netbook (She likes easy and refined interfaces like iOS).
Tip: if you wanna run your old XP apps on it, install wine;
Execute this in a terminal:
```

sudo apt-get update
sudo apt-get install wine1.3 winetricks

```
Copy the installers to your ubuntu, mark the exec bit, click on it and let it run.

If it doesn't work, or the installer/program won't start: PM me, i'll tell you how to determine the problem and install missing components (as is usually the case).
Note: i'm bad at tracking threads so the PM is a good idea.

---

### Post by themuseman on 2012-02-24
Thanks for all the comments and suggestions. Lare

---

