---
title: "The Nokia N800: My new toy"
date: 2008-04-13
forum: The Cafe
---

### Post by jdong on 2008-04-13
I recently bought a N800 after spotting one on sale for $200USD. A quick glance at the specs and I thought it was a nice catch.

Hardware-wise, it's a 400MHz TI OMAP pseudo-dual-core (400MHz ARM CPU with 300MHz TI DSP). Hardware-wise, it runs the Maemo OS, which is a modified version of Debian GNU/Linux.

Overall I am extremely impressed with it. first of all, it works **flawlessly, beautifully, with great polish** from the moment you press the power button. This is, IMO, a lot more than can be said about the Asus EEEPc for example, which even die-hard fans have to admit is far from perfect out of the box.

As far as customizations, the thing comes with a terminal by default and can and a quick look around shows that the OS uses:

(1) Standard armel Debian port, Linux 2.6.21
(2) Standard apt-get, with a user-friendly frontend
(3) Standard freedesktop.org .desktop file launchers
(4) A Mozilla based browser that even takes minimally modified Mozilla plugins!


With that said, there's great room for extensibility on this. While using it, I couldn't help but notice that this thing from a hardware perspective is **completely inferior** to my iPod Touch (RAM, CPU, storage, etc) but Nokia has designed this thing to cater to its users rather than locking them into a proprietary and further crippled OS.


Another highlight: battery life! I've read some of the whitepapers on this, but apparently the battery life goes something like this: 3hrs on intensive (i.e. CPU fully loaded) usage, 9 days (!) if display is shut off and the system is just idling or doing minor e-mail checking, etc.

I've used it on Friday as my laptop replacement for the day, doing everything from webmail to SSHing and at the end of what I'd estimate to be 6hrs of active usage, it reports 3/4 battery life.


This is definitely my new favorite gadget!

---

### Post by PartisanEntity on 2008-04-13
Thanks for the review, I had been toying with the idea of getting myself a N800 for a while too. Specs sound great.

---

### Post by wipeout140 on 2008-04-13
I just upgraded from my 770 to n810 using the latest 2008 OS. There is alot of extra software from these links:

[http://maemo.org/](http://maemo.org/)
[http://www.internettablettalk.com/](http://www.internettablettalk.com/)

**_Great Software to install:_**

Maemo Mapper
[http://maemo.org/downloads/product/OS2008/maemo-mapper/](http://maemo.org/downloads/product/OS2008/maemo-mapper/)

Personal Menu
[https://garage.maemo.org/projects/personal-menu/](https://garage.maemo.org/projects/personal-menu/)

Pidgin
[http://maemo.org/downloads/product/OS2008/pidgin/](http://maemo.org/downloads/product/OS2008/pidgin/)

Numpty Physics
[https://garage.maemo.org/projects/numptyphysics/](https://garage.maemo.org/projects/numptyphysics/)

NuvoClear
[https://garage.maemo.org/projects/nuvoclear/](https://garage.maemo.org/projects/nuvoclear/)

Statusbar Clock
[https://garage.maemo.org/projects/statusbarclock/](https://garage.maemo.org/projects/statusbarclock/)

---

### Post by Onyros on 2008-04-13
Welcome to the "club" :D

First of all, make sure you upgrade to OS2008 (which, among other things, will restore the CPU's default clock to 400MHz), and then there are a few things I'll recommend:

--> First things first: head over to [this site]("http://www.gronmayer.com/it/") and nab a few of those repos. Well, use your first install to test things around, so you can add all repos while you're at it. Forget about using the included App Manager, go through things by the terminal (apt-get). You'll have to install **becomeroot** first, so you use your root account.
--> Install **Modest** and/or **Claws-Mail** - the default app is not working very well, especially with IMAP;
--> Get **Xournal**. Never mind if you don't like it or have found no use for it before on your desktop. It's a must-have app for the N800;
--> Upgrade to **rtcomm**'s beta (that's the default IM on the IT's). With it you can use almost all IM protocols available (Jabber, MSN, AIM, etc);
--> Symlink your MyDocs folder to one of your SD cards - that'll leave more space available for additional apps, especially taking into account you only have 256MB available;
--> Get **XMMS** for the N800 :)
--> Get **osso-statusbar-cpu**. I use it to have the time displayed always, and to launch a few apps... including **emelFM** (which I installed from Debian armel's port, btw - there's also emelFM2 compiled for the IT's, but I prefer the original);
--> Default fonts are huge, HUGE, taking a whole lot of space. There are a few themes with smaller fonts enabled, or you can just edit the existing themes with **nano** (available for download) or **Leafpad** (also available for download);
--> The only option for .doc files available is still **antiword** (or **docreader**, which is just a frontend). AbiWord has been in private beta testing for a while.
--> If you like the oldie goldies... make sure you install **SCUMMVM**.
--> **Contacts** + **Dates** + **Tasks** (also available in Ubuntu's repos, btw) are still the most reliable PIM apps for the N800. Yeah, **Osmo** is also available, but it still hasn't been compiled specifically for the IT's (meaning, Hildonized);
--> **MPlayer** is also a must have, works perfectly with Media Converter for Linux (a java app) for transcoding video files (**mencoder** needed on the desktop, but I suppose you'll have it by default);
--> **gFTP** is the best FTP app for the N800, but you'll have to reduce those themes' font sizes before it is usable. MaemoFTP is very, very limited;
--> **Maemo WordPy** is a great IT blogging software;
--> **Skype** works perfectly, but whenever possible I'd still recommend **Gizmo**;
--> **MaemoPad+** is a great sketching option. Xournal beats it for note-taking, though.
--> **FBReader** is compulsory :)
--> If you are one of the lucky ones to have a Jaiku account, **Mauku** is a great app to have as well;
--> Same goes for **Vagalume**, which is a simple, yet really cool Last.fm client;
--> Get **VNCViewer**, obviously;
--> Finally... just to show off... install **Quake** on your N800. hehe

These are just a few recommendations, from a user's standpoint, not a developer's, obviously :)

Also, never shut it down. Reboot through the terminal when needed ("shutdown -r now"), but other than that just leave it on, like a cellphone. There's no reason whatsoever to shutdown the IT's, especially given the fact that the boot process drains a whole lot of power. Just press the power button and "Lock touch screen and keys" and let the display dim automatically. That way you'll be notified through the IT's led that you've received email, or even leave your IM app open, which will notify you you've received a message pretty much the same way. Mine's with an uptime of around two months now, and that was because I had to reboot it to install some app I don't remember now.

The OMAP CPU is very, very good in terms of power-saving. Look around for a terminal app for the IT's named "battery-status", it'll give you a better idea of what is going on with your IT's battery as well.

---

### Post by jdong on 2008-04-13
Thanks for those tips! I'll look into them today.

---

### Post by bobbybobington on 2008-04-13
I got mine last week, definately awesome. It makes a nice laptop replacement (I consider my laptop a desktop replacement) as it's more portable. I put canola 2 on it and now it makes a nice mp3 player. More fun and flexible that the iPod touch imo. The screen resolution is really nice too.

---

### Post by kerry_s on 2008-04-14
i was just looking at the n800, i spotted 1 in my local craigslist->
[http://honolulu.craigslist.org/oah/sys/641179300.html](http://honolulu.craigslist.org/oah/sys/641179300.html)

i been goggling it, haven't decided yet, seems a bit under powered to me.

---

### Post by jdong on 2008-04-14
> **kerry_s said:**
> i was just looking at the n800, i spotted 1 in my local craigslist->
[http://honolulu.craigslist.org/oah/sys/641179300.html](http://honolulu.craigslist.org/oah/sys/641179300.html)

i been goggling it, haven't decided yet, seems a bit under powered to me.

Well, it's a $200 touchscreen tablet, the specs are what Id consider to be normal and on par with competitors in the size area (see: HTC's Windows Mobile devices, apple's iPhone/iPod Touch, etc)


Sure when Intel comes out with some chip that's powerful AND **idles for 6 days TURNED ON** (that's not standby, that's fully running Linux), I'll be first in line ;-)

---

### Post by kerry_s on 2008-04-14
> **jdong said:**
> Well, it's a $200 touchscreen tablet, the specs are what Id consider to be normal and on par with competitors in the size area (see: HTC's Windows Mobile devices, apple's iPhone/iPod Touch, etc)


Sure when Intel comes out with some chip that's powerful AND **idles for 6 days TURNED ON** (that's not standby, that's fully running Linux), I'll be first in line ;-)

:lolflag:
i'm in line, so will see.

---

### Post by Ioky on 2008-04-14
I get my Nokia 770 about a year ago for 150, I love it so much, it is almost like a laptop, and it can do funny thing, I love the function under the 800 but I like the look of the 770 better. 

by the way, thanks for the reviews. sounds great.

---

### Post by chucky chuckaluck on 2008-04-14
a 'new toy' thread with no pics? i'm reporting this thread.

---

### Post by jdong on 2008-04-14
> **chucky chuckaluck said:**
> a 'new toy' thread with no pics? i'm reporting this thread.

Well I assumed people know or can google for what the N800 looks like. My photographic skills are quite pathetic to say the least :D

---

### Post by Onyros on 2008-04-14
Hehe, mine's imitating his older brother (running Awesome, but the n800 through VNC).

The X31 looks huge compared to it :)

---

### Post by graabein on 2008-04-15
Here's a gallery for you. Had to browse it myself cause this here Nokia stuff sounds interesting.

[http://www.engadget.com/photos/nokia-n810-hands-on/]("http://www.engadget.com/photos/nokia-n810-hands-on/")

---

### Post by qwerty12 on 2008-04-15
Hehe, I have one, really nice :)

Look into running KDE of it :), I have it on one of my SD cards and it's really nice :)

---

### Post by bruce89 on 2008-04-15
It'd be perfect if the Web browser didn't take so bloody long to start.

---

### Post by aeiah on 2008-04-15
ive got a 770. had it ages. i take it if im going on a city break or something so me and the girlfriend can watch a movie on the train and do the odd web search when we're there for a map or opening times for things etc. usually it just sits in the kitchen at our flat connected to some speakers, streaming music via UPnP from my pc.

last year we went around south america for 3 months backpacking. i didnt take it because i didnt want it getting stolen and to be honest, i dont think it would have been all that useful. getting usb sticks to work with it is annoying (gotta power them with 5v and manually mount). next time im backpacking i think ill get an eeepc rather than a newer nokia, but only because usb backup of photos and aircrack-ng packet injection is supported

---

### Post by qwerty12 on 2008-04-15
> **bruce89 said:**
> It'd be perfect if the Web browser didn't take so bloody long to start.

Try the "fennec". I don't have a link but its basically FF 3.0 mobile for the N800. Supports normal FF extensions and the speed is much faster.

---

### Post by jdong on 2008-04-15
> **qwerty12 said:**
> Try the "fennec". I don't have a link but its basically FF 3.0 mobile for the N800. Supports normal FF extensions and the speed is much faster.


I'm already working on patching microb up to xulrunner 1.9 :D

---

### Post by Jackster on 2008-04-15
I have an N800, bought it a little while ago after OS2008 became available for it. My favourite app for it is ScummVM, but then again ScummVM is just my favourite app full stop :)

Hope you have fun with your new toy :-D

---

### Post by wipeout140 on 2008-04-15
> **jdong said:**
> I'm already working on patching microb up to xulrunner 1.9 :D

Sounds Great as its running FF3 aplha1 at the moment

---

### Post by gerrymoth on 2008-04-21
> **Onyros said:**
> Welcome to the "club" :D

First of all, make sure you upgrade to OS2008 (which, among other things, will restore the CPU's default clock to 400MHz), and then there are a few things I'll recommend:

--> First things first: head over to [this site]("http://www.gronmayer.com/it/") and nab a few of those repos. Well, use your first install to test things around, so you can add all repos while you're at it. Forget about using the included App Manager, go through things by the terminal (apt-get). You'll have to install **becomeroot** first, so you use your root account.
--> Install **Modest** and/or **Claws-Mail** - the default app is not working very well, especially with IMAP;
--> Get **Xournal**. Never mind if you don't like it or have found no use for it before on your desktop. It's a must-have app for the N800;
--> Upgrade to **rtcomm**'s beta (that's the default IM on the IT's). With it you can use almost all IM protocols available (Jabber, MSN, AIM, etc);
--> Symlink your MyDocs folder to one of your SD cards - that'll leave more space available for additional apps, especially taking into account you only have 256MB available;
--> Get **XMMS** for the N800 :)
--> Get **osso-statusbar-cpu**. I use it to have the time displayed always, and to launch a few apps... including **emelFM** (which I installed from Debian armel's port, btw - there's also emelFM2 compiled for the IT's, but I prefer the original);
--> Default fonts are huge, HUGE, taking a whole lot of space. There are a few themes with smaller fonts enabled, or you can just edit the existing themes with **nano** (available for download) or **Leafpad** (also available for download);
--> The only option for .doc files available is still **antiword** (or **docreader**, which is just a frontend). AbiWord has been in private beta testing for a while.
--> If you like the oldie goldies... make sure you install **SCUMMVM**.
--> **Contacts** + **Dates** + **Tasks** (also available in Ubuntu's repos, btw) are still the most reliable PIM apps for the N800. Yeah, **Osmo** is also available, but it still hasn't been compiled specifically for the IT's (meaning, Hildonized);
--> **MPlayer** is also a must have, works perfectly with Media Converter for Linux (a java app) for transcoding video files (**mencoder** needed on the desktop, but I suppose you'll have it by default);
--> **gFTP** is the best FTP app for the N800, but you'll have to reduce those themes' font sizes before it is usable. MaemoFTP is very, very limited;
--> **Maemo WordPy** is a great IT blogging software;
--> **Skype** works perfectly, but whenever possible I'd still recommend **Gizmo**;
--> **MaemoPad+** is a great sketching option. Xournal beats it for note-taking, though.
--> **FBReader** is compulsory :)
--> If you are one of the lucky ones to have a Jaiku account, **Mauku** is a great app to have as well;
--> Same goes for **Vagalume**, which is a simple, yet really cool Last.fm client;
--> Get **VNCViewer**, obviously;
--> Finally... just to show off... install **Quake** on your N800. hehe

These are just a few recommendations, from a user's standpoint, not a developer's, obviously :)

Also, never shut it down. Reboot through the terminal when needed ("shutdown -r now"), but other than that just leave it on, like a cellphone. There's no reason whatsoever to shutdown the IT's, especially given the fact that the boot process drains a whole lot of power. Just press the power button and "Lock touch screen and keys" and let the display dim automatically. That way you'll be notified through the IT's led that you've received email, or even leave your IM app open, which will notify you you've received a message pretty much the same way. Mine's with an uptime of around two months now, and that was because I had to reboot it to install some app I don't remember now.

The OMAP CPU is very, very good in terms of power-saving. Look around for a terminal app for the IT's named "battery-status", it'll give you a better idea of what is going on with your IT's battery as well.

I've had my N800 since Dec07 and totally loving it, got the following installed Canola2 beta8 (YouTube & Last.fm addons), Mauku, Maemo Wordpy, PAN Newsreader, MyPaint, Maemopad+, mPlayer, Transmission (Torrent downloads), Skype, USBControl (Connect External HD to the N800) and Fennec.

Checkout my site at nokiaaddict.com on what I've been doing with mine and if anyone needs a Jaiku invites just let me know I have 20 to give away.

Trying to get Ubuntu for ARM at [http://mojo.handhelds.org](http://mojo.handhelds.org) to install on my blooming N800.

---

### Post by EnergySamus on 2008-04-21
It looks pretty awesome... But I am not going to get one because I already have an iPod Touch.:KS:guitar::lolflag:

---

### Post by geoken on 2008-04-21
Call me a nerd, but this is probably the thing that makes me want an N800 more than anything else;

[http://www.gnome-look.org/content/show.php/LCARS+PADD+(Star+Trek)+Themes?content=47430]("http://www.gnome-look.org/content/show.php/LCARS+PADD+(Star+Trek)+Themes?content=47430")

---

### Post by init1 on 2008-04-21
> **EnergySamus said:**
> It looks pretty awesome... But I am not going to get one because I already have an iPod Touch.:KS:guitar::lolflag:
Likewise. Having both would seem redundant.

---

### Post by jdong on 2008-04-21
> **init1 said:**
> Likewise. Having both would seem redundant.

I do have both and they're not redundant at all. The iPod Touch offers the best movie playback in a portable device, while the N800 offers the best PDA computing in a portable device. Plus, loading on a terminal and SSH client on the N800 isn't (1) illegal (2) a matter of 3 hours of cross-compiling to a hacked platform.

They serve different purposes to me.

---

### Post by graabein on 2008-04-22
I don't have one so I have some questions...

Some reviews say application startup times are pretty long and that video playback has issues with image-sound sync... Can anyone confirm this? 

What is the average load time for starting a web browser? What do you use for playing video files? 

I suppose all formats are supported (flac, divx etc) if you can add any codec you want?



Update: Found some more info in this [thread]("http://ubuntuforums.org/showthread.php?t=625550&highlight=maemo").

---

### Post by warbread on 2008-04-22
> **geoken said:**
> Call me a nerd, but this is probably the thing that makes me want an N800 more than anything else;

[http://www.gnome-look.org/content/show.php/LCARS+PADD+(Star+Trek)+Themes?content=47430]("http://www.gnome-look.org/content/show.php/LCARS+PADD+(Star+Trek)+Themes?content=47430")

I'm with you there, actually.  I don't even consider myself a hardcore Trekky.  A geek is a geek is a geek, I suppose...

---

### Post by zmjjmz on 2008-04-22
jdong, stop convincing me!
I'm getting it as soon as I possibly can!

> **jdong said:**
> I do have both and they're not redundant at all. The iPod Touch offers the best movie playback in a portable device, while the N800 offers the best PDA computing in a portable device. Plus, loading on a terminal and SSH client on the N800 isn't (1) illegal (2) a matter of 3 hours of cross-compiling to a hacked platform.

They serve different purposes to me.

I'm not sure if voiding a warranty is illegal, and it takes like 5 minutes these days to install those. (With Ziphone).
Nonetheless, let me point out a few advantages for the N800:
Keyboard doesn't suck
Better software in repos
Debian Linux > Crippled proprietary BSD OS
I get a **choice** regarding my music/video player.
User extensible storage. (It may not seem like much now, but when 32GB SD cards cost 10$ 4 years from now, you'll appreciate it.)
Warranty isn't voided by modifications (from what I hear all over)

---

### Post by jdong on 2008-04-22
> **zmjjmz said:**
> 
I'm not sure if voiding a warranty is illegal, and it takes like 5 minutes these days to install those. (With Ziphone).


You are forgetting that Ziphone violates the EULA of the iPhone's OS, which is the legal concern I am referring to. However, even WITH jailbreaking, you are still fighting with Apple an upstream battle to customize the thing. Every point-release update to the firmware means all your apps stop working; plus there's questions nobody has the answers to, like how can you open the video player via a program (i.e. a file manager)?

> 

Some reviews say application startup times are pretty long and that video playback has issues with image-sound sync... Can anyone confirm this?

Application startup is actually not bad -- I think it's comparable to a desktop Firefox 2 based browser. I'd estimate 3-4 secs for starting up the browser, 1-2 secs for opening a new window.

> 
What is the average load time for starting a web browser? What do you use for playing video files?

I suppose all formats are supported (flac, divx etc) if you can add any codec you want?

For video I use a combination of the built in media player and mplayer which I installed straight from the repositories. All formats are supported, but the ARM+DSP core is MOST efficient at decoding MPEG-4 ASP (aka xvid, divx) video and MP3 audio. With that said, it is a "weak" 400MHz ARM core and 300MHz DSP, and loading on a 720x480 high-bitrate video will likely be choppy. If you encode the video down to MPEG4 at 300-500kbit a 300x240 iPod type resolution, the video looks great and plays great.

In fact, I use mplayer often times to stream video from a HTTP server on my desktop.

---

### Post by tbrminsanity on 2008-04-23
I've been looking into getting either the N810 or the N800 to replace my Palm Tungsten C.  I need a PDA that I can view and edit documents, it needs a calender (If it can run Sunbird that would be great), calculator, checklist/TODO list, Encrypted storage (for private information), and have the ability to share data with my home computer (Ubuntu) easily (either via FTP or a sync tool).  I like the web features of this device (which means I can use Google Docs for most of my office needs) but I'm not sure I need the GPS feature of the N810 (though I like the keyboard).

What would everyone suggest I look into getting?  Where would be the best place to get it?

---

### Post by Wes Doobner on 2008-04-26
> **tbrminsanity said:**
> I've been looking into getting either the N810 or the N800 to replace my Palm Tungsten C.  I need a PDA that I can view and edit documents, it needs a calender (If it can run Sunbird that would be great), calculator, checklist/TODO list, Encrypted storage (for private information), and have the ability to share data with my home computer (Ubuntu) easily (either via FTP or a sync tool).  I like the web features of this device (which means I can use Google Docs for most of my office needs) but I'm not sure I need the GPS feature of the N810 (though I like the keyboard).

What would everyone suggest I look into getting?  Where would be the best place to get it?

A laptop.

---

### Post by Acglaphotis on 2008-04-26
My n800 just died on friday... :( Make sure to upgrade to 2008 OS its much better than the default.

---

### Post by tbrminsanity on 2008-04-27
> **Wes Doobner said:**
> A laptop.

I already have one, but I can't carry a laptop in my picket or take it to board meetings.  I need a PDA and I'm not willing to get a smartphone as the data packages in my area are stupid.  Most of the province has a free Wifi net available if I need it.

---

### Post by helliewm on 2008-04-27
I bought an N800 for the same reason as you, yes it fine as a PDA. 
You can now put Ubuntu on the N800 see here [http://www.linuxdevices.com/news/NS2097004728.html]("http://www.linuxdevices.com/news/NS2097004728.html")
and here [http://mojo.handhelds.org/frisky]("http://mojo.handhelds.org/frisky")
The Internet Tablet Talk forum is solely devoted to the N800/N810
 

Helen

---

### Post by maniacmusician on 2008-04-27
> **tbrminsanity said:**
> I already have one, but I can't carry a laptop in my picket or take it to board meetings.  I need a PDA and I'm not willing to get a smartphone as the data packages in my area are stupid.  Most of the province has a free Wifi net available if I need it.
what about an EeePC? It's a subnotebook, priced similarly to the Nokia Tablets. They have various models rated at different prices, and newer versions with larger screens. It also seems to me that they're slightly more versatile, given the ease with which you can choose different toolkits and working environments. They don't come with GPS, though.

If not, I'd go with the N810, although Nokia is probably going to come out with a new one next spring that will be even more appealing. 

(sorry if you'd already rejected the Eee in previous pages)

---

### Post by graabein on 2008-04-28
Thank you for answering. I can get a N800 for about $300 I think. I'd like to get hands-on experience with it before I buy one though. 

:-k



Update: How is the sound quality if you use regular minijack headphones?

---

### Post by tbrminsanity on 2008-04-28
> **maniacmusician said:**
> what about an EeePC? It's a subnotebook, priced similarly to the Nokia Tablets. They have various models rated at different prices, and newer versions with larger screens. It also seems to me that they're slightly more versatile, given the ease with which you can choose different toolkits and working environments. They don't come with GPS, though.

If not, I'd go with the N810, although Nokia is probably going to come out with a new one next spring that will be even more appealing. 

(sorry if you'd already rejected the Eee in previous pages)

I looked into the EeePC but it is not quite what I want.  I want something I can physically put into my pocket.

---

### Post by graabein on 2008-05-06
Can someone post a screenshot of these forums as seen on the N800/N810 with OS2008? 

I was wondering how [Prism]("http://wiki.mozilla.org/Prism") would work with Google apps like gmail, reader, calendar, docs etc on the N800... 

How are the load times? Does it fit the screen? Font size?

---

### Post by Mr. Picklesworth on 2008-05-06
Prism would be horribly pointless when there is already a web browser with a sleek interface, the window manager is Matchbox and web bookmarks are directly available on the top left of the interface. Having said that, it could work; web pages are surprisingly nice on here, thanks to the 800x480 resolution. (I run an iPod user agent on there, too, which helps with a few sites to get the fancy, mobile and finger-friendly version).

Screenshots: [http://www.internettablettalk.com/forums/showthread.php?t=5014](http://www.internettablettalk.com/forums/showthread.php?t=5014)

Oh, and just to show how themeable this is: [http://synthesize.us/LCARS_PADD](http://synthesize.us/LCARS_PADD)

---

### Post by tbrminsanity on 2008-05-06
> **Mr. Picklesworth said:**
> 
Oh, and just to show how themeable this is: [http://synthesize.us/LCARS_PADD](http://synthesize.us/LCARS_PADD)

That theme alone is what makes me drool over this PDA (And I am not a trekkie).

---

### Post by graabein on 2008-05-06
> **Mr. Picklesworth said:**
> Prism would be horribly pointless when there is already a web browser with a sleek interface, the window manager is Matchbox and web bookmarks are directly available on the top left of the interface. Having said that, it could work; web pages are surprisingly nice on here, thanks to the 800x480 resolution. (I run an iPod user agent on there, too, which helps with a few sites to get the fancy, mobile and finger-friendly version).

That's sort of what I figured then :) Thanks for the screenshots. I can hardly wait to get mine. 

How is the sound quality when playing flac with decent headphones?

---

### Post by tbrminsanity on 2008-05-28
OMG I love my new N800!!!

---

### Post by Onyros on 2008-05-28
Ah... I defected from the N800 lines, just a couple of weeks ago and I already miss mine.

I have a new toy (7 inch EEEPC), though, but it's not as much of a challenge as the N800 was :P

---

### Post by tbrminsanity on 2008-05-28
Is there some way to add Gnomes standard locations into the OS2008.  My home town isn't in the list of possible locations.  In fact the only location in my timezone is in the south of the US (half a continent away from me).  I was shocked to find out that there are only a handful of Canadian cities in the device.  In fact there are very few north American cities period (just enough to cover all the standard DST timezones [which doesn't help me as my province doesn't do DST]).  Plus everything assumes I'm American now, instead of Canadian.

---

### Post by omegamormegil on 2008-06-22
I just got mine.  It's smaller than I thought, which is good, and so far it has exceeded my expectations.  The text it small, but it is very readable.  You can also zoom in if you can't read any particular page. This thing is freakin awesome.  

Thanks for the review, djong.  And thanks to Onyros for the links and software recommendations.  

I want to install vncviewer, but I haven't yet discovered which repo it's in.  Anybody know off hand?  I'm hesitant to add a bunch of repos I don't need just to get that one app.  

Thanks for any help.

---

### Post by vjones777 on 2008-06-25
> **omegamormegil said:**
> I want to install vncviewer, but I haven't yet discovered which repo it's in.  Anybody know off hand?

Debian Nokia repository - [http://repository.maemo.org/extras]("http://repository.maemo.org/extras")

I just installed it from the maemo page - it auto opened the app manager.
This version of VNC Works nicely. :)

---

### Post by vjones777 on 2008-06-25
> **tbrminsanity said:**
> I've been looking into getting either the N810 or the N800 to replace my Palm Tungsten C.  I need a PDA that I can view and edit documents, it needs a calender ..., calculator, checklist/TODO list, Encrypted storage (for private information), and have the ability to share data with my home computer (Ubuntu) easily (either via FTP or a sync tool).

You do know you can install Palm apps on the N800 (& N810)? 
Just install the GarnetVM and you can then install any Garnet apps including PIMs, calculators etc.   :)

---

### Post by tbrminsanity on 2008-06-26
> **vjones777 said:**
> You do know you can install Palm apps on the N800 (& N810)? 
Just install the GarnetVM and you can then install any Garnet apps including PIMs, calculators etc.   :)

I was able to find as many native apps to replace apps on my Palm.  But I do use GarnetVM for stuff I haven't found yet.  I couldn't find a good password generator but Palm has those in spades, plus YAUC (Yet another universal converter).  I got abiword installed on my PDA but it isn't the best.  I wish there was something better that could modify .doc files offline.  As for other office tools I have Gnumeric which is great (very few bugs).  I'm thinking of installing Documents to go on GarnetVM so I can modify .doc files.

---

### Post by Hells_Dark on 2008-06-26
I would one too but no money :'(
Any info for a new NXX0 ?

---

### Post by tbrminsanity on 2008-06-26
> **Hells_Dark said:**
> I would one too but no money :'(
Any info for a new NXX0 ?

Nothing yet, but I have a sinking feeling that the next NX00 will run Symbian (due to Nokia's recent buyout of Symbian and promise to make it FLOSS).  That being said it will probably be a combo of Internet tablet, GPS, and cell phone all together.  It may even be a larger version of their new phone (N96).  

[http://www.finalsense.com/news/it/phone/nokia_n96.htm](http://www.finalsense.com/news/it/phone/nokia_n96.htm)

Of course this is all speculation and nothing is final till pre-release day.

---

### Post by temaki on 2008-06-26
Can you play/convert divx for the device?  This would be one of the main reasons for me to get it.

T

---

### Post by tbrminsanity on 2008-06-26
> **temaki said:**
> Can you play/convert divx for the device?  This would be one of the main reasons for me to get it.

T

Not sure but probably.  It supports a large range of formats to start with.  Doesn't MPlayer support DivX?

---

### Post by wipeout140 on 2008-06-26
also a new firmware come out two days ago for n800/n810. it runs alot smoother

---

### Post by Hells_Dark on 2008-06-26
> **wipeout140 said:**
> also a new firmware come out two days ago for n800/n810. it runs alot smoother

Wanna :(

---

### Post by jdong on 2008-06-26
> **temaki said:**
> Can you play/convert divx for the device?  This would be one of the main reasons for me to get it.

T

It plays almost all formats that ffmpeg can play, but the ARM CPU is limited in processing power, and it helps immensely to resize the videos down to the native display size or smaller to avoid frame skipping and excessive battery usage... What I usually use is 320x240 DIVX@400kbit/s with MP3 audio... just a straight shrink-down of regular downloaded DIVX files.

---

### Post by aktiwers on 2008-06-26
All of a sudden I see no reason to get an Iphone..  I was going to by one.. Think I will go for this one instead! Thanks!

---

### Post by zmjjmz on 2008-06-26
Does anyone know of any way to get Mobile Broadband (preferably 3G) hooked up to this thing?

---

### Post by wipeout140 on 2008-06-27
Also Rotation on Device is even easily (Video to show) - [http://www.youtube.com/watch?v=Mn31X6-t5Z0](http://www.youtube.com/watch?v=Mn31X6-t5Z0)

Complete Walkthrough on getting rotation working step by step (Newbie Friendly) - [http://www.internettablettalk.com/wiki/index.php?title=How_To:_Enable_screen_rotation_in_Diablo](http://www.internettablettalk.com/wiki/index.php?title=How_To:_Enable_screen_rotation_in_Diablo)

For more help and what you go do go here - [http://www.internettablettalk.com/forums/showthread.php?t=17842]("http://www.internettablettalk.com/forums/showthread.php?t=17842&page=6")

> **zmjjmz said:**
> Does anyone know of any way to get Mobile Broadband (preferably 3G) hooked up to this thing?

I assume just pairing your phone with device should work

---

### Post by helliewm on 2008-06-27
3G internet access. 

Yes paring with your phone does work. I have an N800 and a T-MObile Flex 35 with Web n Walk Max 10 gig bandwith including VOIP/Audio Streams contract costs about 40.00but its brilliant. This is the UK though. 

Helen

---

### Post by tbrminsanity on 2008-06-27
> **jdong said:**
> avoid frame skipping and excessive battery usage.

I would say frame skipping may be a problem but not battery usage.  I love this device for the fact that I have it running full media all day at work and when I get home I surf like crazy on it.  The only time I plug it in is when I go to bed.  It is the only device I've ever owned that the battery life is listed in days (vs hours).

---

### Post by jdong on 2008-06-28
Hmm I find this to be largely untrue... on my N800 with ITOS 2008 if I load the ARM CPU core up to full load, the battery lasts 3 hrs at best. Video playback may be 4hrs.... But if I keep it idle, sure, I can reach into several days up to a week of standby much like a cell phone. ARM cores are REALLY power efficient when idle, but as soon as you start using it, performance-per-watt is probably worse than a core 2 duo ULV.

---

### Post by Mateo on 2008-06-28
Just don't see the point in one of these without cellular.  I don't have infinite pockets.

---

### Post by mtron on 2008-07-04
i just discovered the nice UPNP feature. Are you guys using upnp servers on ubuntu in conjunction with the N800?

What i am using now is the upnp server [fuppes]("http://fuppes.ulrich-voelkel.de/"). It streams audio without a glitch (tested with mp3 and ogg files), and also streams avi videos to the N800 internal Media Player - if they are already encoded with the proper DivX MPEG-4 Version 4 codec & 352x288 res. 24 fps ( i use [MediaConverter]("https://garage.maemo.org/projects/mediaconverter") for this)

In theory fuppes should also support on the fly transcoding by using ffmpeg. I managed to compile it with transcoding support But i did not get the [configuration]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Device_specific_settings") working for my N800 till now :( . 

Anyone succeeded in configuring fuppes to trancode video in a N800 friendly format or is there another UPNP Server for ubuntu that does the job?

---

### Post by jdong on 2008-07-04
> **mtron said:**
> 
Anyone succeeded in configuring fuppes to trancode video in a N800 friendly format or is there another UPNP Server for ubuntu that does the job?

I am in the process of writing my own CGI script that does this on the fly too :D

---

### Post by mtron on 2008-07-06
sounds cool. Do you mind sharing the cgi once it's done? The on-the-fly transcoding would be really nice.

Another - a bit off topic - question: is the sandbox sdk for diabolo available now ?

---

### Post by theDaveTheRave on 2008-07-06
Hi all.

this looks like the sort of toy I want to buy. My only question is why don't they make them with phone connectivity?

This is a great idea but with only having wifi access (that isn't exactly "cheap" or fully available) how do you maintain an "always on" connection without it also being able to get on a mobile network? If it could do this then I'm sure it would be even more popular than the Apple Iphone, and available on numerous mobile networks.

I assume that you all have a compatible bluetooth phone in your pocket, so as the tablet can recieve "normal" phone calls...

Also does this item work like a PDA also?? if so I think I want one just for the "PDA" and "SKYPE" facility.

another question (that may have allready been answered, I've only read about half of the thread... so sorry if I'm asking a previous question), how is the N800 for syncing into Gutsy or Hardy?

I look forward to the answers, and an upgraded version that has mobile phone connectivity.

David

I look

---

### Post by graabein on 2008-07-06
I read somewhere you can get Android on it pretty easily. Got mine and I like it a lot, especially with Canola2. Have not updated the firmware yet tough.

---

### Post by galeron on 2008-07-06
Does anyone have a script to encode video for the N800? I'm trying to find a way to convert all my DiVX videos so that I can watch them on the N800...

---

### Post by helliewm on 2008-07-06
thedavetherave: The N800 is not a phone its a mini computer. You can use bluetooth on your phone to establish a modem connection to connect to the internet when WIFI is not available. Go to [http://www.maemo.org]("http://www.maemo.org") there is a huge array of open source software available. Maemo is a debian derivative. So yes it can be used as a PDA. I use mine as a PDA, Mini PC. Instead of buying the Eeec I bought the N800.

The N800 was never intended to be a phone although as with any PC/Laptop you can use SKYPE.

Helen

---

### Post by Mr. Picklesworth on 2008-07-06
I purchased mine *because* it is not a phone, by the way. I have always hated telephones because they are a downright irritating communication method.

Regarding battery life, I agree that my N810 doesn't do well when in use for a huge chunk of time. I definitely get better than 3 hours out of it with web browsing, and can watch a fair number of hour-long videos on a single charge. (In that respect, I believe it holds its own against the iPod, which I should remind has a much smaller screen).

However, where Nokia really stands out is power management! This device seamlessly enters sleep mode in a way that lets me carry it around all day, using it in short bursts without needing to think about the battery. It's a different way of thinking, more in tune with a PDA (difference being this is *very* functional), and takes a little bit of getting used to.

Odd problem: Something I run seems to be constantly accessing the internal memory card. I can no longer connect the device via USB except when it is just starting up. I suspect that MPlayer has something remain after being closed. Anyone else seeing similar issues? Is there some good command line trick to finding the offending process? (What is accessing /media/mmc2?).
Similar issue going on with the backlight getting stuck on for a few minutes (even if I lock the device), this time *definitely* the fault of MPlayer. Why must it be such a decent media player?!

---

### Post by theDaveTheRave on 2008-07-10
helliewm: thanks for the response, that has answered my questions perfectly.... I've been thinking of getting the EeePC almost as a "PDA" type gadget, but why do I need that when I can reasonably easily take my laptop around with me!

I've been on the lookout for a replacement PDA ever since my PalmPilot died (about 3 years ago). Which as far as I'm concerned was the best gadget I ever had (followed a close second by the hand held food processor!), the Nokia E65 was almost a match for the Palm, but I couldn't syn to Ubuntu, and it couldn't email, but WiFi access was cool!

I've also been thinking about the OpenMoko N72 - but don't know when it will be on general release!

Thanks for all the comments of others here, as I now think that I will end up with a "cheap" mobile and something like the N800.

Thanks to all for a great thread and great help.

Dave

---

### Post by helliewm on 2008-07-10
The Openmoko isn't 3G/HDSPA. I have a T-MOBILE FLexT 35 Web n Walk Max Contract 900 MINS/TEXTS 10 GIG bandwith including SKYPE and audio/video streams. It costs about £45 a month. From [http://www.expansys.com]("http://www.expansys.com") I got a T-Mobile contract as above with a HP IPAQ 614c 3G/HDSPA it runs Windows Mobile Professional 6 yes it syncs as a modem with the N800 and my laptop. The Eeec just does not seem good value its just a sub power notebook. I am much happier with the N800 and my laptop. I use the N800 as a IPOD too, just bought a spare battery only £19.00. N800 has loads of open source software and you can use it for SKYPE.  

Let me know if you need more help, just PM me.

Helen

Ps I am 100% Ubuntu and use 64 bit Ubuntu Hardy and my laptop and Desktop, yes I did find a way to sync Windows Mobile Professional 6. I am so happy with this set up and will probably stick with the HP IPAQ's for my phone as they do sync with the N800 and Ubuntu laptop. Expansys has much better T-M0bile phones on contract than the official T-Mobile web site.

---

