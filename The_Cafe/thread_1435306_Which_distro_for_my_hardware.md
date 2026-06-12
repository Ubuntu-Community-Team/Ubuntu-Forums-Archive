---
title: "Which distro for my hardware?"
date: 2010-03-21
forum: The Cafe
---

### Post by Blackmag+c on 2010-03-21
Hello to all 
I don't really know where to put this but...
I have a question as to what would be the best buntu flavour or indeed distro for my current hardware.

The specs are as follows:

Asus K8N motherboard (754)
Sempron 3100+ (1.81ghz)
1GB of DDR SDRAM
Geforce 7600 GS (256mb)

Perhaps the most crucial part of this request is that I have a 18 channel phonic helix fire-wire mixer which I wish to connect and use once the Linux is installed (I don't know how difficult this is).

Thanks in advance ;)

---

### Post by undecim on 2010-03-21
I don't see any reason that most distros wouldn't run on it.

This is more of a question of what you want rather than what your hardware can handle.

---

### Post by Leisko on 2010-03-21
Try it, feel it :D Then you'll see which distro works best

---

### Post by cascade9 on 2010-03-21
The fire-wire mixer might be interesting to get going, but apart from that you should be fine with almost any distro. KDE4 might run a bit sluggish, depending on how much you notice that sort of thing, so I might avoid KDE distros. 

BTW, it might even run 64bit, depending on extactly what 3100+ you have (some are 64bit, some arent)

---

### Post by Blackmag+c on 2010-03-21
it is indeed 64 bit but i've never had a 64bit OS I don't believe

what are the benefits of this?

I have never fully grasped the point of it to be honest..? :)

---

### Post by Psumi on 2010-03-21
> **Blackmag+c said:**
> it is indeed 64 bit

what are the benefits of this?

I have never fully grasped the point of it to be honest..? :)

64-bit is faster than 32-bit in some regards, it can hold more data per WORD, etc. It is not susceptible to the UNIX time problem... etc.

32-bit can have PAE, so having more than 4 GB of RAM isn't exactly a WOW factor.

---

### Post by cascade9 on 2010-03-21
> **Blackmag+c said:**
> it is indeed 64 bit but i've never had a 64bit OS I don't believe

what are the benefits of this?

I have never fully grasped the point of it to be honest..? :)

Aside for addressing 4GB+ of RAM (which, like Psumi said, you can get around with 32bit PAE kernel) its got some advantages. For things like video/audio encoding, and some other programs that to be honest I dont use, 64bit is much faster. 

(pure opinion folowing, its arguable that I'm wrong here)- 64bit is normally about 5-15% faster for most things that 32bit as well.

---

### Post by Blackmag+c on 2010-03-21
Well I'm all about speed at this point

My XP install has long been likened to the snail.

So thank you for the explanation.

I'm currently looking into xubuntu which I think strikes a balance between quickness and attractiveness.

---

### Post by Tikkyca on 2010-03-21
Almost every distro will run fine on that config,you should install ubuntu,because it is stable.

---

### Post by cascade9 on 2010-03-21
I admit, I havent tried Xubuntu 9.10 (which I've heard is better) but the earlier version are not really any faster than standard gnome unbuntu. 

For xfce on ubuntu, get the 'alternate install' version and then install the packages manually. I reccomend this-

sudo apt-get install xorg xdm xfce4 

Then get whatever extra stuff you need/want manuanlly as well. Its _much_ faster and lighter than the xubuntu-desktop install.

---

### Post by Psumi on 2010-03-21
> **cascade9 said:**
> I admit, I havent tried Xubuntu 9.10 (which I've heard is better) but the earlier version are not really any faster than standard gnome unbuntu. 

For xfce on ubuntu, get the 'alternate install' version and then install the packages manually. I reccomend this-

sudo apt-get install xorg xdm xfce4 

Then get whatever extra stuff you need/want manuanlly as well. Its _much_ faster and lighter than the xubuntu-desktop install.

Or follow this: [http://ubuntuforums.org/showpost.php?p=8754516&postcount=3](http://ubuntuforums.org/showpost.php?p=8754516&postcount=3)

for xfce.

In lucid, you have slim available in the repos.

Right now, I'm boasting lucid beta netboot xfce with slim, and it's very snappy.

---

### Post by Blackmag+c on 2010-03-21
great link 

thanks :D

---

