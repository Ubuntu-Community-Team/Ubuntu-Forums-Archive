---
title: "I can't find any PPA to get a kernel-rt for my Ubuntu 11.04 !"
date: 2012-10-11
forum: Ubuntu Studio
---

### Post by feb7 on 2012-10-11
Hi, I've been trying for two whole days to look for a kernel-rt but unlucky some PPA's let me download only several .deb's so I can't install any kernel-rt for my Ubuntu 11.04...  Do You Have any suggestions to give me ??' Thanx !!! And have a good time !!! ;)

---

### Post by jejeman on 2012-10-11
That train is long gone, plus 11.04 is not supported anymore (well until 28. october).
Only solution for you is to build one yourself, or to switch to 12.04.

At one moment there was lowlatency kernel from Abogani's PPA... I have that installed on one computer, the 3.0 version. Maybe I can upload the deb file, if I have one. But I don't know if that is a good solution, and anyway I will not be able to that soon.

See if there is this lowlatency version available somewhere, it works good with Ubuntu studio 11.04.

---

### Post by feb7 on 2012-10-11
Thanx for the "bad" news !!! :P lol!!! The fact is that I don't want to upgrade my 11.04 to 12.04 but on the other hand I really don't know how to compile a kernel-rt ... Are there any links about this stuff ??? Anyway I'm trying to dualboot 11.04 with Puredyne ( Beacuse I'm learning Fluxus and Supercollider ).
See you !

---

### Post by Bucky Ball on 2012-10-11
I thought the rt kernel was default now. I was looking into it awhile ago and was led to believe it didn't exist as a specific Ubuntu-rt kernel anymore ...

I run UStudio on the desktop and that doesn't use it anymore, either.

---

### Post by feb7 on 2012-10-11
I've noticed that about Ubuntu 11.04 but I just believed that this distro was supported still... At now I'm trying Puredyne 9.11 and I have another kind of problem : the kernel doesn't recognize my wireless network :( I suppose I can't add repository at all via terminal because even this distro perhaps is not supported anymore..... but the rest works fine (Fluxus, Jack audio server) and at the end that's all I need... well I'll try in any other way to install the b43 firmware....

---

### Post by jejeman on 2012-10-11
As I recall pure dyne is based on Ubuntu 9.10, which ended its support on 30 April 2011.
for b43 look at this
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

### Post by feb7 on 2012-10-12
Thank You so much for Your help. Yesterday I even tried  this for the b43's fw but unlucky my puredyne version 9.11 can't get the gdebi application :(and furthermore I can't use the Nautilus options to read and write on my filesystem ( I need to put some .png's into one of the fluxus folders and I don't know what to do !!! Please help me if You can :S !!!) Do you have any suggestions about that??? I was also thinking to install a 10.04 server lts (I've another laptop with this ubuntu and I think it's really a great O.S.by the way I was thinking to erase formatting and resetting everything ....reinstalling everything !!!!! :S( Fluxus is a real thread for compiling and installing it.... but I'll try like this if there are no other ways.

---

### Post by jejeman on 2012-10-12
You don't need gdebi to install deb package. As stated in manual
```
:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*
```You can use dpkg to install deb package.
>  I can't use the Nautilus options to read and write on my filesystem I don't understand this, what options?

---

### Post by feb7 on 2012-10-13
Thank You jejeman but Yesterday I decided to give up with both Puredyne 9.11 and the 11.04 ... there's no way to do other operations too... So I'm installing at now the 10.04 Lts one that I find it very cool, versatile and stable for the multimedia media-warez ! Maybe the next week I'll try the 12.04 Precise. :D Have a nice day.

---

### Post by feb7 on 2012-10-13
I wanted to say the nautilus command and not options ... sorry !!! :P

---

