---
title: "How about using Linux for this?"
date: 2005-01-29
forum: The Cafe
---

### Post by eBopBob on 2005-01-29
Hey folks,

Ok - I've a friend who has a very old computer. It's extremely old. So old it has Windows 98 however the first edition - You see where I'm getting with this?

Anyway, he also has an MP3 USB player stick thingy.

I don't know what processor he has, however he only has 64MB RAM. So I presume it's an old Pentium III or Pentium II even. I have no idea unfortunately and don't know how fast the processor is.

Now, as some may know Win98 does not support USB by default (Win98SE does however the first edition doesn't); however he says USB is working on his computer so I don't know - He isn't too computer literate so I am not sure what to believe.

Well, I then thought instantly to Linux. I don't think he'd be allowed to have it installed completely on his system - however I don't think there'd be a problem about a LiveCD.

Now, this is what he would like: To put in a CD and copy the music to his sytem (I know Linux can do this - I know what programs to use in both Gnome and KDE as I've done it many times before myself; I just hate having my CDs in my DVD-ROM all the time - I've the constant fear they deteriate in there :P  and also I don't like switching CDs when I want to listen to something else), but then he wants to convert the file format they come in to MP3 format (Now this I have no idea - Is it even possible in Linux? TBH I don't even know a program in Windows to do this so I can't even check the equivalents list!) and then he wants to transfer them to his MP3 USB thingy (This I also know how to do).

So basically - Is all the above possible, and on such a slow and old machine? I was actually thinking of using the Ubuntu LiveCD because it's very light and very good IMO. If not, would Knoppix work? I've an old Knoppix version which I could give to him to use. I don't have ADSL though so I can't download anything unfortunately and burn it for him. He also only has 56k.

And if the above is possible then which program must be used to convert from normal file format to MP3?


Thanks :)

---

### Post by dare2dreamer on 2005-01-29
For a machine of such limited resources I'd recommend a look at DamnSmallLinux:

[http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)

It's the same base as knoppix/morphix/etc livecd's, but stripped down to run on older hardware and in a much smaller footprint. The iso for the livecd is designed to fit on a  mini-cd, only 50 megs.

I currently have an aging laptop with DSL installed to the hard disc and tweaked a bit, it turned a Pentium 133 (with only 48 megs of ram and a 600 mb hard drive!) into a fully functional, albeit a tad pokey, multimedia/surf/work machine.

It of course spends most of its time serving as a wireless NXclient to my Ubuntu box, so don't kick me out of the fan club for straying. ;-)

As for the USB thing, the only problem I could see is if the usb ports are v1.0 only and the device does not properly support the older specifications. I ran into this on my laptop where some newer 1.1/2.0 usb sticks will actually hardlock the wee little beast.

My suggestion is to try testing with live cd's to see what works reasonably well, and then realize it can only get faster/better/more customized to your needs with a hard disc install and a bit of tweaking.

---

### Post by eBopBob on 2005-01-29
[QUOTE=dare2dreamer]For a machine of such limited resources I'd recommend a look at DamnSmallLinux:

[http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)

It's the same base as knoppix/morphix/etc livecd's, but stripped down to run on older hardware and in a much smaller footprint. The iso for the livecd is designed to fit on a  mini-cd, only 50 megs.

I currently have an aging laptop with DSL installed to the hard disc and tweaked a bit, it turned a Pentium 133 (with only 48 megs of ram and a 600 mb hard drive!) into a fully functional, albeit a tad pokey, multimedia/surf/work machine.

It of course spends most of its time serving as a wireless NXclient to my Ubuntu box, so don't kick me out of the fan club for straying. ;-)

As for the USB thing, the only problem I could see is if the usb ports are v1.0 only and the device does not properly support the older specifications. I ran into this on my laptop where some newer 1.1/2.0 usb sticks will actually hardlock the wee little beast.

My suggestion is to try testing with live cd's to see what works reasonably well, and then realize it can only get faster/better/more customized to your needs with a hard disc install and a bit of tweaking.[/QUOTE]
 Then wouldn't Ubuntu LiveCD work do you think? - Would the system be too small / slow?
Unfortunately I don't have ADSL and 50mb would take a while - 2mb takes about 15 or so minutes, meaning 50mb would take about 375 minutes or about six hours. So I cannot download it for him. And he has only 56k so neither can he.
I have only Knoppix and Ubuntu LiveCD. He does not have any Linux LiveCDs.

So unfortunately the only Linux options are either Ubuntu or Knoppix.
It's either that, or him trying to get Windows to work with USB and get it to do what he wants (*Which would actually have me end up going over to his place and do it for him...*).

He may be able to have a hard drive install later on. His hard hard drive is 10gb I think - If he likes the look of Ubuntu, or Linux in general, I'll probably do a dual boot for him. Therefore he can do some things in Linux and the rest in Windows.


Also though, what program can one use to convert audio cd files to MP3 format?

Thanks :)

---

### Post by TravisNewman on 2005-01-29
[QUOTE=eBopBob]
Now, as some may know Win98 does not support USB by default (Win98SE does however the first edition doesn't); however he says USB is working on his computer so I don't know - He isn't too computer literate so I am not sure what to believe.[/quote]
No offense but you're sounding computer illiterate. Windows 95 OSR2 and everything after that INCLUDING Windows 98 first edition supported USB. Trust me, I know very well. One of my friends had a computer that was ALL usb-- no serial,  ps2, or parallel ports-- and he bought Windows 98 the day it came out and we installed it. AND Windows 95OSR2 worked fine, so why wouldn't Windows 98 first edition?

---

### Post by costoa on 2005-01-29
I agree with dare2dreamer on damnsmalllinux. I recently rebuilt an old machine with an AMD K6 200MHz CPU, 64M RAM and on board video (an old "[thinknic](http://costoa.dyndns.org:9861/think-nic)" thin client with a hacked in HD) from spare parts. For giggles I installed Ubuntu just to see how it would run. Basicly it was unusable. Ubuntu does run at accepted speeds on a PIII 866MHz but 200MHz and 64M RAM was just too week. Ubuntu is meant to be cutting edge stable and does run sweet on my Athlon XP 2500 with 512M of RAM =) .

damnsmalllinux on the other hand was quite usable. Clearly it's not Ubuntu because it's built to run well on older hardware. Download the live cd and try it out. If you like it there's instructions on how to install it. 

The machine can become usable and stable again. IMO worth the couple of hours of work. It'll be fun too.

BTW, I turned that old thinknic into a mini web and smb server by using the Debian net install and carefully selecting the bare minimum of applications. Total install was just under 100M with apache, php, python, etc. Not bad and it runs rather well. Zero GUI programs or X Windows for that matter is installed. Everything is done via ssh so the only thing plugged in is AC power and ethernet, no video, keyboard or mouse. It was a fun project.

Good luck and post the results.

costoa

---

### Post by rudi on 2005-01-29
Windows prior to XP don't recognize the USB sticks. They do support USB, but not such a peripheral device. I would suggest to look on the manufacters website and search for a windows9x driver. Any computer that has got a USB connection isn't regarding old to me, when you say old computer i think of a 8088 :p

---

### Post by eBopBob on 2005-01-29
> No offense but you're sounding computer illiterate. Windows 95 OSR2 and everything after that INCLUDING Windows 98 first edition supported USB.
Well - I've never used Windows before Win98SE so wouldn't normally know about it.


> so why wouldn't Windows 98 first edition?
I was told by about 15+ people that Win98 First Edition does not support USB.


> Windows prior to XP don't recognize the USB sticks. They do support USB, but not such a peripheral device. I would suggest to look on the manufacturers website and search for a windows9x driver
Exactly. He had two USB ports however my USB stick wouldn't work on it. Although his USB/MP3 Player-Stick would. :confused:



Anyway though.
Thank you all for your replies - They were very much appreciated.
I went round to his today, downloaded and installed a program to convert from standard CD Audio format to MP3, and then it came to the MP3/USB Stick-Player. What he forgot to mention was that it came with drivers - Meaning there was no actual problem. After properly connecting the MP3/USB Stick-Player it worked and there was no problem.

So, thanks all for your replies! :)

---

### Post by rkn on 2005-01-29
[QUOTE=panickedthumb] Windows 98 first edition supported USB.[/QUOTE]

For me and (many others) it recognized USB devices, but would crash if you tried to do anything with USB devices.

AFA the original post in this thread:
You should be able to get 96MB of RAM in that old box.   You can use [ Lame ](http://lame.sourceforge.net/) even in the existing OS to convert the music files.  Once it is cleaned up, I would install a Debian-based distro and use icewm for a desktop.

-BoB

---

### Post by bitfoo on 2005-01-29
Just to clear up any confusion on USB supported devices in early Windows versions:

Windows 98 (Gold) 

Audio
HID 1.0 (Includes Keyboard, Pointing Devices)

 

Windows 98 SE

HID1.1 (Allows Interrupt OUT transfers)
Communications (modem)
Still Image Capture (Scanner, Camera) (First phase/preliminary)

 

Windows 2000 / Windows ME

Mass Storage
Printer

---

### Post by dare2dreamer on 2005-01-31
One nice thing about Ubuntu and DSL is that, under the hood, they are both Debian. You knowledge applies, and all you really need to learn is the specifics of that distro or the fact that it is a livecd.

RE: mp3 tools.

On my media server, I use a tool called jack to rip/encode/tag/sort my music. It's little more than a python front end for cdparanoia, lame and the like, but damn if it doesn't work well once you get it configured.

I was so happy with it I ended up not installing a ripping tool on my desktop.

For tagging, I use easytag and audio tagtool, depending on what I'm doing. Easytag's good for large piles of mp3s, tagtool's better for cleaning up one file (and it's a lot prettier to look at)

RE: old hardware

Whenever I've messed around with older hardware, I've found its best to look for a console solution first...leave the big shiny graphical tools to your powerhouse machines. Sure, it often isn't pretty, but the system requirements are a heck of a lot lower than launching some bloated k-app.

For the record, I've installed Ubuntu on systems as low a spec as a pII-300 thinkpad with 160 megs of ram. I wouldn't call it even remotely fast, but I would call it useable. By comparison, Damnsmalllinux screams of course...but then again was specifically designed for this sort of graveyard hardware resurrection.

One point of bragging rites, the low-end laptop install was accomplished on a laptop with no cdrom and a dead floppy. Net install? Nah...I tossed the hard drive in another old laptop, did the base-only (custom/minimal) install, moved the hard drive back to the patient and apt-get'ed the ubuntu-desktop metapackage. To date, one of my favorite hacks.

---

### Post by king20878 on 2005-02-04
For the record I'm using Ubuntu on a Thinkpad 600E with a PII 366 and 192 megs of RAM.  I got it for about $200 off of Retrobox.com a while back.  I'm probably more productive with it than some folks with laptops costing 10 times as much. (he said smugly) :mrgreen:

---

### Post by poofyhairguy on 2005-02-04
[QUOTE=king20878]For the record I'm using Ubuntu on a Thinkpad 600E with a PII 366 and 192 megs of RAM.  I got it for about $200 off of Retrobox.com a while back.  I'm probably more productive with it than some folks with laptops costing 10 times as much. (he said smugly) :mrgreen:[/QUOTE]

Its that ram that get you by. Ubuntu with less than 128mb is a pain!

---

### Post by totalshredder on 2005-02-04
Hey, I'm new here, but I had a list of some good distros for that type of machine. Almost all of these distros will run VERY well on that computer you have there.

[Amigo Linux](http://www.amigolinux.org/) 
[Puppy Linux](http://www.goosee.com/puppy/index.shtml) 
[Luit Linux](http://luitlinux.sarovar.org/) 
[Deli Linux](http://delilinux.berlios.de/) 
[DamnSmall Linux](http://www.damnsmalllinux.org/)
[Feather Linux](http://featherlinux.berlios.de/) 

You should definitely check them all out, but I would actually not recommend damnsmall linux. Damn Small Linux may be small, but it is still going to run slower than some of the ones that are optimized for old computers. Damn Small Linux is completely optimized to be small, not nessisarily to be fast.

Good Luck on whatever you do, 

Luke

---

### Post by adbak on 2005-02-05
You may even want to try BeatrIX.  It's based on Ubuntu, but optimized to run on almost all pc's made in the last 10 years.  It's either 150 or 200 mb, so it's nothing huge, but it's not Damn Small.

[http://www.watsky.net/](http://www.watsky.net/)

---

