---
title: "ubuntu on older hardware?"
date: 2004-12-26
forum: The Cafe
---

### Post by OrangeSlice on 2004-12-26
Might already be some topics on this, but I did a search and didn't find any.

I am trying to get my dad onto Ubuntu.  Currently he uses Windows 98 on a 333mhz AMD K-6 w/ 64mb of RAM and a 6gb hard disk.  I booted into the Live CD and it was pretty slow, but I'm wondering how well Ubuntu will run on this old machine if I install it.

Has anyone put Ubuntu on an older pc?
And how well did it perform?

Ubuntu's one of the fastest distro's I've used (out of the 4 I tried,) but on older, slower equipment, you never know how something's going to work out.

---

### Post by istoyanov on 2004-12-26
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

The above link may be useful to you;)

---

### Post by az on 2004-12-26
The desktop is a little sluggish (responsive to clicks) but you can get things done just as fast, if not faster in Ubuntu in comparison to win 98.
For example, web pages do not stall or take ages to display.  This was my wife's first reaction to mozilla1.1 some time ago.  Firefox is even faster than that, now.

300 MHz is probably the slowest computer I would expect Ubuntu to run fine on.  I would probably use a faster, fewer-featured desktop on a system that was any slower (like icewm and a basic filemanager like rox-filer. )

64 megs is pretty small.  Expect a big (really big) performance improvement by just adding 32 or 64 more megs of ram (five bucks on ebay...)  Unless you are running a lot of things at the same time (like seven or eight digital pictures in the gimp at one time) you will not need more ram than that.

Ubuntu is just as fast as debian.  If you want to play around with a leaner desktop, try debian...

---

### Post by OrangeSlice on 2004-12-26
Thanks for that guide.

As for using a lower-memory desktop (icewm), I'd rather not.  My pop doesn't know too much about computers and I'd rather have him using something easy like Gnome (perhaps KDE, but damn I hate it.)  I tried IceWM a bit back in my Mandrake days and it didn't seem very user-friendly (in fact it crashed a lot, but I blame Mandrake for that.)

And actually I just asked and there's 128mb of ram in this.  Also, Gnome (and Ubuntu) are things I know how to use, and can help him with.  
About Debian, I don't want to download *7* cd's :x

---

### Post by dare2dreamer on 2004-12-26
While I'd definitely recommend installing ubuntu on a desktop machine over stock debian, one point of order...you do not need to make a 7 cd set in order to install debian.

The multi-volume cd set covers all packages on all architectures. You can actually get by on a single net-install cd or floppy in most cases.

Have a look at this:

[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

For more information on installing without using the entire cd set.

---

### Post by az on 2004-12-26
"The multi-volume cd set covers all packages on all architectures"

Not mostly true.
1-  The current stable (Woody) on i386 has upwards of 8000 packages which take seven cds to contain.  For each architecture, there are six or seven cds.  Of course, you only need the first cd for a desktop system.  It is however, over two years old.  Most of the software is pretty dated.

2-  The next stable version (Sarge) which may be released soon will span 12 cds.  Again, that is for each architecture.

Debian is a general-purpose distribution, which is why you have so many packages and so much choice.  Ubuntu is mainly a desktop distribution;  fewer packages.

---

### Post by charleyramm on 2004-12-27
I have a pII 233 with 128mb of ram that is running better than i could possibly have imagined. The only downer is openoffice takes a long while to load (1minute or more)  Though it is smooth once it is loaded. But everything else seems fine so long as you understand its limitations. I imagine that if your dad has been using windows, he will have learned not to run a great many different programs at once.

 Previously I had debian and fluxbox on this machine, and i dont know why, (possibly all my network servers, apache, ftp, mysql etc) But it ran like shit. Firefox was hardly useable. Now it is running a full gnome desktop and firefox is smooth as a babies bottom.  I can only suppose that something was wrong with my debian install.

 Good luck. 

P.S. If it is 64mb I would seriously recommend an upgrade to 128, it is a massive improvement.

---

### Post by poofyhairguy on 2004-12-28
first of all, it helps to prelink the programs when you are done. 

Second of all, as others have said, ram is the main limit. I have an Ubuntu system running great on an old computer now, it just took me buying 256mb of ram!

---

### Post by az on 2004-12-28
Another two cents:  Dont use openoffice but install abiword instead.

---

### Post by jdodson on 2004-12-29
[QUOTE=istoyanov][http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

The above link may be useful to you;)[/QUOTE]

this is great, thanks for the link.

---

### Post by GNU/Hippie on 2004-12-29
[QUOTE=dare2dreamer]While I'd definitely recommend installing ubuntu on a desktop machine over stock debian, one point of order...you do not need to make a 7 cd set in order to install debian.

The multi-volume cd set covers all packages on all architectures. You can actually get by on a single net-install cd or floppy in most cases.

Have a look at this:

[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

For more information on installing without using the entire cd set.[/QUOTE]

You know, it's funny. I just got finished building a box with an ITX mobo, 200MHz Cyrix CPU, 64M and 20G HD. I came to the same solution you did. The Debian net install will give you a very minimal install (something I needed). I should say that there's no GUI software installed. Apache, php, samba, python and sshd. With that it runs at an acceptable speed. Power and ethernet are the only cables plugged in.

The only other distro I could recommend is [http://damnsmalllinux.org](http://damnsmalllinux.org). Very, very small and ran much fast than Ubuntu. Not that it's nearly as nice but with slow CPU and little HD space it's a good choice.

I did try Ubuntu and for me it was too slow. Ubuntu runs nicely on a PIII 866 though and since it's a modern distro I couldn't expect it to run great on 200MHz CPU.

Hey dare2dreamer, if you had posted this suggestion a week ago you would've saved me a lot of hassle. =)

---

### Post by Ozitraveller on 2004-12-29
[QUOTE=istoyanov][http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

The above link may be useful to you;)[/QUOTE]

Thanks for the great link, I saw a similar Debian one the other day on OSNews which I tried.

---

### Post by OrangeSlice on 2005-01-01
Happy new year everyone!

That Debian net install is looking nice.  I might have to go with that, although I've already got my Ubuntu cd's here.  The main thing I'm worried about is my pops using IE.  I put Firefox on here but he won't use it.  Spy/adware is an issue, and I usually have to run Spybot when I visit (which isn't often.)  He's old, and doesn't want to learn anything new.  So he says, heh.  I let him play with the LiveCD a bit, and he liked it.  Won't let me do an install though.  My powers of persuation simply aren't working.  geh.  Look at me I made my own thread to whine about stuff in.

---

### Post by Ste on 2005-01-01
[QUOTE=OrangeSlice]Happy new year everyone!

That Debian net install is looking nice.  I might have to go with that, although I've already got my Ubuntu cd's here.  The main thing I'm worried about is my pops using IE.  I put Firefox on here but he won't use it.  Spy/adware is an issue, and I usually have to run Spybot when I visit (which isn't often.)  He's old, and doesn't want to learn anything new.  So he says, heh.  I let him play with the LiveCD a bit, and he liked it.  Won't let me do an install though.  My powers of persuation simply aren't working.  geh.  Look at me I made my own thread to whine about stuff in.[/QUOTE]
 There are plugins for firefox to make it look like IE.
;)

---

### Post by Ozitraveller on 2005-01-01
Did you see this other thread as well?

[COLOR=Red]Ubuntu Mini-RAM HOWTO[/COLOR]

[http://ubuntuforums.org/showthread.php?t=8338](http://ubuntuforums.org/showthread.php?t=8338)

---

### Post by Ozitraveller on 2005-01-01
[QUOTE=azz]Another two cents:  Dont use openoffice but install abiword instead.[/QUOTE]

I read a little article in the last couple of days that suggested abiword was a bit buggy? What about Ted-gtk or aee?

---

### Post by dare2dreamer on 2005-01-02
Hippie, funny thing is we think alot alike on both counts. I've used damnsmalllinux a number of times to bring old hardware up for general use. Once it's hard drive installed, you can do a lot to forcibly bring it a bit more up to date. :-)

As for the "no desktop" minimal install thing, you can always apt-get whatever you need AFTER the minimal net install completes. In point of fact, I've used this trick to get Ubuntu installs up on non-booting laptops...we tossed the hard drive into another laptop, did a minimal expert install of Ubuntu, then tossed it into the right machine and did an apt-get on the ubuntu-desktop metapackage.  Worked like a champ.

For the record, current "best of the worst" Ubuntu install is running remarkably snappily on a pII 233 with 128 MB ram. 

To the people who mentioned older machines running better with Ubuntu vs. Stock Debian stripped down...yup, I've seen it too. Best guess is less cruft in the way of server packages running, but I'm just guessing there. I'm pretty much split between Ubuntu and Damnsmall on older machines, depending on which feels better on the hardware in question.

Oh, and sorry about my 'tardy post', but the holidays have been hell on my free time to be a technical wiz. :-)





[QUOTE=GNU/Hippie]You know, it's funny. I just got finished building a box with an ITX mobo, 200MHz Cyrix CPU, 64M and 20G HD. I came to the same solution you did. The Debian net install will give you a very minimal install (something I needed). I should say that there's no GUI software installed. Apache, php, samba, python and sshd. With that it runs at an acceptable speed. Power and ethernet are the only cables plugged in.

The only other distro I could recommend is [http://damnsmalllinux.org](http://damnsmalllinux.org). Very, very small and ran much fast than Ubuntu. Not that it's nearly as nice but with slow CPU and little HD space it's a good choice.

I did try Ubuntu and for me it was too slow. Ubuntu runs nicely on a PIII 866 though and since it's a modern distro I couldn't expect it to run great on 200MHz CPU.

Hey dare2dreamer, if you had posted this suggestion a week ago you would've saved me a lot of hassle. =)[/QUOTE]

---

### Post by az on 2005-01-02
"I read a little article in the last couple of days that suggested abiword was a bit buggy"

I use abiword.  It is not buggy,

---

### Post by Ozitraveller on 2005-01-02
[QUOTE=azz]"I read a little article in the last couple of days that suggested abiword was a bit buggy"

I use abiword.  It is not buggy,[/QUOTE]

Excellent! I was hoping you'd say that.. Thanks!

---

