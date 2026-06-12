---
title: "recording using Creox, Audacity, Jack"
date: 2010-01-24
forum: Ubuntu Studio
---

### Post by zeelog on 2010-01-24
I'm a guitar player. I'm trying to use creox in Ubuntu Studio but I
can't get it to do anything with Audacity.
Creox seems to start OK when I have the Jack Audio Connection Kit running.
Audacity starts OK too, but I can't get creox to record a track in
Audactiy. I'm playing the guitar through a hardware mixer and into the M-Audio sound card. 
In the computer I'm using the software envy24control mixer.
The guitar records into Audacity OK, but creox has no effect on the
guitar sound. So creox isn't doing anything.
Creox has practically no documentation. I can't figure out how to make
 it do anything. It must be of some use or it wouldn't be in
Ubuntu Studio, right?  Any information would be very welcome!

---

### Post by AutoStatic on 2010-01-24
Hello Zeelog, maybe [Rakarrack]("http://rakarrack.sourceforge.net/") suits you better than Creox. Development of Creox has stopped also, the version in Karmic is from 2003. Rakarrack on the other hand is continuously getting better.
And if you want realtime effects to be recorded in Audacity you have to use JACK as the Interface in Preferences - Devices. That option is only available when JACK has started up correctly.

---

### Post by transmogrifox on 2010-01-25
"And if you want realtime effects to be recorded in Audacity you have to use JACK as the Interface in Preferences - Devices. That option is only available when JACK has started up correctly."

In the event more info is helpful to you:
Creox (or any open jack app) will appear in the list under recording devices.  

You have to configure it from within Audacity because it doesn't show up in qjackctl or patchage (basically does not register with jack) until you click play or record.  

I really like the way Creox gui lets you adjust the delay :)... 

Here's the "more than what you asked for" blurb:

I give +1 to Rakarrack.  I am now part of the Rakarrack dev team, so I know it sounds like self-promotion, but I started as a user who really likes using Rakarrack.  In the process of using it I saw ways to contribute, so in the GNU spirit I wrote some code :)  In the end, I'm still a user promoting what I think is a great project. ;)

Another good guitar rig is Guitarix.  Guitarix is alive and well...always improving.  Guitarix devotes more specific attention to amp modeling.  Rakarrack is more like a pedalboard with stomp boxes, whereas Guitarix is like a tube amp with a DSP brain.

I use Debian Sid on my iBook G4 and Debian Lenny on my Intel box, so I'm not sure of the state of Rakarrack in Ubuntu repositories right now.  It looks like Lucid Lynx has version 0.3.0 in official repo.

Karmic package for 0.4.2
[https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75](https://launchpad.net/~philip5/+archive/extra/+index?start=75&batch=75)

I am not aware of any Ubuntu packages for Guitarix, but it was an easy build...pretty easy to meet required dependencies.  Download sources and follow instructions on the web page.  Use apt-get install to get anything the waf configure command tells you is missing.
[http://guitarix.sourceforge.net/](http://guitarix.sourceforge.net/)

---

### Post by sgx on 2010-01-26
Hi zeelog, as mentioned, press record in audacity, then press pause, then look for 'portaudio', its 'nik' in the qjackctl gui, make connections, then resume recording.

creox has an activation button that must be pressed (as does rakarrack, it took a certain moron I know about 7
hair-ripping mouse-crushing minutes to figure that out wink wink) and must also be connected in qjackctl to the appropriate input. After that, its easy sliders and knobs. And of course, you can route creox to another creox, etc etc be creative!

Rakarrack is wonderful, one of the few 'killer apps' for linux. As such,
I would encourage the dev team to maintain a .deb, and .rpm file at the
homepage, encouraging distro maintainers to test it for inclusion, and
making it easy pickings for linux newbies not yet able or willing to compile apps. For years, the status quo has been
'no rpm/deb at sourceforge', only source/cvs releases. I dare say that
historically, most windows/mac users just walked away at that point.

Thanks T'fox, for your work on such important and quality software!:D

---

### Post by AutoStatic on 2010-01-26
> **sgx said:**
> As such,
I would encourage the dev team to maintain a .deb, and .rpm file at the
homepage, encouraging distro maintainers to test it for inclusion, and
making it easy pickings for linux newbies not yet able or willing to compile apps.For Ubuntu, that's where PPA's come in handy. I don't think it's up to the devs to package their software, they're busy enough developing.

> **sgx said:**
> For years, the status quo has been
'no rpm/deb at sourceforge', only source/cvs releases.Is that true? I can sum up a few projects that have deb's on their sourceforge page as long as I can remember (Hydrogen, LMMS, Qtractor).

---

### Post by sgx on 2010-01-26
> **AutoStatic said:**
> For Ubuntu, that's where PPA's come in handy. I don't think it's up to the devs to package their software, they're busy enough developing.

Is that true? I can sum up a few projects that have deb's on their sourceforge page as long as I can remember (Hydrogen, LMMS, Qtractor).
Its time for bacon and eggs here, but if it wasn't packaged when I went shopping for it, I'd at least have to bring my own bags. Commercial coders really don't have much choice, present an installer or go belly up. Linux devs that host packages are maybe 20-30%? And some of those are not recent versions, (but it looks like Hydrogen and Qtractor are! :D ) Which may beg the issue that the burden of
1. coding
2. packaging
3. basic testing to prevent distro chaos

 is too much work for most volunteer coders, who also have a life after work. And its not the goal of every coder to present finished bug-free software, some software is for proof of concept, some is the product of curiosity, some is to win a personal challenge, some is a personal tool that is kindly shared. That we have DVDs of excellent software at every turn is quite amazing. I should make a paypal account. I really don't enjoy banking. It feels like friday.
Cheers

---

