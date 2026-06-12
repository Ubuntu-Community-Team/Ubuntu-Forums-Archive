---
title: "OSX Running On My Starling"
date: 2010-02-22
forum: System76 Support
---

### Post by Taxadermist Now on 2010-02-22
I know the System76 guys don't advocate this at all, and if this is inappropriate to be posting here we can close this thread whenever.  But...

I've got OSX running flawlessly on my Starling.  Its quick, sound, microphone, webcam, wifi and everything all work without a hitch.  I was pleasantly surprised by the ease of the whole process.  So here's what I did:

1. Made a boot USB key using the instructions at [http://osx.mechdrew.com/guides/nbi1.shtml](http://osx.mechdrew.com/guides/nbi1.shtml) including the update to 10.6.2.  The thing just booted up and installed itself real easy.  But...

2. Wifi and sound were both broken. oh no!  So I headed over to [http://kexts.com/](http://kexts.com/) via my ethernet connection, which was working fine.  I downloaded OSX86Tools from the programs section and the VoodooHDA.kext extension from the audio section.

I did some googling then and came across a thread at [http://www.infinitemac.com/f57/official-patched-realtek-usb-rtl8187b-wifi-kext-release-t5472/](http://www.infinitemac.com/f57/official-patched-realtek-usb-rtl8187b-wifi-kext-release-t5472/) that gives a link to some patched audio drivers for the board that the Starling uses.  Well on my way now, so I...

3. Found a guide at [http://www.ihackintosh.com/2009/02/what-is-kextwhere-is-kext-how-to-install-kext/](http://www.ihackintosh.com/2009/02/what-is-kextwhere-is-kext-how-to-install-kext/) that details how to install .kext extensions via the terminal and got to work.  Once both the Audio and Wifi drivers were copied to the right spots, I used OSX86Tools to clear the OS's extension cache and restarted.

And that's it.  It took a good five or six minutes to start because of the empty extension cache (it starts much faster after the first initial boot), but when it did my sound was back, wifi connected itself to my home network, and here I am, typing up this thread on my OSX86 Starling. :D

Edit: First post ever.  Nice to meet you.

---

### Post by Taxadermist Now on 2010-02-22
Decided to add a screenshot for proof.  Check out the "About this mac..." Dialog :D

[[IMG]http://img695.imageshack.us/img695/8445/screenshot20100222at429.th.png[/IMG]]("http://img695.imageshack.us/i/screenshot20100222at429.png/")

---

### Post by samalex on 2010-02-23
Nice!  I wonder if this would work in VirtualBox...  Also why is the site Netbook specific?  Could this work on regular laptops or desktops?  

Though I've used Linux since the 90's, I moved my primary system from Linux to OSX around 2005 but then back to Linux last year with my PanP5.  I still love OSX and would enjoy having it at my fingertips for iLife and other apps, but I'd rather not blow away my entire system to experiment with trying to make it work.

Also one problem I always read with OSX on non-Mac systems is it won't always control the fans properly, so overheating can be a problem.  Just watch your temps unless your Netbook doesn't have any fans :)

Take care and kudos!  I might need to start researching this myself.

Sam

---

### Post by Noah0504 on 2010-02-23
> **samalex said:**
> Also one problem I always read with OSX on non-Mac systems is it won't always control the fans properly, so overheating can be a problem.  Just watch your temps unless your Netbook doesn't have any fans :)

Maybe that's just a flaw in Mac OS X.  :P  My MBP would always get HOT!  I had to run an application called SMC Fan Controller that would keep the fans on the system running at a minimum speed just to keep it cool.

---

### Post by samalex on 2010-02-23
> **Noah0504 said:**
> Maybe that's just a flaw in Mac OS X.  :P  My MBP would always get HOT!  I had to run an application called SMC Fan Controller that would keep the fans on the system running at a minimum speed just to keep it cool.

The MB drivers help control the fans, so if your system doesn't have what it needs or is running generic drivers the fans might not work.  This was a huge problem on the Intel-based Macs when people started loading Windows on them, and now on non-Mac hardware when OSX is installed.

Just something to keep an eye on and another reason I'd prefer to run it virtually.

Sam

---

### Post by Taxadermist Now on 2010-02-23
The fan problem is indeed a recurring one with osx86 systems, but it appears to work okay with the starling.  So far at least :o

As for the site, it's just the one I used.  Hackintosh.com has how-to's and tutorials for just about any kind of system, including desktops and larger laptops.  The netbook specific site is necessary as it includes instructions on how to make a USB boot drive.

And here's a nice testament to System76's excellent hardware choices:  My little HackBook running Steam and Half-Life through Crossover Wine:

[[IMG]http://img715.imageshack.us/img715/938/screenshot20100223at557.th.png[/IMG]](http://img715.imageshack.us/i/screenshot20100223at557.png/)

And Logic Studio Pro 9:

[[IMG]http://img715.imageshack.us/img715/5407/screenshot20100223at559.th.png[/IMG]](http://img715.imageshack.us/i/screenshot20100223at559.png/)

It also runs the mac version of Halo well, SixtyForce (an N64 emulator) and PCSX (playstation games) all fairly well.

---

### Post by macabrem on 2010-02-26
That's pretty awesome.  I still keep a Mac for my desktop, so I don't need to run OS X on my Starling.

I didn't even think Half-Life would work on the hardware a Starling has.  That's pretty awesome.  I haven't played Half-life in years.  I might have to look into playing it again.

---

### Post by savantelite on 2010-02-26
*Slow golf clap starts*

Congrats, stuff like this proves us linux guys know what we are talking about no matter what OS. We all prefer our linux #1 but there is stuff on Mac that is nice to have as well as nice things on XP. I use to have a powerbook that was very nice for video and audio creation. And I still use my XP partition to download Audiobooks from audible. 

So congrats again. You are part of the elite few that could run anything from one place.

---

### Post by Megafag on 2010-03-15
> **Taxadermist Now said:**
> I've got OSX running flawlessly on my Starling.  Its quick, sound, microphone, webcam, wifi and everything all work without a hitch.  I was pleasantly surprised by the ease of the whole process. 

:O

I wish i was in america so i could buy one, i have tried unsuccessfully to hackintosh my Eeepc 1000HE for ages!!

---

### Post by isantop on 2010-03-16
I offer my congratulations on getting a working Hackintosh running, but I really don't approve of anything OSX has to offer at all.

A few main reasons:
[list]First off, OS X shuts the user out of the system. So sure, it's UNIX. But can you really say that, given that all of the appeal of UNIX is lost?
[/list]

[list]Does suspend (sleep) work? That seems to be a big bugger.[/list]

[list]If i really wanted to use Mac, I'd use a Mac. PC's are for Linux, Macs are for OS X. That's just the way it is. That's why a PC running OS X is a *hack*intosh.[/list]

[list]OS X is closed source. I avoid it at if I can (Drivers excluded.)[/list]

---

### Post by thomasaaron on 2010-03-16
However, a key component of freedom is FREEDOM. People should be able to run whatever they choose on their systems.

You've got to be careful, or you become that which you wage war against.

---

