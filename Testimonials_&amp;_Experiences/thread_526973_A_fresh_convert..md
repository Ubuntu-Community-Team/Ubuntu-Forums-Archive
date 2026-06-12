---
title: "A fresh convert."
date: 2007-08-16
forum: Testimonials &amp; Experiences
---

### Post by leathco on 2007-08-16
Well, while I am hammering the repositories, I'll tell my story to see what you all think.  This might be long, grab a drink and a snack.  :popcorn:

Well, my system is an HP Pavilion dv6227cl, desktop is custom made, still running windows til my next major hardware upgrade which will include parts easy to use in Ubuntu, but that's for another time, this story is about the laptop.  Here's the specs:  TL-50 Dual Core x64 CPU, 2 gigs of RAM, nVidia 6150 Video, 120 gig hard drive.  The system shipped with Vista, which was at first interesting, than delved into frustration.

First of all, Microsoft makes you pay extra if you want to install the 64 bit version by making you order the 64 bit install disc.  If I buy a 64 bit processor, why would I limit myself to a 32 bit OS?  I could understand if it's a licensing thing, but with Vista the license works for both 32 and 64 bit systems, it's just an extra charge.  Plus, tons of software and even some hardware I've had for a while are now non-working, with no hope of working due to no patches/drivers being released for these items anymore.  Due to this, and my semi-interest in Linux over the past 6 or 7 years, now was the perfect time to switch and start anew.

As a trial, I installed Ubuntu Ultimate 1.4.  Interesting disc with some minor problems.  No widescreen support, no 64 bit,  wifi support the biggest problems.  However, I used this to learn about the Ubuntu and Linux OS and how to operate it before I made my final leap, what I am working on right now, Ubuntu 7.04 64 big edition, DVD edition.  I was quite pleased at how easy it was to burn the disc under Linux.  I was also pleased with the general ease of use of Ubuntu, as prior experiences with Linux were interesting but quickly turned nightmarish.  The software repository was an excellent idea I quickly took advantage of, making a huge list of software I was interested in and started to download.  Open Arena quickly became a favorite game of mine.

The install was a bit frustrating, as it kept hanging.  After doing some research, hitting F6 and disabling a splash screen was all it took to install smoothly.  Also, it automatically set up my widescreen display perfectly, and the image was much crisper than it was under Ubuntu Ultimate.  

However, there's still minor issues here and there.  Still don't have wifi functional...the system sees the card as a Dell Broadcom device, so I think the driver is installed, but I can't connect to the network.  That's fine though, I love a challenge and this is the only major piece of hardware not functional, with the other being the Expresscard remote control, which I'm really not concerned with.  Surprisingly, the Quickplay buttons on my laptop are working flawlessly, and I expected to lose them when I made the switch.

Currently I am working on building a nice software collection through the suppositories, than exploring what I downloaded and learning the ways of the OS.  I'm also working on setting everything up in a darkened theme, as the defaults are rather bright.  Granted, Windows has the same issues, but it looks like Ubuntu is MUCH more customizable than Microsofts cash cow.

My goals right now are to get wifi working, learn the ins and outs of the OS, and begin setting up my usual system of downloads with new software on Linux.  I'm more or less giving up on moving on with Windows, though I will keep an old desktop with XP for old software purposes for now, although eventually if I get good enough with Linux it too will switch over.

Any chance on there being any good Ubuntu or Linux books I can read at work to help me along?

---

### Post by ukripper on 2007-08-16
Do you know what chipset your broadcom is? Doesyour card show up in restricted drivers?

if you do follwoing in terminal chipset will show up:

```
lspci
```

---

### Post by ukripper on 2007-08-16
The other day I saw a great book in BOOKS etc. store.

I couldn't help smiling to myself when i saw a complete shelf stacked  for Ubuntu.

Book name is Ubuntu unleashed. It is a great read although you can find eveything in forums and google but if you are travelling it is a great read and also good for quick references.

EDIT:

Here are few reviews on amazon for this book. 
[http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093](http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093)

---

### Post by leathco on 2007-08-16
Well, when I type that in it throws this at me for the chipset:  Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01), odd, considering I own an HP.

And I'll definately pick that book up.  I know I can find what I need in the forums, but I'm the type when I try to l try to learn something major, in this case an OS, I wanna bury myself in it.
.
EDIT:  Looks like there is a plethroa of books on Amazon.com solely on Ubuntu.  Should I start with the Official Ubuntu Book?

---

### Post by ukripper on 2007-08-16
> **leathco said:**
> Well, when I type that in it throws this at me for the chipset:  Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01), odd, considering I own an HP.

And I'll definately pick that book up.  I know I can find what I need in the forums, but I'm the type when I try to l try to learn something major, in this case an OS, I wanna bury myself in it.
.
EDIT:  Looks like there is a plethroa of books on Amazon.com solely on Ubuntu.  Should I start with the Official Ubuntu Book?

You can try this guide to make your chipset work - [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Your laptop maybe HP but chipset in the wirless card used would be similiar to the one for other Dell cards.

---

### Post by ukripper on 2007-08-16
Official ubuntu book is very similiar to the official guide provided.

if you are a beginner then certainly i would reccomend you fro ubuntu unleashed. I am going to get Hacking ubuntu soon but that is not for beginners but has pretty good customizations.

Regarding you wirless - Can you install wlassistant and try first configuring it perhaps your card is detected and could be working as normal.
to install type:
```
sudo apt-get install wlassistant
```

then to run it - 
```
sudo wlassistant
``` as it is a kde app you would need command line for that to run.

---

### Post by leathco on 2007-08-16
OK, after the current repository download is done I'll work on that wifi card.  Amazing how fast people are to help on these forums.

Already got 3d acceleration enabled using Envy.  Got a nice dark themed system too, so it don't shine like a light bulb, lol.

Interesting how the card is almost the same to a Dell card.  I figured it would be proprietary HP and be a pain to get to work.  Well, I'm off to the other thread mentioned to see if I can get it to work.

EDIT:  I also ordered both the Official Ubuntu book and Ubuntu Unleashed.  Since I'm a total beginner, these should help a bit.

---

### Post by ukripper on 2007-08-16
For more themes try [www.gnome-look.org](www.gnome-look.org) (incase you don't know)

Helping each other is what open source is all about.:)

EDIT:
Good job done man, I can't wait for my Hacking Ubuntu to be delivered on monday.

---

### Post by leathco on 2007-08-16
> **ukripper said:**
> For more themes try [www.gnome-look.org](www.gnome-look.org) (incase you don't know)

Helping each other is what open source is all about.:)

EDIT:
Good job done man, I can't wait for my Hacking Ubuntu to be delivered on monday.



I can't wait til I get far enough along to dive into something like that.  Thanks for the tip on where to get more themes.  Switching to Linux has been a long time coming, but the final few straws during the week just pushed me over the edge and in an inpulse it was download, format, and install.  Much smoother than the last time I tinkered with it, I've already made much more progress with it than the last time I tried it.  Granted, last time I used Mandrake (Mandriva now, I think) and nothing wanted to work.  This time it's just a matter of ironing a few bugs out.

EDIT:
Wireless now works thanks to the guide posted earlier.  Not sure how it worked, but it got it working.  Many thanks.  Now I'm interested in knowing how that worked.

---

### Post by ukripper on 2007-08-16
Once you are committed you can iron out all bugs. Being optimistic you can achieve your goals I have seen people giving up and slagging off ubuntu as a whole in despair - I just feel sad for them that they don't even want to learn anything other than the  OS they being used to. New things always comes with complications but the person who  is committed only makes it to the shore.

You doing good job man keep it up!:)

---

### Post by leathco on 2007-08-16
It does seem odd how many come to try than give up.  I've done it a few times to be honest, but I'm not sure if it was me or if perhaps Linux wasn't ready yet, as I've never had a set up this smooth or fast before.  I'm really surprised at the speed, the entire OS just screams along, even when multitasking.  Gotta be the combo of Linux speed to begin with plus the addition of me now utilizing the 64 bit processor.

What really caught me off guard was all the people having trouble getting Flash working on 64 bit Ubuntu.  I expected a battle, but within a google search found a script that did the full Flash install.  

Honestly with the WiFi card running I'm extremely happy with this setup and ready to dig into the guts of how this works.  I'm kind of wondering even, since everything is smoking fast on this thing, if I used the guides to get Doom 3 and Quake 4 running if even those games would run decent on my not quite smoking 6150 videocard.

---

### Post by ukripper on 2007-08-16
Personally I havn't installed Quake 4 or doom3 on ubuntu yet but there are many games I play in ubuntu i don't feel the need to bother installing them.

There are few good games you can find on here for ubuntu -
[https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)

---

### Post by freebeer on 2007-08-16
> 

Currently I am working on building a nice software collection through the ***suppositories***

See? Even a newbie can teach me a new trick... I didn't know software could be installed that way!  :shock:  That's taking one for the team!  :D


(Sorry, I couldn't resist.)


Nice write-up though!  Welcome!

---

### Post by leathco on 2007-08-16
> **freebeer said:**
> See? Even a newbie can teach me a new trick... I didn't know software could be installed that way!  :shock:  That's taking one for the team!  :D


(Sorry, I couldn't resist.)


Nice write-up though!  Welcome!

lol, sorry, every time I try to type repositories, I gotta slow down cause the other one wants to be typed out instead.

Rectal install FTW!  :lolflag:

Erm....maybe not, that sounds painful.

---

### Post by freebeer on 2007-08-16
lol.  I know what you mean.  I suffer from that myself with different words.

But I got thinking about it a bit.. with all these artificial limbs, 'n hearts, etc. that people are getting, maybe it isn't too far of a stretch to imagine that suppositories would be used to upgrade the software on these things.  :D

---

### Post by leathco on 2007-08-16
> **freebeer said:**
> lol.  I know what you mean.  I suffer from that myself with different words.

But I got thinking about it a bit.. with all these artificial limbs, 'n hearts, etc. that people are getting, maybe it isn't too far of a stretch to imagine that suppositories would be used to upgrade the software on these things.  :D

I gotta wonder, would that be called Plug and Play?

Happily got another step made, Beryl running flawlessly, with the cube set up as a Borg cube with a space background when in cube mode.  Perhaps not original, but still sweet looking.  I also just said screw it and downloaded everything from the repositories that I could, install took a few hours but now I've got plenty of software to play with before I make the jump to the command line.

---

### Post by freebeer on 2007-08-16
> **leathco said:**
> I gotta wonder, would that be called Plug and Play?




USBum device?  :D

Nice job with the cube... I haven't tried it yet.  Maybe someday.

---

### Post by leathco on 2007-08-17
It's neat....only prob is I'm getting a glitch when loading Beryl that it won't draw borders around the windows.  Weird....

---

