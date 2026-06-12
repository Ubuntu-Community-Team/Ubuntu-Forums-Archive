---
title: "Any plans to backport xorg?"
date: 2005-01-04
forum: Ubuntu Backports
---

### Post by AndersAA on 2005-01-04
It'd be nice to have a safe way (well, relativly) of installing a xorg deb package on warty and testing it a bit.  And if I find out it works worse than xfree86 with my current binary only drivers I could just install the old one again.

Well... it'd be nice :p, the only real reason because then I could startup another X server on :1, running composite and xfce4.2 with skippy-xd (read expose-linux) or something, to show off for friends what you can fit into 50mb memory on a linux box ;)

---

### Post by jdong on 2005-01-04
Over the holidays, I was thinking about it..

Thoughts from others?

---

### Post by jdodson on 2005-01-04
[QUOTE=jdong]Over the holidays, I was thinking about it..

Thoughts from others?[/QUOTE]

if the plusses outweigh the pitfalls(you could really mess up some users install).  

what is so great about xorg?  are there that many new features?  i am really curious about the differences.

the preview release of hoary should be out march 7th(contains xorg), might be good to just wait around till then or april 4th for the real deal.

---

### Post by jdong on 2005-01-04
A few pro's I can think of: 
1. Better performance -- X.org starts faster (esp. when dealing with Nvidia 3D drivers) and gives me higher gaming framerates.
2. Composite... Hey, it looks cool.


However, there is the whole breakage with ATI problem. Any word on that?

I think I'll keep my original position (when I started the project): X is too big of a system component for me to backport, quality-test, watch for security problems... AHHH.

---

### Post by jdodson on 2005-01-04
[QUOTE=jdong]A few pro's I can think of: 
1. Better performance -- X.org starts faster (esp. when dealing with Nvidia 3D drivers) and gives me higher gaming framerates.
2. Composite... Hey, it looks cool.[/QUOTE]

wow, faster programs(as long as they keep stability) are great things.  as for the composite thing, gotta google that one.


[QUOTE=jdong]However, there is the whole breakage with ATI problem. Any word on that?[/QUOTE]

ATI keeps telling people to hold on and wait and they will come out with something "super cool."  we are waiting and crap still doesnt work.

[QUOTE=jdong]I think I'll keep my original position (when I started the project): X is too big of a system component for me to backport, quality-test, watch for security problems... AHHH.[/QUOTE]

i agree.

---

### Post by AndersAA on 2005-01-04
ATI has actually already released the driver they said would work with xorg.... it didn't.. but it has been released.

---

### Post by lockenkeyster on 2005-01-04
There were small things that made xorg nicer... I would have stayed with hoary and (kept using xorg) except I needed to start using my laptop for actual work  = )

I think that xorg would make a nice addition, I know that march is just around the corner and you run the risk of some people messing up their perfectly good distro, but what the hey, where's the fun if you don't have to fix anything?

seriously though, if people are using the backports they are probably already willing to take a some risks anyways... Thanks for the great backports so far, expecially having firefox 1.0 has made life grand!

= )

---

### Post by fng on 2005-01-04
[QUOTE=jdodson]ATI keeps telling people to hold on and wait and they will come out with something "super cool."  we are waiting and crap still doesnt work.[/QUOTE]

Yeah :(

---

### Post by daniels on 2005-01-04
Please don't backport it -- it's hard enough to fix people's problems when I know exactly which environment they have, and throwing warty backports into the mix would make my job just about impossible.  Hoary preview isn't far off!  And the more Hoary testers ...

As for ATI's stuff, they have released to a closed beta group a version of fglrx which supports AMD64, X.Org, PCIE, et al.  This is apparently pretty much their gold version; it just needs to run through their internal driver-posting processes.

In not-necessarily-unrelated news, I have a linux-restricted-modules on my hard drive, eagerly awaiting the release of these drivers.

---

### Post by ZakZak on 2005-01-04
[QUOTE=AndersAA]skippy-xd (read expose-linux) or something[/QUOTE]

Holy florking shnit!  I had no idea there was anything like Expose available for X.  I wasn't all that hyped about X.Org before but now I can't freaking wait for Hoary. :)  I use Expose ALL THE TIME on my wife's iBook!

-Zak

---

### Post by fng on 2005-01-05
Once you get hooked on Expose, you cant work without it :). I know the feeling

---

### Post by jdong on 2005-01-05
[QUOTE=daniels]Please don't backport it -- it's hard enough to fix people's problems when I know exactly which environment they have, and throwing warty backports into the mix would make my job just about impossible.  Hoary preview isn't far off!  And the more Hoary testers ...[/QUOTE]

I respect that. To say it again to those who still hold out hope: I'm not gonna backport X.org.

P.S. Has backports caused you any grief yet?

---

### Post by rbrimhall on 2005-01-05
This is possibly unrelated but the mono packages in backports don't seem to like tomboy or vice versa. It crashes constantly if I upgrade mono from the tseng repositories. Not sure why...

---

### Post by AndersAA on 2005-01-05
there should be a huge "do not report these bugs into the warty tree" warning or something, as this isn't strictly warty...  If a backport bugtree is seperate most of the bugs could probably be pushed upstream after they've been screened to confirm they have absolutly nothing to do with the backports.

Extra work, but better to take that work off the official devs.

---

### Post by daniels on 2005-01-05
I don't think they've caused us any troubles thus far, no.

---

### Post by jdong on 2005-01-05
[QUOTE=AndersAA]there should be a huge "do not report these bugs into the warty tree" warning or something, as this isn't strictly warty...  If a backport bugtree is seperate most of the bugs could probably be pushed upstream after they've been screened to confirm they have absolutly nothing to do with the backports.

Extra work, but better to take that work off the official devs.[/QUOTE]

To me, that'd be a pretty common-sense implication...

---

### Post by cutterjohn on 2005-01-05
I'd support a backport of X.org, but I guess it's a moot point as it looks like there are no ppc builds in the backport releases...

Geez. 6 mos old packages and you guys are moaning! }:)

I just switched over to Ubuntu from Yellowdog Linux 3.0.1 for more up-to-date packages that I didn't have to track down the source, the source of dependancies(and what those were.  Alot of projects aren't very clear on dependencies.), etc. build test install for recent versions.  

Basically everything from YDL 3 was ~2yrs old except for a very few items like firefox, thundrbird, and a few others plus security updates.  And really, only the security updates were official builds, the others were done by people like me who wanted fresh packages and had to build it on their own.  The final straw for me was the incredibly bloated YDL4 size(from 1 disk YDL2, 2 disks YDL3, 4! disks YDL4, I still remember early distros that fit on <20 floppies!, diku linux + SLD + others) plus the lack of updated packages, meaning that many times even if I did find more recent sources they start to tend to all require HUGE updates(e.g. GNOME 2.6+, KDE/Qt > 3.2, etc.) which are not fun over dialup...

(Also YDL just plain missed quite a few useful utilities and applications altogether, and I had been considering installing Debian when Ubuntu came along...)

---

### Post by nehalem on 2005-01-06
I wouldn't limit it to that.

Damage is a very interesting feature that's new to xorg 6.8.  Basically this allows programs to know exactly what is being redrawn on the page.  So VNC servers, like vino (I thought I read it supports it), are potentially much faster since it knows exactly what to redraw (not the whole thing).

By far, though, the composite feature is the new and cool feature.  Right now it's limited to Nvidia but that should be changing in time for hoary(refer [here](http://www.rage3d.com/board/showthread.php?t=33794067&page=6) , while ATI has a long ways to go it appears that mttippen is leading the way to much better linux support and relations as shown on this board).  Right now metacity support is pretty lacking for this extension, anyone care to comment on what we can expect from it by hoary?

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=jdong]Over the holidays, I was thinking about it..

Thoughts from others?[/QUOTE]
More trouble than it's worth.

---

### Post by daniels on 2005-01-06
I don't think Metacity will have any amazing Composite support.  Compositing managers are small, though, and I'll try to package the better ones as I find them.

---

### Post by techn9ne on 2005-01-06
Backporting x.org could possibly break a lot of things.

A lot of people rely on backport for stable versions of new software. Major things like a  complete replacement of a major appliance that nearly every other application relies should be done by people that know what they're doing manually.

---

### Post by nocturn on 2005-01-07
[QUOTE=lockenkeyster]seriously though, if people are using the backports they are probably already willing to take a some risks anyways... Thanks for the great backports so far, expecially having firefox 1.0 has made life grand!
= )[/QUOTE]

Backports for now have a great track record of working on Warty.
I only installed Firefox 1.0 from them because I absolutely wanted it, then I disabled the repository again until some other must-have comes up.

As it currently is, newer versions of FireFox, Gaim, ... are very unlikely to break anything.
Moving to Xorg is a very big thing, even if it works at first glance, there may be some apps that break (until you get a newer version).  I do not think this is a good thing on warty (even for people using backports) as Hoary is always available for people who do not mind taking the risk of occasional breakage.

Backports are a great way of providing some updated/extra packages on a stable release, especially for people requiring the update for some reason (like newer vesions of Gaim if you are using MSN).

---

### Post by AndersAA on 2005-01-07
[QUOTE=daniels]I don't think Metacity will have any amazing Composite support.  Compositing managers are small, though, and I'll try to package the better ones as I find them.[/QUOTE]

metacity does have some experimental composite support, supposingly very bad atm though.  But XFCE4.2 does look rather nice on xorg ;)

---

### Post by ZakZak on 2005-01-07
[QUOTE=nocturn]
Moving to Xorg is a very big thing, even if it works at first glance, there may be some apps that break (until you get a newer version).  I do not think this is a good thing on warty (even for people using backports) as Hoary is always available for people who do not mind taking the risk of occasional breakage.[/QUOTE]

I totally agree.  If you want X.org today, update to Hoary.  I'd rather see backports limited to mostly-self-contained updates and stuff that's easy to prove safe.  I really want to play with X.org, but I'd rather wait a few months and get it with a full set of heavily tested updates.

-Zak

---

### Post by HiddenWolf on 2005-01-10
[QUOTE=ZakZak]I totally agree.  If you want X.org today, update to Hoary.  I'd rather see backports limited to mostly-self-contained updates and stuff that's easy to prove safe.  I really want to play with X.org, but I'd rather wait a few months and get it with a full set of heavily tested updates.

-Zak[/QUOTE]
Warty is supposed to be a production-safe platform.
And, dispite being a no-brainer, people will start reporting bugs from backports into the main bugzilla.
Keep it to 'simple' things. :-)

---

### Post by ulrich on 2005-01-10
as far as i read throughout the net a backport of x.org isnt worth the effort...
what ive read so far was that x.org includes all these nice features but they are not ready for everyday use/production system.
so far i only read comments by people that composite really looks cool but its just usable for screenshots to impress your friends ;)
also damage/etc.. relies on the windowmanager and all that...

but i am in NO WAY a programmer and daniels could be the one to answer this :)


ulrich

---

