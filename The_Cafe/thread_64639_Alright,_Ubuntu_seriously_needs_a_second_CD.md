---
title: "Alright, Ubuntu seriously needs a second CD"
date: 2005-09-11
forum: The Cafe
---

### Post by jdong on 2005-09-11
When I switched back to Breezy a few weeks ago, I completely forgot about its lack of drivers for my Wireless card (not Ubuntu's fault -- the drivers aren't super-stable yet).

However, Breezy didn't have a compiler or kernel headers installed, which further complicated the issue. Few distros use GCC 4.0, so cross-compiling from another machine was virtually an impossibility, too.

Fortunately, I solved this problem by booting back into my old distro (on another hard drive), chrooting into the new Ubuntu install and getting on the network via the old distro's drivers.



Recently, a friend had the same issue with his system. However, this time it was a bit more complicated. He didn't have another OS on the system, and didn't have a copy of the drivers on hand. Eventually, it meant trips back and forth to a neighbor's house, while on the phone with me for 3+ hours trying to get compilers and headers installed via packages.ubuntu.com.


Now, I understand the convenience of Ubuntu being on a single CD. However, that seriously sacrifices convenience when Ubuntu doesn't include support for some drivers...


I'd like to see Ubuntu produce a "supplemental CD" that one can add via Synaptic/update-manager's "Add CD..." tool (sources.list) that contains compilers, kernel headers, and kernel sources, and maybe some other commonly used development libs. That way, those who need them have them, and those who don't want them don't have to deal with the extra download.

---

### Post by benplaut on 2005-09-11
i heartily agree!!!

it would have to be optional, however... the install will complete fine without it, but it adds some other stuff

why just dev stuff? put KDE and XFCE in there, too... stop alot of griping  :wink: 

might be cool to have an option in the initial install whether or not you want gnome or kde, and ask for the extras CD is they choose KDE  :)

---

### Post by Knome_fan on 2005-09-11
/me agrees.

And while we are at it, put some other apps on it too. That way Ubuntu will be much more viable for people who don't have broadband.

---

### Post by xequence on 2005-09-11
Whatever happens, id be really mad if you needed two CDs for an install. I think there is already an extras CD...

I just dont want ubuntu to go over one CD... Debian and fedora are both 4 CDs, which I dont particulary like :/


> And while we are at it, put some other apps on it too. That way Ubuntu will be much more viable for people who don't have broadband. 

Broadband is needed to download the one CD in a decent ammount of time... The only way a second CD would help is if the person used shipit.

---

### Post by jdong on 2005-09-11
Yeah, sure, fill it up with extra packages, too!

I'd be perfectly optional -- in fact, the installer wouldn't ask for it at all. After install, you can use any of the three installed package managers to add the CD (see screenshot). Also, when you insert it, Ubuntu'd come up with the "Detected Software CD, add Packages?" dialog like it does with Ubuntu setup CD's.

---

### Post by Knome_fan on 2005-09-11
[QUOTE=xequence]
Broadband is needed to download the one CD in a decent ammount of time... The only way a second CD would help is if the person used shipit.[/QUOTE]
1. Download the CDs at a friend, at an internet caffee, etc.
2. Use shipit.
3. Use one of the many online shops that sell Linux isos cheaply.

So, no, you don't need broadband.

---

### Post by jdong on 2005-09-11
[QUOTE=Knome_fan]1. Download the CDs at a friend, at an internet caffee, etc.
2. Use shipit.
3. Use one of the many online shops that sell Linux isos cheaply.

So, no, you don't need broadband.[/QUOTE]

4) have a friend download and give you the CD, so you **DONT WASTE HIS ENTIRE SATURDAY ON THE PHONE RESOLVING DEB DEPENDENCIES WHEN APT SHOULD BE DOING IT!!!!!!** ;)

---

### Post by Knome_fan on 2005-09-11
[QUOTE=jdong]4) have a friend download and give you the CD, so you **DONT WASTE HIS ENTIRE SATURDAY ON THE PHONE RESOLVING DEB DEPENDENCIES WHEN APT SHOULD BE DOING IT!!!!!!** ;)[/QUOTE]

LOL, exactly! :grin:

---

### Post by poofyhairguy on 2005-09-11
Does the DVD have this stuff? Could Ubuntu just split the dvd?

---

### Post by xequence on 2005-09-11
[QUOTE=Knome_fan]1. Download the CDs at a friend, at an internet caffee, etc.
2. Use shipit.
3. Use one of the many online shops that sell Linux isos cheaply.

So, no, you don't need broadband.[/QUOTE]

1. I for one find it a little odd to walk into a friends house...
"Can I download a 600 MB File on your computer?"
"Sure!"
2. I said unless they use shipit...
3. What if you dont have a credit card? Or no other means to pay over the internet?


Anyway, as long as its not NEEDED to install im happy :)

I only have two burnable CDs left. One with 5.04 installer and one is blank, im gonna burn windows 98 to it as soon as I find out how to burn .img files. K3B doesent work with them =O

---

### Post by jdong on 2005-09-11
[QUOTE=poofyhairguy]Does the DVD have this stuff? Could Ubuntu just split the dvd?[/QUOTE]

I think the DVD does.... and splitting the DVD would be just as easy as making the new CD image, since I think it's all built automatically, given a package list file.

---

### Post by xequence on 2005-09-11
[QUOTE=poofyhairguy]Does the DVD have this stuff? Could Ubuntu just split the dvd?[/QUOTE]


I think the DVD is all versions of ubuntu... x86, powerpc, amd64.

edit: Nope, its a livecd and installer in one...

"The combined install/live DVD allows you either to install Ubuntu permanently on a computer, or (by entering 'live' at the boot prompt) to try Ubuntu without changing your computer at all. There are three images available, each for a different type of computer:"

---

### Post by Kvark on 2005-09-11
It'd really be a shame if Ubuntu started taking up more then 1 CD. If there isn't enough room for all the drivers or something else that is important out of the box for some people then ditch the small games, duplicate tools for the same thing and other less important things to make room.

But a series of extra CDs containing everything in the official repos would be very nice. Specially if things where sorted so related sections end up on the same CD. For example "Python Programming Language" plus the other geek sections on one and "Word Proccessing" plus the other office related sections on another.

---

### Post by Quest-Master on 2005-09-11
What more to say.. this is an EXCELLENT idea.

---

### Post by TravisNewman on 2005-09-11
isn't build-essential already on the disk? It was in hoary (which came in handy for me once or twice), and I certainly hope they didn't scrap it in Breezy.

---

### Post by az on 2005-09-11
[QUOTE=panickedthumb]isn't build-essential already on the disk? It was in hoary (which came in handy for me once or twice), and I certainly hope they didn't scrap it in Breezy.[/QUOTE]

I think the daily build cd images do not have syncing linux-headers packages, nor do all drivers compile with gcc 4.

There is a popularity-contest package that the MOTU could make use of.  I think this is the kind (an extra cd) of thing the MOTU must do,

Run popularity-contest and find out what packages from universe people want the most.  Then build and distribute the cd.

---

### Post by jdong on 2005-09-11
[QUOTE=azz]I think the daily build cd images do not have syncing linux-headers packages, nor do all drivers compile with gcc 4.
[/QUOTE]

Build-essential is certainly not on the Preview CD (or I wouldn't be bitching right now), linux-headers isn't on there either. GCC 3.4 doesn't stand a chance of being on there, and that's the ONLY GCC that'd compile kernel modules (the magic is wrong if you use another version)

---

### Post by macgyver2 on 2005-09-11
Yup, I really like this idea.  I ran into a similar problem last week: needed to compile some modem drivers...and couldn't find a compiler.  I was also an hour from any place I knew of to download the packages.

---

### Post by MetalMusicAddict on 2005-09-11
The DVD isnt a option for you jdong? It has everything in the Universe repos right?

---

### Post by TravisNewman on 2005-09-11
[QUOTE=MetalMusicAddict]The DVD isnt a option for you jdong? It has everything in the Universe repos right?[/QUOTE]
 it has everything in main

---

### Post by jdong on 2005-09-11
[QUOTE=MetalMusicAddict]The DVD isnt a option for you jdong? It has everything in the Universe repos right?[/QUOTE]

No; as unfortunate as it may be, not every system has a DVD drive, and not all systems in my house with a wired network connection suitable for downloading DVD ISO's have DVD burners ;)

---

### Post by xmastree on 2005-09-11
[QUOTE=xequence]1. I for one find it a little odd to walk into a friends house...
"Can I download a 600 MB File on your computer?"[/quote]If someone asked me, I'd gladly do it. Not right there ahd then, it takes time here, but I'd download it and give them a call when it was finished.
> 2. I said unless they use shipit...
3. What if you dont have a credit card? Or no other means to pay over the internet?Shipit is free. No credit card required.

---

### Post by TravisNewman on 2005-09-12
[QUOTE=xmastree]If someone asked me, I'd gladly do it. Not right there ahd then, it takes time here, but I'd download it and give them a call when it was finished.
Shipit is free. No credit card required.[/QUOTE]
 the proposed idea of the extra cd in shipit is NOT free, however.

---

### Post by benplaut on 2005-09-12
yeah... it'd be safe to say that most Ubuntu users don't have DVD burners  ;-)

---

### Post by weasel fierce on 2005-09-12
I think it'd be a great idea to offer an extra CD with optional stuff and app's, as long as its stuff you dont need to use Ubuntu

---

### Post by felixdzerzhinsky on 2005-09-12
> I dont like linux distros that have multi CD installers. Like Fedora. Are 4 CDs really nessecary for an OS? Even windows has only one. 

Windows is just gives you the OS on one CD. Linux gives you Office Suites, Photoshop equivalents, etc.

I too think there should be an "optional" cd and the choice of desktop environment. By all means default to gnome but give a choice. Keep it possible to install from one cd but have the options open.

Also you should have AIDE as an integrity checker and Bastille installed for hardening BEFORE you connect to the Internet.

---

### Post by ScoobyDan on 2005-09-12
[QUOTE=xequence]im gonna burn windows 98 to it as soon as I find out how to burn .img files. K3B doesent work with them[/QUOTE]

If you rename the ".img" file to ".iso", you can then right-click and select "Burn to disc". I do this all the time (running Hoary and Gnome)

Daniel

---

### Post by Richard Rowlands on 2005-09-12
I disagree, one of the things I don't like about other Linux distributions is the bloat.  To have such a great Linux distribution come on a single CD is perfect for me.  I like a system to be lean and mean.  Why would I want 25 different text editors?  To have an "extras" CD would be fine so long as it wasn't required.  Any movement away from a single installation CD and Ubuntu might lose the niche it has carved for itself among the multitude of multiple CD Linux distibutions out there.

Just my opinion, feel free to disagree.  Regards, Richard.

---

### Post by Havoc on 2005-09-12
Yes, of course they should keep the 1 CD approach, but, WE NEED A SECOND CD!.
Seriously though, the first thing I do after I fresh install Ubuntu Hoary, is install the Unofficial Add-On CD...

What you need to make, is a CD that updates your base system, and has common development libraries (Like xorg-dev) and normal applications & libraries.

We don't really need bloated CDs, with more applications one needs for one given task.But there are some exceptions to that rule.For instance, I like having Abiword on my system (To simply edit my .doc files, without the unneeded bloat of a fully featured Word Proccesor), even though I've got OpenOffice.So, wise choices have to made.

Heh, I'm ranting... :roll:

---

### Post by Vidar on 2005-09-12
[QUOTE=xequence]1. I for one find it a little odd to walk into a friends house...
"Can I download a 600 MB File on your computer?"
"Sure!"[/QUOTE]

Heh, that would hardly take five minutes including downloading and burning the cd, so sure - If a friend asked me I would do it as soon as I had the time to spare (actually, I already have on several occasions). :D

---

### Post by xaque on 2005-09-12
[QUOTE=xequence]1. I for one find it a little odd to walk into a friends house...
"Can I download a 600 MB File on your computer?"
"Sure!"[/QUOTE]

Yep, you need to find some geekier friends... Mine wouldn't bat an eyelid if I asked them that question, in fact, I regularly use their broadband connections to download 4 GB DVD images.

---

### Post by macgyver2 on 2005-09-12
Actually, take a look at the [cd image sizes for Breezy Preview]("http://releases.ubuntu.com/5.10/").  There's quite a bit of room for more on the CD...definitely enough for the build-essential packages.  Might be worth talking to the developers and pointing out that in the future it would be valuable to have build-essential available on the CD...not installed by default, of course...just available if necessary.

Even before then, though, you can just make your own slightly modified CD and add what you need after you burn the normal iso.

---

