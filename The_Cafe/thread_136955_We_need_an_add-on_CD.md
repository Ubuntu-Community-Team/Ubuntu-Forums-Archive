---
title: "We need an add-on CD"
date: 2006-02-27
forum: The Cafe
---

### Post by aysiu on 2006-02-27
It breaks my heart when people post on here that they don't have internet access on their Ubuntu computers, but they want Xubuntu or some other random thing. They have a computer with low specs and no internet connection, but they can download something from another computer... but what do they download? They can't just start downloading .deb files and then hope to resolve dependencies somehow.

I know there used to be an add-on CD for Hoary (5.04).

Using the instructions from [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto), I've created a 432 MB .ISO for an add-on CD, but...

1. I would need someone (or several mirrors) to host it. My little website has nowhere near the bandwidth sufficient to handle multiple downloads of a CD image.

2. My add-on CD is rather random--it just has a few things I added on to my installation. XFCE stuff is there, so are some random other things like MPlayer and whatnot. I'd rather people have my CD than *no* CD, but ideally there should be some kind of consensus on what the "essential" stuff for dial-up or no-connection users would be to have on a second CD.

3. Even though the HowTo was generally easy to follow, that public key stuff just seemed like too much trouble to me. I tested out the CD on my test computer using Synaptic to add it, and I could install stuff--it was just marked as "not authenticated." While someone who's desperate for packages may not care, eventually it'd be nice to have something that's authenticated, even if not "official."

The .ISO is sitting on my desktop. Let me know if you're willing to host it, and I'll tell you a temporary location you can download it from.

**Edit**: Actually, I'm an idiot. My webspace can't accommodate even 432 MB for a temporarily uploaded .ISO. I don't know how I'd get it to people. Hm. This is annoying.

[b]There is now a Wiki for this project:
[https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD](https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD)[/b]

A preliminary version of an addon CD is available here:
[http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/)

---

### Post by Jucato on 2006-02-27
Yeah, I concur. But I do hope that these just remain "add-ons". I don't want Ubuntu to lose its image of being a 1-CD installer (and soon to be 1-Live CD-installer).

It would be good if there would also be a sort of community project to make these add-on CDs for these packages:
1. kubuntu-desktop (includes, if possible, the kde metapackage)
2. ubuntu-desktop (for those who have downloaded the kubuntu installer)
3. xubuntu-desktop
4. multimedia packages (without w32codec, for legal issues)
5. gcc and build-essential packages (or anything else that is needed to compile and make from source code)

Something like these so that people can pick the ISO that they need. I wish I only knew how, or had the resources to host them.

Aysiu, btw, how about distributing it through torrent?
(OT: I see you've updated our ubuntu user guide. nice! but your other links in your sig are gone... :( )

---

### Post by K.Mandla on 2006-02-27
A thought, or rather, a link to a similar thought ...

I think the Automatix CD gang found someone to host their CD. If you PM one of them, they might be able to help.

[http://ubuntuforums.org/showthread.php?t=87382](http://ubuntuforums.org/showthread.php?t=87382)

So is your CD different from the downloadable DVD? I've seen threads where people built Xubuntu-desktop installations onto a CD, for use on older machines without Internet connections.

---

### Post by aysiu on 2006-02-27
[QUOTE=Fenyx]Yeah, I concur. But I do hope that these just remain "add-ons". I don't want Ubuntu to lose its image of being a 1-CD installer (and soon to be 1-Live CD-installer).[/quote] No, you're absolutely right. When I first started, this is what initially turned me off Debian. I saw that there were 14 CDs, and I thought I needed all of them for an ordinary install.

> 
It would be good if there would also be a sort of community project to make these add-on CDs for these packages:
1. kubuntu-desktop (includes, if possible, the kde metapackage) Well, I think the regular Kubuntu .ISO would work for this.

> 
2. ubuntu-desktop (for those who have downloaded the kubuntu installer) Likewise, I think the regular Ubuntu .ISO would work for this.

> 
3. xubuntu-desktop Yes, definitely! Especially since those computers with no internet connection are also likely to be older machines with modest specifications.

> 
4. multimedia packages (without w32codec, for legal issues)
5. gcc and build-essential packages (or anything else that is needed to compile and make from source code) Yes, and yes.

> 
Aysiu, btw, how about distributing it through torrent? I don't really have a lot of experience with BitTorrent. How would that work exactly? Would it just remain on my desktop for the most part...?

> 
(OT: I see you've updated our ubuntu user guide. nice! but your other links in your sig are gone... :( ) Well, I just wanted to switch things up a bit. The links still exist... just not in my sig.

---

### Post by aysiu on 2006-02-27
[QUOTE=K.Mandla]
So is your CD different from the downloadable DVD?[/quote] I don't know, to be honest, as I don't have a DVD burner. And it would take me forever to download the DVD .ISO.

> I've seen threads where people built Xubuntu-desktop installations onto a CD, for use on older machines without Internet connections. Can you point some out for me? Post a few links? Maybe my idea's redundant.

---

### Post by aysiu on 2006-02-27
Okay. I'm looking in Synaptic, and I see bittorrent and bittornado.

Which would you recommend?

---

### Post by Jucato on 2006-02-27
the reason why I suggested separate kubuntu-desktop/ubuntu-desktop add-on CDs was that the official ISO are full installers. To use them, you would have to install it over (and probably mess up)  your existing system. But if I understand your goal correctly, that add-on CD you would be distributing is an offline repository in a CD. This would be useful for those who would like to test kubuntu/ubuntu/xubuntu without going through installation. (Am I sounding a bit confusing? :D)

---

### Post by aysiu on 2006-02-27
[QUOTE=Fenyx]To use them, you would have to install it over (and probably mess up)  your existing system.[/QUOTE] The regular installation CDs can be added as offline repositories in Synaptic as well. You don't have to install it over your existing system.

---

### Post by Jucato on 2006-02-27
Oh yeah, I overlooked that. But how about the kde/kde-core packages? Kubuntu doesn't install these by default, since it mixes up it's own KDE flavor. I'm presuming the same goes for GNOME and Ubuntu?

About the torrent stuff, I'm sorry I can't be of much help. I'm not really a torrent expert. But I think you have to make a .torrent file for your ISO. Then there are some "tracker" stuff that I don't know of. The only advantage of having that ISO in a torrent is that after uploading/seeding it for a few days, other people can take the burden off you by seeding. Of course, the disadvantage is that you would have to seed it yourself for some time.

---

### Post by Sutekh on 2006-02-27
[QUOTE=aysiu]
It breaks my heart when people post on here that they don't have internet access on their Ubuntu computers, but they want Xubuntu or some other random thing. They have a computer with low specs and no internet connection, but they can download something from another computer... but what do they download? They can't just start downloading .deb files and then hope to resolve dependencies somehow.[/QUOTE]
I think this is a good idea.  One of the more common problems I see is getting wireless internet adaptors working.  Maybe a collection of common ones?  But there are so many...

[QUOTE=aysiu]
[QUOTE=Fenyx]
3. xubuntu-desktop[/QUOTE]
Yes, definitely! Especially since those computers with no internet connection are also likely to be older machines with modest specifications.
[/QUOTE]
I second this.

[QUOTE=Fenyx]
5. gcc and build-essential packages (or anything else that is needed to compile and make from source code)[/QUOTE]
These are on the install CD already.

[http://mirrors.uwa.edu.au/ubuntu-releases/5.10/ubuntu-5.10-install-i386.list]("http://mirrors.uwa.edu.au/ubuntu-releases/5.10/ubuntu-5.10-install-i386.list")

---

### Post by Sutekh on 2006-02-27
[QUOTE=aysiu]Okay. I'm looking in Synaptic, and I see bittorrent and bittornado.

Which would you recommend?[/QUOTE]
bittornado seems to get a good write up from alot of my friends/colleagues.  I have absolutely no experience when it comes to seeding, and trackers, etc.

---

### Post by Malphas on 2006-02-27
Well if you wanted to start distributing it via BitTorrent immediately you could just use a public tracker (such as the PirateBay) and seed it from there for now, which is no harder than posting on a forum.

---

### Post by aysiu on 2006-02-27
Okay, I tried BitTornado, and it was a bit confusing.
KTorrent seems more intuitive, but I don't know how to create a .torrent file.

I'm Googling around...

Let's see when I can get this working.
As I said before, this probably isn't the best thought-out or most complete .ISO (especially since it's only 432 MB instead of 700 MB). If someone can make a better .ISO, the instructions here are not hard to follow (just copy and paste commands into the terminal:

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

In the meantime, something's better than nothing.

---

### Post by Jucato on 2006-02-27
KTorrent (using version 1.2) has a utility to make a .torrent from a file or folder (in your case an ISO). It's only that "Tracker" part that I don't understand how to use. :D

---

### Post by briancurtin on 2006-02-27
would people be interested in downloading the ISO straight off my site? i can mirror it if people are interested in getting it from there

aysiu: check your PMs, i set you up with an FTP account to my site to load it up if you want, in case you didnt see my PM yet

---

### Post by K.Mandla on 2006-02-27
[QUOTE=aysiu]Can you point some out for me? Post a few links? Maybe my idea's redundant.[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=101790](http://www.ubuntuforums.org/showthread.php?t=101790)

I don't think the idea is necessarily redundant. If it adds to a basic installation, or even a server install, it would be useful.

---

### Post by aysiu on 2006-02-27
Okay the torrent is on Pirate Bay.

**Edit**: Pirate Bay *says* it's uploaded, but it's not the actual file, I think. I'm getting this error in KTorrent. I don't really have a lot of experience with all this torrent stuff, to be honest.

---

### Post by aysiu on 2006-02-27
[QUOTE=K.Mandla][http://www.ubuntuforums.org/showthread.php?t=101790](http://www.ubuntuforums.org/showthread.php?t=101790)

I don't think the idea is necessarily redundant. If it adds to a basic installation, or even a server install, it would be useful.[/QUOTE] I read that thread before, but it just gives instructions for how to make the .ISO. There are no links to *actual* ISOs that anyone can download.

---

### Post by nickle on 2006-02-27
[quote=aysiu]Okay the torrent is on Pirate Bay.

**Edit**: Pirate Bay *says* it's uploaded, but it's not the actual file, I think. I'm getting this error in KTorrent. I don't really have a lot of experience with all this torrent stuff, to be honest.[/quote]

If the torrent file is available this evening, it will start to download/upload it. As soon as some people get it going, it will build up its own momentum. Thats exactly what torrent is all about, making file available for distribution, especially when you don't have the bandwidth to do it yourself. I will let you know how I get on.... Got to work now though.:cry:

---

### Post by Virak on 2006-02-27
[QUOTE=aysiu]I read that thread before, but it just gives instructions for how to make the .ISO. There are no links to *actual* ISOs that anyone can download.[/QUOTE]
Well, I just made an ISO of a Xubuntu add-on CD based on the server install of breezy (yay for vmware!), following [these instructions](https://wiki.ubuntu.com/AptMoveHowto), including that fancy public key stuff. :P

It seems to work just fine, so if anyone's interested in it I'll upload it somewhere or torrent it. (Though not right now; I need to get to sleep.)

---

### Post by xequence on 2006-02-27
I can upload it to bittorent if you want. Then you can give out the torrent to everyone so they can download it.

> Edit: Pirate Bay says it's uploaded, but it's not the actual file, I think. I'm getting this error in KTorrent. I don't really have a lot of experience with all this torrent stuff, to be honest.

Dude, you dont use the pirate bay as a tracker! You use demonoid :)

Many other members of this website have uploaded ubuntu install CDs to it.

But if you insist on doing the torrent yourself, use Azureus to make it and seed it. Too bad there is no uTorrent for linux for you to use...

PLUS I know that there are many ubuntu users on demonoid, so they would want this. And its a public tracker, so you can upload the torrent to anywhere else you want like an indexing site. (There must be dozens of them out there).

---

### Post by CompShrink on 2006-02-27
I think Aysiu has a great idea. I have thought this in the past... but there wasn't that wiki article back then.

Anyway, I think rather than a bunch of people making different CD images as it seems to be heading right now, lets take things slowly, and discuss what we think should be included in the ISO. Lets build up a list, figuring out how much room it would take, and then when we have some level of consensus, we can make 1 or 2 CDs and release them.

I don't mean to steal Aysiu's thunder or anything, I just think if we discuss it a little and come up with a list of what would be useful for the majority of people, we could make a more useful ISO.

So, first off, my thoughts, some of which were taken from previous posts:

-1.KDE and GNOME can be gotten from the official install CDs. They probably don't need to be included.

+1.XFWM, would the entire XUbuntu-Desktop perhaps be easiest/best? Need to check the size.

+2.Programs especially useful for dialup users, and dialup modem drivers. For example, Downloader for X can split downloads into multiple pieces (think threads if you like) and download them in parallel. This can really help on a dial-up modem sometimes. WWWoffle is an interesting looking caching program so you can look through webpages offline, which might also be useful. Anyone know of any other specific useful ones?

+3.Media Programs. FFMPEG, can play a lot of the common formats without w32codecs anyway. The MPlayer compiled from CVS in another thread on these forums I have is very stable, and it can play everything I've thrown at it so far, without w32codecs. Of course that's only my experience, but it plays quicktime, Divx/Xvid, H.264, and some WMV. That should cover a lot of people pretty well. Wouldn't hurt to also include VLC.

+4.The dev packages to make compiling easier, when necessary. This is difficult to deturmine what should be essential. Of course gcc, g++, and other common compilers, X, GTK, QT (KDE's windows), but it quickly becomes debatable what source files you need. Building from source is hard without downloading a lot... this might be a minor priority, or a seperate CD?

What else should we add? Virak, what's on your CD other than xubuntu-desktop?

I think if we think this out and do it in an organized manner, it could be very useful, and maybe make it into the 3rd party projects sub forum. That would give it a lot more coverage, and allow it to reach more Ubuntu dial-up users.

Any specific suggestions to add to this list? Or anyone wanna tell me to shut up, you're entitled to your opinion too.

---

### Post by aysiu on 2006-02-27
[QUOTE=CompShrink]
Anyway, I think rather than a bunch of people making different CD images as it seems to be heading right now, lets take things slowly, and discuss what we think should be included in the ISO. Lets build up a list, figuring out how much room it would take, and then when we have some level of consensus, we can make 1 or 2 CDs and release them.[/quote] Yes, let's do this. I'm glad my poor efforts have at least sparked this. God knows I don't even know how to generate and use public keys, and I don't even know how to use BitTorrent. I'm not really the person to be making this ISO--I just figured something was better than nothing.

> 
I don't mean to steal Aysiu's thunder or anything, I just think if we discuss it a little and come up with a list of what would be useful for the majority of people, we could make a more useful ISO. Please, steal it! I just wanted to get things moving.

> 
-1.KDE and GNOME can be gotten from the official install CDs. They probably don't need to be included. Yes.

> 
+1.XFWM, would the entire XUbuntu-Desktop perhaps be easiest/best? Need to check the size. It's small (as my 432 MB .ISO includes the entire Xubuntu desktop plus some random other packages). Maybe we'd want to keep it small, though, to make the download time shorter? Or maybe we'd want to shove as many packages in as would fit on 700 MB of CD image?

> 
+2.Programs especially useful for dialup users, and dialup modem drivers. That would make sense. Does anyone have a list of suggested packages that would work for this?

> 
+3.Media Programs. FFMPEG, can play a lot of the common formats without w32codecs anyway. The MPlayer compiled from CVS in another thread on these forums I have is very stable, and it can play everything I've thrown at it so far, without w32codecs. Of course that's only my experience, but it plays quicktime, Divx/Xvid, H.264, and some WMV. That should cover a lot of people pretty well. Wouldn't hurt to also include VLC. I think we could probably include everything but w32codecs and libdvdcss2.

> 
+4.The dev packages to make compiling easier, when necessary. This is difficult to deturmine what should be essential. Of course gcc, g++, and other common compilers, X, GTK, QT (KDE's windows), but it quickly becomes debatable what source files you need. Building from source is hard without downloading a lot... this might be a minor priority, or a seperate CD? Okay. Sounds good.

> 
What else should we add? Virak, what's on your CD other than xubuntu-desktop? I would guess whatever Automatix adds? Or is that too much to fit on a CD?

By the way, that Wiki site looks scary, but it's really simple (except for the key stuff). You have to follow the instructions exactly as is. I tried using sudo, but you can't do that (there's a certain part of the instructions even sudo doesn't have permissions for). You actually need to be root, as the instructions indicate.

---

### Post by Virak on 2006-02-27
[quote=CompShrink]What else should we add? Virak, what's on your CD other than xubuntu-desktop?[/quote]Nothing, just it and its dependencies.
[quote=aysiu](except for the key stuff)[/quote]The key stuff is pretty easy too, you just need to have a GPG key pair made.

And I've made the torrent, using the demonoid tracker (as xequence suggested). I've attached the torrent, but if that doesn't work, its page on demonoid is

---

### Post by xequence on 2006-02-27
Ok. First, good job with the xubuntu CD... No more will people be complaining that there isnt a CD for it =D

But Aysiu's extras CD should be a whole different thing then Virak's Xubuntu cd, so I dont see why aysiu needs the xubuntu stuff in there.

And Aysiu, try to pack as much into 650MB. Why? Because they want to get the most out of their CD, and some people have CDs that are only 650MB, so, yea...

But if you wanted to you could go to 780MB, and people can just overburn their 700MB cds :P

---

### Post by aysiu on 2006-02-27
[quote=Virak]And I've made the torrent, using the demonoid tracker (as xequence suggested). I've attached the torrent, but if that doesn't work, its page on demonoid is here.[/quote] Awesome! That's totally awesome.

I think CompShrink's idea of getting this organized and well-thought-out may be a good goal for Dapper, as we'd have almost two months to plan it. For now, though, it's better just to have something... and a Xubuntu CD was sorely needed. Good job, Virak!

[QUOTE=xequence]
But Aysiu's extras CD should be a whole different thing then Virak's Xubuntu cd, so I dont see why aysiu needs the xubuntu stuff in there.[/quote] I'm with you on that. The smaller the CD, the quicker the download.

> 
And Aysiu, try to pack as much into 650MB. Why? Because they want to get the most out of their CD, and some people have CDs that are only 650MB, so, yea...

But if you wanted to you could go to 780MB, and people can just overburn their 700MB cds :P Good point. I'm thinking 700 MB because I have 700 MB blank CDs, but there are still 650 MB CDs out there, so it should probably be 650 MB... but, yeah, why not pack in as much as possible?

So, it would be something like this, then?

Official Ubuntu CD
Official Kubuntu CD
Unofficial Xubuntu add-on CD (until the official one arrives)
Unofficial extras add-on CD

---

### Post by xequence on 2006-02-27
> Good point. I'm thinking 700 MB because I have 700 MB blank CDs, but there are still 650 MB CDs out there, so it should probably be 650 MB... but, yeah, why not pack in as much as possible?

I remember trying out distros but I had to be very picky because I only had 650MB CDs. Trust me, it wasnt fun :P

But I dont know how many people accually still dont have 700MB CDs, so I cant say much.

> So, it would be something like this, then?

Official Ubuntu CD
Official Kubuntu CD
Unofficial Xubuntu add-on CD (until the official one arrives)
Unofficial extras add-on CD

Sounds right.

And you could have it called "Unofficial Ubuntu 5.10 Extras CD by Aysiu v1.0" and do a couple revisions and change the version number each time.

But please, include the codecs for audio and video. No extras CD is complete without it :P

---

### Post by aysiu on 2006-02-27
What codecs do people need?

I took a quick peek at the Ubuntu Guide, and these were the ones there: ```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg lame sox ffmpeg mjpegtools vorbis-tools
``` Are there others that are needed, apart from w32codecs and libdvdcss2, which we shouldn't include with the CD?

What about programs?

---

### Post by xequence on 2006-02-27
> Are there others that are needed, apart from w32codecs and libdvdcss2, which we shouldn't include with the CD?

No, you should include w32codecs and the libdvd thingy =P

You know that the patent holder wont come after you. You know they dont care =P

And about programs, is there anyway way to see what programs are the most popular from the repos? I think debian has something like this, which is how it chooses what packages to put on what CD.

---

### Post by aysiu on 2006-02-27
[QUOTE=xequence]No, you should include w32codecs and the libdvd thingy =P

You know that the patent holder wont come after you. You know they dont care =P[/quote] I know you're the pirate king, but I'd prefer to do things properly. I don't think it's that big a deal. Both w32codecs and libdvdcss2 can be downloaded as .deb files separately--neither has dependencies.

---

### Post by RaptorRaider on 2006-02-27
I don't want to nag, but why not include w32codecs and libdvdcss2 with a huge "use at your own risk/you are responsible/this might not be legal depending on where you live"-sign (like Automatix does I think)?

As far as I know it is not illegal to redistribute these packages, since Ubuntu and other distributions seem to have been doing this for a very long time.
It seems proper enough to me.

---

### Post by aysiu on 2006-02-27
[QUOTE=RaptorRaider]I don't want to nag, but why not include w32codecs and libdvdcss2 with a huge "use at your own risk/you are responsible/this might not be legal depending on where you live"-sign (like Automatix does I think)?

As far as I know it is not illegal to redistribute these packages, since Ubuntu and other distributions seem to have been doing this for a very long time.
It seems proper enough to me.[/QUOTE] We could do that. I believe Automatix's disclaimer is something like "do not do step #24 if you live in the United States."

---

### Post by RaptorRaider on 2006-02-27
No, when you start it (for the first time?) there's a large prompt with warnings and info. I just don't know what it says exactly.

Beside that, could the USA (because of the DMCA?) really be the only country where it is illegal?

---

### Post by xequence on 2006-02-27
> I know you're the pirate king, but I'd prefer to do things properly. I don't think it's that big a deal. Both w32codecs and libdvdcss2 can be downloaded as .deb files separately--neither has dependencies.

While that title sounds really cool, I do not think that putting ether of those into your extra CD would be considered piracy. Its just the patent holders dont care.

Not like pirating windows and saying microsoft doesent care or it doesent affect microsoft, but really, all it is is the fact that it -might- be a little less legal in the US. But its also illegal to drag a horse through the streets of toronto on a sunday, but that doesent stop anyone does it? Ok. Bad example. But I hope you know what I mean =P

---

### Post by RaptorRaider on 2006-02-27
[QUOTE=xequence]Its just the patent holders dont care.[/quote]
That's still piracy I'm afraid.
[quote=xequence]But I hope you know what I mean =P[/QUOTE]
[This]("http://www.dumblaws.com/")? :p


I think a simple warning is fine; legal and user-friendly.

---

### Post by Jucato on 2006-02-27
About Automatix and the propriety codecs: doesn't Automatix download them only after you have allowed it to install those stuff? I mean it's one thing to have an option to download the thing, and another thing to actually be distributing it on CDs. I don't know but doesn't this kind of goes against Ubuntu's philosophy? Even if it were an "unofficial" add-on, shouldn't we at least consider maintaining the spirit of Ubuntu?

But anyway, I suggest not to include them for the meantime, to avoid a bit of debate, or until some people reach a consensus.

---

### Post by xequence on 2006-02-27
> But anyway, I suggest not to include them for the meantime, to avoid a bit of debate, or until some people reach a consensus.

What is the point of the add on CD? To put highly used packages on an easy to install from place.

Who do you know that has all their music collection in vorbis? Who do you know that has all their movies and videos in theora?

Noone.
So they should be included.

---

### Post by Jucato on 2006-02-27
I was only referring to the w32codecs deb. Actually your argument could also be used against Ubuntu's philosophy of not including it in the default install (unlike other distros). 

But anyway, you're probably right. Besides, it's unofficial. I rest my case.

---

### Post by engla on 2006-02-27
I'd love to help with this project, this is actually something I've been thinking about the last days.

I would naturally like us to have versions for all architectures, but that shouldn't be hard if we make a full process out of this.
Let's get a wiki page and begin listing packages. We should be generous with small packages that are used more than occationally.

Anyway -- if we do this properly, it shouldn't be hard to do it for multiple architectures. I volunteer to do the actual iso-making for ppc when we are done with the "design"

---

### Post by basketcase on 2006-02-27
I'd say include automatrix, and everything that could be installed, with the disclaimer.  

That should cover the necessary basics for everyone.  

Just my .02.  I've got a host with a large amount of bw (not sure how fast it is) but I figure I should put it to use.

---

### Post by CompShrink on 2006-02-27
Ok, the forum just hiccupped and logged me out, got rid of my post... forgive me if I miss anything retyping this, it was long...

I agree, keep it under 650mb.

Thanks Engla! Definitely would like to make one for each arch. Ubuntu supports. I can do i386, anyone up for making the AMD64?

Like Fenyx said, distributing and linking to w32codecs are different. It's arguably illegal in the US to link to it, it's definitely illegal to put it on the CDs we distribute. Also, it can easily be worked around with FFMPEG, and other legal codecs, as I said before. 

It won't get 100% of the media files w32codecs does, but it will get most of the common ones, of course including MP3, Divx, Xvid, mpeg1 & 2. I know most people have their backups in divx/xvid with mp3. These do not need w32codecs. For example, mp3 works with lib-mad in Gstreamer, and thus Rhythmbox.

Gstreamer 0.8, which is the breezy version has major issues with audio and video desyncing. I don't think going with that would be good. I think adding totem-xine, MPlayer, VLC, FFMPEG, MAD etc will work better. I am not on ubuntu at the moment, but tonight I will try to figure out specifically what packages are needed to playback most files, without using w32codecs.

Oh, and I'm GMT +9, not US time.

As for wiki, I think we should discuss what we want the name to be first, so that will show up in the URL. As for the layout, here's my suggestion:

**Goals and Description:**
Obviously, and also include a link to this thread. Also explain the layout of the following 4 sections.

**Approved Packages:**
This is a nice clean concise list of generally agreed upon packages for inclusion, and a brief description of what they do.

**Packages Under Consideration:**
A list of packages upgraded from the "Newly Suggested" which will probably have multiple comments in debates over why it should or shouldn't be included, what other packages might be better, etc.


**Newly Suggested Packages:**
Anyone can add what they think should be included. Give a brief description of what it does, and why it should be included.

**Rejected Packages:**
Including w32codecs, (probably, considering the resistance it's getting in this thread, and not just from me) this is the list of the absolutely not included packages, so people won't keep suggesting them, or wondering why they never get upgraded out of the newly suggested section.


This is just my idea of a good layout. If anyone has alternate suggestions, or suggestions for changes to mine, feel free to post.

Also, as I said, what should we name the wiki page?

Aysiu, consider you thunder (partially) stolen. I'm currently attempting to dole it out to the community.

One last thought about w32codecs (and of course this goes for libdecss too), do other distributions actually ship with it? I mean major ones that stay on the legal side? SuSE, Redhat, Mandriva, do their CDs come with it on it? There are a lot of 3rd party sites distributing it, but I don't think the distros officially do.

Ubuntu does not in any official repo. I just used [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to search through all Ubuntu repos, including multiverse/universe. It's not there.

Show me otherwise, and that's fine. Personally I think there are perfectly fine alternatives, but if it's completely legal in the US to include it, I may be swayed.

Also, how would you suggest this warning? Automatrix is a program, it has it's own warning. We're talking about just making a repo CD. Unless we change what we're doing, we can't put a warning easily.

---

### Post by super on 2006-02-27
this is a brilliant idea aysiu! 

i've been in the no-internet situation many times. as a matter of fact, until dapper came out and my wireless suddenly started working, i had to unplug my computer and lug it downstairs to my modem everytime i wanted to apt-get something.

as for w32codec/libdvdcss or not, i think you should include it. if it's in multiverse then why not. unless you live in the states, in which case it might not be such a hot idea for you personally.

[QUOTE=xequence]but its also illegal to drag a horse through the streets of toronto on a sunday, but that doesent stop anyone does it?[/QUOTE]
dang! where was i for that one? :p

---

### Post by CompShrink on 2006-02-27
[QUOTE=super]
as for w32codec/libdvdcss or not, i think you should include it. if it's in multiverse then why not. unless you live in the states, in which case it might not be such a hot idea for you personally.
[/QUOTE]
I know my posts are long but...

As I said, it's not in multiverse! (I will confirm this when I get home... but I don't see why the official Ubuntu repository search engine would be wrong...)

Ok, while w32codecs and libdecss are important considerations, lets talk about other issues too, ok? Lets not just get bogged down in this one.

---

### Post by aysiu on 2006-02-27
[QUOTE=CompShrink]
Aysiu, consider you thunder (partially) stolen. I'm currently attempting to dole it out to the community.[/QUOTE] Thanks so much. I may sometimes be an initiator (instigator?), but I'm not a leader. I just think this is important, but I don't know if I have the technical or organizational chops to make it happen the way it's supposed to.

I'm all for leaving out w32codecs and libdvdcss2 for a few reasons:

1. They're controversial and possibly illegal.
2. Anyone (Xequence?) can make another very similar .ISO that has them. Nothing can stop people from creating a second unofficial unofficial add-on CD.
3. Unlike XFCE and other more complex packages, the .deb files for w32codecs and libdvdcss2 have no dependencies, so it's not so difficult to download them on another computer, copy them to the internet-less Ubuntu and ```
sudo dpkg -i *.deb
```

I'm going to propose at least two goals people can edit or add to as they see fit:

A. To provide additional packages for those who have an internet connection *somewhere*, just not on their Ubuntu computer(s).

B. To allow dial-up users an easy route for installing packages on multiple PCs or reinstalling on the same computer more than the default packages for Kubuntu and Ubuntu.

---

### Post by basketcase on 2006-02-27
my .02$ for what it's worth. 

What about ndis wrapper?  I can't remember if that is included in 5.10.  This *may* allow a few ppl to get online with their wifi.

Also try and determine who 90% of your 'customer' base might be.  Then determine what they might need.  

For the average user, I'd think web broswer, e-mail, audio/video, IM of some sort, Open Office, PDF.  I'm sure I'm missing others, but that would probably take care of your average use by most end users.

---

### Post by aysiu on 2006-02-28
[QUOTE=basketcase]
What about ndis wrapper?  I can't remember if that is included in 5.10.  This *may* allow a few ppl to get online with their wifi.[/quote] Any packages that help with wireless or dial-up should be included. I just don't know what those packages are (since I have neither wireless nor dial-up).

> 
For the average user, I'd think web broswer, e-mail, audio/video, IM of some sort, Open Office, PDF.  I'm sure I'm missing others, but that would probably take care of your average use by most end users. Well, since this is an add-on CD, it would probably include stuff that's *not* on the regular Ubuntu/Kubuntu CDs. The base install includes a web browser and email and IM and OpenOffice.

---

### Post by CompShrink on 2006-02-28
Although those are all included by default, he brings up a good point.

I think we should also consider alternatives to the packages in the areas he specified for our users.

Part of out target audience of dial-up users is likely to have older hardware. Thus, althought OpenOffice is an excelent office productivity suit, putting alternatives, such as abiword for word processing, would be very useful. Gnumeric does excel like functions, and opens those documents, but I don't know how much lighter than OO.o it is.

Dillo is a tabbed web browser much lighter than firefox on ram, and slightly faster. I discovered it myself through using Damn Small Linux.

Any suggestions for lighter weight web browsers and office applications?

---

### Post by basketcase on 2006-02-28
Maybe include other e-mail, browser(s) and IM applications.  I think I remember putting Thunderbird on my 5.10 install, and using something other than what came with 5.10 as far as IM apps go. 

I knew OO was included, but just thinking about the average user.

---

### Post by super on 2006-02-28
[QUOTE=CompShrink]I know my posts are long but...[/QUOTE]
touche. i think i missed your post.

[QUOTE=CompShrink]Ok, while w32codecs and libdecss are important considerations, lets talk about other issues too, ok? Lets not just get bogged down in this one.[/QUOTE]
my suggestions would be things that i install after a clean installation:
java?
nvidia binary?
mono?
nedit? or scite?
thunar?
beep-media-player?

---

### Post by Sutekh on 2006-02-28
[QUOTE=basketcase]
What about ndis wrapper?  I can't remember if that is included in 5.10.  This *may* allow a few ppl to get online with their wifi.[/QUOTE]

From the i386 install CD package list [http://mirrors.uwa.edu.au/ubuntu-releases/5.10/ubuntu-5.10-install-i386.list]("http://mirrors.uwa.edu.au/ubuntu-releases/5.10/ubuntu-5.10-install-i386.list")
> ...
/pool/main/n/ndiswrapper/ndiswrapper-utils_1.1-4ubuntu2_i386.deb
...So ndiswrapper is there, but I totally agree about wireless.  Like I said before there are so many cards.  I don't know much about them either.

Just take a look at the wiki howtos to see the number of wifi cards.

[Ubuntu Wiki Search - 'wifi']("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wifi&titlesearch=Titles")

I wouldn't even know where to start.  Alot of these pages don't even require downloading packages/source.  Maybe I'll check the most common cards that people on the *forum* have problems getting.

---

### Post by CompShrink on 2006-02-28
Super, could you give some more details about your sugggestions? Java sounds good, as does thunderbird (thanks basketcase), but if I recall, nVidia and ATI official binary drivers are licenced as non-redistributable. Please proove me wrong, I would be glad if we could include them.

Also, about the wiki, that give me an idea. We should include part of the Wiki as additional documentation. I have a program that will download all links on a page recursively(excluding links to offsite pages), and alter their links to point to the downloaded copy. I could point this program at certain sub sections of the wiki, and we could include this as documentation.

I'm sure I could figure out how to put this into a deb, but maybe it should be in a more obvious place? Any thoughts?

And speaking of Wikis, lets hear some suggestions for what we should call this project!

(Wow this is growing fast!)

---

### Post by Jucato on 2006-02-28
I think the blackdown-java and flash-nonfree versions are available in the repositories, and these may be included in the add-ons.
Also, the nvidi-glx is also in the repositories and should have no "legal" problems. However, the binary installer that can be downloaded from the nvidia site might be a no-no.
I don't know if firestarter and guarddog are in the installer CDs, but they might be a good addition to the addons. The unrar-nonfree package, I think, should also be included.

---

### Post by CompShrink on 2006-02-28
Ah, yes, I have seen the ATI and nVidia binary drivers in the universe/multiverse. Ok, those sound good.

Unrar is good, as is flash. Java is an issue, is the official Sun version not redistributable? Blackdown is not in the official Ubuntu repos either, though it might be worth looking into.

---

### Post by Jucato on 2006-02-28
Blackdown Java (j2re1.4) is in the multiverse section.

---

### Post by xmastree on 2006-02-28
[QUOTE=CompShrink]And speaking of Wikis, lets hear some suggestions for what we should call this project![/QUOTE]
**[SIZE="5"]Extrabuntu[/SIZE]**

---

### Post by Jucato on 2006-02-28
[QUOTE=xmastree]**[SIZE="5"]Extrabuntu[/SIZE]**[/QUOTE]
LoL \\:D/ 
Normally I would agree with something like this, but don't you think people might mistake it for another *buntu derivative/distro?

---

### Post by xmastree on 2006-02-28
So, think about what the CD **is**. It completes an installation.
How about **Completion**?

---

### Post by engla on 2006-02-28
My suggestion for a name is **Friend** or **Ubuntu Friend**. Hmm, at bit whimsical, but it would work...

Should we include emacs? It's a large download for anyone who wants it, I'd like to have it on an add-on cd.

---

### Post by xmastree on 2006-02-28
[QUOTE=engla]Should we include emacs?[/quote]Nahh.
>  It's a large download for anyone who wants itYeah, but who wants it?
> I'd like to have it on an add-on cd.You're weird! :rolleyes:

(Confession, I've never even seen emacs. I just know the name from all those "I use dreamweaver" "Well **I** use notepad" "Yeah? Well **I** use edlin!" "Yeah? Well **I** use vi" "Oh yeah? Well **I** use emacs!" discussions where the more geeky you are, the less fancy software you use to code html.) :p

Names? **Son of ubuntu!** or **ubun-two**

---

### Post by Leo_01 on 2006-02-28
Name + slogan :

Ubuntu Plus - A Super way to power charge your Ubuntu experience!

---

### Post by xmastree on 2006-02-28
Hmm... slogan, huh? :-k

Ubuntu Plus - It already rocks, let's make it Roll!

Ultimate ubuntu

---

### Post by CompShrink on 2006-02-28
I personally like Ubun-two...

It get's the point across, it's a second CD of ubuntu, not a first. Now while you don't immediately read "ubun-two" and think "oh it's an add-on cd, of course!" It is a nice & catchy name. Once you learn what it is, it seems, at least to me, like a name you won't forget.

"Gah, what's the name of that Ubuntu add-on CD? Oh, yeah, Ubun-two!"

Some of the others sound pretty good too, but right now this is my prefered.

Oh, and just throwing it out there:

"Ubun-two.* But I heard it was a 1 CD distro...*"

or

"Ubun-two. *Bringing multiple CD versatility to a single CD distro.*"


Oh, and about Java, I searched for blackdown and java seperately, but not j2re. I agree it should be included.

---

### Post by xmastree on 2006-02-28
[QUOTE=CompShrink]I personally like Ubun-two...[/quote] :D 

> "Ubun-two. *Bringing multiple CD versatility to a single CD distro.*"That's a bit of a mouthful...

---

### Post by Jucato on 2006-02-28
Ubun-two sounds a bit... um... cheesy? :D
I like Ubuntu Plus better. Simple and gets the message across. Hmm... I wonder if MS will complain if it ever becomes Ubuntu+ ?

Ubuntu Plus - More than just human beings
Ubuntu Plus - Just Works, even more
\\:D/

---

### Post by jpkotta on 2006-02-28
I would like to second the request for emacs.  People use it and once you get up the learning curve (which isn't that steep, I'd describe it as Emacs:Nedit::Linux:Windows), you realize why people use it.  

I'd like to suggest LaTeX, which is a HUGE download, and like Emacs, is a great package.  OO.org for quick documents, LaTeX for professional documents and books.  Plus AUCTeX for emacs (small) and any other LaTeX editors that people suggest.

I'll suggest Octave and Octave Forge (and GNUPlot) (also big downloads).  Anyone in a technical field will appreciate both LaTeX and Octave.

---

### Post by Sutekh on 2006-02-28
[QUOTE=jpkotta]I would like to second the request for emacs.  People use it and once you get up the learning curve (which isn't that steep, I'd describe it as Emacs:Nedit::Linux:Windows), you realize why people use it.  

I'd like to suggest LaTeX, which is a HUGE download, and like Emacs, is a great package.  OO.org for quick documents, LaTeX for professional documents and books.  Plus AUCTeX for emacs (small) and any other LaTeX editors that people suggest.

I'll suggest Octave and Octave Forge (and GNUPlot) (also big downloads).  Anyone in a technical field will appreciate both LaTeX and Octave.[/QUOTE]
Totally agree.  

I use [**kile**]("http://kile.sourceforge.net/"), [**lyx**]("http://www.lyx.org/") and **emacs** for TeX editing.

I second Ocatve, its another good idea.

---

### Post by Jucato on 2006-02-28
Perhaps Emacs and all those other programs used for editing, programming, or technical stuff could be made into another add-on CD.

Btw, no need to include OO.o in an add-on, since it is installed by default in Ubuntu/Kubuntu and is included in the installer CD.

---

### Post by CompShrink on 2006-02-28
I agree with Fenyx, no reason why this has to be only one CD. I think the main CD should be aimed at the general end user, who will not be needing LaTeX for writing books or other uncommon uses.

Please don't misinterpret this as saying they are "unworthy" in some way. I simply don't think they are appropriate for the end users we are aiming for.

A seperate CD with some or all of jpkotta's suggestions, along with build-essentials and some other -dev packages would be extremely useful for some people. But I think that these things aren't needed by everyone, including my view of our target audience.

BTW, for the record, I do use Emacs regularly. I don't think it should go in the main CD though.

---

### Post by GreyFox503 on 2006-02-28
Cool idea.  Just have to remember the target audience.

I wonder if people who like to use LaTeX and emacs will be installing Ubuntu on a computer w/o an internet connection.

---

### Post by Jucato on 2006-02-28
Well, the add-on CD need not necessarily be just for people without broadband connections. Remember that one of the advantages of Linux is that you can install it on as many units as you want. Having an add-on CD only emphasizes that beauty. No need to download the same stuff again and again whenever you need to install/reinstall. :D

---

### Post by CompShrink on 2006-03-02
I just did a fresh install of Breezy last night for this project, and all the updates on a fresh install are about 65mb to download. I think this would be good in the CD as well.

Any more suggestions for the project name?

---

### Post by aysiu on 2006-03-07
So where are we with this?

---

### Post by tikal26 on 2006-03-07
aysiu I have about 500 gigs of bandwith that I don't use so if you want to have another alternative since sometimes when we use bitorrent after the hype is hard to get a dowload. Send me a PM and we can arrange. I know that it is probbly not going to cover the need but it might be a start.

---

### Post by bjweeks on 2006-03-07
I didn't read the whole thread but if you did not get the bittornt set-up I can help...

---

### Post by basketcase on 2006-03-07
I'd be willing to donate some bandwitdh or help with the torrent.

---

### Post by CompShrink on 2006-03-07
[QUOTE=aysiu]So where are we with this?[/QUOTE]
We're stagnant.

For now we need to start a wiki, write up the current definitely included and under debate packages. I will just make it a generic name, and we can decide on a name later since there seems to be no consensus about that at all yet. There is already a "UnofficialUbuntu504AddOnCD" entry (which appears to be more or less dead), so I created  "[UnofficialUbuntu510AddOnCD]("http://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD")" on the wiki, which seems logical to me, even if this CD is made by different people.

Please, anyone feel free to add to it, though I'd appriciate no one editing sections 2 and 5, the approved and rejected package lists.

EDIT: And about the above offers for bandwidth, they are appriciated but we are still working, with Aysiu, on creating a new more well rounded and fully-featured version to replace Aysui's CD.

---

### Post by tikal26 on 2006-03-07
sound good, but if you ever need it just let me know

---

### Post by aysiu on 2006-03-07
[QUOTE=CompShrink]
EDIT: And about the above offers for bandwidth, they are appriciated but we are still working, with Aysiu, on creating a new more well rounded and fully-featured version to replace Aysui's CD.[/QUOTE] I understand that we should do it right--but in the meantime I'd rather have *something* than nothing.

---

### Post by Ugeek on 2006-03-07
Guys, check this out.... its probably what yoy need. thanks to the italian team.
[http://www.zipman.it/UbuntuPiu/](http://www.zipman.it/UbuntuPiu/)

---

### Post by aysiu on 2006-03-07
[QUOTE=Ugeek]Guys, check this out.... its probably what yoy need. thanks to the italian team.
[http://www.zipman.it/UbuntuPiu/](http://www.zipman.it/UbuntuPiu/)[/QUOTE] Awesome! Sure, it's a bit Italian-centered (as it should be), but that's a good "in the meantime" CD to recommend, as it has random other stuff, not just Italian localization software. Thanks for the link.

---

### Post by aysiu on 2006-03-08
Tikal26 has been generous enough to donate some webspace and bandwidth to my stop-gap measure (until we get a well-thought-out add-on CD together).

There is what I consider a rather high bandwidth cap, but I still think we should not abuse this. For now, recommend this only to people who do not have internet access on their Ubuntu boxes. If every forum member starting downloading the .ISO, Tikal26's site would be brought down quite quickly.

Anyone participating in this thread, of course, is welcome to download the .ISO just to see what's on it. libdvdcss2 and w32codecs are omitted, as per Tikal26's request.

Once again--this is not well-thought-out. These are random packages I just happened to have, but I figure it's better to have *something* than *nothing*. By the time we get things organized (a name, a wiki, a list of agreed-upon packages), we may have a solid add-on CD (or two CDs) for Dapper, but this Breezy one should do in the meantime.

[http://www.tikal26.net/ubuntu/breezyaddon.iso](http://www.tikal26.net/ubuntu/breezyaddon.iso)

P.S. As I stated earlier in the thread, the signatures thing went above my head, so these are unauthenticated.

---

### Post by Danni on 2006-03-08
I have a 1000GB bandwidth limit on my server, and rarely go above 100, so if you need another mirror I don't mind helping out. You can pm me if you need any more details.

---

### Post by aysiu on 2006-03-08
Thanks for the offer, Danni.

You're also welcome to just upload the .ISO from Tikal's server to yours if you want to create that mirror.

---

### Post by bjweeks on 2006-03-08
aysiu you should put a placeholder on the main mirror to track the progress and link to other mirrors.

---

### Post by aysiu on 2006-03-08
[QUOTE=bjweeks]aysiu you should put a placeholder on the main mirror to track the progress and link to other mirrors.[/QUOTE] I don't know what that means.

---

### Post by bjweeks on 2006-03-08
A page like put a page under [http://www.tikal26.net/ubuntu](http://www.tikal26.net/ubuntu) and link to all the mirrors and give info about the project.

---

### Post by aysiu on 2006-03-08
[QUOTE=bjweeks]A page like put a page under [http://www.tikal26.net/ubuntu](http://www.tikal26.net/ubuntu) and link to all the mirrors and give info about the project.[/QUOTE] Right now, there are no other mirrors, unless Danni set one up.

There's also no info about the project yet. This thread is the info so far. We haven't come up with a name for it. There's no Wiki page about it. There's not even an agreed-upon list of packages or number of CDs.

What's on Tikal26's site is just something--a stop-gap measure, a bandaid--something for people with no internet on their Ubuntu boxes. There's no info to give until we figure stuff out.

---

### Post by bjweeks on 2006-03-08
You could set-up a fourm or ask for one to be made here where people can request packages...

---

### Post by tikal26 on 2006-03-08
bjweeks:
That is a good idea. I'll probably do that, but I don't know if someone is mirroing this, so if anyone is let me know so that I can put you as a mirror.
Thanks

---

### Post by Danni on 2006-03-09
Sorry about the delay- went to bed not long after I posted last night :)

Will have the mirror up and running by this afternoon at the latest, depending on transfer speeds.

---

### Post by Danni on 2006-03-10
OK, had a few problems, but it's up and running now

[http://ubuntu.jndhost.com/breezyaddon.iso](http://ubuntu.jndhost.com/breezyaddon.iso)

---

### Post by Jucato on 2006-03-10
I have a few suggestions to make regarding this project:

1. We need a project leader. Just someone who will coordinate efforts, inputs, hostings, etc. I suggest aysiu for this since he has initiated the project.
2. We need someone to take care of the wiki. There's already one, made by CompShrink. Naturally, I suggest that he be the one for this job. Mainly, his job would be to update the wiki with what's happening, of course coordinating it with aysiu :D
3. Well, a name is important too, but it can come later. Ubuntu Add-on CD seems to work, for now.
4. for those who have made their add-on CDs (this includes you aysiu :D), I would suggest you post/include a list of the packages included in that CD. It doesn't need to be a very long one-item-per-line list. Even a list like the one you would put on an multiple package apt-get install would do. Just to give a picture of what packages are available.
5. For those  hosting mirrors, I think it would be good if you include in your post which/whose Add-on CD you are mirroring. This would be very helpful when more versions start pouring in.
6. md5sum anyone?
7. If possible, maybe someone could coordinate with the forum admin and/or the ubuntu devs. Just so that they would know what we are doing, avoid any conflicts, give/take suggestions, etc.
8. Not that essential, but I think aysiu's name in red would be terribly nice. :D But I would hate it if his cat avatar would go away (it's so cute!)

Ok, on my part, what can I do to help? Well, I'm not yet that technically adept at making ISO's and CD repos, nor do I have abilities to set up a host/mirror. I could, however, help in seeding the ISO. I'm currently seeding the Ubuntu and Kubuntu 386 CD installers 18hrs a day until Dapper comes out, so I guess I could include the add-on cd as well. I don't know anything about trackers and stuff. All I know is how to download and seed :D So if you need seeding help, I'm your man! (my ISP has no upload cap, AFAIK)

Hope this helps a bit :D

---

### Post by xmastree on 2006-03-10
[QUOTE=aysiu] w32codecs are omitted[/QUOTE]Whaaaaat? :confused: 

That has to be the #1 thing that's missing from the distro, and now it's missing from the add-on too?

---

### Post by tikal26 on 2006-03-10
xmaxstree:

I am sorry but I am inside the USA and I just can't afford to put myself put up a simple  in theline like that. 

I put up a very simple page ( I mean simple) that point to both places. I'll PM Aysius to see what direction he thinks we should take now.

[http://www.tikal26.net/ubuntu/index.html](http://www.tikal26.net/ubuntu/index.html)

---

### Post by aysiu on 2006-03-10
[quote=Fenyx]1. We need a project leader. Just someone who will coordinate efforts, inputs, hostings, etc. I suggest aysiu for this since he has initiated the project.[/quote] I don't know if I'm going to "lead" the project, but if it seems to slow down, I'll nudge it again. I think this should be a community effort, but I definitely want it to happen, even if shabbily.

[quote=Fenyx]
2. We need someone to take care of the wiki. There's already one, made by CompShrink. Naturally, I suggest that he be the one for this job. Mainly, his job would be to update the wiki with what's happening, of course coordinating it with aysiu [/quote] There's already a Wiki? Can you post the address here?

[quote=Fenyx]4. for those who have made their add-on CDs (this includes you aysiu ), I would suggest you post/include a list of the packages included in that CD. It doesn't need to be a very long one-item-per-line list. Even a list like the one you would put on an multiple package apt-get install would do. Just to give a picture of what packages are available.[/quote] I'll do that some time in the next few days.

[QUOTE=xmastree][quote=aysiu]w32codecs are omitted[/quote]Whaaaaat? :confused: 

That has to be the #1 thing that's missing from the distro, and now it's missing from the add-on too?[/QUOTE] Well, first of all, Tikal is hosting, and that's part of her/his terms of hosting the .ISO. w32codecs are illegal in certain countries, including Tikal's.

I don't see what the big deal is. The add-on CD, as I see it, is primarily for people who don't have internet connections on their Ubuntu computers. This is a frequent question, believe it or not. People have a Ubuntu computer that doesn't connect to the internet, but they have a Windows computer that does (or it's the same computer with the Ubuntu *partition* not connecting).

The difficulty is that most packages have a lot of dependencies. Downloading the package and all its dependencies individually in Windows is a pain.

w32codecs is a .deb that has no dependencies. You can download it in Windows, transfer it to your desktop in Ubuntu and then do ```
cd Desktop
sudo dpkg -i w32*.deb
``` Simple as that. To install something like AmaroK is a bit more complicated.

---

### Post by tikal26 on 2006-03-10
it's a she. I am a girl. Just to let you know.

---

### Post by aysiu on 2006-03-10
[QUOTE=tikal26]it's a she. I am a girl. Just to let you know.[/QUOTE] Thanks for the clarification. I didn't want to assume you were male (as a lot of folks do on these forums, just because [the majority of users here are male](http://www.ubuntuforums.org/showthread.php?t=61048)), and I guess it's a good thing I didn't!

---

### Post by aysiu on 2006-03-10
**Edit**: sorry. Nothing.

---

### Post by Jucato on 2006-03-10
Wiki from CompShrink:
[QUOTE=CompShrink]For now we need to start a wiki, write up the current definitely included and under debate packages. I will just make it a generic name, and we can decide on a name later since there seems to be no consensus about that at all yet. There is already a "UnofficialUbuntu504AddOnCD" entry (which appears to be more or less dead), so I created  "[UnofficialUbuntu510AddOnCD]("http://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD")" on the wiki, which seems logical to me, even if this CD is made by different people.

Please, anyone feel free to add to it, though I'd appriciate no one editing sections 2 and 5, the approved and rejected package lists.
[/QUOTE]

[QUOTE=aysiu]I think this should be a community effort, but I definitely want it to happen, even if shabbily.[/QUOTE]

Of course it will be a community effort. But any project, especially in an open-source community-driven one, will need a leader. Not really to dictate or stuff like that. Just someone to coordinate everything. You don't have to do it alone, you can have a central group to do it. Just a few thoughts from Mark Shuttleworth himself:

[QUOTE=http://www.markshuttleworth.com/archives/date/2003/11/]The issue, as I see it, is leadership. Most open source projects are founded by one or two people who have a very clear idea of what they want to create and how they plan to do so. They have an itch to scratch. Once they have a basic framework together, other people start to use it and the stone soup effect kicks in&#8230; some of the users become developers, and the bazaar magic happens. But here&#8217;s what&#8217;s critical - the success of the project continues to depend on it&#8217;s leadership, usually by the founders but sometimes in a more institutional way (like the Debian project).[/QUOTE]

Again, if anyone has successfully made a torrent/tracker for this, I'll be more than willing to seed it, if it will help ease tikal's bandwidth. :D

---

### Post by majikstreet on 2006-03-10
about w32codecs, why not make a warning about it? like automatix has? or make two isos, one that includes w32codecs and one that doesn't, and you could have a huge arning on the w32codecs one.

---

### Post by bjweeks on 2006-03-10
[QUOTE=majikstreet]about w32codecs, why not make a warning about it? like automatix has? or make two isos, one that includes w32codecs and one that doesn't, and you could have a huge arning on the w32codecs one.[/QUOTE]

and host the win32codes iso in france.

---

### Post by Jucato on 2006-03-10
Well, I think the issue now is that the one hosting the ISO is not in France, and has specifically requested not to include the w32codecs.

Would it really be advisable to make a separate ISO just for this .deb? I see 2 reasons why it isn't really necessary to do so, given the already controversial nature of this package:
1. If it's the only package that is wanted, why would you even download the whole ISO?
2. If you want it AND the ISO, then I guess you will have the resources to download something as large as an ISO, why won't you be able to download a 12MB file and keep it for future use?

I guess it won't be much of a problem if the one who will host is not encumbered by copyright laws, or the one who will make the ISO will agree to include it. But as it stands, neither tikal (hosting) nor aysiu (maker) has agreed to do so... yet. Hope you guys understand their situation. I'm sure they're also considering other people's interests, too. :D

EDIT: I'm not exactly sure about the situation with Automatix, but if I'm not mistaken, Automatix only automates the download of the w32codec. It does not (upon checking the deb file with Ark) include the codec in the package itself. It merely downloads it from a host, probably the one linked to in the wiki pages.

---

### Post by aysiu on 2006-03-10
Fenyx, you're right on.

And I will repeat again that the w32codecs .deb has no dependencies. It's very easy to download and install by itself, unlike some other packages (Gtkpod, Inkscape, etc.).

---

### Post by Rumor on 2006-03-10
[QUOTE=Fenyx]
Again, if anyone has successfully made a torrent/tracker for this, I'll be more than willing to seed it, if it will help ease tikal's bandwidth. :D[/QUOTE]

I don't know if it has seeded, but I've made and uploaded the .torrent file to the tracker. I've never seeded from Linux before, so i am not sure it will work. The torrent file is attached, but I make no guarantees :D

---

### Post by Jucato on 2006-03-10
[QUOTE=Rumor]I don't know if it has seeded, but I've made and uploaded the .torrent file to the tracker. I've never seeded from Linux before, so i am not sure it will work. The torrent file is attached, but I make no guarantees :D[/QUOTE]

Ok, I'm downloading it now. Looks like I'm only connected to one peer (would that be you? :D) Anyway, once I've finished downloading (KTorrent says in 5 hours), I'll be seeding it for at most 18hrs a day, 6 days a week (that 1 day I'm not seeding, my sister will be here and will be using the PC on XP!!!!) Hope this helps ease tikal's bandwidth a bit :D

Rumor: I'm not an expert at seeding either. All I do is leave the torrent open after I've downloaded the whole thing. It says "Seeding" anyway so I guess it's seeding.

EDIT: would it be possible if you just posted the untarred-unzipped torrent? It would be more convenient, I guess. Unless there are some rules against it

---

### Post by Rumor on 2006-03-10
[QUOTE=Fenyx]Ok, I'm downloading it now. Looks like I'm only connected to one peer (would that be you? :D) Anyway, once I've finished downloading (KTorrent says in 5 hours), [/QUOTE]

Yep, that's you. A second just joined. I'll leave it up and running for a few days.

[QUOTE=Fenyx]
EDIT: would it be possible if you just posted the untarred-unzipped torrent? It would be more convenient, I guess. Unless there are some rules against it[/QUOTE]

I can upload it as a .zip or a tar.gz, but .torrent is not listed in the allowed file format list.

---

### Post by basketcase on 2006-03-10
It's me...I'll let it seed till the cows come home

---

### Post by akniss on 2006-03-10
aysiu,
check out this thread if you're still looking for someone to host an iso:
[http://www.ubuntuforums.org/showthread.php?t=142610](http://www.ubuntuforums.org/showthread.php?t=142610)

---

### Post by tikal26 on 2006-03-11
akniss:
i guess that it can be a solution for the w32 codecs. I think taht we probably have enough bandwith now. for what I have expirience I use about 500 megs to 1 gig og bandwith and with the new mirror that has more bandwith it we should be fien as long as we don't get everyone on the forums to dowloaded. Still bittorent should be a nice option too.

---

### Post by andlinux21 on 2006-03-11
Is it possible to make an Ubuntu DVD where i can apt-get install things like dillo, beep-media-player, build-essentials, fluxbox and so on?  Will i be able to fit just about everything on a DVD?

---

### Post by xmastree on 2006-03-11
[QUOTE=basketcase]It's me...I'll let it seed till the cows come home[/QUOTE]
I'm torrenting it too. i don't really need it, but I think it will be useful to give away with install discs. Also, once I have it I can seed it for as long as the computer is on.

---

### Post by Jucato on 2006-03-11
[QUOTE=andlinux21]Is it possible to make an Ubuntu DVD where i can apt-get install things like dillo, beep-media-player, build-essentials, fluxbox and so on?  Will i be able to fit just about everything on a DVD?[/QUOTE]

I think there already is. Follow this [link]("http://www.ubuntu.com/download"). Near the bottom part, there's a "DVD Release" section. I'm just not sure w/c packages are included in it. :D

(Oh, btw, build-essentials is included in the regular install CD)

---

### Post by CompShrink on 2006-03-11
For those who didn't notice:
**[SIZE="6"][https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD](https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD)[/SIZE]**

Sorry, I was without internet access for a few days, but I notice no one has edited the Wiki page I made... please people, contribute.

And Aysiu, could you edit your first post to include the wiki link? Perhaps more people would notice it that way.

---

### Post by Jucato on 2006-03-11
Whoopee!! Just finished downloading. I will now be seeding until... well, until kingdom come? Or until a new torrent needs to be seeded.

*Special thanks to Rumor for being the first to seed the torrent ([Here]("http://www.ubuntuforums.org/showpost.php?p=812088&postcount=104") is his post)

[Ubuntu 5.10 Add-on CD ISO from aysiu (torrent file)]("http://www.ubuntuforums.org/attachment.php?attachmentid=6924&d=1142047360")
[List of contents to follow soon]
NOTE: download file is in .tar.gz format
EDIT: Contents of ISO (c/o aysiu)
> acroread alien amarok apt-move build-essential cabextract cdrdao epiphany-browser fakeroot ffmpeg flashplugin-nonfree goobox gstreamer0.8-ffmpeg gstreamer0.8-lame gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-plugins gtkpod inkscape juk k3b kcalc kgpg kolourpaint kword lame linux-image-k7 mjpegtools mozilla-acroread mozilla-mplayer mozilla-thunderbird mplayer-386 mplayer-fonts msttcorefonts numlockx nvidia-glx nvidia-settings qemu smb4k sox toolame wine xfce4 xfce4-appfinder xfce4-artwork xfce4-datetime-plugin xfce4-icon-theme xfce4-panel xfce4-panel-menu-plugin xfce4-showdesktop-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-windowlist-plugin


EDIT: CompShrink, maybe I could help in editing the wiki, once I learn how :D (still new to the wiki world). I will be sending you and aysiu PM's if and when I will add/modify something. For now, I don't have any. :D

---

### Post by aysiu on 2006-03-11
[QUOTE=CompShrink]
And Aysiu, could you edit your first post to include the wiki link? Perhaps more people would notice it that way.[/QUOTE] Done.

By the way, these, as far as I can tell, are the packages (and their dependencies) in my add-on CD: ```
acroread alien amarok apt-move build-essential cabextract cdrdao epiphany-browser fakeroot ffmpeg flashplugin-nonfree goobox gstreamer0.8-ffmpeg gstreamer0.8-lame gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-plugins gtkpod inkscape juk k3b kcalc kgpg kolourpaint kword lame linux-image-k7 mjpegtools mozilla-acroread mozilla-mplayer mozilla-thunderbird mplayer-386 mplayer-fonts msttcorefonts numlockx nvidia-glx nvidia-settings qemu smb4k sox toolame wine xfce4 xfce4-appfinder xfce4-artwork xfce4-datetime-plugin xfce4-icon-theme xfce4-panel xfce4-panel-menu-plugin xfce4-showdesktop-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-windowlist-plugin
```

---

### Post by Ghetto_Smurf on 2006-03-11
i will still have to wait till april (possible release) for xubuntu .iso.

i have this p3 733mhz with 128 that will soon have 512, but xubuntu will be welcome even with more memory

---

### Post by aysiu on 2006-03-11
The official unofficial add-on CD will not include Xubuntu, as it is generally agreed upon that that should be a separate .ISO.

However, my unofficial unofficial add-on CD has XFCE and a bunch of other XFCE components on it.

---

### Post by Jucato on 2006-03-11
aysiu: I think there would be no problem if you also made available the unofficial unofficial (oh boy, that sounds redundant :D) add-on cd w/ xfce for now, at least until the official ISO is released. With the pending delay of the release of Dapper, that might not happen until May or June. I'd be happy to seed it once somebody has done the tracker stuff (or maybe I'll study about making a torrent a bit later so I can do it myself). :D

Um... you're unofficial unofficial add-on cd happens to be the one tikal is hosting and I'm seeding right? gosh I feel stupid. I thought you were talking about something different :D

---

### Post by aysiu on 2006-03-11
[QUOTE=Fenyx]
Um... you're unofficial unofficial add-on cd happens to be the one tikal is hosting and I'm seeding right? gosh I feel stupid. I thought you were talking about something different :D[/QUOTE] Yeah, it's that one. I wasn't that precise with my language, but I called mine *unofficially unofficial* because it isn't endorsed by Canonical *or* the forum members participating in this thread.

The idea is that the *official unofficial* add-on wouldn't be supported by Canonical either but would at least have the approval of the forum members here.

---

### Post by mstlyevil on 2006-03-11
[QUOTE=aysiu]Yeah, it's that one. I wasn't that precise with my language, but I called mine *unofficially unofficial* because it isn't endorsed by Canonical *or* the forum members participating in this thread.

The idea is that the *official unofficial* add-on wouldn't be supported by Canonical either but would at least have the approval of the forum members here.[/QUOTE]

Stop! I am too easily confused.:confused:

---

### Post by Jucato on 2006-03-11
[QUOTE=aysiu]Yeah, it's that one. I wasn't that precise with my language, but I called mine *unofficially unofficial* because it isn't endorsed by Canonical *or* the forum members participating in this thread.

The idea is that the *official unofficial* add-on wouldn't be supported by Canonical either but would at least have the approval of the forum members here.[/QUOTE]

Wouldn't it be easier if it were like this?
Unofficial Add-on CD - isn't endorsed by Canonical, endorsed by the project coordinator/s (like you :D)
Official Add-on CD - endorsed by Canonical (if and when they plan to do so)

Add-on CD's that won't be accepted/endorsed by the project coordinators are still welcome to post their CD's on another thread. This will be easier when we have our own stickied thread or section and the first post will reflect the list of endorsed Add-on CD's.

Btw, you're ISO would be the first endorsed Unofficial Add-on CD :D

---

### Post by aysiu on 2006-03-11
I think I may just call it the aysiu Add-on CD to avoid confusion.
It's random packages I happened to have.
They're not authenticated because I couldn't figure out the whole signature thing.

---

### Post by Jucato on 2006-03-11
aysiu Unofficial Add-on CD :D
I think we'll just come up with a naming convention later. Anyway, I think that there will be very few add-on CD projects that won't get the endorsement of the community members here, except if they included the w32codecs or the libdvdxx (i forgot the name :D)

---

### Post by mstlyevil on 2006-03-11
[QUOTE=Fenyx]aysiu Unofficial Add-on CD :D
I think we'll just come up with a naming convention later. Anyway, I think that there will be very few add-on CD projects that won't get the endorsement of the community members here, except if they included the w32codecs or the libdvdxx (i forgot the name :D)[/QUOTE]

Those things could easily be added later by the user. I believe aysiu is doing the right thing by not including them for legal reasons.

---

### Post by Jucato on 2006-03-11
Not only for legal reasons. I think that by excluding these two, we will be more in line with the Ubuntu philosophy.

...and that will make it easier to get Canonical's endorsement!!! :D

---

### Post by aysiu on 2006-03-11
It's partially and indirectly for legal reasons. Tikal was quite explicit about not letting me include those codecs, and since she's hosting the .ISO for me on her server, she calls the shots, and I'm more than willing to abide with that.

Also, the whole idea of the project, as I envisioned it, is to allow users who have Windows with internet and Ubuntu with no internet to download on their Windows computers and install on their Ubuntu computers easily.

Stuff like XFCE isn't easy to download on one computer and install on another, as it has a lot of dependencies.

libdvdcss2 and w32codecs, however, have no dependencies, so there's no dire need to include them on an add-on CD, since one can just download the .deb by itself and *sudo dpkg -i blah.deb* it.

---

### Post by CompShrink on 2006-03-12
[QUOTE=mstlyevil]Stop! I am too easily confused.:confused:[/QUOTE]
No need to be confused... just edit the wiki please with any suggestions, listed in the first post now (Thank you Aysiu) and in my last post in probably too big bold.

---

### Post by andlinux21 on 2006-03-12
I am downloading the DVD now from bittorrent this is going to be a nice experience I will be able to set up serveral boxes without having internet access  for a daycare

---

### Post by jpkotta on 2006-03-16
Suggestions:

For the wiki: 
There should be some sort of way to vote for packages.  Now, I just added some suggestions there, but from reading the thread here, support for them might be lukewarm.  
Also, maybe there should be a suggestions section there?  I find forum threads get to be to long to get caught up on, and there's too much noise on them.

For the CD: 
I'm not sure if this has been mentioned, but I think we should consider 3 things on whether a package is included: dependencies, size, and popularity.  Popular packages should obviously get on there.  Packages with many dependencies should get on there because they're hard to install outside of apt-get.  Large packages should go on there because this is not just for people with no internet access, it's also for those with slow access.  This brings me to my next concern:
Who is this for exactly?  Is it for most users in general, as a convenience?  Is it for mainly those with slow or no internet?  Maybe there should be several different CDs, e.g. one with a bunch of scientific software, one with all sorts of -dev packages, etc.

---

### Post by aysiu on 2006-03-16
[QUOTE=jpkotta]
For the wiki: 
There should be some sort of way to vote for packages.  Now, I just added some suggestions there, but from reading the thread here, support for them might be lukewarm.  
Also, maybe there should be a suggestions section there?  I find forum threads get to be to long to get caught up on, and there's too much noise on them.[/quote] I, too, agree there should be some way to vote, but how? Polls here allow only 10 options maximum. I don't know how to set up a voting thing on the Wiki...

> 
Who is this for exactly?  Is it for most users in general, as a convenience?  Is it for mainly those with slow or no internet?  Maybe there should be several different CDs, e.g. one with a bunch of scientific software, one with all sorts of -dev packages, etc. Others can disagree, but I think the top priority should be given to those with no internet access (or slow internet access).

Convenience should be an absolute last priority.

---

### Post by jpkotta on 2006-03-16
[QUOTE=aysiu]I, too, agree there should be some way to vote, but how? Polls here allow only 10 options maximum. I don't know how to set up a voting thing on the Wiki...[/QUOTE]

The only idea I could come up with is if you put you name after a package.  This is ugly because it's messy, and unscrupulous people could vote multiple times and unvote others.  There has to be some sort of software that handles this sort of thing.  Or maybe we could use Debian's popularity contest.

---

### Post by Jucato on 2006-03-16
Perhaps we could take votes on some packages. But popularity might not always be the best measuring stick. For one, I bet that the w32codecs will be in demand the most, but I stand firm on my opinion not to include this.

@aysiu: given the 1 month delay of Dapper, not to mention having actually no temporary release date for the official Xubuntu CD's, won't you reconsider an Xfce/Xubuntu add-on CD?

---

### Post by aysiu on 2006-03-16
[QUOTE=Fenyx]
@aysiu: given the 1 month delay of Dapper, not to mention having actually no temporary release date for the official Xubuntu CD's, won't you reconsider an Xfce/Xubuntu add-on CD?[/QUOTE] I'm confused by this request. First of all, I'm not some kind of authority. I may have started this thread, but I think it's definitely a community project.

Also, I've never been against having a Xubuntu add-on CD. I think, actually, the general consensus was that we should have a Xubuntu add-on CD.

---

### Post by Jucato on 2006-03-16
oh sorry about that. Take a look at the bottom of the Add-on wiki page and you'll see what I mean. 

Of course it's a community project. But even communities need someone to lead/coordinate. :D But anyway, again I'll be happy to seed any ISO if someone would be willing to set up a tracker for it and seed it initially. I'm still seeding your add-on. But I guess no one's downloading it for now. :(

---

### Post by aysiu on 2006-03-16
[QUOTE=Fenyx]oh sorry about that. Take a look at the bottom of the Add-on wiki page and you'll see what I mean.[/quote] I took > Xubuntu-desktop - Will be made available as a separate CD to avoid bloat. to mean that it won't be included with the rest of the add-on CD but would be its *own* separate add-on CD.

> 
Of course it's a community project. But even communities need someone to lead/coordinate. :D But anyway, again I'll be happy to seed any ISO if someone would be willing to set up a tracker for it and seed it initially. I'm still seeding your add-on. But I guess no one's downloading it for now. :( Most people probably don't need it, but anyone without an internet on Ubuntu will be very grateful--these folk do pop up from time to time.

By the way, my extremely unofficial add-on has XFCE and a bunch of other XFCE-related packages on it (not all the Xubuntu stuff is there, though).

---

### Post by Jucato on 2006-03-16
> Generally Rejected Packages:
Xubuntu-desktop - Will be made available as a separate CD to avoid bloat.
Kinda ambiguous. Could also mean that an add-on CD won't be made because the official "separate" Xubuntu CD will be made available. When? Don't know.

Oh yeah, I forgot that it included Xfce, but not Xubuntu. Sorry 'bout that aysiu. :D (I feel sheepish again...)

---

### Post by aysiu on 2006-03-16
[QUOTE=Fenyx]Kinda ambiguous. Could also mean that an add-on CD won't be made because the official "separate" Xubuntu CD will be made available. When? Don't know.[/quote] If it is ambiguous, I'm glad you're clearing it up now. Is anyone willing to say that means Xubuntu will take the place of any other add-on CD? My understanding was that it would be in addition to another add-on CD. So...

1. Kubuntu CD
2. Ubuntu CD
3. Ubuntu DVD
4. Unofficial Xubuntu CD
5. Unofficial add-on CD

---

### Post by Jucato on 2006-03-16
I also thought that there would be an unofficial Xubuntu (add-on) CD until the official Xubuntu CD comes out. That's why I was surprised when I read the wiki. I presumed it to mean that since an official Xubuntu would *probably* come out together with Dapper, it won't be included in the Unofficial Add-on CD project. But upon further thinking, I haven't seen any official timeline from Canonical regarding Xubunut. All they have is Ubuntu, Kubuntu and Edubuntu.

---

### Post by aysiu on 2006-03-16
It looks as if Virak already made a Xubuntu CD:
[http://www.ubuntuforums.org/showpost.php?p=774971&postcount=20](http://www.ubuntuforums.org/showpost.php?p=774971&postcount=20)
[http://www.ubuntuforums.org/showpost.php?p=775979&postcount=24](http://www.ubuntuforums.org/showpost.php?p=775979&postcount=24)

---

### Post by Jucato on 2006-03-16
I seem to be having problems with his links. The demonoid tracker link gives me an error, and his attachment contains a file called attachment.php. I'll try sending him a PM to clarify.

Anyway, I'm going to get a bit off-topic here. How do I get to edit that wiki page, to remove Xubuntu from the "Generally Rejected Packages" section? I also wanted to include your unofficial add-on CD with the links and list of packages, with your permission of course. Also, what is Ubuntu's/Canonical's policy in posting these "unofficial" stuff? 
I hope CompShrink logs in and sees reads this thread again so we could coordinate the contents of the wiki. I think the Xubuntu community is growing. Some are asking for a separate section in the forums already.

---

### Post by Virak on 2006-03-16
[quote=aysiu]It looks as if Virak already made a Xubuntu CD:
[http://www.ubuntuforums.org/showpost.php?p=774971&postcount=20]("http://www.ubuntuforums.org/showpost.php?p=774971&postcount=20")
[http://www.ubuntuforums.org/showpost.php?p=775979&postcount=24]("http://www.ubuntuforums.org/showpost.php?p=775979&postcount=24")[/quote] Indeed I did. Unfortunately, the tracker is down, so it's a bit useless at the moment. I'm uploading it somewhere right now but I can't upload it very fast, so it won't be done for at least an hour.

---

### Post by Jucato on 2006-03-16
That's nice. (And what a fast response! :D)
I'll help you seed the ISO once you get it up and running. I've been seeding aysiu's for quite a few days now.

Also, if it would be possible and if it won't be too much of an inconvenience, could you provide a list of packages included in your ISO, just like what aysiu gave when I asked him. I'll be using that info when I post the links to the add-on CD's (with full credits to you of course :D). Something like I did here:[http://www.ubuntuforums.org/showpost.php?p=812666&postcount=114](http://www.ubuntuforums.org/showpost.php?p=812666&postcount=114)

---

### Post by Virak on 2006-03-16
Actually, I'm uploading it to [yousendit]("http://yousendit.com"), not making a torrent with a different tracker (demonoid probably won't be down very long, anyway), though you can seed it if you want when it comes back up. And I'd add a list of everything on the disc to this post, but it's a bit long.

EDIT: Well, the tracker seems to be back up, so you can get the CD 


EDIT link removed

---

### Post by Jucato on 2006-03-16
I see to be having a problem with Demonoid.com (either that or I'm just plain stupid when it comes to this kind of thing.) Why does it ask me for a username and password? do I have to register to be able to get that .torrent file? (btw, registrations are down, so I wouldn't be able to register anyway).

About the list of packages: it's ok. it's not really essential. Just wanted to have it in case someone asked or was interested to know what's in the ISO's. Thanks for the effort you are putting in this. :D

---

### Post by Virak on 2006-03-16
Hmm, I didn't know you needed to register to access it. I've attached the torrent file (bzip'd, since it doesn't allow you to upload torrents), could you try using that and tell me if it works? If not, I'll find another tracker to use instead.

---

### Post by Jucato on 2006-03-16
Ok... I'm feeling a bit lost here. I don't know if I'm doing it right. Does that bz2 file contain a .torrent file? Because it's showing that the contents is an attachment.php... or I might be doing something wrong... PHP scare the hell out of me. :D

---

### Post by Virak on 2006-03-16
The attachment works just fine for me, but if you're having a problem with it, try [this](http://24.76.176.29/Xubuntu add-on CD.torrent) one instead.

---

### Post by Patrick-Ruff on 2006-03-17
hold on a sec, can someone give me a little overview of xubuntu? I don't exactly understand what it is, does it like modify the GUI or something? also, is the add-on cd gonna include the xubuntu modifications + extra programs?

thanks,

---

### Post by Jucato on 2006-03-17
ok the 2nd link worked better.
Actually I'm having a bit of a problem with PHP's. I just tested it out in Firefox and everything works perfectly. :(
I'm downloading it right now and I'll be seeding it till kingdom come. :D
Thanks for your work! I'll be able to test it out for a while once I finish downloading it.

EDIT: Hi Patrick-Ruff, welcome to this project. What is Xubuntu. To make it short, it goes like this:
Ubuntu = Ubuntu using GNOME
Kubuntu = Ubuntu using KDE
Xubuntu = Ubuntu using Xfce

Well, basically this Xubuntu add-on CD (made by Virak, thank you!) lets you install the xubuntu-desktop without an internet connection. The xubuntu-desktop metapackage contains the the Xfce desktop environement, xfwm window manager, and all other dependencies needed to run an independent Xubuntu installation. 

the Add-on cd made by aysiu is a blend of different packages, including the xfce desktop environment. However, it does not have all the packages included in the xubuntu-desktop metapackage. If you read my post a few pages back (I'll make a link in a while) aysiu was kind enough to provide a list of packages included in her ISO. check it out if you're interested.

---

### Post by Patrick-Ruff on 2006-03-17
ok so, xfce replaces gnome? or what? what does it look like?  (sorry for all the questions :P)

whew, excuse me there. the request for the screenshots definately wasent necessary, hell, all those questions are irrelevant. however, I have a particular interest in the Mac OS X GUI, is it possible to make this look like it?

---

### Post by Jucato on 2006-03-17
replaces GNOME... well you could say it like that. 
Xfce is a desktop environment that's also based on GTK+ (the same toolkit that GNOME uses), so basically they are very close cousins. The common opinion is that Xfce is a lightweight desktop environment that runs very well and fast even on older machines

Here's a link to the official Xfce page: [http://www.xfce.org/](http://www.xfce.org/)
Here are a few screenshots of Xubuntu: [http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=26](http://shots.osdir.com/slideshows/slideshow.php?release=517&slide=26)

But please take note that Xubuntu itself, as a separate Ubuntu derivative, is still under the works. Meaning they haven't released an official Xubuntu Live CD/Installer CD (but that's on the way). The xubuntu-package is, however, already available in the repositories.

If you want to try out xubuntu and have the internet connection to do so, you don't need to have a fresh install. Just download the xubuntu-desktop package (through Synaptic or apt-get, your choice) and leave it while it does it's stuff. When it downloads and installs successfuly, you will have a new option in the "Session" when you log in your computer (GNOME, Xfce, Default, failsafe).

EDIT: Alternatively, you could also download this Xubuntu add-on CD (made by Virak) and install it without an internet connection. The advantage of this is that it's a one time download and you can reinstall it again and again or install on a different machine. You do need to burn the ISO to a CD hwoever.

---

### Post by towsonu2003 on 2006-03-17
[QUOTE=Patrick-Ruff]ok so, xfce replaces gnome? or what? what does it look like? (screenshots possibly?) (sorry for all the questions :P)[/QUOTE]
let's say you already have gnome. when you install xubuntu-desktop, it install xfce for you and some utilities for you. it also places an entry to the list of windo managers (gnome, kde, balckbox, fluxbos etc) you have / might have. you logout of gnome, choose "session" than xfce, and login. boom, you're in a very lightweight environment. log out, choose gnome from sessions, log in, hop you're in gnome. xfce is nice bc it is not bloated like gonme or kde. it's fast and nice on hardware (less RAM usage etc). so it's faster. search google images for xubuntu and you're bound to find nice screen shots :) I have it besides my gnome just in case I want speed instead of bloat"ation" etc (and also for fun).

---

### Post by Patrick-Ruff on 2006-03-17
that kicks *** guys, nice work :D

---

### Post by CompShrink on 2006-03-17
Ok, a little off topic, but oh well:

Patrick, Xbuntu is more lightweight, which along with being faster, means less fancy looking stuff. It won't look like OSX. Now, if you get KDE, use snaptic and install "kubuntu-desktop" then you can switch in the login area to KDE. Install the[ Baghara ]("http://www.kde-look.org/content/show.php?content=8692")package. In synaptic (or apt-get) the package is kwin-baghira. Make sure you have Universe enabled.


Now, as for on topic:

Rather than voting, as Fenyx mentioned the issue with that, I think having people debate it would be better. I'm almost temped to find some other wiki besides the Ubuntu one, because I'd like to have people be able to edit it without registering. With the official Ubuntu wiki, you need to have a launchpad account, which is understandably good for most pages, but I want this to be more free. Wiki's have rollback systems, so you can see the history and if someone is deleting other people's opinions.

So, in short, thoughtful opinions and explanations are much more useful than mindless voting, in my opinion. We need somewhere where people can contribute without registering, so maybe we'll get more cooperation.

And as for the packages you suggested... I will take a closer look at the ones I don't know, but I don't think they are commonly used packages. I don't think adding them would be worthwhile, as I agree with Aysiu that the target audience, at least for the first version of the CD, is no-internet and slow-internet (dialup or extremely underperforming broadband). For dialup users, for example, I don't think the added download time for those packages would be worthwhile.

Now, maybe I can look into making a script that can automate the CD creation process, and allow users to add their own packages to the CD. This should satisfy Fenyx and those who want w32codecs as well. I only have a basic knowledge of scripting, and no knowledge about making a custom APT CD, *yet*. I have a few hours of free time today, finally, so I'll look into it.

---

### Post by xmastree on 2006-03-17
Hmm, I see there's an Automatix CD now. :-k
Nothing like a bit of competition, eh?

BTW, I'm seeding Aysiu's CD, but there's no takers. ratio is 0.004 just now...

---

### Post by Jucato on 2006-03-17
[QUOTE=CompShrink]This should satisfy Fenyx and those who want w32codecs as well[/QUOTE]

Um... I don't know if I understand that sentence correctly, but just let me clarify my position. I am absolutely **not** in favor of including w32codecs and any other propriety codec in any of unofficial add-on cd that will be endorsed by this project. If people want to make an add-on cd that contains these, they are more than welcome to. But I think that these should not be included in our official list (which currently only consists of aysiu's and Virak's ISO's). But that's just my opinion, of course. I can post my reasons (again), but that will make this post a bit too long. :D

Btw, this was posted this in the Automatix secton: [http://www.ubuntuforums.org/showthread.php?t=145889&highlight=automatix+cd](http://www.ubuntuforums.org/showthread.php?t=145889&highlight=automatix+cd)
Before any reactions come, I'd like to emphasize this fact, though: it does not include the propriecty codecs:
[QUOTE=michals]- Windows' codecs and DVD playback capability packages are not included by
 default. If you want to install these offline - you can play with the script
 "download-restricted" (READ EVERYTHING INSIDE IT FIRST), then re-author the CD.
 Scripts should work unmodified after injecting these restricted packages.
 Reason: all that "licensing" crap - No one wants to go to jail :)))[/QUOTE]
I'm not sure how keen they will be in including that CD to our list (it will be 3 ISO's if they agree).

About the wiki page, I might be more inclined in leaving it in the Ubuntu wiki, unless Launchpad registration requires some sort of payment. The reasons I have for remaining inside the Ubuntu wiki are these:
1. It's more integrated with Ubuntu, unlike something like the easy ubuntu thing. Also, if ever it gets the sign of approval from Ubuntu/Canonical, we won't have much of a problem with moving/transferring/etc.
2. I'm not sure how other wiki pages operate with regards to editing, but keeping it within the jurisdiction of Ubuntu makes sure that it won't/can't be edited just by anyone with a wiki account who feels like doing something.

Of course, I'm no wiki expert (I don't even know how to add/edit anything. I just have an account in wikipedia :D) so my views might actually be invalid/unrelated to this situation.

Update: I'm almost finished downloading the Xubuntu add-on. KTorrent says I still have about 3 hours to go. After that, I'll be seeding it as promised. :D

EDIT: @xmastree: nah, no competition there. We each have stuff that the other doesn't have (automatix doesn't have Xfce :D). I'm actually thinking of posting there to ask if it would be ok if we added their project to the (growing) list of add-on CD's. 

yeah, no takers on my side either. Maybe we need more advertisement, or perhaps a stickied thread. or maybe... aysiu, is there a way we could change the thread title to something like "Unofficial Ubuntu 5.10 Add-on CDs Project"?

---

### Post by CompShrink on 2006-03-17
I for one do NOT support the Automatrix ideology. The concept of making it easy to get your system into a usable condition is of course a great goal. The way Automatrix (and their CD??) go about this is dead wrong, in my opinion.

It ignores the package manager (synaptic/apt) for many of the packages, leaving them not upgradable. It also overwrites your sources.list for the ones it does use apt for, which is a very dangerous thing to do. It is especially dangerous because Automatrix is targeted at people who are beginers and will not necessarily know how to deal with these issues, especially the lack of auto-upgradability of some programs.

This is my own personal opinion, and anyone is free to contridict me. Please, I would like to be wrong about this.

EDIT:
>  - it is uncertain whether it will work on a system "updated" in any way,
for now it is "guaranteed to work" (a grain of salt required :) ) only
BEFORE even security updates occur,
- it cannot upgrade itself to newest versions of programs - you'll need
to redownload the whole CD (or to update it "by hand"),

Personally, I think it's better to stay with a purely APT approach to installing. For non internet users who use someone else's connection, redownloading the new CD for updates is probably ok. But 56k users won't want that, and especially dangerous bugs which are fixed by updates of small filesize packages (like the recent breezy password incident) shouldn't wait until you download the next giant filesize (to a 56k user it is giant) CD.

Also, not friendly for the secondary goal of installation on multiple CDs, as it isn't easily upgradable through normal methods.

---

### Post by Jucato on 2006-03-17
As much as I don't also like how Automatix does things, I've seen it work miracles in helping beginners with their initial problems. It has made people who almost quit Ubuntu/Linux take a second look. I personally would like to encourage people to do it the "conventional" way because of the educational benefits, there are those who just want thing to just work. I see Automatix as a sort of middle ground between Ubuntu and other distros that include these stuff by default (Knoppix, MEPIS, etc.)

How does Automatix ignore apt? I thought that it's basically a script that 1) modifies your sources.list to include the needed repos; 2) downloaded the packages through apt-get; and, 3) installed them using apt-get; of course except for those packages that couldn't be installed that way (java, firefox, flash).

EDIT: I'm not sure if I understood what you quoted from that page, but to me it means that the CD won't update itself if a new version/patch comes out. Meaning if the CD contained package1.0, it won't suddenly have package1.1 if it comes out. But it says nothing that you won't be able to update the package through usual means (apt-get, etc), just that the CD itself won't be updated. At least that's how I understood that statement.

---

### Post by CompShrink on 2006-03-17
Um, just one thing: think about your last post. How is Firefox not installable via apt? It's the default browser, it's on the install CD in apt. There is also an apt version of Java mentioned earlier in this thread. There are a few, very few, things which cannot be installed by deb, the main one I can think of is Real Player, due to the way they made the proprietary installer.

As I said, it does not ignore apt completely. In fact, for the part that doesn't ignore apt, it changes the sources.list, which i understand the reasoning behind, and it does make sense actually, but I don't agree with the idea. I have also not paid attention to recent versions.

Oh, and Arnieboy, creator of Automatrix has said he won't make any versions for dapper or any other releases beyond Breezy. I am not saying it's the devil incarnate or anything, it is deffinately useful. But uninstalling is rediculously difficult (individual command line processes for many programs), and upgrading is harder than it needs to be.

---

### Post by mstlyevil on 2006-03-17
[QUOTE=CompShrink]Um, just one thing: think about your last post. How is Firefox not installable via apt? It's the default browser, it's on the install CD in apt. There is also an apt version of Java mentioned earlier in this thread. There are a few, very few, things which cannot be installed by deb, the main one I can think of is Real Player, due to the way they made the proprietary installer.

As I said, it does not ignore apt completely. In fact, for the part that doesn't ignore apt, it changes the sources.list, which i understand the reasoning behind, and it does make sense actually, but I don't agree with the idea. I have also not paid attention to recent versions.

Oh, and Arnieboy, creator of Automatrix has said he won't make any versions for dapper or any other releases beyond Breezy. I am not saying it's the devil incarnate or anything, it is deffinately useful. But uninstalling is rediculously difficult (individual command line processes for many programs), and upgrading is harder than it needs to be.[/QUOTE]

You failed to mention that Arnieboy is giving the code to the community for further development after Dapper is released.

---

### Post by Jucato on 2006-03-17
Oh, I'm sorry. I should have mentioned Firefox 1.5 (I'm not sure if it installs 1.5 or 1.5.0.1). The one in the repositories is the older version. Sure, you can install that easily. But if you wanted the updated one, there's just no newbie-friendly way to do it. Same with Sun Java and Flash (I actually have the repo versions installed, so no need to install them for me). Real player is a bit easier since it comes in a .deb file.

Well, I have mixed feelings knowing that there won't be an Automatix for Dapper. One, there might be no need for it for the time being (Dapper includes the latest Firefox, OpenOffice, etc). But then it might turn off some beginners who've become a bit confident in using Linux, knowing that Automatix is just around the corner.

Until the time that we could make it a bit easier to install some of the things that Automatix installs, or until the open source versions (of Java and Flash, for example) will be on par with the propriety ones, there will always be a need for something like Automatix. If only we could make .deb files for the Java, Flash, and nVidia installers, then Automatix would be a thing of the past.

---

### Post by mstlyevil on 2006-03-17
Arnieboy has said a number of times that there will be a automatix for Dapper. He will not be the one developing it but he has people who are more than willing to take over for him.

---

### Post by CompShrink on 2006-03-17
You're right, I guess the way I put it sounds like I meant it wouldn't exist for the next release. What I meant by that was that the creator and main driver of the project is leaving.

That wasn't my main point anyway.

This is also a good read, including the comments: [http://applications.linux.com/article.pl?sid=06/03/12/209257&from=rss](http://applications.linux.com/article.pl?sid=06/03/12/209257&from=rss)

I think it's fine to have seperate projects, but personally I'd rather not have our project associated with that one. They can stick to their ideals, and that's fine.

---

### Post by Jucato on 2006-03-17
Ok, so we won't be asking them if we could include them in our list? aysiu, any comments? How about you mstlyevil? :D

So for now, we still have only 2 available ISO's: aysiu's custom mix (246mb) and Virak's Xubuntu add-on (200mb).

---

### Post by Jucato on 2006-03-21
Hi! How's everybody doin?

I forgot to ask something: what should I put in my sources.list when I want to add your add-on CDs to the repos?

The original cd-rom entry in the repos is this
```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```
But I guess that has to be changed to use your (aysiu's and Virak's) CDs. I might be testing Virak's Xubuntu CD next week. Server install + add-on CD should do the trick to make a clean Xubuntu install right?

Still no takers for the add-on CDs :(

@aysiu: do you think we could ask the mods to change the name of the thread to something more formal? The present title looks more like a sort of poll rather than an ongoing project.

---

### Post by Sutekh on 2006-03-21
[QUOTE=Fenyx]Hi! How's everybody doin?

I forgot to ask something: what should I put in my sources.list when I want to add your add-on CDs to the repos?[/QUOTE]

Use
```
sudo apt-cdrom add
```
Then chuck in the add-on CD, and you shouldn't need to do any typing

---

### Post by Jucato on 2006-03-21
Sutekh: thanks! another command I learned today! I know I should be reading the man pages frequently, but it isn't really the easiest thing to read for non-technical/semi-technical people. :D

OT: Wow! I'm a Half-shot Low foam Ubuntu! Does that mean low fat, too? :D

---

### Post by aysiu on 2006-03-21
There's a Wiki for more formal discussion. This thread is just background chit-chat.

You can also add the CD-ROM using Synaptic Package Manager--you don't need to manually edit the sources.list.

---

### Post by Jucato on 2006-03-21
Just wanted people to know that there's an ongoing project. But anyway,the first post says it all.

If I use synaptic, what do I put inside the URL, and section fields?
Binary (deb)
URL: ???
Distribution: breezy
Section: ???

Sorry, I haven't tried adding a CD-ROM repo before. :D

---

### Post by engla on 2006-03-21
[QUOTE=Fenyx]Just wanted people to know that there's an ongoing project. But anyway,the first post says it all.

If I use synaptic, what do I put inside the URL, and section fields?
Binary (deb)
URL: ???
Distribution: breezy
Section: ???

Sorry, I haven't tried adding a CD-ROM repo before. :D[/QUOTE]
You don't use those fields, rather, use:
Edit -> Add CD...
:)

---

### Post by UbuWu on 2006-03-21
There are also DVD's available from [http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en) containing the complete repositories, i.e. main, universe and multiverse. 3 DVD's total.

---

### Post by CompShrink on 2006-03-22
[QUOTE=UbuWu]There are also DVD's available from [http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en) containing the complete repositories, i.e. main, universe and multiverse. 3 DVD's total.[/QUOTE]
Restricted too?

And although that is very useful, not everyone has a dvd burner, and that's way too much to download for someone using a dialup modem.

Thanks for pointing it out though.

---

### Post by hezral on 2006-03-22
hi. i burned the iso but when i tried to update it thru synaptic i get md5sum errors when installing some packages. is there a way to turn off md5sum checking or do i have to download the iso again?

thanks for effort guys

---

### Post by aysiu on 2006-03-22
[QUOTE=hezral]hi. i burned the iso but when i tried to update it thru synaptic i get md5sum errors when installing some packages. is there a way to turn off md5sum checking or do i have to download the iso again?

thanks for effort guys[/QUOTE] Which ISO? And can you post a quick screenshot of what those errors look like in Synaptic?

---

### Post by hezral on 2006-03-23
sorry forgot to mention that. i downloaded the 246mb one..umm from [www.tikal26.net](www.tikal26.net). i burned it using nero in windows, at first nero said that it had some block errors or something but i went ahead and burned it. then i tried burning it using nautilus.. still same errors. 

I'm not at my pc right now but i will post the screenshot later. 

btw i tried using sudo apt-cdrom add and it went ok but it still says that it had errors with some packages. 

thanks

---

### Post by aysiu on 2006-03-23
You are burning it as a disk image, right?

Unforunately, there's no MD5SUM because I just cooked it together with my limited knowledge--no signature, no checksum.

I can testify that if it's not corrupted, it works. I added it to my repositories through Synaptic (not apt-get)--all point-and-click. It does give me a warning that it's not authenticated (it's not), but no other errors.

---

### Post by GreyFox503 on 2006-03-23
It would helpful if md5sums were available alongside these .iso's for download.  Making them is a piece of cake:

```
 md5sum add-on.iso >> add-on.iso.md5
``` 

This will generate a small text file named "add-on.iso.md5" which can used to validate the download of the file "add-on.iso".

---

### Post by aysiu on 2006-03-23
Okay. Here's it is...

I had to give it a .txt extension to upload it, but the filename should probably be *breezyaddon.iso.md5*.

---

### Post by Jucato on 2006-03-23
oooh... I've always been doing that to check the md5sums. never knew that's exactly how they are generated. :D

Btw, what's the difference between
```
md5sum add-on.iso >> add-on.iso.md5sum
```
and
```
md5sum add-on.iso > add-on.iso.md5sum
```
The latter is the one I use.

aysiu, I'll check if the on I'm seeding in the torrents is a match to the one you have on your pc.

EDIT: here's the MD5SUM on aysiu's iso that I'm seeding:

EDIT-EDIT: WTH? we have completely different MD5SUMs??? Well, anyway, I didn't get the ISO directly from you. I wonder if the MD5SUM from tikal is the same as yours.

---

### Post by hezral on 2006-03-23
[QUOTE=aysiu]You are burning it as a disk image, right?

Unforunately, there's no MD5SUM because I just cooked it together with my limited knowledge--no signature, no checksum.

I can testify that if it's not corrupted, it works. I added it to my repositories through Synaptic (not apt-get)--all point-and-click. It does give me a warning that it's not authenticated (it's not), but no other errors.[/QUOTE]

yes i burned it as a disk image. well up to the point to adding it to the synaptic repositories was ok. But after i tried installing some updates..it says some of the packages could not be retrieved or something (sorry im not at home right now so i cant really remember) and when i check the details for the process it had md5sum error or something. thanks for the md5sum i'll check it with my iso file to see if it's the same.

---

### Post by aysiu on 2006-03-23
I don't know if this helps, but when I tested out using the add-on CD through Synaptic, I temporarily disabled the online repositories because I was worried about conflicting sources.

That's weird that you'd get an MD5 error, though.

If the MD5 checks out (i.e., matches your CD), can you try ```
sudo apt-get update
``` from the terminal and post the output here?

---

### Post by GreyFox503 on 2006-03-23
[quote=Fenyx]
Btw, what's the difference between
```
md5sum add-on.iso >> add-on.iso.md5sum
``` and
```
md5sum add-on.iso > add-on.iso.md5sum
``` [/quote] 
Both the ">>" and ">" are special characters that makes the shell redirect the output into the filename that follows.  The difference is that using ">>" will append that output onto the end of the file, while ">" will erase the destination file if it already exists.  In other words, ">" will clobber that file and then write the output, while ">>" will tack the output on to the end of the file.

If the file does not exist, you get the exact same result from both commands.  It will create the file for you.

> 
EDIT-EDIT: WTH? we have completely different MD5SUMs??? Well, anyway, I didn't get the ISO directly from you. I wonder if the MD5SUM from tikal is the same as yours. 
I have no idea...  The almighty MD5 does not lie.. :)

---

### Post by Jucato on 2006-03-23
I'll download the ISO from tikal now and try to compare the md5sums. I can't believe we've been seeding an iso that doesn't match the md5sum of aysiu's iso... :(

---

### Post by aysiu on 2006-03-23
The one on Tikal's site is directly uploaded from my hard drive.

---

### Post by CompShrink on 2006-03-23
[QUOTE=aysiu]The one on Tikal's site is directly uploaded from my hard drive.[/QUOTE]
That doesn't mean there wasn't a hickup while you were uploading it. Thats why people use md5 sums to check. It can just as easily get corrupted in uploading as downloading.

I'm not an expert in md5 at all though, there might be another reason why they don't match... but I doubt it.

---

### Post by Jucato on 2006-03-23
Well, the one I have been seeding didn't come from aysiu or tikal, so the corruption might have been there. I didn't bother checking the md5sum since there was nothing to compare it with. but now that we do, I'll be more careful.

I'll know in a few hours whether tikal's copy will pass the md5sum test. If it does, then I'll easily swap the ISO I'm seeding with that one. Good thing someone was able to test the add-on CD, so that as early as now, we can double check the copies that we're distributing. :D

---

### Post by xmastree on 2006-03-23
FWIW, the one I got with bittorrent, and am now seeding (0.004 ratio :rolleyes:), matches aysiu's checksum.

---

### Post by Jucato on 2006-03-23
I don't understand it. I just downloaded the one from tikal's site and got the same md5sum as the one I've been seeding, which is different from aysiu's... 
I typed ```
md5sum breezyaddon.iso > breezyaddon.iso.md5.txt
```

This is a bit frustrating and confusing... :(

---

### Post by BoyOfDestiny on 2006-03-23
[QUOTE=Fenyx]I don't understand it. I just downloaded the one from tikal's site and got the same md5sum as the one I've been seeding, which is different from aysiu's... 
I typed ```
md5sum breezyaddon.iso > breezyaddon.iso.md5.txt
```

This is a bit frustrating and confusing... :([/QUOTE]

Also, when downloading, maybe it's using something cached... I always use wget for big files anyway... You can trust bittorrent since it uses SHA1 you know the file integrity is 100%..

---

### Post by hezral on 2006-03-23
okay. i compared the 2 checksums that you guys gave and it matched ayisu's one. but i still got the error. 

> W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/main/p/perl/perl-modules_5.8.7-5ubuntu1.2_all.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/main/p/perl/perl_5.8.7-5ubuntu1.2_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/main/p/perl/libperl5.8_5.8.7-5ubuntu1.2_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/main/p/perl/perl-base_5.8.7-5ubuntu1.2_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-386_2.6.12-10.28_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/restricted/l/linux-restricted-modules-2.6.12/linux-restricted-modules-2.6.12-10-386_2.6.12.4-11.1_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/main/m/mesa/libgl1-mesa-dri_6.3.2-0ubuntu6breezy1_i386.deb
  MD5Sum mismatch


W: Failed to fetch cdrom:[Ubuntu-Updates 2006-02-26]/pool/main/m/mesa/libgl1-mesa_6.3.2-0ubuntu6breezy1_i386.deb
  MD5Sum mismatch



and here's a screenshot of sudo apt-get update

---

### Post by aysiu on 2006-03-23
I wonder what the MD5 is trying to compare to...

---

### Post by hezral on 2006-03-23
[QUOTE=aysiu]I wonder what the MD5 is trying to compare to...[/QUOTE]

me too :D 

i did this on a fresh install of breezy.. has anyone else tried the cd? the downloaded ones..

---

### Post by GreyFox503 on 2006-03-24
The fact that you're seeding on bittorrent is even more puzzling, because all the bittorrent clients I've used automatically hash check the pieces as you receive them.  It's part of the torrent file itself.  I check these all the time with my downloads, but I don't have much experience in generating them.  Very odd indeed...

---

### Post by CompShrink on 2006-03-25
Sounds to me like you may have had an error when you burned the disc perhaps? Have you tried burning another CD and seeing if you still get errors on those same packages?

And has anyone else tried to install those packages from the CD they have? Maybe someone else could check to see if it's an isolated issue or not.

And bittorrent clients check while recieving pieces, and every time you re-open a file (to seed or finish downloading).

---

### Post by jc87 on 2006-03-25
By the way , i was thinking that would be nice in the future (when we have add-on cd´s for all the packages needed)  a GUI tool (similar to automatix or easyubuntu) for automatically adding thoose cd´s to the sources.list , and installing all the packages from the cd´s (would rock install Ubuntu in a friend computer this way , less work , more Ubuntuers out there).

---

### Post by aysiu on 2006-03-25
[QUOTE=jc87]By the way , i was thinking that would be nice in the future (when we have add-on cd´s for all the packages needed)  a GUI tool (similar to automatix or easyubuntu) for automatically adding thoose cd´s to the sources.list , and installing all the packages from the cd´s (would rock install Ubuntu in a friend computer this way , less work , more Ubuntuers out there).[/QUOTE] It's not automatic, but there is a GUI tool--Synaptic Package Manager.

---

### Post by mstlyevil on 2006-03-25
[QUOTE=aysiu]It's not automatic, but there is a GUI tool--Synaptic Package Manager.[/QUOTE]

ROFLMAO.  I personally prefer Synaptic to any GUI frontend like Automatix. The best part about Synaptic is it helps control dependency problems.

---

### Post by CompShrink on 2006-03-27
Although helping control dependancy problems is awesome of course, I think it's ability to help with reducing conflicting libraries/programs is just as important.

Who wants various programs rewriting the same files? Live on windows for a while while installing a fair amount of programs, it's not fun.


Oh and I noticed [this other similar project]("http://ubuntuforums.org/showthread.php?t=142697") today. I think including a fair amount of the packages listed there might be good.

Specifically Beagle, fonts, gparted, firestarter (firewall GUI, if I recall correctly).

Any other suggestions?

Lets actually get this going somewhere!

---

### Post by jpkotta on 2006-03-27
There is a new project to make making CDs easy.  
[Forum thread]("http://ubuntuforums.org/showthread.php?p=867624").
[Wiki page]("https://wiki.ubuntu.com/Add_On_CD_Creation").

---

### Post by CompShrink on 2006-03-30
Ok, so here's a start, please can we get a discussion about this list of packages, should I add or remove any of these?

Update 30th March 2006
Sun-j2re1.5 with Firefox Plugin
Flashplayer-Mozilla
D4X
gFTP
Mplayer with Firefox Plugin
Easytag
Kino - video editing
Audacity - audio editing
NVU - website design
BUM - boot up manager
Gparted - hdd partioning
Firestarter - firewall
Rar & Unrar(free & non-free)
gDesklets
Alien - install rpms
smbfs - mount samba as filesystems
Samba Server (and openssl)
Liferea - RSS agregator
F-Spot
Beagle
Mozilla Firefox 1.5.0.1 - not yet added, would need a script
Mozilla Thunderbird, with offline and pgp extentions
many various language input methods
many various international fonts
TOTAL SIZE: 248mb

Adding kubuntu-desktop would add a bit under 150mb... is that worth it? Or it could be a seperate unofficial addon cd. downloading the whole ~650mb Kubuntu install cd in addition to the ~650mb Ubuntu install cd is a pain for 56k users.

---

### Post by aysiu on 2006-03-30
[QUOTE=CompShrink]
Adding kubuntu-desktop would add a bit under 150mb... is that worth it? Or it could be a seperate unofficial addon cd. downloading the whole ~650mb Kubuntu install cd in addition to the ~650mb Ubuntu install cd is a pain for 56k users.[/QUOTE] My guess is that anyone who would be using dial-up would be downloading the CD through another source (i.e., another computer--at work or a friend's or relative's house) broadband. Otherwise, they could just as easily *sudo apt-get install* the 150 MB themselves on dial-up.

---

### Post by jpkotta on 2006-03-30
I've been playing with apt-move lately, and I don't think it's doing what I want.  How do you make a CD with package1, package2, etc., and all of their dependencies, and nothing else.  It seems like apt-move can copy my package cache and set up a mirror with those, but not resolve dependencies.  It can also get *all* packages that I have installed, but I don't want all of those in my local mirror.  How are you guys making CDs with just these packages and their deps?

---

### Post by aysiu on 2006-03-30
The CD I made was from my cache, actually.

But any package you install will be in the cache--along with the package's dependencies.

The first part of the tutorial flushes out packages that came with the regular Ubuntu installer CD, so you should be left with only any additional packages (and their dependencies) in your cache folder.

Does that make sense?

---

### Post by jpkotta on 2006-03-30
[QUOTE=aysiu]The CD I made was from my cache, actually.

But any package you install will be in the cache--along with the package's dependencies.

The first part of the tutorial flushes out packages that came with the regular Ubuntu installer CD, so you should be left with only any additional packages (and their dependencies) in your cache folder.

Does that make sense?[/QUOTE]

Yes, it makes sense, and this is what I have.  However, there are packages that I have installed that I don't want on the CD, in addition to the ones that are on the official CD.  For instance, I have a ton of -dev packages, non-standard packages (which I suppose wouldn't be in the cache anyway), games with big data files, etc.  I know there are "exclude" files for apt-move, but I want "include" files.  I want to say: install these and all of their dependencies, but nothing else.  I worried that I'm going to have to write a tool to do this, and it will be error prone.  I can't imagine that no one has tried to do this before, whether in Ubuntu or Debian.  I've been searching around for a while, and it doesn't look like there is a tool for this.

---

### Post by aysiu on 2006-03-30
[QUOTE=jpkotta]Yes, it makes sense, and this is what I have.  However, there are packages that I have installed that I don't want on the CD, in addition to the ones that are on the official CD.  For instance, I have a ton of -dev packages, non-standard packages (which I suppose wouldn't be in the cache anyway), games with big data files, etc.  I know there are "exclude" files for apt-move, but I want "include" files.  I want to say: install these and all of their dependencies, but nothing else.  I worried that I'm going to have to write a tool to do this, and it will be error prone.  I can't imagine that no one has tried to do this before, whether in Ubuntu or Debian.  I've been searching around for a while, and it doesn't look like there is a tool for this.[/QUOTE] What I'm saying is that you shouldn't have to do a separate include for the dependencies--they should be with the originally requested programs.

Let's say for clarity's sake that you wanted to install program A.
It depends on C, D, E, and F.

E and F on the regular Ubuntu installation.
C and D needed to be downloaded separately.

Presumably, before you install A, E and F should already be in your archives.
Then, after you install A, C and D will be in your archives.

So, by the end, you'll have A, C, D, E and F in the in your .deb archives.
If you follow the AptMove Howto, it'll get rid of E and F before making a CD that will have A, C, and D.

Does that make sense? Why did I leave out B? I don't know.

---

### Post by NoteMe on 2006-03-31
I have looked through most of the posts here now. But can't see any link to the CD. Does that mean that there is no CD at all yet, or have I just missed the link.

BTW: Really great job you guys are doing, thanka a million.
- ØØ -

---

### Post by aysiu on 2006-03-31
[QUOTE=NoteMe]I have looked through most of the posts here now. But can't see any link to the CD. Does that mean that there is no CD at all yet, or have I just missed the link.

BTW: Really great job you guys are doing, thanka a million.
- ØØ -[/QUOTE] It's buried somewhere around post #81 or #89. I've now edited the first post in the thread to include a link to the Tikal-hosted one.

---

### Post by CompShrink on 2006-03-31
[QUOTE=aysiu]What I'm saying is that you shouldn't have to do a separate include for the dependencies--they should be with the originally requested programs.

Let's say for clarity's sake that you wanted to install program A.
It depends on C, D, E, and F.

E and F on the regular Ubuntu installation.
C and D needed to be downloaded separately.

Presumably, before you install A, E and F should already be in your archives.
Then, after you install A, C and D will be in your archives.

So, by the end, you'll have A, C, D, E and F in the in your .deb archives.
If you follow the AptMove Howto, it'll get rid of E and F before making a CD that will have A, C, and D.

Does that make sense? Why did I leave out B? I don't know.[/QUOTE]
I believe what jpkotta is saying is that yes it gets all the dependancies. But it also gets EVERY file (except those on the install cd) he has installed. He only wants to pick a few.

What I did, is dedicate a seperate ~8gb partition to this project. I did a fresh install of Breezy on it. That way, I pick and choose the packages, and there's no extras, since it's a fresh install.

Probably not the ideal way to do it, but it's a very clean way. I would imagine if you followed the instructions on making a debootstrap with chroot jail that people are using to run 32bit programs on their 64 bit installed system, and install the packages and run apt-move in the chroot jail, that *might* work...

---

### Post by jpkotta on 2006-03-31
[QUOTE=CompShrink]I believe what jpkotta is saying is that yes it gets all the dependancies. But it also gets EVERY file (except those on the install cd) he has installed. He only wants to pick a few.

What I did, is dedicate a seperate ~8gb partition to this project. I did a fresh install of Breezy on it. That way, I pick and choose the packages, and there's no extras, since it's a fresh install.

Probably not the ideal way to do it, but it's a very clean way. I would imagine if you followed the instructions on making a debootstrap with chroot jail that people are using to run 32bit programs on their 64 bit installed system, and install the packages and run apt-move in the chroot jail, that *might* work...[/QUOTE]

Yes, that's what I want.  Unfortunately, that's not what I wanted to hear.  I figured I could use chroot, but I was hoping there was an easier way.  My adventures with apt-cache and others haven't yeilded a good basis for a package list generator either (i.e. something to generate a list of deps given a list of packages or .debs).  I'll probably just do what you did, since I have a spare partition.  Oh well, thanks anyway.

---

### Post by aysiu on 2006-04-03
My CD on Tikal's website appears to be gone now.
Anyone else getting a 404 error on this?

[http://www.tikal26.net/ubuntu/breezyaddon.iso](http://www.tikal26.net/ubuntu/breezyaddon.iso)

---

### Post by GreyFox503 on 2006-04-04
I just went up a directory:

[http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/)

Does that look right?

---

### Post by aysiu on 2006-04-04
[QUOTE=GreyFox503]I just went up a directory:

[http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/)

Does that look right?[/QUOTE] I see. I must have gotten the name wrong.

---

### Post by NoteMe on 2006-04-11
I have finaly had the time to try this out now. But as of now I have tried to install about 20 packages, but only one was installed. Am I doing someting wrong?

- I mouted the ISO file.
- I find a deb file and do: sudo dpkg -i NameOfTheDepFile.deb


then I get weird "apt-split can't read" errors. Is it dependencies it complains about? Or am I doing something wrong?

---

### Post by aysiu on 2006-04-11
You really should burn the CD; though, I think you can mount the ISO, too--I just don't know if that'll work.

Once you pop the CD in, it should automount.

Go to Synaptic Package Manager. The second menu option (whatever it's called) has "Add CD-ROM" as an option within it.

Do that.

Then click Reload. Search for what you want to install, click to mark them for installation, and then click Apply.

---

### Post by Sutekh on 2006-04-11
If you want to use the ISO rather than burn a CD you can give this a try.  This is how I use local repositories that I create on my home network.

Backup and edit your sources.list
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
And add this line, replacing the red text with the folder that you mounted the ISO too.  (Should be deb file:// then add the path)
```
deb file://[color=red]/path/to/iso/[/color] breezy main restricted
```
Save (Ctrl+O) and exit (Ctrl+X), then try and update the repositories
```
sudo apt-get update
```
Let me know if this works.

(AYSiu - is there any source code on your addon CD, or just .deb packages?)

---

### Post by aysiu on 2006-04-11
[QUOTE=Sutekh]
(AYSiu - is there any source code on your addon CD, or just .deb packages?)[/QUOTE] I think it's just .deb packages. I don't know. I followed the AptMove Howto on the Wiki...

---

### Post by Sutekh on 2006-04-12
From inspection and the wiki page i'd say that there is only packages.  I just wanted to know, because if there was source code you could add a repository entry for that too (deb-src).

No worries.

---

### Post by arphe_el on 2006-04-12
I'm trying to update my other pc from hoary to breezy this time I encounter this error from the message box:

E: Read error - read (5 Input/output error)

W: MD5 mismatch for: main/binary-i386/Packages
W: MD5 mismatch for: main/debian-installer/binary-i386/Packages

my processor is AMD and i'm using the celeron / AMD installer disk. Any suggestions?

---

### Post by MenZa on 2006-04-12
How about... msttcorefonts?

---

### Post by CompShrink on 2006-04-12
[QUOTE=arphe_el]I'm trying to update my other pc from hoary to breezy this time I encounter this error from the message box:

E: Read error - read (5 Input/output error)

W: MD5 mismatch for: main/binary-i386/Packages
W: MD5 mismatch for: main/debian-installer/binary-i386/Packages

my processor is AMD and i'm using the celeron / AMD installer disk. Any suggestions?[/QUOTE]
You really should post this question in [Breezy 5.10 Support Forum]("http://ubuntuforums.org/forumdisplay.php?f=90") not on this thread. The topic of this thread is an addon cd, so your question is unrelated.

I would help you anyway if I could, but I'm sorry i don't know what that could be.

And Menza, that would be good, but the msttcorefonts is a debian package that downloads the fonts off Microsoft's server. This is because they aren't allowed to be redistributed. We can't legally put them on our CD. In the list I made I have included many other fonts, however.

---

### Post by zugu on 2006-04-12
I want to help by seeding the torrent. Where can I find it?

---

### Post by NoteMe on 2006-04-12
Sorry for taking so much time to get back to you, but I fell alsleep in front of my PC yesterday..:)

I did work to burn it as a CD. So all good now. Thanks.

PS:  If I could suggest someting it would be Emacs, Mono, Monodevelop packages to be added to the CD. That would be great.

---

### Post by aysiu on 2006-04-12
[QUOTE=zugu]I want to help by seeding the torrent. Where can I find it?[/QUOTE] Here?
[http://24.76.176.29/Xubuntu%20add-on%20CD.torrent](http://24.76.176.29/Xubuntu%20add-on%20CD.torrent)

---

### Post by basketcase on 2006-04-12
[QUOTE=aysiu]Here?
[http://24.76.176.29/Xubuntu%20add-on%20CD.torrent](http://24.76.176.29/Xubuntu%20add-on%20CD.torrent)[/QUOTE]

That is Xubuntu

---

### Post by ace2005 on 2006-04-12
[QUOTE=andlinux21]Is it possible to make an Ubuntu DVD where i can apt-get install things like dillo, beep-media-player, build-essentials, fluxbox and so on?  Will i be able to fit just about everything on a DVD?[/QUOTE]

Thats just what everyone needs, anl Kubuntu / Ubuntu Maxi Disk with everything you want to install stuff Like:

Kubuntu-desktop (and all the other versions, i'm thinking, something like suse's boot screen but instead of hello it has the names of all the ubuntu based distros in their own colours on a black background and at the bottom there is menu, and you select which one you want to install, and it could also have an advanced option at the end which will allow the user to select more than one to be installed. and you can install others later)
Build Essential (and some of the others like the java build thing, kde dev packages, gtk dev and x11 dev stuff)
Codecs (every single one you can get your hands on, maybe w32codecs also?)
Media Players (well you have to have some media players, otherwise the codecs would be useless, i like xine, why on earth is there no xmms in ubuntu on the cd, its small and wouldn't take much space on the disk)
Web Browsers
Email Clients
Image Editors (gimp, sodipodi, inkscape stuff like that)
Office Programs (open office, koffice, gnome office)
Drivers (nvidia, Ati,,,,)
Fonts/Language support stuff

just out of curiosity could you put the w32codecs on a deb on the cd with a licence agreement? or a tar.bz2 file? which reminds me:

Archivers and Libraries (tar, lha, rar...)
oh and the whole of kde and gnome (including stuff like juk)

Thats about all i can think of, and i think this addon disk is a great idea, what about a DVD edition?

---

### Post by jpkotta on 2006-04-12
There is already a Universe DVD.  You can get .torrents from anywhere you can get the official CDs.

There has been much discussion about w32codecs; they're not going on this CD or any other.  They're of questionable legality, and there are no dependencies for them, so it's an easy download.  If you can download a .iso, you can download the w32codecs .deb.  The most we need to do is say "w32codecs is not on this CD, get it here instead".

I'm thinking about doing a "technical CD" myself.  It would have scientific packages like octave, and development packages.  This would have as little overlap as possible from the unofficial CD that this thread is all about.

If you have packages that you want included, *edit the [wiki]("https://wiki.ubuntu.com/UnofficialUbuntu510AddOnCD")*.

---

### Post by Sutekh on 2006-04-14
I want to begin by saying I really have no idea how P2P works, except that it downloads Linux ISO *fast*.

I have been trying to seed the Add-On ISO for about 2 days now, and I never seem to be able upload *any* data.  There is never any more than 1 other seeder, is this like a dead tracker (hope that the right terminology) or are there no people downloading it by torrent?  (IMO there's a very likely chance I'm not doing this right)

[ATTACH]8299[/ATTACH]
(Now that's a thin attachment!)

Is anyone else trying to seed/download this ISO and having problems?

---

### Post by aysiu on 2006-04-14
I also know very little about torrents.

I think what has to happen is that the four or five people who want to seed the torrent need to do this:

1. One person has to download the actual .ISO and check it against the MD5SUM.
2. That person needs to upload the torrent.
3. They need to coordinate a day when they'll all try to leech / seed the torrent.

---

### Post by Sutekh on 2006-04-14
Oh.  I thought I downloaded the ISO via torrent and that it was automatically seeding (Azureus usually does this after downloading).

And now that I check, the MD5 sums do not match
```
a4905e24bbe5baa063ae71964171d9a7  breezyaddon.iso - the one you posted on this thread
d88dca263653696cc6247a2fac6d98c8  breezyaddon.iso - the one I downloaded
```
Guess that means I need to download it again?

---

### Post by aysiu on 2006-04-14
[QUOTE=Sutekh]Oh.  I thought I downloaded the ISO via torrent and that it was automatically seeding (Azureus usually does this after downloading).

And now that I check, the MD5 sums do not match
```
a4905e24bbe5baa063ae71964171d9a7  breezyaddon.iso - the one you posted on this thread
d88dca263653696cc6247a2fac6d98c8  breezyaddon.iso - the one I downloaded
```
Guess that means I need to download it again?[/QUOTE] No, apparently, there are a couple of different add-ons out there. Did you download the one from Tikal26's website? That's my .ISO.

---

### Post by Sutekh on 2006-04-14
I wish I could remember.  I will say no, because as someone said earlier, the MD5 doesn't lie.  

I will make sure that I get the one from [http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/) and try again.

---

### Post by Jenda on 2006-04-14
Hello - I admit not to have read the whole thread, but this might be of interest to you:
[https://wiki.ubuntu.com/EasyUbuntu/OfflineModeSpec](https://wiki.ubuntu.com/EasyUbuntu/OfflineModeSpec)
It is the Offline Mode of EasyUbuntu, which is planned/considered. It might make sense to add xubuntu and kubuntu to easyubuntu with consideration for low-spec users...
And it will save a little bit of bandwidth to the downloader (as it downloads only what's necessary) and eliminates the need for .iso hosting.

---

### Post by CompShrink on 2006-04-14
What do people think about adding something that Ubuntu will recognize and popup to give a little explanation of the CD?

We could make an image and put it in a position that Breezy will think the CD is a photo CD, and will ask if they want to import photos. If they select Yes, it could pop up a brief overview.

I think we should also make some sort of user friendly documentation, like a set of HTML
 pages in the root of the CD, which can explain how to add the CD to synaptic, how to use Synaptic, and how to use any non-deb additions we may add.

For one thing, Aysui made a Firefox 1.5 installation & removal scripts. Since Firefox 1.5 is such a big leap, it will never be backported to Breezy (according to the Backportting people themselves), and many people will want it for the very fact that it's a large jump. Therefore, no deb, but still a very useful addition.


Opinions?

---

### Post by CompShrink on 2006-04-15
Aysui, could you please send me a private message? I'd like your help testing something before "releasing it into the wild" on these forums, so I don't want to just post a link here.

And no this is not off topic, as I hope to include it in the addon CD.

For anyone curious, I just made my first .deb file.

In that respect, what do people think about making meta packages? Commonly known examples are ubuntu-desktop, ubuntu-base, build-essentials, etc, those types of deb's. We could create ones such as Dialup-Internet Utilities, Essential Media Playback, etc.

Any suggestions for other ones?

---

### Post by aysiu on 2006-04-16
[QUOTE=CompShrink]Aysui, could you please send me a private message? I'd like your help testing something before "releasing it into the wild" on these forums, so I don't want to just post a link here.[/QUOTE] I've enabled private messaging.

---

### Post by ace2005 on 2006-04-16
Slightly confused

[http://www.tikal26.net/ubuntu/](http://www.tikal26.net/ubuntu/)

Is [http://www.tikal26.net/ubuntu/addon.iso](http://www.tikal26.net/ubuntu/addon.iso) the addon CD for Blender? or is it just general apps for breezy like i think the one above it is? or are they both stuff for blender for breezy?

---

### Post by DarkED on 2006-04-19
Not sure if anyone said, but FileFront is your friend :D

-up to 1gig sized files
-file can stay as long as you wish (i do believe, mine have been there for months)
-you have an upload time of 10 hours (meaning you have 10 hours to finish the upload)
-free
-unlimited number of files, unlimited total space

Hypothetically, you could back up a HDD on this site if none of the files are over 1gig. I use it as an archive for all my bigger stuff, such as cd isos and a zipped version of my website.

So if FF would do what you need, you can host as many .isos as needed for as many add-on CD's.

The servers arent FAST as in the 300kb/s sense, but they are way faster than Bittorrent.

[http://www.filefront.com/](http://www.filefront.com/)

---

### Post by proudmonkeynum1 on 2006-04-19
i've searched through the thread and i can't figure out if the cd has build essentials or not can anyone clarify?

---

### Post by aysiu on 2006-04-19
[QUOTE=proudmonkeynum1]i've searched through the thread and i can't figure out if the cd has build essentials or not can anyone clarify?[/QUOTE] The CD on Tikal's website has it.

---

### Post by GarethMB on 2006-04-19
This thread is a bit long. I'm happy to seed this CD. Can someone post a link to a final torrent. Also, if it hasn't already been started, a new thread without all these replies should be posted. So people can just grab the torrent. Anyways. Can i have a link to the latest torrent.

---

### Post by aysiu on 2006-04-19
[QUOTE=GarethMB]Can i have a link to the latest torrent.[/QUOTE] If someone posts that link, I'll update the first post of this thread so that people won't have to go digging through all these pages.

---

### Post by CompShrink on 2006-04-20
Well, since no one's really been making any new suggestions, I will go with the last list of packages I posted once I have finished packaging thunderbird into a deb. Probably will be done this weekend.

I have started a page at ubuntuplus.bountysource.com, I hope no one minds what I'm doing, but we don't seem to be getting anywhere otherwise. If anyone has any suggestions comments or anything, I would be happy to hear them.

Here is my latest list of included packages:
[http://ubuntuforums.org/showpost.php?p=875571&postcount=200](http://ubuntuforums.org/showpost.php?p=875571&postcount=200)

The only change from the above package list is Firefox will be 1.5.0.2 and Thunderbird will be 1.5, and they will be debs installable by apt-get or Synaptic rather than scripts.

Also, I will be making a repository at ubuntuplus.bountysource.com for installing the unique packages I make, such as the Thunderbird 1.5 and Firefox 1.5 debs built for breezy, and most likely some other meta files.

What would be really great is if we could have some artwork for the project. Logo and maybe a little something else for the website or a guide to the CD.

---

### Post by Paloseco on 2006-04-20
First of all, I think that having a DVD-installer does not change the ubuntu feeling. That is one of the things that Debian has and that Ubuntu lacks. Also, ubuntu, kubuntu and xubuntu should be in the same dvd-installer, with all apps and you just choose what you want during the installation, like suse does. SuSE has worked that in very well.

---

### Post by proudmonkeynum1 on 2006-04-21
I'm having some trouble installing the cd. I went into synaptics and clicked add cdrom and checked the software I wanted but it had dependancy issues. Is there either a way to add the whole cd or get around the dependancies?

---

### Post by CompShrink on 2006-04-21
There will soon (hopefully in a week) be a new CD, with a more thought out and complete set of packages. 

The current CD is just Aysui's set of packages he put into a CD and shared with everyone. Of course that's very useful, but we've been working on getting a more complete and focused add on cd out.

What specific dependancies issues are you having, by the way?

---

### Post by proudmonkeynum1 on 2006-04-22
i had some with build essentials but got that working and i can't get the libraries and other files to install for amarok

---

### Post by stevenjoseph on 2006-04-23
hi thanks for the cd but does this work for an 64 bit pc

---

### Post by CompShrink on 2006-04-23
[QUOTE=stevenjoseph]hi thanks for the cd but does this work for an 64 bit pc[/QUOTE]
We are planning to release the next version of the CD for AMD64, PPC, and i386 if possible. I would say it's pretty likely.

The current CD from Aysui is all i386 packages as far as I know... so no if you installed from the AMD64 version of the Breezy install CD, the current one won't work.

---

### Post by CompShrink on 2006-05-30
Well, the first version of the new CD is out, I [made a thread here]("http://ubuntuforums.org/showthread.php?t=183933") about it.

Currently it is only i386, but I'm hoping to get an AMD64 and PPC version out soon. It's a really simple process, if anyone can spare 5gb on their hard drive to make a new partition, I can step them through the process of making an AMD or PPC version.

Also, anyone will to help with documentation or art (making a logo) would be great. I was hoping to make HTML based help, or any other type where you can imbed in little screen shots so it's a lot more new-user friendly than the text-only help.

---

### Post by C Shore on 2007-03-22
On another thread [http://ubuntuforums.org/showthread.php?p=2335694#post2335694]("http://ubuntuforums.org/showthread.php?p=2335694#post2335694")

I have posted some information about some scripts and information I have been generating on this topic.

---

