---
title: "my suggestions for ubuntu"
date: 2009-03-22
forum: Testimonials &amp; Experiences
---

### Post by bertolo on 2009-03-22
I think ubuntu is in a good path.
I have no doubt that in a few years linux will be more established compared with nowadays, microsoft will be doomed, mainly because of ubuntu and it's user friendly filosophy.
People should focus on improving things that are already included.

Audio drivers and graphic card drivers are awful. (180 version of graphic drivers are ok / i still got no sound output since i upgraded from 8.04 to 8.10).
The Random freeze bug while installing it's a nightmare for most of my friends.(initramfs + busybox trouble installing).
Printer, Wireless and Lan features are very very good in version 8.10.
I love gnome desktop style, wine, pidgin and compiz.
Despite of loving gnome, i have to admit that for a new user it looks too childish, and not very professional.

Ubuntu should include latest open office version by default, be prepared for more that 4gb ram and be more user friendly in small screens.
Kernel should not be updated so many times.

About the community, i think that ubuntu should have a website concerned in the organization of big protest in every country around the world against the huge and unfair microsoft monopoly.

A big hug for the open source, freeware and ubuntu community.
i love your work. :)


ps: there are probably solutions for everything i said. but should be included by default.

---

### Post by MYGRA1N on 2009-03-23
> **bertolo said:**
> I think ubuntu is in a good path.
I have no doubt that in a few years linux will be more established compared with nowadays, microsoft will be doomed, mainly because of ubuntu and it's user friendly filosophy.
People should focus on improving things that are already included.

Audio drivers and graphic card drivers are awful. (180 version of graphic drivers are ok / i still got no sound output since i upgraded from 8.04 to 8.10).
The Random freeze bug while installing it's a nightmare for most of my friends.(initramfs + busybox trouble installing).
Printer, Wireless and Lan features are very very good in version 8.10.
I love gnome desktop style, wine, pidgin and compiz.
Despite of loving gnome, i have to admit that for a new user it looks too childish, and not very professional.

Ubuntu should include latest open office version by default, be prepared for more that 4gb ram and be more user friendly in small screens.
Kernel should not be updated so many times.

About the community, i think that ubuntu should have a website concerned in the organization of big protest in every country around the world against the huge and unfair microsoft monopoly.

A big hug for the open source, freeware and ubuntu community.
i love your work. :)


ps: there are probably solutions for everything i said. but should be included by default.

If you want Ubuntu to use more than 4GB of ram then use the 64bit version. All 32bit operating systems(Windows XP/2000, Ubuntu etc..) have a 4GB RAM limit.

---

### Post by 3rdalbum on 2009-03-23
Audio drivers - are you using a Creative X-Fi-based sound card? Those are horrible but slowly getting better as Creative has finally open-sourced them. Some audio problems are caused by Ubuntu's implementation of the Pulseaudio sound system, but there is a HOWTO on these forums about fixing Pulseaudio. Believe me, it's worth following (you get some useful new features and your sound will always work). I hope the Pulseaudio HOWTO is rolled into Jaunty.

Graphics card drivers are not Ubuntu's responsibility, but I'm happy that Nvidia's drivers seem to be getting better. I believe we'll also start to see open-source Nvidia drivers (the Nouveau project) in Ubuntu soon.

I use Ubuntu on a 9 inch netbook, and while there are some instances of having to alt-drag windows upwards, in general things still work pretty well on the small screen.

If you don't want to apply kernel updates, you don't have to; but unless you've got custom-build drivers it shouldn't affect you? New kernels can fix bugs and security problems and they very rarely cause any dramas, so I think it's worth updating the kernel from time to time.

One of the dangers of anti-Microsoft-monopoly websites is that they tend to become a breeding-ground for extremists and people who will twist any sort of story into a "LOOK AT WHAT EVIL MICROSOFT IS DOING NOW!" piece of FUD, like our friends at BoycottNovell.com. Besides, the best way of protesting Microsoft is by stealing all their users away from them! :-)

Anyway, I'm glad you're enjoying Ubuntu and I appreciate your comments.

---

### Post by bertolo on 2009-03-23
> **MYGRA1N said:**
> If you want Ubuntu to use more than 4GB of ram then use the 64bit version. All 32bit operating systems(Windows XP/2000, Ubuntu etc..) have a 4GB RAM limit.

in windows xp , its very easy to use more than 4gb.
i tried everything to get my audio working and still nothing. i will wait for 9.04.

i love to steal microsoft users. :)
my mother and my sister love ubuntu already.

---

### Post by Calmor on 2009-03-23
I thought it was only 64-bit Windows XP that could access more than 4GB?  In fact, Microsoft's site says that PAE (which allows access to more RAM) is only an option on Windows Server 2003 Enterprise and Datacenter editions.  I only ask because I'm curious how you access more than 4GB?

There is a 64-bit Windows XP offering, but I've never seen anyone running it - mostly Vista at this point.

---

### Post by issih on 2009-03-23
Fair enough, I know you said that you want these things included by default, and that is a separate argument, one that gets into questions of overall performance with and without pae extensions and whether 64 bit is better or not. For whatever reason, ubuntu currently ships its 32 bit desktop distro with pae off. If you want it though, there are a few options:

[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

Just grabbing the server kernel is probably the simplest, as its simply a few ticks in synaptic and you are done, suddenly all your memory is visable.

Generally though ubuntu runs beautifully in 1 gig of ram never mind more, which might explain the decisions.

Hope that helps

---

### Post by jbysmith on 2009-03-23
> **Calmor said:**
> I thought it was only 64-bit Windows XP that could access more than 4GB?  In fact, Microsoft's site says that PAE (which allows access to more RAM) is only an option on Windows Server 2003 Enterprise and Datacenter editions.  I only ask because I'm curious how you access more than 4GB?

The PAE option *is* available in XP, but the OS still has a hard coded limitation of 4GB.  Windows 2003 Server has the same limitation, depending on the edition.  Web is 2GB, Standard is 4GB, Enterprise up to 64GB, and Datacenter up to 128GB. It's just like other things that are intentionally crippled depending on what build you use, number of maximum network connection and the like for example.

[http://msdn.microsoft.com/en-us/library/aa366778.aspx](http://msdn.microsoft.com/en-us/library/aa366778.aspx)

Gotta love Microsoft.

---

### Post by Simian Man on 2009-03-23
> **bertolo said:**
> Audio drivers and graphic card drivers are awful. (180 version of graphic drivers are ok / i still got no sound output since i upgraded from 8.04 to 8.10).
...
Kernel should not be updated so many times.

You realize the kernel is responsible for drivers?  It has nothing to do with Ubuntu.


> **bertolo said:**
> Despite of loving gnome, i have to admit that for a new user it looks too childish, and not very professional.
Take a look at Fedora or OpenSuse.  Both have much more polished and professional default looks. 


> **bertolo said:**
> Ubuntu should include latest open office version by default
I agree.  Fedora has had OpenOffice 3 in the repos for ages.  Why Ubuntu doesn't package newer versions for old releases is befuddling.  One of the reasons I don't use it any more.

---

### Post by wolfen69 on 2009-03-23
> **Simian Man said:**
> Why Ubuntu doesn't package newer versions for old releases is befuddling.  One of the reasons I don't use it any more.

with that kind of thinking, ubuntu may as well go with a rolling release model. besides, doesn't canonical have enough to do without having to port every app to every previous version of ubuntu? geez people, i can't believe some of you.

if you're so smart and know everything, why don't you start your own distro? we'll see how far you get. i'm always ready for a good laugh.

---

### Post by Simian Man on 2009-03-23
> **wolfen69 said:**
> with that kind of thinking, ubuntu may as well go with a rolling release model. besides, doesn't canonical have enough to do without having to port every app to every previous version of ubuntu? geez people, i can't believe some of you.

Who said anything about "every app"?  Just big things like OpenOffice.  I mean isn't it crazy that OO3 has been out since ***October*** and isn't officially available on any current version of Ubuntu (supposedly the most popular version of Linux)?  Besides it isn't difficult to install on Ubuntu, so there are no technical difficulties.  If Fedora can manage it, why can't Ubuntu?


> **wolfen69 said:**
> if you're so smart and know everything, why don't you start your own distro? we'll see how far you get. i'm always ready for a good laugh.

Well that's OK, because I like to laugh at fan boys like you :).

---

### Post by MYGRA1N on 2009-03-23
> **bertolo said:**
> in windows xp , its very easy to use more than 4gb.
i tried everything to get my audio working and still nothing. i will wait for 9.04.

i love to steal microsoft users. :)
my mother and my sister love ubuntu already.

Wow, I didn't know that. Sorry for giving bad advice:p

---

### Post by cariboo on 2009-03-23
> I mean isn't it crazy that OO3 has been out since October and isn't officially available on any current version of Ubuntu (supposedly the most popular version of Linux)?

If you can't wait six months for a new version of some application that you use, you migh be better off with a rolling release distribution. 

Most Ubuntu users don't seem to care if the latest and greatest isn't available in the current release, they seem to be satisfied to wait for the next release. After all it's only software and nobody is going to die if it isn't included.

Jim

---

### Post by bertolo on 2009-03-23
please delete this.

---

### Post by bertolo on 2009-03-23
> 
I agree.  Fedora has had OpenOffice 3 in the repos for ages.  Why Ubuntu doesn't package newer versions for old releases is befuddling.  One of the reasons I don't use it any more.

that's not so easy.
nobody will die lol. agreed.

---

### Post by Simian Man on 2009-03-23
> **cariboo907 said:**
> If you can't wait six months for a new version of some application that you use, you migh be better off with a rolling release distribution. 

Fedora is not rolling release but still provides new packages for older releases.  I just don't get why Ubuntu doesn't do this.  I guess it just isn't intended for power users.

---

### Post by ve4cib on 2009-03-23
> **wolfen69 said:**
> with that kind of thinking, ubuntu may as well go with a rolling release model. besides, doesn't canonical have enough to do without having to port every app to every previous version of ubuntu? geez people, i can't believe some of you.

I don't think anyone would expect every single update to every single app ported to older releases.  But the "core" applications that get installed by default off the Live CD would be nice.  (For example: OpenOffice, Pidgin, and Firefox.)

If those applications are sufficiently important/fundamental to the distro that they are part of the Live Disc session and are installed automatically I think that they are worthy of some extra attention and support when it comes to updates and porting those updates back to older releases.

---

### Post by true vladimir on 2009-03-24
I'am not sure is this right place, if not please direct me to right place.
So, suggestion is before power manager puts computer to sleep to give user
chance to abort. It's easy when screen saver is activated computer comes back quickly,
but it gone sleep just when I finished my dinner and wanted to continue work.

---

### Post by 3rdalbum on 2009-03-25
> **true vladimir said:**
> I'am not sure is this right place, if not please direct me to right place.
So, suggestion is before power manager puts computer to sleep to give user
chance to abort. It's easy when screen saver is activated computer comes back quickly,
but it gone sleep just when I finished my dinner and wanted to continue work.

Truevladimir: The right place for this suggestion is [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com).

---

### Post by mdsmedia on 2009-03-25
> **ve4cib said:**
> I don't think anyone would expect every single update to every single app ported to older releases.  But the "core" applications that get installed by default off the Live CD would be nice.  (For example: OpenOffice, Pidgin, and Firefox.)

If those applications are sufficiently important/fundamental to the distro that they are part of the Live Disc session and are installed automatically I think that they are worthy of some extra attention and support when it comes to updates and porting those updates back to older releases.
So who decides which app to upgrade on a regular basis? Who decides which are the core or important apps?

To me, OOo 2.4 is fine. If you want the latest version you can install it.

I used 6.06 long after 8.04 was released. The apps were fine.

People complained that Firefox 3.x was released with 8.04, because it was in Beta, even though it was to be released within weeks of 8.04 being released. Now people complain that OOo's latest release isn't included or updated in a current Ubuntu release.

Some people just can't be pleased. You CAN download and install the latest releases of any app. You can choose not to use Ubuntu. You can choose to use a Beta or an Alpha of Ubuntu. You DO only have to wait 6 months for the next release of Ubuntu, or you CAN use its Beta before release.

Ubuntu freezes app versions for stability etc. reasons.

---

### Post by bertolo on 2009-03-25
> **mdsmedia said:**
> 
Ubuntu freezes app versions for stability etc. reasons.

ok then. it's better than upgrade a version full of problems.

---

### Post by jbysmith on 2009-03-25
> **mdsmedia said:**
> Ubuntu freezes app versions for stability etc. reasons.

Exactly, plus since they have a set schedule, they do need to cut off updates/new software at some point before release so they have time to test everything. 

As far as OpenOffice goes, Ubuntu 8.10 went into a freeze at the end of August if I recall.  OpenOffice 3 was released in mid October, well past the cutoff, around the time 8.10 was in beta.  There was just no way it could have been included in 8.10 without the possibility of some major issues.  

It's the nature of a distro with a release cycle.  It has its merits as the software is typically more stable, but not always current.  

But if you're the type that has to have constantly bleeding edge software, you may want to look into a distro that has a rolling release.  Debian Testing/Sid, Arch, and the like.. install it once and that's it.  Just keep updating, there's no dist-upgrades.  Typically get updated to current within days, but then you risk the occasional breakage which does happen occasionally on rolling release distros.  I use Arch for example; their package maintainers are pretty good at testing things out before pushing updates into the main repository, but the occasional glitch slides by; typically minor, but serious breakage is possible.  I typically check the forums/mailing lists before doing a major update just to make sure.

Third choice of course is a LTS type of release.  Ubuntu 8.04, Debian Lenny and the like.  Not bleeding edge by any means, but typically super stable, which is the primary focus of that type of release.

---

