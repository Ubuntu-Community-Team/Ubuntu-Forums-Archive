---
title: "rolling release debian based os"
date: 2014-03-28
forum: Ubuntu, Linux and OS Chat
---

### Post by rburkartjo on 2014-03-28
just looking for something to mess around with. can anyone recommend a rolling release debian based linux distro. any flavor fine. tks

---

### Post by slooksterpsv on 2014-03-28
Linux Mint Debian Edition may be what you're after.

[http://blog.linuxmint.com/?p=2577](http://blog.linuxmint.com/?p=2577)

---

### Post by Frogs Hair on 2014-03-28
***Moved to Ubuntu Linux and OS Chat ***

---

### Post by lykwydchykyn on 2014-03-28
If you mean rolling as in "Doesn't have distinct releases, but is just constantly upgraded over time", then try SolydXK.  I've been playing with it lately, and it's pretty solid.  They do quarterly update packs to keep it fresh, and the "home" edition is based on Debian Testing.

Now, if you mean rolling as in "Always gets the latest software as it becomes available", a la Arch, that doesn't exist in Debian due to the way Debian's repositories work.  Closest you can get is to run Sid with the experimental repository enabled.  There always seems to be at least one Sid-based distro around, but I don't know what the current ones are.

---

### Post by TeamRocket1233c on 2014-03-28
How 'bout Debian Sid?

---

### Post by grahammechanical on 2014-03-28
I am on what I think will be a Ubuntu rolling development release. It is trusty tahr with the repositories renamed from trusty to devel with this command.

```
sudo sed -i 's/trusty/devel/g' /ect/apt/sources.list
```

Now I wait to see if daily updates will roll this installation from Trusty Tahr development to <Uname> development. I think that this is the closest we are going to get to a Ubuntu rolling release.

I do get some errors when I update because some of the usual repositories do not exist as devel repositories. If using software Updater never accept the offer to run a partial upgrade. Always click continue and the update will take place as normal. This is what I see when I run the update using apt-get

> Err [http://extras.ubuntu.com](http://extras.ubuntu.com) devel/main Sources                                 
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) devel-security/main Sources
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) devel/main amd64 Packages   
  404  Not Found
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) devel/main i386 Packages    
  404  Not Found

> W: Conflicting distribution: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) devel Release (expected devel but got trusty)
W: Conflicting distribution: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) devel-updates Release (expected devel-updates but got trusty)
W: Conflicting distribution: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) devel-backports Release (expected devel-backports but got trusty)
W: Conflicting distribution: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) devel-proposed Release (expected devel-proposed but got trusty)
W: Conflicting distribution: [http://security.ubuntu.com](http://security.ubuntu.com) devel-security Release (expected devel-security but got trusty)
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/devel/main/source/Sources)  404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/devel/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.




The error messages can be ignored or we can edit the sources.list to direct apt-get to look for trusty repositories instead of the missing ones.

Regards.

---

### Post by orb9220 on 2014-03-28
SolydXK that has a great debian based Xfce & KDE version. As well as a Business and Back Office versions.
The nice thing I like about Debian based is a rolling release so no more Clean installs every 6 months or borked dist-upgrades.

Been on the KDE version of SolydXK and it even comes in pretty light at 287mb to desktop and that is with all the bells & whistles.
And Xfce is even lighter. Been doing updates based on Testing branch since Aug 2013 with zero issues and zero need to do a complete reinstall. And SolydXK does quarterly with next one on Apr. 15th. Which is based on Testing branch and end up with pretty fresh kernel desktop and apps.
Steam,PlayonLinux and Codecs installed by default.

[Linux Action Show just did a review on it]("http://youtu.be/ScfVvpyAXpc?t=38m") giving it thumbs up.

So for me it's near perfect fit for me. Take a look may be what you need? If not good luck as sure you will find what fits your needs.
.

---

### Post by craig10x on 2014-03-28
@grahammechanical: recently, Mark Shuttleworth did mention that once convergence took place (probably by 14.10 or no later then 15.04)...that they would consider replacing the 6 month releases with a sort of semi-rolling release...a stable ubuntu core that would get newer apps, and i guess kernels when they are stable and ready for release...much in the same way that say, an android device gets updated versions of stuff automatically...

Of course...he has said things like this before...though this time he sounded a bit more serious about it... ;)

---

### Post by KBD47 on 2014-03-28
Probably the easiest way is to install Solydxk and change sources directly to Debian Testing or to Sid/Unstable if you want to live a bit more dangerously. Or you could grab a snapshot of Debian Testing from Debian and run that or distribution-upgrade it to Sid.

---

### Post by sammiev on 2014-03-29
SolydXK is a rolling release and it seems to be solid.

---

### Post by su:bhatta on 2014-03-29
> **lykwydchykyn said:**
> If you mean rolling as in "Doesn't have distinct releases, but is just constantly upgraded over time", then try SolydXK.  I've been playing with it lately, and it's pretty solid.  They do quarterly update packs to keep it fresh, and the "home" edition is based on Debian Testing.


And also @ Sammiev :

Any idea if Flgrx can be used with SolydXK ? Debian Jessie/Testing doesn't have a Fglrx client. 
My laptop overheats without one and also screen resolution is a problem.

OP, I am trying out KaOS ( [http://kaosx.us](http://kaosx.us) ) and it is holding up pretty good. 
But it is a pure Qt environment, though some GTK stuff can be added.

---

### Post by craig10x on 2014-03-29
By the way, this is where he said it:
[http://www.omgubuntu.co.uk/2013/12/ubuntu-touch-plans-2014](http://www.omgubuntu.co.uk/2013/12/ubuntu-touch-plans-2014)

Would sure love to see an ubuntu that you didn't have to re-install or upgrade to every 6 months...but who knows if they will really do it...i can dream, can't i? ;) :D

---

### Post by monkeybrain20122 on 2014-03-29
> **bhattabhishek said:**
> 

Any idea if Flgrx can be used with SolydXK ? Debian Jessie/Testing doesn't have a Fglrx client. 
My laptop overheats without one and also screen resolution is a problem.

OP, I am trying out KaOS ( [http://kaosx.us](http://kaosx.us) ) and it is holding up pretty good. 
But it is a pure Qt environment, though some GTK stuff can be added.

Unless you need a few extra fps and higher versions of OpenGL for gaming I would rather use the open driver. With fglrx the next kernel update may leave you with a broken display, also amd support  for your card may expire before your next OS upgrade if it happens to be an older card.

 If you use a recent enough kernel (3.11+?)  and a supported card you may try to enable dynamic power management and see if it helps with your overheating.

Open /etc/default/grub and change the line
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash "
to
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"

then update grub and reboot.

It works well on this hp netbook I have just installed Ubuntu on. Runs for hours playing videos and what not and still remains cool. It also turns off the fan when not needed (before enabling dpm it was blowing non stop even when idle) 

On the other hand I can't even install fglrx on this machine (OS ubunti 13.10, gpu AMD hd 6310), tried the package suggested by additional driver, then the other ones, and xorg-edgers, always booted into black screen. I could try to trounle shoot it or install the .run file from AMD but I couldn't even be bothered. I installed the latest open driver from the oibaf ppa, it works nicely and I even get vdpau for video decoding. From what I read the open driver is actually smoother than fglrx for most 'normal' desktop usage.

---

### Post by mips on 2014-03-29
[http://semplice-linux.org/](http://semplice-linux.org/)
[http://forum.siduction.org/](http://forum.siduction.org/)
[http://linuxbbq.org/](http://linuxbbq.org/)
[http://aptosid.com/](http://aptosid.com/)

---

### Post by rburkartjo on 2014-03-29
tks all for the suggestions appreciate it

---

### Post by su:bhatta on 2014-03-29
> **monkeybrain20122 said:**
> Unless you need a few extra fps and higher versions of OpenGL for gaming I would rather use the open driver. With fglrx the next kernel update may leave you with a broken display, also amd support  for your card may expire before your next OS upgrade if it happens to be an older card.

 If you use a recent enough kernel (3.11+?)  and a supported card you may try to enable dynamic power management and see if it helps with your overheating.

Open /etc/default/grub and change the line

to


then update grub and reboot.

It works well on this hp netbook I have just installed Ubuntu( I am running Ubuntu Studio 14.04 so Kernel 3.13) on. Runs for hours playing videos and what not and still remains cool. It also turns off the fan when not needed (before enabling dpm it was blowing non stop even when idle) 

On the other hand I can't even install fglrx on this machine (OS ubunti 13.10, gpu AMD hd 6310), tried the package suggested by additional driver, then the other ones, and xorg-edgers, always booted into black screen. I could try to trounle shoot it or install the .run file from AMD but I couldn't even be bothered. I installed the latest open driver from the oibaf ppa, it works nicely and I even get vdpau for video decoding. From what I read the open driver is actually smoother than fglrx for most 'normal' desktop usage.

I am aware of DPM, and yes it works great in Ubuntu( I am running Ubuntu Studio 14.04 hence Kernel 3.13), using it since the day it was posted on Webupd8
But in KaOS, it is heating up the laptop when it is being charged. 

My only problems with Open Source drivers are that they heat the laptop very much ( so much that it cannot be termed a laptop, more of a table top, and yes sometimes that is a big problem) and cannot give me the best screen resolution.

My card is pretty recent HD 6480, so no leagcy support needed till date, never know when that woe turns up !

Sorry, for posting in a 'Solved' thread.

---

### Post by TeamRocket1233c on 2014-04-02
> **KBD47 said:**
> .....Or you could grab a snapshot of Debian Testing from Debian and run that or distribution-upgrade it to Sid.


There's also downloading the netinstall ISO and installing Sid directly from it.

---

