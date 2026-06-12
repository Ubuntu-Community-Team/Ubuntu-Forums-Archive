---
title: "Xubuntu reverting to non-pae kernel?"
date: 2012-03-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-03-17
Just noticed this:

[https://wiki.edubuntu.org/Xubuntu/Meetings/Archive/Minutes/2012-03-14](https://wiki.edubuntu.org/Xubuntu/Meetings/Archive/Minutes/2012-03-14)

> cjwatson will look at using non-PAE kernel with xubuntu precise i386, knome to follow-up with him if problems arises

And maybe the alternate images have already been changed:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009](https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009)

I hope it's true .......... now if Lubuntu follows suit we should be in good shape :D

NOTE: There are currently no daily images for Xubuntu i386 so we'll have to be patient.

UPDATE: Lubuntu doing likewise:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/958866](https://bugs.launchpad.net/ubuntu-cdimage/+bug/958866)

UPDATE #2: The alternate images are still borked as of March 21, so I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/961218](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/961218)

WOW! Colin Watson got right on this and I'm testing images now!

---

### Post by dentaku65 on 2012-03-17
> **kansasnoob said:**
> Just noticed this:

[https://wiki.edubuntu.org/Xubuntu/Meetings/Archive/Minutes/2012-03-14](https://wiki.edubuntu.org/Xubuntu/Meetings/Archive/Minutes/2012-03-14)



And maybe the alternate images have already been changed:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009](https://bugs.launchpad.net/ubuntu-cdimage/+bug/955009)

I hope it's true .......... now if Lubuntu follows suit we should be in good shape :D

NOTE: There are currently no daily images for Xubuntu i386 so we'll have to be patient.

+1 here
I really hope that Xubuntu Pangolin will use NON-PAE kernel for i386 (really nonsense decision using PAE only kernel for i386)

I'm downloading the alternate right now, I'll feddback on it.

---

### Post by grahammechanical on 2012-03-17
It makes sense for these light Ubuntus to have non-pae because the hardware being discussed will give a better user experience with these lightwieght Ubuntus than perhaps standard Ubuntu. And this kind of hardware may not be compatible with the pae kernel. Is that not the reasoning?

Regards.

---

### Post by dentaku65 on 2012-03-17
...mmm... there is not live option in alternate CD, did not know that :(

---

### Post by nm_geo on 2012-03-17
> **grahammechanical said:**
> It makes sense for these light Ubuntus to have non-pae because the hardware being discussed will give a better user experience with these lightwieght Ubuntus than perhaps standard Ubuntu. And this kind of hardware may not be compatible with the pae kernel. Is that not the reasoning?

Regards.

+1 graham

I just looked and the Xubuntu non-pae is not spun yet.. Maybe soon..  I am in hope Lubuntu will follow suit..
Only makes sense to me too..

---

### Post by keithpeter on 2012-03-17
Hello All

Probably a good compromise here, the xubuntu and lubuntu flavours defaulting to non-PAE release.

11.10 ran (jogged?) on a Dell C610 P3 with 512Mb of ram. I wrote most of the Unity2d tutorial linked in my sig on that machine, but I have to admit that Scientific Linux 5.7 runs a lot better. The Dell boots off the current i386 Precise cd so I guess it is one of the Pentium Mobile processors that *does* have PAE.

The T42 thinkpad I used to have that was definitely non-PAE could run 11.10 at a very respectable speed and could run full Unity and Gnome-Shell.

---

### Post by kansasnoob on 2012-03-19
Bumped so people notice that Lubuntu is also reverting to non-pae :guitar:

---

### Post by kansasnoob on 2012-03-19
It looks like the first non-pae Xubuntu images are ready for testing:

[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

From the i386 manifest:

> linux-generic	3.2.0.19.21
linux-headers-3.2.0-19	3.2.0-19.30
linux-headers-3.2.0-19-generic	3.2.0-19.30
linux-headers-3.2.0-19-generic-pae	3.2.0-19.30
linux-headers-generic	3.2.0.19.21
linux-headers-generic-pae	3.2.0.19.21
linux-image-3.2.0-19-generic	3.2.0-19.30
linux-image-generic	3.2.0.19.21
linux-libc-dev	3.2.0-19.30

I may have time to test one myself later today ;)

---

### Post by dentaku65 on 2012-03-19
> **kansasnoob said:**
> It looks like the first non-pae Xubuntu images are ready for testing:

[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

From the i386 manifest:



I may have time to test one myself later today ;)
 
I confirm; the release cited is NON-PAE :biggrin:):P
Really good!

---

### Post by Miykel on 2012-03-19
G'Day guys; Would it be possible for you to explain, in simple terms, what PAE is all about ??, I searched on-line and the answers were so complicated I got brain ache trying to understand the relevance of pae and non-pae and how it effects the OS. all I could understand was PAE stands for Physical Address Extension, which is as clear as mud to me.
Kind Regards Miykel

---

### Post by kansasnoob on 2012-03-19
> **Miykel said:**
> G'Day guys; Would it be possible for you to explain, in simple terms, what PAE is all about ??, I searched on-line and the answers were so complicated I got brain ache trying to understand the relevance of pae and non-pae and how it effects the OS. all I could understand was PAE stands for Physical Address Extension, which is as clear as mud to me.
Kind Regards Miykel

Please look here for the moment:

[http://ubuntuforums.org/showpost.php?p=11777302&postcount=3](http://ubuntuforums.org/showpost.php?p=11777302&postcount=3)

I know there are several links to plow through, and it's still not an entire explanation, but I'm busy testing the newest images ;)

I will try to come up with something coherent by Beta 2.

---

### Post by Peripheral Visionary on 2012-03-19
If we stay with the current 12.04 Xubu installation, will regular normal updates bring us the non-pae kernel eventually?

Thanks!

---

### Post by ranch hand on 2012-03-19
> **Miykel said:**
> G'Day guys; Would it be possible for you to explain, in simple terms, what PAE is all about ??, I searched on-line and the answers were so complicated I got brain ache trying to understand the relevance of pae and non-pae and how it effects the OS. all I could understand was PAE stands for Physical Address Extension, which is as clear as mud to me.
Kind Regards Miykel
The link kansasnoob gave you is the place to go for knowledge.

Until you study that the pae kernel is used with 32bit OS's so that they can use more than 3 gigs of ram.

Seeing how Xubuntu and Lubuntu are aimed at older boxes they are very unlikely to have the opportunity to use more than 3 gigs of ram.  If the box has more than 3 gigs it is easy enough to install the pae kernel.

---

### Post by kansasnoob on 2012-03-19
> **Peripheral Visionary said:**
> If we stay with the current 12.04 Xubu installation, will regular normal updates bring us the non-pae kernel eventually?

Thanks!

My best guess is that if you're running the non-pae kernel it will stay that way throughout updates, and vice versa.

But we need to remember that 12.04 is the end of the road for the non-pae kernel! But 12.04 is a 5 year LTS (except for Lubuntu) so it's doubtful too many will still be hanging onto such old laptops by then.

This change should buy those requiring a non-pae kernel another 5 years, thank Colin Watson any chance you get ;)

---

### Post by dentaku65 on 2012-03-19
> **kansasnoob said:**
> My best guess is that if you're running the non-pae kernel it will stay that way throughout updates, and vice versa.

But we need to remember that 12.04 is the end of the road for the non-pae kernel! But 12.04 is a 5 year LTS (except for Lubuntu) so it's doubtful too many will still be hanging onto such old laptops by then.

This change should buy those requiring a non-pae kernel another 5 years, thank Colin Watson any chance you get ;)


afaik, it is possible for sure

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)

:-)

---

### Post by kansasnoob on 2012-03-19
> **dentaku65 said:**
> afaik, it is possible for sure

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)

:-)

Even before this change to the Xubuntu and Lubuntu images it would still have been possible to install a **buntu based 12.04 distro with non-pae, just more difficult (particularly for those w/o wired access).

ATM I'm working on out-of-the-box iso's. Care to help?

---

### Post by kansasnoob on 2012-03-19
Just downloading the actual Xubuntu Beta 1 because I need to make some comparisons to the latest non-pae daily but I checked the default installed size of the new image and it's 4.3GB! That's some major bloat! I'll bet there are parts of Unity in it.

---

### Post by cariboo on 2012-03-20
> **Peripheral Visionary said:**
> If we stay with the current 12.04 Xubu installation, will regular normal updates bring us the non-pae kernel eventually?

Thanks!

If your system is already working properly with the pae-kernel. why would you want to use the non-pae kernel?

---

### Post by dentaku65 on 2012-03-20
> **kansasnoob said:**
> Even before this change to the Xubuntu and Lubuntu images it would still have been possible to install a **buntu based 12.04 distro with non-pae, just more difficult (particularly for those w/o wired access).

ATM I'm working on out-of-the-box iso's. Care to help?

Well with mini-iso or netinstall... but I think that with these two possibilities you are not able to use the live option; is isn't it?

---

### Post by dcstar on 2012-03-20
> **kansasnoob said:**
> 
But we need to remember that 12.04 is the end of the road for the non-pae kernel! But 12.04 is a 5 year LTS (except for Lubuntu) so it's doubtful too many will still be hanging onto such old laptops by then.


12.04 should be the **last** Ubuntu release to support non-PAE. If people want to keep using hardware from 2004 then they can stick with 12.04 until it dies, it is unfair to impose this fringe requirement on the developers for all the future non-LTS releases.

---

### Post by WasMeHere on 2012-03-20
> **kansasnoob said:**
> My best guess is that if you're running the non-pae kernel it will stay that way throughout updates, and vice versa.

But we need to remember that 12.04 is the end of the road for the non-pae kernel! But 12.04 is a 5 year LTS (except for Lubuntu) so it's doubtful too many will still be hanging onto such old laptops by then.

This change should buy those requiring a non-pae kernel another 5 years, thank Colin Watson any chance you get ;)
... and thank *you, kansasnoob* :KS

---

### Post by Peripheral Visionary on 2012-03-20
> **cariboo907 said:**
> If your system is already working properly with the pae-kernel. why would you want to use the non-pae kernel?

It *is* working fine and I don't need to change anything... I was just wondering - because I have read that updates make our testing versions eventually become the final product - if I will *lose* the pae kernel and if it will be *replaced* with the non-pae kernel in *my* copy of Xubu 12.04 in future updates.

Still a newb, and a slow learner, lol.

---

### Post by jerrylamos on 2012-03-20
Latest today's daily build of lubuntu installed as generic without the pae on this Pentium M which does not have the pae flag.  

I haven't tried Xubuntu.  I run lubuntu and unity-2D depending on the pc.

Jerry

---

### Post by jerrylamos on 2012-03-20
Latest today's daily build of lubuntu installed as generic without the pae on this Pentium M which does not have the pae flag.  

I haven't tried Xubuntu.  I run lubuntu and unity-2D depending on the pc.

Do note lubuntu may be smaller than Xubuntu on the hard drive if that matters to you.  I'm at 1.9 MB after removing chromium, installing firefox, flashplugin, aptitude, updates of course even though it's today's build, my own wallpaper pic of my wife on holiday on a beach in Australia.

Jerry

---

### Post by jerrylamos on 2012-03-20
Just for giggles zsync'd today's pangolin i.e. unity and it installed generic-pae on this Pentium M, which has no pae flag.

I'm rebooting back to lubuntu which is a nice fit on this Thinkpad-T40.

Jerry

---

### Post by kansasnoob on 2012-03-21
Neither the Xubuntu of Lubuntu alternate images work ATM. They both show "No kernel modules found", thus this bug report:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/961218](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/961218)

They're fixed now.

---

