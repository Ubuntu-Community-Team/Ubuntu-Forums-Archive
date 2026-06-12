---
title: "13 Things Do After Installing Ubuntu"
date: 2009-02-07
forum: The Cafe
---

### Post by izizzle on 2009-02-07
[http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

Great start for new Ubuntu users. Sticky it if you must :D

---

### Post by mb_webguy on 2009-02-07
I agree with that list up to #2.  :)

At this point, bittorrent has completely eclipsed the other P2P networks.  It's nearly impossible to find anything but porn on the other P2P networks.  (Of course, if that's what you're looking for... *shrug*)

I would roll #4 (installing Adobe Reader) into #2, along with all of the other niceties found in Medibuntu.

#5 could be more easily done by simply installing the ubuntu-restricted-extras package, and you get a lot more besides.

Scribus is nice, but useless unless you need desktop publishing software, which most people don't.  It has no place on a generic list of things you need to do after installing Ubuntu.

Downloader for X is also nice, but only one of many such solutions for download management.  Since Firefox is the default web browser, it would make more sense to me to recommend DownThemAll, since most downloads that would be handled by Downloader for X would be initiated through the web browser.  And there are plenty of other equally valid recommendations for a download manager.

I can't believe that Google Desktop is even being suggested.  Ubuntu has other native apps (one of which is installed by default in Ubuntu!) that provide similar functionality, and Google Desktop is a resource hog.

The recommendation of Picasa is even more confusing, especially since the author suggests running it under Wine, but then provides a link to a deb and never mentions how you'd go about installing Wine.

Google Earth is a nifty application, and I can sort of see why it might possibly be on such a list, but again, I'd fold this into the Medibuntu section.

Not everyone wants to clutter their desktop with widgets.  But I'll go along with the inclusion of gDesklets on the list, for those people moving from Vista or Mac OS X who expect the functionality.

And that brings us to #13, Realplayer.  First of all, I hate Realplayer with a passion, and don't think it's really necessary at this point as real media files are becoming increasingly rare.  But that aside, this is yet another suggestion that could be included in the "stuff to get from Medibuntu" section.  Half of this list is from the Medibuntu repos, and several can be installed with the same metapackage.

--------------------

I think several things *should* have been mentioned in such a list which weren't in this one.

First, the recommendation of turning on the advanced desktop effects is pointless without first addressing the issue of installing proprietary video drivers.  An "Install proprietary drivers" section, mentioning Hardware Drivers and possibly [EnvyNG]("http://albertomilone.com/nvidia_scripts1.html") would be nice.

Second, considering the number of people who end up having to do this, I'd add something about [installing Windows wireless drivers]("http://kimbriggs.com/computers/computer-notes/linux-notes/ubuntu-linux-wi-fi-card.file") with ndisgtk, and provide a link to the [ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847").

While Scribus isn't something that most people need, OpenOffice is.  And while OpenOffice comes preinstalled with Ubuntu, I'd add a section about [upgrading to OpenOffice 3]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml") using the [openoffice-pkgs PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa").

I'd include a section about [modifying the GRUB menu]("http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/"), including setting or removing the timeout, adding a GRUB password, and removing old kernel entries.

I'd also mention [how to install Wine]("http://www.winehq.org/download/deb") to run Windows applications.

I'd certainly point them to some lists of Linux games (like [this one]("http://www.linuxlinks.com/article/20080510052539217/Games.html"), [this one]("http://www.linuxlinks.com/article/20080522164112313/Games-Part2.html"), and [this one]("http://www.linuxlinks.com/article/20080530054213402/CommercialGames.html")).

For people who dual-boot or otherwise have unmounted partitions they don't want to see on their desktop or in the Places menu, I might mention [how to hide unmounted partitions]("http://ubuntuforums.org/showthread.php?t=1060256").  Then again, since this would be a general list of things most people might want to do after installing Ubuntu, I might not.

But that would be the sort of list I'd make, if I were to write one.

---

### Post by TheLions on 2009-02-07
#8 Google Desktop

no, don't install that!

Why?
Because your Ubuntu would crawl!
I just removed Google desktop and all hdd seeking times where bisected
Also indexing takes a long long time (~90 idle hours)

---

### Post by hikaricore on 2009-02-07
I agree the realplayer step is a moot point.

If you properly install all extra video codecs you won't need realplayer for anything.

---

### Post by dcstar on 2009-02-07
> **izizzle said:**
> [http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)
........

Don't things written 2 years ago really date in something that evolves every six months.......    :(

People really have to discount anything like this by the examining the time it was created. Things that may have had a lot of relevance when initially created can do more harm than good when used by people who don't understand the changes that have occurred since that time.

Sometimes I think that half the issues posted in these forums are because people have hacked their systems with now inappropriate instructions that they have found somewhere on the 'net........

---

### Post by izizzle on 2009-02-07
**+1 DCStar**. Actually, I just came back to linux after a while, and back then, this was a great writeup!

Times have changed....so true...

---

### Post by -kg- on 2009-02-07
> **dcstar said:**
> Don't things written 2 years ago really date in something that evolves every six months.......    :(

People really have to discount anything like this by the examining the time it was created. Things that may have had a lot of relevance when initially created can do more harm than good when used by people who don't understand the changes that have occurred since that time.

Sometimes I think that half the issues posted in these forums are because people have hacked their systems with now inappropriate instructions that they have found somewhere on the 'net........

Yes, yes, and YES!!  I don't know how many times I've come across some information on the net that doesn't sound quite right, and when I find out when it was written, it was mega-years ago (of course, I'm exaggerating with the "mega," but you get my point).

It's unfortunate that some don't keep up with their postings such as this, because it can indeed cause big problems when some follow advice that is currently erroneous, or conflicts with something that was already fixed with which it is incompatible.

+1 on "dated information?"  More like +10

---

### Post by Mason Whitaker on 2009-02-07
Wonderful guide! :P

---

### Post by Therion on 2009-02-07
The article being two years old, aside, I have trouble putting to much faith in any author who doesn't know the difference between "decent" and "descent".  Not a typo, it's repeated throughout the article.

---

### Post by bgs100 on 2009-02-07
Replace 3 and 5 with install ubuntu-restricted-extras

Remove the part of 3 about dc++ and amule (why are they both 3 anyway?)

Remove 4.  It was always slow on Windows, for me.  And the only thing better in it for me is using the mouse to go up and down instead of scrolling.

Take away 8 and get the nice catfish program. Faster and you can choose backend (find, locate, slocate, and beagle (if you have beagle installed))

Take away 9.  Just use F-Spot, gosh. Or better yet, just browse through your pictures directory, really.

Take away 10.  It's slow, and why is it needed anyway?

11 is okay, but if you just want a cool system monitor, use gkrellm.

Make 12 a section with more than just one music player. Not everyone likes quod libet (although everyone does love ex falso)

Obliterate 13. Who needs it, seriously?

Add a thing about gnome-do. It rocks

Add a thing about tilda/yauake.  They rock (only tried tilda. Heard they're just like each other.)

Add a thing about SMplayer. It rocks.  Hey, SMplayer could replace the realplayer section!

Add a thing about Ubuntu Tweak. Totally something to install

Possibly add things about XChat and prism-google-mail

Add a thing about firestarter.  It lets you see if you're being "hit" as a friend of mine calls it.

Add a thing about inkscape.

You know, I think I'll make my own post for 8.10

---

### Post by 73ckn797 on 2009-02-07
#1 New users need to be directed to the community documentation. Many questions could be answered there.

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

There are many other very useful, first step, resources available besides what I mention.

#2 Read the Sticky Threads.

---

### Post by bgs100 on 2009-02-08
My new and improved (IMHO) version!

[http://randombuntu.blogspot.com/2009/02/few-things-to-do-immediatley-after.html](http://randombuntu.blogspot.com/2009/02/few-things-to-do-immediatley-after.html)

---

### Post by izizzle on 2009-02-08
Great writeup bgs100! Perfect for the Ubuntu Multimedia-ist! :guitar:

---

### Post by bgs100 on 2009-02-08
> **izizzle said:**
> Great writeup bgs100! Perfect for the Ubuntu Multimedia-ist! :guitar:

Thanks. :)
By the way, I am updating this, so there may be new items added since you viewed it.  Did you see the part about gkrellm?
Another BTW, My very favorite things I have there are:
Banshee
SMPlayer
ubuntu-restricted-extras
Exfalso
Catfish
Gnome Do!!!

---

### Post by bgs100 on 2009-02-08
Just added GCStar to list. Love it.

BTW, Please post/comment-on-blog any suggestions you have for it. :)

---

### Post by izizzle on 2009-02-09
> **bgs100 said:**
> Thanks. :)
By the way, I am updating this, so there may be new items added since you viewed it.  Did you see the part about gkrellm?


Yes! I did see the part about GKRellm. Seems like a worthy competitor for conky. Gonna try it out one I reinstall my system. :P

---

### Post by bgs100 on 2009-02-09
Thnks. When I try to use conky, It comes up in an ugly window and not my desktop

---

### Post by bgs100 on 2009-02-09
> **izizzle said:**
> Yes! I did see the part about GKRellm. Seems like a worthy competitor for conky. Gonna try it out one I reinstall my system. :P

BTW, You might want to go to gkrellm website and get skins. Jut google gkrellm

---

### Post by unplugged23 on 2009-02-09
Not bad but i feel it was rather incomplete. I think it should mention wine or something of the like, learning shell scripting, obviously getting involved in the forums, and maybe a guide to removing you windows partition lol.

---

### Post by Faolan84 on 2009-02-09
that guide is like the worst ever. RealPlayer? Gdesklets?? Quod Libet?! d4x?! These programs are in a word, awful.

My Recommendations:
ADD
+ GQView
+ Mozilla Thunderbird
+ Qalculate! GTK+
+ Tilda
+ Start-up Manager
+ Inkscape
+ Easytag
+ OGM Rip
+ Inkscape
+ Google Earth

REMOVE
- Gcalculator
- that default photo and image viewer
- mono (unless you want tomboy)
- ekiga (never use it anyways)
- a couple other programs i can't think of right now

---

### Post by adamlau on 2009-02-10
I completely disagree with all points except for the first. The guide is outdated and is not recommended for even the n00biest of n00bs. Why would I install aMule and not MLDonkey? Downloader for X over aria2? No way. Picasa? No, no, let the end user decide what is to be installed.

---

### Post by RiceMonster on 2009-02-10
eck, install RealPlayer? No thanks. I don't want to install DC++ either, I hate that thing. Actually, I don't see why most of those applications are listed there at all. The codecs, repositories and flash support are fine though.

---

### Post by cb951303 on 2009-02-10
naah... 2, 3, 4, 6, 8, 9, 10, 11 and 13 are useless for me

---

### Post by cb951303 on 2009-02-10
> **Faolan Devyn Aodfin said:**
> that guide is like the worst ever. RealPlayer? Gdesklets?? Quod Libet?! d4x?! These programs are in a word, awful.


I agree, except Quod Libet. One of the best jukebox software out there.

---

### Post by Faolan84 on 2009-02-10
I don't understand why you would want a download manager if you were using Firefox 3. It comes with one, and if it doesn't have the features you need try the "Download Them All" extension or any one of the other download enhancer extensions.

Or you could just use wget...

---

### Post by bgs100 on 2009-02-10
> **unplugged23 said:**
> Not bad but i feel it was rather incomplete. I think it should mention wine or something of the like, learning shell scripting, obviously getting involved in the forums, and maybe a guide to removing you windows partition lol.

Mine? (Lol I did all of those you mentioned on my own).  I might add wine.  This is partially of for n00bs, who possibly just want a cool desktop and not necessarily learn shell scripting (although is great skill). I might divide guide into two sections, one for normal n00bs and the other for *real* linux users. :)

---

### Post by wolfen69 on 2009-02-10
i disagree starting with #1. I always do system updates before i touch anything. doing *any* configuring *then* doing updates can lead to problems. so far, my approach has worked for me and my friends and customers.

---

### Post by bgs100 on 2009-02-10
BTW, 
Steps 3.5 (VLC), The second number 3 (DC++ aMule, why are they both 3 anyway?), 4 (Acrobat), 7 (Downloader for X), 8 (Google Desktop, Just get catfish), 9+10 (Google stuff no one needs, especially for ubuntu), 11 (gdesklets), 13 (Realplayer) = bleh

---

### Post by Faolan84 on 2009-02-10
First thing I do when installing Ubuntu: remove Compiz and the like. Compiz really brings very little to the party: wobbly windows, and some snazzy effects but it's a waste of resources -- especially for anyone running a computer with more than four years on it.

Metacity really isn't all that bad, and in a few releases I wouldn't be surprised if it will contain compositing effects too like Xfwm does now, and it will be way more efficient than Compiz. Ubuntu doesn't need Compiz, and it should not even be provided in the default install because it does present problems when it breaks or meets with an incompatible system.

---

