---
title: "Adobe Shockwave -- is it possible to get it working in Linux?"
date: 2009-08-25
forum: System76 Support
---

### Post by samalex on 2009-08-25
Hi Everyone,

I've gotten everything working with my online class thus far with Sun Java, Flash 10 (still using wrapper and 32-bit version), etc, but the one thing I can't get going is Shockwave which is required by the online virtual lab.

I was able to get Firefox 3.5 installed through Wine and then installed Flash and Shockwave for Windows, but Firefox (in Wine) crashes when it tries to load the virtual lab.

Under Linux without shockwave it just comes up saying I'm missing a plugin, but clicking Next says it can't find what's needed.

In all my reading I've found Adobe doesn't have a version for Linux, so this may be one of those times when I'll have to resort to Windows running in VirtualBox.  But before doing that I wanted to pose the question to the group since Shockwave is rather popular out there so I figured there's gotta be a work around. 

Thanks --

Sam

---

### Post by samalex on 2009-08-25
Hi everyone,

Nevermind on this. I found this link - [https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave) - which got me up and going.  I had already installed Firefox 3 and Shockwave through Wine, so it was just a matter of installing mozplugger and modifying a few config files.  Now the online courses are working great (thus far anyway), and with some luck I won't have to mess with Windows for any of my online stuff.

Take care -

Sam

---

### Post by thomasaaron on 2009-08-25
Nice job, Sam.

---

### Post by ralphmcknight on 2009-09-04
you dont need windows stuff, to get adobe shockwave working.

you may have to play a tad, but i got mine working as follows:

i have finally got this working: :-) by comparing 2 systems and finding the difference, as flash / shockwave worked on one and not the other!
anyway, the solution for me was to remove the following:

libswfdec-0.8-0
swfdec-gnome
swfdec-mozilla

these can easily be removed by going into 
system / admin / synaptic package manager.

once these are removed everything may start to work, if it doesnt, remove all the adobe packages ysing the package manager again, then go to the adobe main site and download flash again, i think its the 8.04+ .deb version, just click on the link on their site.  You can then update to a later version, via the package manager again if you like.

the version of shockwave will then show as shockwave flash 10.0 r22.
you can see this in firefox browser / tools / add-ons, in the plugins tab.

then all will work.

---

