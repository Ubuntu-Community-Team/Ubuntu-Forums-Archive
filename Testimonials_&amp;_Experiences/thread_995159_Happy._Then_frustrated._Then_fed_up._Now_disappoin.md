---
title: "Happy. Then frustrated. Then fed up. Now disappointed."
date: 2008-11-27
forum: Testimonials &amp; Experiences
---

### Post by tkbremnes on 2008-11-27
A while back, I was a happy Linux user. Didn't miss anything. Showed it to my friends who were all impressed. I was a happy Linux user for almost a year.

And then the shortcomings started showing.
All the hurdles I had to jump just to get my shiny new 22" monitor working (this was pre 8.10). I mean, Windows easily splits the desktop over several monitors easily, and has done for a decade.
The thing when any flash based player stopped playing video if Firefox had more than 3 tabs open. Sound available only on weekdays with an n.
The blinking screen when I open anything in Wine.
Facebook being unbearable to browse.

I installed Windows again. Which was refreshing, everything just worked. No work-arounds, no disabling effects to get some software to work, and then enabling it to get other software to work. A bit of trouble with drivers, yes, but after that everything was great.

And now, with Intrepid, things are even worse. The Intel driver is broken, making the window manager slow as heck. Unable to use compositing, making Air-based apps looking ugly. Can't use awn any more. Gaming is a huge no-no.

But I'm still hoping. Installed Intepid again today, I missed the command line, symbolic links, the customizability. Some of the issues have been fixed, some reduced and some are worse. So I'm disappointed.
I just hope that things work out someday.

---

### Post by wolfen69 on 2008-11-27
why not try a different distro? how about debian lenny? ubuntu is not the only player in town. you may be surprised by what other distros have to offer.

---

### Post by Paqman on 2008-11-27
Yeesh, you sound like you've had a nightmare of a time.

If you ever get a new machine, try out Linux/Ubuntu again. I'd be willing to put money on the fact that your problems are all caused by the hardware on your current machine not playing nicely with Linux. You might find that on a different machine everything works perfectly.

---

### Post by Tamlynmac on 2008-11-27
> tkbremnes
A while back, I was a happy Linux user. Didn't miss anything. Showed it to my friends who were all impressed. I was a happy Linux user for almost a year.

And then the shortcomings started showing.
All the hurdles I had to jump just to get my shiny new 22" monitor working (this was pre 8.10). 

If your were satisfied with Gusty or Hardy then why not stay with that version? There's really no need to upgrade if your system's fully functional. Simply reinstall the version that made you "a happy Linux user". Then prior to any future upgrading, take time and assure that your system is compatible and that the upgrade will improve your experience. If either of these requirements aren't met - don't upgrade?

Or if Windows works for you use it. 

Bottom Line - ***Use What Works***

---

### Post by jayson.rowe on 2008-11-27
> **tkbremnes said:**
> 
And now, with Intrepid, things are even worse. The Intel driver is broken, making the window manager slow as heck. Unable to use compositing, making Air-based apps looking ugly. Can't use awn any more. Gaming is a huge no-no.



Instead of using (the default) Compiz for the compositing manager, why not try Metacity's built in compositing manager?

Simply hit Alt+F2 and type:
```

gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true

```

This will enable Metacity compositing. This will disable if you decide you don't like it after all:

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

The reason I recommend this is that the requirements for Metacity compositing are much lower than Compiz (it will even work in a virtualized Ubuntu install, such as in VirtualBox or VMware while Compiz won't do to lack of 3D accel. on the Virtual Vid card). Yeah, the effect's aren't as "cool" - but it'll keep stuff like AWN, and AIR working as expected!

Hope this helps!

---

### Post by wolfen69 on 2008-11-27
i subscribe to the K.I.S.S. theory. match the right OS to the hardware. it's a fact of life that all OS's don't work on all computers. find the right one that works on that hardware and call it a day. pretty simple to me. that's why i have at least 15 distros on hand at all times. plus you have fun by trying different things.

---

### Post by 3rdalbum on 2008-11-28
There are definite sound problems on Hardy and Intrepid. There is a sticky HOWTO in the Tutorials and Tips forum that can resolve some Pulseaudio problems. No idea what your Facebook problem is.

Until Ubuntu sorts itself out you might want to look at adopting Debian. Sometimes things do work better in Debian than they do in Ubuntu.

---

### Post by steveneddy on 2008-11-28
> **wolfen69 said:**
> i subscribe to the K.I.S.S. theory. match the right OS to the hardware. it's a fact of life that all OS's don't work on all computers. find the right one that works on that hardware and call it a day. pretty simple to me. that's why i have at least 15 distros on hand at all times. plus you have fun by trying different things.

I agree that hardware compatibility is the main cause of Linux frustration.

Check your hardware on a compatibility list to see how well it is or isn't supported.

---

### Post by Auraomega on 2008-11-28
I heard [SimplyMEPIS]("http://www.mepis.org/") is a good distro for hardware compatibility, I dunno how true the claims are, but when I used it years ago it was the only distro I tested that would run on my laptop "out of the box".

-Aura

---

### Post by phidia on 2008-11-29
> **Auraomega said:**
> I heard [SimplyMEPIS]("http://www.mepis.org/") is a good distro for hardware compatibility, I dunno how true the claims are, but when I used it years ago it was the only distro I tested that would run on my laptop "out of the box".

-Aura

I have an install of mepis 8 (which is still in beta) it does a great job of finding hardware and even set up the atheros wireless card automatically.
So yes simplymepis is worth looking into.

I've been mystified with what the Ubuntu devs have done with xorg for 8.10 (some changes were made in 8.04 too). Does anyone know where the configuration data that was in xorg.conf is now? And does anyone care that it's nearly impossible to manually edit your video card or monitor set up?

I love that hardware incompatibility excuse-my hardware isn't exotic but 8.10 won't boot half the time while there are no  problems with 7.10.

---

### Post by forkandles on 2008-11-30
I can only second the above suggestions. I learned an awful lot more about Linux by using different distributions. There are plenty more fish in the sea.
My recommendations would be Mepis 8 Beta, Linux Mint, Debian and Dreamlinux.
As mentioned earlier, Mepis is very good at hardware recognition.

Give one or more a try. You have nothing to lose and everything to gain.

---

### Post by aysiu on 2008-11-30
Stick with XP until you're in a position to buy new hardware.

Then buy Ubuntu preinstalled and make sure all peripherals are Linux-friendly.

---

