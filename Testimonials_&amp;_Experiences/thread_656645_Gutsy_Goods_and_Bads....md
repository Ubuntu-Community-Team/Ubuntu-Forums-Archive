---
title: "Gutsy Goods and Bads..."
date: 2008-01-02
forum: Testimonials &amp; Experiences
---

### Post by High_Yield on 2008-01-02
Hi-

I'm new to Linux and want to briefly share my unedited thoughts on Gutsy w/ Gnome stuff...
First, the "goods":
- It's free !!!!
- Updater seems to work
- Add/Remove apps is nice, and works
- Compiz is VERY pretty to look at and w/ some tweaking can run all the time(while gaming)
- Open Arena
- System Monitor and other apps integrate nicely into the navigation bars
- Free childrens games
- tons of free applications in general
- Video capture using firewire(IEEE 1394) works - but needs tweaking first - bummer.
- Pidgin and Evolution are nice
- Abiword and Open Office (OO exists in "bads" as well) integration w/ Microsoft docs
- Nautilus is OK
- It Runs, as long as power management is off - she stays running ;)

Now the "bads"
- We'll start with the worst, gedit.
- - It simply does not play well with samba - it sux0rs.
- -  It looks nice and has "neato" features, but doesn't work with my Linux NAS ;(
- - Getting some "tude"(attitude) from developers when posting issues - BIG bummer
- - It's not a Samba problem, it's gedit - other apps work just fine w/ SMB thank you...
- Firefox sux, slow.  IE is better and faster, sorry fans. Trying Opera and SeaMonkey next
- Flash installation sux with... everything
- Navigation bars lose their settings from time to time - annoying
- Weird CDRom duplicate mountings appear on my desktop some time
- Some apps simply to not wish to see the network during a file/open
- sudo this, sudo that...
- Starcraft and wine - boooo  (just do a dual boot and be done with it)
- Power management is buggy and problematic
- Open Office takes seemingly forever to load initially - bummer
- Startup and shutdown time is slower than M$ Windows, sorry again fans
- SMB setup/integration could be a bit more user friendly via UI
- I can change some default apps (internet, terminal) but not text editor?  why?
- Sessions? Services? Hal ??
- - Why so many Getty's running, and "kgameportd" is running when off in the bios ?

So, on the whole I will certainly be moving away from M$.  They've been good to me, and me to them but it's time to part ways.  I can do everything I need in Linux save Battlenet and an old Win2K partition and Grub edit solves that problem.  Internet, video capture, MS Word interoperability, Email, Chat, Calculator, BitTorrent - all I need is there - thanks guys.

Please get the Nautilus guys to work on GEdit - or - replace the default text editor with something else.

Flame if you must - I said unedited thoughts... Take care all.

- B

---

### Post by Sef on 2008-01-02
Moved to Testimonials and Experiences.  

> Flame if you must - I said unedited thoughts... Take care all.

Flaming is not allowed on Ubuntu Forums.

---

### Post by cytg on 2008-01-03
linux noob throwing in some comments ;

1. firefox : but anything else but firefox with noscript is just an invitation to get infested.
2. OO is plenty fast here.
3. Ubuntu load AND shutdown times is way faster than windows on this system too.. and thats a windowsxp loading off a raptor disc and ubuntu off a 500G hitachi.

Im having hardware that just works out of the box like printer and tv-card .. the printer really did me in in windows, if you made an error during installation under windows you'd be fsck'ed, just wouldnt reinstall.
Linux got edges. Windows got edges.
Windows is microsoft, and you gotta hate that just by observing how the company conducts it self.
Windows got games. There is no denying it, gaming under linux sucks a big one. 
I suspect until we get fullblown 3D accellerated virtualization gaming under linux it will remain a geeks wine-quest.( but it would be cool wouldnt it, fire up virtual box, start the windows(tm)-game-emulation engine to play you favorite FPS)

I'll be dualbooting until that happens :)

---

### Post by Geekkit on 2008-01-03
I don't think you'll get any flames in here - maybe a couple of rebuttals ... such as mine:  :)

1.) I'm curious about the SMB/Gedit thing ... what exactly was wrong? I haven't noticed anything weird about it myself and I've edited SMB and other config files with Gedit. Could you elaborate on the exact issue(s)?
2.) "Tude" sux yes. I hate that too. I once complimented a dev group on a particular feature and got banned for not putting it in the correct forum. That sort of thing kills O/S efforts (IMO)
3.) Did you file a bug report on the NAS problems?
4.) IE being faster is a misnomer. IE appears faster because it's part of the OS and therefore is loaded into memory (or at least parts of it are loaded into memory)  even before you click on the icon. If Firefox was loaded into memory just like IE is, you would see the same immediate startup.
5.) The last Flash update has been fixed. They were pointing to a different part of the Adobe site and Adobe changed the URL (I think that's what the issue was). If you grab the Deb version or if you get the latest update it works like a charm.
6.) Nav bars .... yes, this is a bug. I saw this listed. This one pisses me off too. Name and date keep rearranging themselves ... it's like some sort of psychological warfare on me. Hopefully they'll fix this.
7.) CD-ROM error? That sounds odd. H/W issue? I haven't seen this since ... XP without the service pack. :)
8.) Sudo this and sudo that help protect you from downloading and installing something that is hostile. Doesn't Vista do the same too? I seem to remember it pops up with reminders that "you are performing an unsafe operation" or something to that extent.
9.) OO does take a while to load the first time. I also remember M$ Office 2007 being horrible to load as well too (although M$ Office 2003 was quite peppy)  ... even after the 2nd and 3rd time loading. :)
10.) Text editor can be changed quite easily actually. All you do is right click on a text file, click on the properties menu item in the popup menu, click on the "open with" tab in the popup dialog, and select your favorite editor. I have mine set to Geany. That sort of configuring is quite similar to Windows and so I found it quite intuitive.

I agree with you, Ubuntu is not perfect and in fact I think a few things in 7.10 have made this version of the Ubuntu distro less stable. But it is free and I'll be damned if I'll downgrade to Vista. ;)

---

### Post by High_Yield on 2008-01-04
Good guys - keep in mind that I'm not a M$ fanboi - just staing my unbiased observations.

Quick notes:
- My ubuntu box is dual boot with Windows 2000.  I'used Windows so long I can really pare down the services and memory, which I have running normally at ~ 64 meg - so it is FAST to boot and run IE 6.  I'm telling you, on my PC it is much faster than firefox, opera, and Flock.  But again - I have this this really tuned.

- Geekit - my Samba issues are listed in detail as a bug - and you get to see some of the developer "tude" as well ;(  Bug# [https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/177710](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/177710)
You'll see they refer me to another issue wihch is similar, and related in functionality.
At the ensd of the day - it does not operate as well as the other GNome programs I've used.

- And for the text editor, thanks and I am familiar w/ the "open with" option.  But, I was looking for something like what exists in the SYSTEM/PREFERENCES/PREFERRED APPLICATIONS menu so I can simply single click to open.  I'm sure there is a config file out there storing this info - I just haven't found it yet.

Take care guys - still having fun w/ ubuntu and as stated - I'm never looking back to M$.

- B

---

### Post by armandh on 2008-01-04
I had flash and firefox speed issues in 7.10 but not in 7.04

---

### Post by Geekkit on 2008-01-04
> **armandh said:**
> I had flash and firefox speed issues in 7.10 but not in 7.04

I have found the same problems too.

---

### Post by cytg on 2008-01-04
One more thing.
I have been very frustrated with my HP AllInOne printer/scanner/etc under windows. Windows would have to have some perfect combination of regional setting or the installation would br0k halfway thorugh with missing dll' files ... and god forgive me if tried installing the drivers by just plugging in the usb cable and pointing to the files.. Windows would NOT recover from that one.(well, windows would, but the printer be dead).
lots and lots of issues under windows with this printer "hp psc 1210".

But not under ubuntu. Just works. Out of the box. XSane for scanning there you go.

Just like that. I've spend HOURS troubleshotting this thing in windows.

THANKS!

(now i only need a good ocr application like omnipage, anyone know ? :))

---

### Post by Geekkit on 2008-01-05
> **High_Yield said:**
> Take care guys - still having fun w/ ubuntu and as stated - I'm never looking back to M$.
- B

Cheers High_Yield, take care mate. :)

---

### Post by Comhra on 2008-01-06
Easy to speed up Open Office:

[http://www.ghacks.net/2007/08/18/speed-up-open-office/](http://www.ghacks.net/2007/08/18/speed-up-open-office/)

---

### Post by conehead77 on 2008-01-06
> **Comhra said:**
> Easy to speed up Open Office:

[http://www.ghacks.net/2007/08/18/speed-up-open-office/](http://www.ghacks.net/2007/08/18/speed-up-open-office/)

Very nice!

---

