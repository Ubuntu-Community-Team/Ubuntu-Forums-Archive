---
title: "What technologies Ubuntu needs real bad?"
date: 2006-06-18
forum: The Cafe
---

### Post by PryGuy on 2006-06-18
Hello everybody!
I wonder what technology should be done for Ubuntu next? Thank you!;)
...And I meant the DirectX analogue that would support the DirectX hardware capabilities, not the DirectX itself...

---

### Post by rai4shu2 on 2006-06-19
The thing Linux needs most is a more mature Office suite, then some nice full-featured, robust video editing tools.

---

### Post by mostwanted on 2006-06-19
Auto-detected, non-intrusive wifi and authentication support available from the get-go. What I'm saying is that I really need NetworkManager installed by default once it supports the most common authentication types and Gnome keyring properly.

Otherwise, a well integrated XGL Metacity or Compiz would be nice.

---

### Post by lapsey on 2006-06-19
We have XGL, but (aside from a few functionalities that can be reproduced in  another wm without so much overhead) it's not that useful for most yet.  

If we are going to have professional video editing tools we are going to need color profiles. 
There are tons of word-processing apps out there - a good OSS DTP suite is really what we need right now.

---

### Post by forrestcupp on 2006-06-19
As far as video editing goes, they should at the very least get cinerella in the repositories.  I don't have a clue why they haven't yet.  Cinerella is the closest thing Linux has to a professional video editing program.

---

### Post by djsroknrol on 2006-06-19
out of the box wifi and video detection would be nice.....

---

### Post by briancurtin on 2006-06-19
video editing shouldnt even be on anyones list. its not important in getting linux to move forward, at all.

---

### Post by terminatorkobold on 2006-06-20
I think an open DirectX implementation, which would be compatible with MS DirectX would be a big step to help porting games and other 3D hungry windows applications to Linux. 

I think that the present rift between Open GL and DirectX is quite unhappy and could be colsed wit great benefits for the Linux community. But I fear that it will never happen. Bah, let's dream a bit!

---

### Post by B0rsuk on 2006-06-20
Where's the 'neither' option ? All of them seem uninteresting for me.

Directx ? WHY ??? Why would you support closed microsofted standard instead of OpenGL ?
xgl/compiz - just eyecandy.

NTFS support works (read only). I have no idea why would I need NTFS support at all on my 100% linux machine.

The other options... I can't remember them, which probably describes their importance well. Ah, photoshop. Sorry, I'm a GIMP addict.

---

### Post by bruce89 on 2006-06-20
I had a thought, if DirectX was supported, then that would be yet another market that MS would own.  3D graphics is one of the few places where they don't have a huge majority.  Also, it would mean that OpenGL would dissappear, as there would be no use for it.

---

### Post by forrestcupp on 2006-06-20
[QUOTE=briancurtin]video editing shouldnt even be on anyones list. its not important in getting linux to move forward, at all.[/QUOTE]

That's a laughable statement.  Just because it's not important to you, doesn't mean it's not important to anyone.  Video editing is becoming a lot more commonplace as businesses, churches and other organizations are seeking to use more multimedia for their presentations and advertisements.  As digital camcorder prices are getting lower, a lot of home users are beginning to use software video editors to edit their home videos.  Video editing is becoming more and more important on every front, and just because you don't think it's important doesn't mean that the future of linux should depend on that.  Why do you think Microsoft includes their Windows Movie Maker for free with Windows?  Even if its a poor excuse for a video editor, they still see the importance in it.  For the Linux community to not pay any attention to video creation would be a big mistake.

---

### Post by bruce89 on 2006-06-20
[QUOTE=forrestcupp]Just because it's not important to you, doesn't mean it's not important to anyone.[/QUOTE]
Again, we come to the "I don't want your feature, as I wouldn't use it (but I want my feature implemented, because I would use it" idea.

---

### Post by Compucore on 2006-06-20
Wouldn't OpenGL be the equivilant to DirectX? The Office suites do need to mature more on this. Bu that will always be an ongoing basis it takes time to do that. Video editing is not a really a high priority for myself since I don't own a camcorder over here. So that is out as well. I know that not many will agree with me on this. But if there was a beter program than Giam for Iming with a web cam and a microphone would be nice. Yahoo and MSN messenger have these capabilitis in them already. Something like this should be available for linux as well. 

Compucore

[QUOTE=bruce89]I had a thought, if DirectX was supported, then that would be yet another market that MS would own.  3D graphics is one of the few places where they don't have a huge majority.  Also, it would mean that OpenGL would dissappear, as there would be no use for it.[/QUOTE]

---

### Post by bruce89 on 2006-06-20
I am against DirectX, I was just saying that if it worked on linux, then there would be no incentive for OpenGL.

---

### Post by jc87 on 2006-06-20
**Full NTFS compatibility** - Read works , and if you need writing i think there is a tool for windows that allows to access Gnu/Linux filesystems.

**DirectX** - And how would this **ever ever EVER** be implemented? DirectX happens to be a proprietary and closed  M$ format , so no way in hell can this be done both technological and legally! 

The true solution is PC games start to being made in OpenGL , and with the growing Gnu/Linux adoption that is what will start to happen.

**XGL or something like that** - XGL is nice , maybe in future Ubuntu releases something like an on/off gui button for it would fracking (BSG fan) rock!

I personally think Ubuntu really needs :

**apt-torrent** (Mark is going to save a fortune at the net bill:rolleyes: )

**Gui´s for Grub/Xorg** (i think some guys already made them , just need to be implemented at the distro)

**Even more packages** at the repos , specially universe (tons of stuff i think should be there)

---

### Post by Lord Illidan on 2006-06-20
Some more speed would be good. What I'd like is to see Office and Firefox made real faster, not the slow apps they are now.

Also, I think, multimedia codecs would be a great feauture, even though there are the legal issues.

And if we could support more windows apps...then why use Windows at all?

---

### Post by forrestcupp on 2006-06-20
[QUOTE=jc87]
**DirectX** - And how would this **ever ever EVER** be implemented? DirectX happens to be a proprietary and closed  M$ format , so no way in hell can this be done both technological and legally! 
[/QUOTE]


It's called "reverse engineering."  It can be done, and it is legal, so long as the people involved never had anything to do with the original proprietary code, and they don't have access to that code.  If you don't believe it can be done, go to [www.reactos.com](www.reactos.com) where you will see a group of people that are reverse engineering the complete MS Windows system with all the drivers, dll's and everything.
> ReactOS aims to achieve complete binary compatibility with both applications and device drivers meant for NT and XP operating systems, by using a similar architecture and providing a complete and equivalent public interface.


This includes directx support.  Reverse engineering is also how we have the free lame for mp3's.  It isn't legal to produce true mp3's without purchasing a license to do that, so we produce "lame" mp3's for free.

Reverse engineered directx compatibility is legal, and possible, but is it wise and profitable to the future of Linux and Free Software?  maybe not.

---

### Post by jc87 on 2006-06-20
> Some more speed would be good. What I'd like is to see Office and Firefox made real faster, not the slow apps they are now.

Then install firefox using apt-build , same speed starting the app , but it gets fracking fast for general cpu usage , i done it a week ago it looks like a divine blessing:rolleyes: 

> And if we could support more windows apps...then why use Windows at all?

Talk is easy , implement not:wink:

---

### Post by Lord Illidan on 2006-06-20
[quote=jc87]Then install firefox using apt-build , same speed starting the app , but it gets fracking fast for general cpu usage , i done it a week ago it looks like a divine blessing:rolleyes: 
Talk is easy , implement not:wink:[/quote]

How many normal users would know how to use apt-build? And speed starting the app is also an issue here. Too long.

And I believe wine needs an improvement. Cedega imho is not doing enough.

---

### Post by bruce89 on 2006-06-20
[QUOTE=Lord Illidan]How many normal users would know how to use apt-build? And speed starting the app is also an issue here. Too long.[/QUOTE]
OO.o and firefox are slow as they are not implemented in GTK+, or QT.  They take ages to start up, as their widget toolkit has to be loaded up as well.

---

### Post by hizaguchi on 2006-06-20
I'd like to see the GTK and QT libraries commonized, myself.  This way you wouldn't have to pick your DE based on which programs you need.  It would benefit both environments and allow more freedom of choice.  Of course, I'm sure there's a technical reason this isn't done, but still my wish. :)

Otherwise, I think an OpenBSD level of security would be nice.  Just because Linux is more secure than Windows now doesn't mean that will always be the case.

---

### Post by bruce89 on 2006-06-20
[QUOTE=hizaguchi]I'd like to see the GTK and QT libraries commonized, myself. This way you wouldn't have to pick your DE based on which programs you need. It would benefit both environments and allow more freedom of choice.[/QUOTE]
Then you'd like the [Portland Project]("http://portland.freedesktop.org/wiki/").

[QUOTE=hizaguchi]Otherwise, I think an OpenBSD level of security would be nice.  Just because Linux is more secure than Windows now doesn't mean that will always be the case.[/QUOTE]
But then, if OpenBSD were popular, it would be insecure too.  The only way you can have an truely "secure" OS is if you don't have it connected to the internet.

---

### Post by dvarsam on 2006-06-21
In my opinion:

1. NTFS support is my most important issue!
(my personal files are split: some stuck in EXT3 format & some stuck in NTFS format)

2. Wired Networking should be improved - selecting from Menu "Places\Network Servers" should show me some real Network Representation man...  

3. OOO should be faster!

That is all  I need for now...

---

### Post by joflow on 2006-06-21
[QUOTE=bruce89]Again, we come to the "I don't want your feature, as I wouldn't use it (but I want my feature implemented, because I would use it" idea.[/QUOTE]

that mentality is very prevalent in the linux community.

Features you dont want = bloat

I dont want your feature implemented no matter how simple it is, so my app can start up .000002 milliseconds faster.  And if the developers decide to implement it, I'll whine about it being bloated.

---

### Post by Lord Illidan on 2006-06-21
If this portland project can manage to get KDE and GNOME apps looking the same no matter in which DE they are in, I'd really like it.

For example. I use Amarok in GNOME, and Synaptic in KDE. Yet they both look really out of place. If the widgets could be standardised, that would look real cool.

I hear SUSE has done something about it in 10.1, but that is upon using their default theme. I'd like it so if I am using a different theme in GNOME, KDE apps would have widgets from that theme...

Thanks for the heads up about why Firefox and Open Office are that slow. Is that why AbiOffice is faster in Gnome?

---

### Post by Virogenesis on 2006-06-21
Personnaly I'd like to see colour profiles as we need no excuses for graphic designers, mac and windows both can do colour profiles.
I see no need for NTFS write currently and I do see a need for a framework based around opengl thats opensource that will be able to stand up against directx.

xegl would be nice to have I will admit but we should really have colour profiles first.

---

### Post by PryGuy on 2006-06-23
[QUOTE=bruce89]I had a thought, if DirectX was supported, then that would be yet another market that MS would own.  3D graphics is one of the few places where they don't have a huge majority.  Also, it would mean that OpenGL would dissappear, as there would be no use for it.[/QUOTE]Why do you think so? Look at the gfx card market, all the modern cards have the DirectX support, right? And this market is not controlled by Micro$oft, correct me if I'm wrong. And the Open Source DirectX (OpenX sounds nice to me :-D) would be a salvation for game creators. Please remember how Micro$oft made it's Windows successful? With powerful office suite or graphics software? No! Games mostly made it. Like it or not Linux should do the same. Games rule the world!!!:D

Many people here say there's no need for DirectX port since Linux has OpenGL. Think it's not true 'cause OpenGL is OpenGL and DirectX is DirectX. Windows has both platforms and noone says "we don't need OpenGL 'cause we already have DirectX".:D

But I voted for NTFS personally...

---

### Post by bruce89 on 2006-06-23
[QUOTE=PryGuy]Why do you think so? Look at the gfx card market, all the modern cards have the DirectX support, right? And this market is not controlled by Micro$oft, correct me if I'm wrong. And the Open Source DirectX (OpenX sounds nice to me :-D) would be a salvation for game creators. Please remember how Micro$oft made it's Windows successful? With powerful office suite or graphics software? No! Games mostly made it. Like it or not Linux should do the same. Games rule the world!!!:D[/QUOTE]

No, the market isn't controlled by them, and I hope you realise that [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") exists.  MS themselves say that OpenGL is better for non-games, but my opinion is that OpenGL is the best for everything, as it is not controlled by any one company.  [X-Plane]("http://www.x-plane.com/") uses OpenGL, as it was originally for Mac, but I must stress it is not a game, but a flight simulator.

[QUOTE=PryGuy]Many people here say there's no need for DirectX port since Linux has OpenGL. Think it's not true 'cause OpenGL is OpenGL and DirectX is DirectX. Windows has both platforms and noone says "we don't need OpenGL 'cause we already have DirectX".:D[/QUOTE]

Yes, that is true, but OpenGL is mostly used by applications that have to be cross platform, and for scientific ones, as it is better at this sort of thing.  Games are almost always DirectX, as they are not required to be cross-platform (they think), and also DirectX is suited to that sector.

[QUOTE=Lord Illidan]If this portland project can manage to get KDE and GNOME apps looking the same no matter in which DE they are in, I'd really like it.[/QUOTE]

I don't think that the idea is to make GNOME and KDE core applications to look nice on either platform, but to allow developers to target both platforms for certain applications.

[QUOTE=Lord Illidan]Thanks for the heads up about why Firefox and Open Office are that slow. Is that why AbiOffice is faster in Gnome?[/QUOTE]

Yes, they don't take the native widgets of the environment, as they are both cross platform.  They need to translate their widgets into the native set at run time.  Abiword and Epiphany are fast on GNOME, as they use the native GTK+ widgets, and there is no translation required.

[QUOTE=joflow]that mentality is very prevalent in the linux community.

Features you dont want = bloat

I dont want your feature implemented no matter how simple it is, so my app can start up .000002 milliseconds faster.  And if the developers decide to implement it, I'll whine about it being bloated.[/QUOTE]
Yes, this kind of thing is very annoying in the free software community, we need things that the majority of people need first, before moving on to specific needs.  I mean look at what Linus said about raw devices:
[QUOTE=Linus Torvalds]The main reason there are no raw devices [in Linux] is that I personally think that raw devices are a stupid idea.[/QUOTE]
That kind of attitude doesn't get us anywhere.

---

### Post by PryGuy on 2006-06-23
[QUOTE=bruce89]No, the market isn't controlled by them, and I hope you realise that [OpenGL]("http://en.wikipedia.org/wiki/OpenGL") exists.  MS themselves say that OpenGL is better for non-games, but my opinion is that OpenGL is the best for everything, as it is not controlled by any one company.  [X-Plane]("http://www.x-plane.com/") uses OpenGL, as it was originally for Mac, but I must stress it is not a game, but a flight simulator.[/QUOTE]Okay, okay, but the thing is that games are built on one of the given platforms usually. And who writes games for OpenGL? ID Software is really great, yet I like their love for Linux. But it's only one company. You can name some other game makers using OpenGL, but agree there are a few of them. And I can name you hundreds of DirectX games written by many companies...

---

### Post by bruce89 on 2006-06-23
[QUOTE=PryGuy]Okay, okay, but the thing is that games are built on one of the given platforms usually. And who writes games for OpenGL? ID Software is really great, yet I like their love for Linux. But it's only one company. You can name some other game makers using OpenGL, but agree there are a few of them. And I can name you hundreds of DirectX games written by many companies...[/QUOTE]
Yes, not many of them do, as they see no need to, "if we can get 90% of the computer market, that's fine" they believe.  Mac is another platform where OpenGL is the only one, and it doesn't have that many games for it either.  Mac has about the same share as Linux, and you see a lot more 3rd party stuff for Mac.  For instance look at Palm PDAs, they have support disks for Windows and Mac, but not Linux.  I expect that this is the difficulty of writing software for it, as all distros use different versions/environments etc., but hopefully LSB and the Portland Project will solve this.
On a slightly related note, my brother ported Doom to the Playstation 2. (he works for Sony at the moment, trying to get a job with Google)

---

### Post by Stormy Eyes on 2006-06-23
The ability to sucker-punch script kiddies over standard TCP/IP. :evil:

---

### Post by neighborlee on 2006-07-25
> **bruce89 said:**
> Yes, not many of them do, as they see no need to, "if we can get 90% of the computer market, that's fine" they believe.  Mac is another platform where OpenGL is the only one, and it doesn't have that many games for it either.  Mac has about the same share as Linux, and you see a lot more 3rd party stuff for Mac.  For instance look at Palm PDAs, they have support disks for Windows and Mac, but not Linux.  I expect that this is the difficulty of writing software for it, as all distros use different versions/environments etc., but hopefully LSB and the Portland Project will solve this.
On a slightly related note, my brother ported Doom to the Playstation 2. (he works for Sony at the moment, trying to get a job with Google)

Does ubuntu actually fully embrace LSB now ?

I see the lsb-core package in synaptic but it doesn't say  really how far the compliance goes, just so gibberish that ' lsb being here should not constitute the idea that ubuntu IS lsb compliant '  LOL..Ooooooooook but what does that mean to a d eveloper wanting to  write once and                                          have it work everywhere...will it work in just suse, mandriva, redhat and other LSB complaint distros and not ubuntu ?

cheers
g.leej(nl)

---

### Post by Stormy Eyes on 2006-07-25
> **Lord Illidan said:**
> How many normal users would know how to use apt-build?

Who cares?

> **Lord Illidan said:**
> And speed starting the app is also an issue here. Too long.

That's what prelink is for.

> **Lord Illidan said:**
> And I believe wine needs an improvement. Cedega imho is not doing enough.

How do you go about improving crutches?

---

### Post by erikpiper on 2006-07-25
A NATIVE free office suite BETTER than microsoft office 2007- I may just have to use crossover- office 2007 looks AMAZING....

(Students need a good office suite...)

Anything better than OOO? I dont care about speed- (Slower than OOO would be a BAD thing tho..) I need freatures. Citations, grammar checking, etc.

---

