---
title: "Intel/Amd Hybrid graphics"
date: 2014-03-03
forum: Ubuntu Development Version
---

### Post by Burkey on 2014-03-03
Not sure if this is the right place, however I just installed 14.04 on a new SSD, it setup the MESA driver by default (MESA 10 looks hot) and the usability was very nice.

I then switched to the ATI proprietary driver which crashed unity... after an 

```
aticonfig -- intial
```

I was back in business, first up noting vsync still does not work, and then trying a game (World of Warcraft) in wine FPS was barely above the MESA offering.

So, my question is.. has anyone been testing this sort of a combo out (laptop with Ivy Bride + AMD/ATi 7670m) and got suggestions?  I have reverted back to MESA as I cannot stand the lack of vsync

And my second question is.. with MESA, how do I get it to use the ATi chip instead of the Intel one?  Can I have it launch certain apps on different GPU, change what one is in use etc.  Maybe I have it all wrong but I thought MESA 10 included an ATI xorg driver of sorts, but I do not understand how I switch between the GPU's in use.

Cheers!

---

### Post by Bashing-om on 2014-03-03
Burkey; Hi !

An ongoing endeavor to make this work, some with great results.
see:
[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)
Our Mega - Thread on this issue:
[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)

As to what now applies in release 14.04, I just have no idea.

[INDENT][INDENT]you are not alone
[/INDENT][/INDENT]

---

### Post by Burkey on 2014-03-03
Hi Bashing, thanks for the reply.  I have seen those manual steps on 13.04 & 13.10 but was really hoping this sort of thing was fixed in 14.04.  Making people jump through hoops like this is what chases people away and it is not something that is rare... in fact I would dare say the number of people getting laptops is actually increasing and sine every Intel CPU nowadays has a GPU inbuilt, hybrid setups are pretty much becoming the norm.

---

### Post by Bashing-om on 2014-03-03
Burkey; Hey,

It may be related to vendor lock in, if the manufacturers are concerned about "proprietary" information and will not provide for their hardware on a linux system, 
We do the best we can to reverse engineer their hardware.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

in my small frame of reference, I can not tell what deals the big boys make.

It is a tough world out there and we 
make do - the best we can - with what we have to work with.

---

### Post by Burkey on 2014-03-03
Yeah I understand there is a lot of complications with closed source, not to mention the quite low quality ATi drivers!

The HybridGraphics effort looks admirable, I did not realise it was something of an option when I was on 13.10 last year so perhaps the pxpress additions will sort out a lot of the problems.  Previously it come down to getting some DEB files of a specific intel driver, a specific udev deb and then manually installing to make it work.. which then broke whenever an update come along because it usually replaced the intel+udev files (fglrx usually rebuilt thanks to dkms)

I am just really hoping 14.04 will be somewhat more user friendly in this regard and am interested if that Hybrid graphics work will continue for 14.04

The other mentioned issue of no vsync is a real downer too, but my guess is ATi have to fix that (I don't really know though).

---

### Post by Bashing-om on 2014-03-03
Burkey; Yeah,

veering slightly off topic:
Things are coming along, albeit not nearly as quick as the hardware that is available. 
Nvidia has also gotten onboard with DKMS support, making things a little easier in that realm.

it is sad that we in the linux realm
[INDENT][INDENT]just make do _________but then again, that too is a part of being linux
[/INDENT][/INDENT]

---

### Post by Burkey on 2014-03-03
It is slowly changing though ;) ATi and nVidia will be doing battle for SteamOS supremacy which should benefit all of us.

---

