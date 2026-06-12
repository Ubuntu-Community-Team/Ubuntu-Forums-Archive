---
title: "Wine and Music Applications"
date: 2008-09-15
forum: Ubuntu Studio
---

### Post by digitalpulse on 2008-09-15
Hello,  I am looking to replace windows as most here are with the only thing keeping my music XP box still alive is my investment and work flow i have in applications such as Ableton Live 7.0 , Pro tools Mpowered 7.3, Reason 4 and my favorite VST and RTAS plugins Reaktor etc. Has anyone had any luck getting these applications to run in ubuntu?

Can anyone help?  Are there any useful guides to getting wine to run properly? Support seems to be for more graphic based apps, but what about users such as myself.

Any help would be sincerely appreciated.

---

### Post by prshah on 2008-09-15
> **digitalpulse said:**
> the only thing keeping my XP box still alive is my investment and work flow i have in applications such as Ableton Live 7.0 , Pro tools Mpowered 7.3, Reason 4 and my favorite VST and RTAS plugins Reaktor etc. 

You can search for specific apps and their usability with Wine at appdb.winehq.org

Aside from that, I can tell you from firsthand experience that most investment programs don't work in Wine. The reasons are many; one specific reason: most investment programs use ping to check server uptime and "lag"; such pings from behind wine will not usually work.

Many are also "married" to Microsoft's jvm (MSJVM), and though MSJVM has been EOL'd (end of life) these products do not work on Sun's JVM (usually due to bad programming practices, especially concerning security issues).

I suggest you use a VM (Virtual machine) of Windows in Ubuntu's VirtualBox, so that you don't have to keep switching (rebooting) between Windows and Ubuntu.

---

### Post by Stochastic on 2008-09-15
Some VST plugins will run on Linux if you do the proper setup steps.

Beyond that, I doubt you'll get any of the mentioned programs to run.  But on the upside there are many FOSS programs that can replace those programs (not all of them - Ableton Live is a nice little app that's yet to really be replicated in FOSS).  Check out Ardour [www.ardour.org](www.ardour.org) - it's better than Pro Tools and allows you to use nicer sounding sound cards.  The LADSPA set of plugins are also quite nice.  The list goes on, but you should take a look at [www.ubuntustudio.org](www.ubuntustudio.org) if you're serious about audio on Linux.

---

### Post by kalmdave on 2008-09-15
[http://en.wikipedia.org/wiki/Ubuntu_Studio](http://en.wikipedia.org/wiki/Ubuntu_Studio)
[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

Am in the same stage as yours and Ableton Live is my all time favourite. But i'd like you to check the above mentioned links for a s;ow and study move. Check this track named "Muse" entirely done in Ableton Live " [http://www.myspace.com/pathania](http://www.myspace.com/pathania) "

Best of Luck.

---

### Post by eric71 on 2008-09-16
Reaper works very well under Wine with wineasio. It should be a decent replacement for your apps, and most of your vsts should work. A good howto is here:

[http://forum.cockos.com/showthread.php?t=16786](http://forum.cockos.com/showthread.php?t=16786)

---

### Post by digitalpulse on 2008-09-16
Thanks so much for the pointers I have had a go at ubuntu studio but unsure of the way to use my m-audio firewire 410. Jack, alsa ?? i'll keep digging. might lead me down a new path.:)

---

### Post by Stochastic on 2008-09-16
Firewire cards need the freebob or ffado driver (same thing, different versions), but IIRC the folks at m-audio have refused to give the developers any info on how to work with their firewire cards.  I might be wrong, but you may need to switch your cards.

---

### Post by ram130 on 2008-09-17
i try ubuntu at the studio with a  m audio delta and all i getting is noise and no real sound. I also try the mbox two. but nothing, any suggestions??

---

### Post by Stochastic on 2008-09-17
> **ram130 said:**
> i try ubuntu at the studio with a  m audio delta and all i getting is noise and no real sound. I also try the mbox two. but nothing, any suggestions??

Sounds like you need to start your own help thread rather than hijacking the subject of this one.

---

