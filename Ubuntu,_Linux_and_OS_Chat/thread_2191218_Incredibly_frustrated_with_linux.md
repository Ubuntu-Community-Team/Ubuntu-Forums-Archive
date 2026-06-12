---
title: "Incredibly frustrated with linux"
date: 2013-12-01
forum: Ubuntu, Linux and OS Chat
---

### Post by keller.ee on 2013-12-01
Here we are, 2 decades in, and it's not stable.  I've been using 12.04 for quite some time, and I like it.  And it works great if you can keep it running.  But I'm having a problem with my system, and forum posts from last year offer solutions that simply don't work on the current version.  And that situation is recursive, back as far as I can remember, there is much more information about fixes that don't work than fixes that do work.

I'm using a liveCD I created on Windows because my system doesn't boot and the cd creator on Ubuntu doesn't work, at least for most people.  

Here is something that has always bothered me.  The livecd boots, sees my network and my video just works.  My installed system is somehow misconfigured so that it doesn't see the network and the video doesn't work so I can't get X to run.  Is there no way to fall back to that initial configuration so that the system can be fixed without running back and forth to a browser on another system?  Oh, and I didn't change the configuration.  I tried to install a proprietary video driver because I thought it worked, but installation failed, almost silently.  My system kept working, so I didn't think about it, but today we had a power outage and now no network and no video.  If you go onto these forums about how to fix a problem, it's fairly deep stuff.  Especially if you only have a terminal.  Yeah, it's nice to be able to twiddle the settings, but come on, my system is just barely misconfigured but I have to touch a dozen files distributed all over the file system?  And most of the suggested twiddling doesn't work, nobody actually knows how this stuf works.  Read any tutorial, it's a jumble of suggestions.  

Guess what, the recovery option on boot is known not to be worthwhile.  The "low resolution warning" thing is a joke.  I finally figured out that alt-o would select yes.  But I still haven't figured out how to change the selected option in the next screen.  And if you select "continue in low resolution mode" it goes to a command prompt.  If you want to fix your system, you have to go into a command prompt.  Good luck remembering everything, because all the linux commands and file names you have memorized are no longer working.  Some group of geniuses decided that way of doing things wasn't good enough.  Now we have network manager, which is broken, Xorg, which is broken.  And any number of other programs sitting on this system are broken.

I've wasted all morning and I think I'm just going to reinstall.

---

### Post by ajgreeny on 2013-12-01
> **keller.ee said:**
> Here we are, 2 decades in, and it's not stable.  I've been using 12.04 for quite some time, and I like it. 
You sound like a really good candidate for using only the LTS versions, which I have always found to be stable and fantastically good OSs.  There may be an odd bug immediately after LTS release, but they are usually cleared up very quickly and all goes well after that.

What are you going to install now?

---

### Post by buzzingrobot on 2013-12-01
Failures due to loss of power can leave any OS in an unstable and unusable condition, as well as produce hardware damage. If power outages are an issue, consider buying an UPS.

An installed system should recognize the same hardware recognized by the LiveCD.  If that works, a reinstall is probably the best approach. 

The only problem I've had with using "Additional Drivers" is that the package from Nvidia sometimes fails to create the required xorg.conf file.  A "sudo nvidia-xconfig" before the reboot will create the file.

---

### Post by keller.ee on 2013-12-01
> **ajgreeny said:**
> You sound like a really good candidate for using only the LTS versions, which I have always found to be stable and fantastically good OSs.  There may be an odd bug immediately after LTS release, but they are usually cleared up very quickly and all goes well after that.

What are you going to install now?

I reinstalled 12.04. Fortunately I hadn't installed much software that takes much work to reinstall. The worst thing is Plex media server, and I should have it working in a half hour if all goes well.  I might go back and see if I can take some of the automation out of the network setup, that just seems like it's asking for problems.

 I used Fedora for many years, but gave up when it became obvious that their approach relied on you formatting your hard drive every few months and installing a new version.  On a bad day, I might have thought they were breaking things just for the fun of it.

---

### Post by keller.ee on 2013-12-02
Just to follow up, I ended up fixing the system.  Some update apparently blacklisted my network driver and fglrx was only partially installed.  And when the install failed, it left the computer in an unstable state for the next boot.  I am going to replace the network driver when I get around to it, apparently the vendor driver works much better than the OSS.

---

