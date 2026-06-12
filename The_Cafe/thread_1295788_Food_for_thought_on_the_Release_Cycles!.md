---
title: "Food for thought on the Release Cycles!"
date: 2009-10-19
forum: The Cafe
---

### Post by evilaim on 2009-10-19
The Ubuntu community is seemingly happy that the development team are releasing Ubuntu on a 6 month release cycle, but is this a feasible time frame to keep Ubuntu a solid Linux distribution or are they rushing too many factors just to keep up with the time limits?  Well, I've been beta testing 9.10 Beta.  It is 10 days before they are releasing it, and I'll tell you right now, this release is no where near being complete.  So, will they do what they always do, and release it on October 29th?  Of coarse, but with the issues at hand, such as the new Grub 2 beta having so many issues with compatibility, and the new Flash player for FireFox being about as stable as Charley Manson (which really isn't the Ubuntu team, but rumors said it might actually be included in 9.10, but I think that was scrapped), they will most likely just omit these new updates until 10.04.  Fully understandable, but would it not be a bit more efficient if the teams weren't constricted by time frames and releasing Ubuntu 9.10 without actually meeting the targets they set?  It seems that Ubuntu has been getting closer and closer with the amount of work that is needed and making a dash for the finish line and cutting code very close.

Would anyone really hurt from an open ended release cycle?

---

### Post by Frak on 2009-10-19
I've too thought about them just getting the thing done when it's done. Make a milestone. They want X, Y, and Z done by the next milestone. I'd rather them apply the [suckless manifesto]("http://suckless.org/manifest/") to it and make it work than to rush everything at the last minute and cause major breakage in the final product.

---

### Post by Regenweald on 2009-10-19
> **evilaim said:**
> The Ubuntu community is seemingly happy that the development team are releasing Ubuntu on a 6 month release cycle, but is this a feasible time frame to keep Ubuntu a solid Linux distribution or are they rushing too many factors just to keep up with the time limits?  Well, I've been beta testing 9.10 Beta.  It is 10 days before they are releasing it, and I'll tell you right now, this release is no where near being complete.  So, will they do what they always do, and release it on October 29th?  Of coarse, but with the issues at hand, such as the new Grub 2 beta having so many issues with compatibility, and the new Flash player for FireFox being about as stable as Charley Manson (which really isn't the Ubuntu team, but rumors said it might actually be included in 9.10, but I think that was scrapped), they will most likely just omit these new updates until 10.04.  Fully understandable, but would it not be a bit more efficient if the teams weren't constricted by time frames and releasing Ubuntu 9.10 without actually meeting the targets they set?  It seems that Ubuntu has been getting closer and closer with the amount of work that is needed and making a dash for the finish line and cutting code very close.

Would anyone really hurt from an open ended release cycle?

Indeed, lets have an open ended release structure, because there are not any users other than single machine desktop users depending on the delivery of releases. Whenever its done guys, no biggie. Lets model it after the xserver release schedule. Good stuff.

---

### Post by Frak on 2009-10-19
> **Regenweald said:**
> Indeed, lets have an open ended release structure, because there are not any users other than single machine desktop users depending on the delivery of releases. Whenever its done guys, no biggie. Lets model it after the xserver release schedule. Good stuff.
You really have to think about it:

Quickly rushed, sorta unfinished crap OR Time taken to make it less smelly crap.

---

### Post by evilaim on 2009-10-19
> **Regenweald said:**
> Indeed, lets have an open ended release structure, because there are not any users other than single machine desktop users depending on the delivery of releases. Whenever its done guys, no biggie. Lets model it after the xserver release schedule. Good stuff.

Oh, so all of a sudden, doing something in 7 months instead of 6 will completely take down all the servers in the world.  Companies aren't in need of a 6 month release cycle, they are in need of timely upgrades and updates.  Such as Mile stones could provide.  Think that if a release takes 7 months so be it, but lets not take this to extremes, I'm not saying every 10 years.  I'm saying fix what your targets are, and then release.  Is that difficult?

---

### Post by kpholmes on 2009-10-19
i heard that ubuntu was going to work with debian and try and "sync" their release each others release cycles (when possible cause debian doesn't release on a 6 month cycle) for improved stability, which sounds like a pretty good idea. 

i agree on your points, maybe larger features should be postponed until the lts versions. idk though, im not a coder/developer and dont want to start talking about something i dont really know a whole lot about. either way i like ubuntu alot.

---

### Post by AllRadioisDead on 2009-10-19
I think all the the *.04 releases should be feature releases, while all the *.10 releases should focus on improving the current release (stability, performance, etc). I know, what about the stability and performance of the *.04 releases? Well, I still think this would be better than rushing everything into 6 month cycles, and everyone ending up frustrated with something.

---

### Post by Regenweald on 2009-10-19
> **Frak said:**
> You really have to think about it:

Quickly rushed, sorta unfinished crap OR Time taken to make it less smelly crap.

> **evilaim said:**
> Oh, so all of a sudden, doing something in 7 months instead of 6 will completely take down all the servers in the world.  Companies aren't in need of a 6 month release cycle, they are in need of timely upgrades and updates.  Such as Mile stones could provide.  Think that if a release takes 7 months so be it, but lets not take this to extremes, I'm not saying every 10 years.  I'm saying fix what your targets are, and then release.  Is that difficult?

Look at it this way, all project go from hard and fast delivery targets to aim for(give or take a day or two, worst case scenario a week) to convenient milestones. how do you then package any distro ? 

Mplayer is done, but it depends on nouveau, what's up with nouveau ? few more weeks maybe, we don't really know. New boot depends on the latest xorg, when do we get it ? when it's done....

These are just some hypotheticals, but my point is, once releases go soft, it all slips and it gets very hard to put forward a contiguous release. The milestone style was being used for xserver, and it failed them(and nearly us) miserably. They have now gone to kernel type, fixed release schedule.

anyways, i kind of jumped on you, apologies.

---

### Post by evilaim on 2009-10-19
> **ihermit said:**
> I think all the the *.04 releases should be feature releases, while all the *.10 releases should focus on improving the current release (stability, performance, etc). I know, what about the stability and performance of the *.04 releases? Well, I still think this would be better than rushing everything into 6 month cycles, and everyone ending up frustrated with something.

That my friend, is a very good idea in my opinion.  I'm glad you've said that.  It makes a lot of sense.  I think cramming huge changes into 6 months really doesn't give the 'beta' time to be tested fully.  1 month Beta doesn't seem very sufficient for what Ubuntu is trying to achieve.  You've got the best idea I've heard yet!

Thanks!

---

### Post by aesis05401 on 2009-10-19
Hello, 

The people recommending changing the release cycles are not taking the distributed and community nature of Linux development into account.  A feature freeze that lasted from a 04 to an 04 release would kill a small project that missed the window - or worse - leave a full year during which the first impression of a package is the result of a madcap rush to beat the feature freeze deadline just to get into the official repos.

---

### Post by evilaim on 2009-10-19
I don't think that a 'feature freeze' would be very good either, I just suggesting that the time frames be a bit more flexible.  If the 'Marks' aren't completed, don't release.  And either way, a feature would have to rush to even make a release either way.  But I'm more concentrated on the large scales, such as Grub 2 for example.  Wait until it is stable, and then use the update-manager to update it.  That isn't difficult.

---

### Post by AllRadioisDead on 2009-10-19
> **evilaim said:**
> That my friend, is a very good idea in my opinion.  I'm glad you've said that.  It makes a lot of sense.  I think cramming huge changes into 6 months really doesn't give the 'beta' time to be tested fully.  1 month Beta doesn't seem very sufficient for what Ubuntu is trying to achieve.  You've got the best idea I've heard yet!

Thanks!
Just food for thought. :popcorn:
That's actually exactly what I was thinking, at the same time it's important for ubuntu to deliver a release every 6 months, so I kinda thought this might be a best of both worlds idea.

---

### Post by Rainstride on 2009-10-19
> **evilaim said:**
> The Ubuntu community is seemingly happy that the development team are releasing Ubuntu on a 6 month release cycle, but is this a feasible time frame to keep Ubuntu a solid Linux distribution or are they rushing too many factors just to keep up with the time limits?  Well, I've been beta testing 9.10 Beta.  It is 10 days before they are releasing it, and I'll tell you right now, this release is no where near being complete.  So, will they do what they always do, and release it on October 29th?  Of coarse, but with the issues at hand, such as the new Grub 2 beta having so many issues with compatibility, and the new Flash player for FireFox being about as stable as Charley Manson (which really isn't the Ubuntu team, but rumors said it might actually be included in 9.10, but I think that was scrapped), they will most likely just omit these new updates until 10.04.  Fully understandable, but would it not be a bit more efficient if the teams weren't constricted by time frames and releasing Ubuntu 9.10 without actually meeting the targets they set?  It seems that Ubuntu has been getting closer and closer with the amount of work that is needed and making a dash for the finish line and cutting code very close.

Would anyone really hurt from an open ended release cycle?

a VERY large number of people would be hurt by this. that and the 6 month cycles serve to keep people interested. if they think theres nothing getting done, they will leave. besides, if you have a problem with stability, use 8.04, and don't upgrade till it hits end of life. then the same for that lts.

> **Frak said:**
> You really have to think about it:

Quickly rushed, sorta unfinished crap OR Time taken to make it less smelly crap.

8.04 = stability
9.10 = newest and still in progress

the lts is meant for people who want stability, if you upgrade to 9.10(especialy when it is still in RC) expect at least a couple problems.

> **ihermit said:**
> I think all the the *.04 releases should be feature releases, while all the *.10 releases should focus on improving the current release (stability, performance, etc). I know, what about the stability and performance of the *.04 releases? Well, I still think this would be better than rushing everything into 6 month cycles, and everyone ending up frustrated with something.

i will direct you to the answer to the quote above.

---

### Post by Frak on 2009-10-19
Why can't we make one just SUPER MEGA AWESOME release like Microsoft did with XP. That things been around for nearly a decade, but almost all software that exists actively supports it.

I'm glad people are going with the "half-year to keep things interesting", but again, I'd rather have a good release than one that feels rushed. A release every 6 months that feels rushed is not comparable to a good software product.

---

### Post by lovinglinux on 2009-10-19
> **Rainstride said:**
> a VERY large number of people would be hurt by this. that and the 6 month cycles serve to keep people interested. if they think theres nothing getting done, they will leave. besides, if you have a problem with stability, use 8.04, and don't upgrade till it hits end of life. then the same for that lts.

8.04 = stability
9.10 = newest and still in progress

the lts is meant for people who want stability, if you upgrade to 9.10(especialy when it is still in RC) expect at least a couple problems.

+1

Besides, try to explain to the angry mob why they can get the latest Firefox release or other popular applications. We had already enough threads and posts complaining about Shiretoko and asking when the "new" Firefox would be available in the repositories, just after Firefox 3.5 release. So try to explain they have to wait a year to get the latest applications running by default...

---

### Post by Ocxic on 2009-10-19
Ubuntu has a great devolpment cycle I'm suporised that no one has mentioned LTS releases.

The LTS releases are for those people/businesses that need a stable reliable system to work with, and are supported and updated for 3-5 years depending if you have the desktop or server respectively. 
As well as a new LTS every 2 years. the 6 month development cycle allows for a fast, intriguing, and bleeding edge software to be tested and integrated into Ubuntu, and people like me and you who update every 6 mos. are the testers, and debuggers.

The 6 month release cycle is great if you that worried about stability then stick with the LTS releases.

---

### Post by Rainstride on 2009-10-19
> **Frak said:**
> Why can't we make one just SUPER MEGA AWESOME release like Microsoft did with XP. That things been around for nearly a decade, but almost all software that exists actively supports it.

I'm glad people are going with the "half-year to keep things interesting", but again, I'd rather have a good release than one that feels rushed. A release every 6 months that feels rushed is not comparable to a good software product.

if i didn't know any better i would say you are trolling. trolling REALLY hard.

that "SUPER MEGA AWESOME" release sucked harder than anything when it first came out. its full of security bugs to this day. still sucks in fact.

---

### Post by Rainstride on 2009-10-19
> **Ocxic said:**
> Ubuntu has a great devolpment cycle I'm suporised that no one has mentioned LTS releases.

you did not read the whole thread:).

---

### Post by aysiu on 2009-10-20
> **ihermit said:**
> I think all the the *.04 releases should be feature releases, while all the *.10 releases should focus on improving the current release (stability, performance, etc). I know, what about the stability and performance of the *.04 releases? Well, I still think this would be better than rushing everything into 6 month cycles, and everyone ending up frustrated with something. When I proposed that on Brainstorm, I got voted way down:
[Idea #133: Formalize the focus of fall and spring releases](http://brainstorm.ubuntu.com/idea/133/)

---

### Post by AllRadioisDead on 2009-10-20
> **aysiu said:**
> When I proposed that on Brainstorm, I got voted way down:
[Idea #133: Formalize the focus of fall and spring releases]("http://brainstorm.ubuntu.com/idea/133/")
I actually like the idea a lot, I guess people are just comfortable with the way things are then.

[quote=aysiu]Why would that be disastrous? I would love to have a "boring, uneventful" release that's stable. And then the cutting edge folk could have the "buggy/unreliable" ones. Frankly, with this proposed release cycle, the "buggy/unreliable" one wouldn't be any more buggy or unreliable than both of our current releases each year. [/quote]
What if there were two development branches? One Stable, and one Bleeding edge?
Kind of like what [URL="http://www.phpbb.com/community/viewtopic.php?f=14&t=1715935"]phpbb has recently taken up.
[/URL] Just thinking out loud.:popcorn:

---

### Post by Frak on 2009-10-20
> **Rainstride said:**
> if i didn't know any better i would say you are trolling. trolling REALLY hard.

that "SUPER MEGA AWESOME" release sucked harder than anything when it first came out. its full of security bugs to this day. still sucks in fact.
XP has had the largest market share for the longest time considering OS's. Something can be learned from that.

I have a valid point, and you know it.

> **The YerATroll.**  YerATrolls are those whining forumites who devote a tremendous amount of time and energy complaining about the tremendous amount of time an energy expended by Troll Bashers and Angry Forumites on the practice of troll-hunting. A self-righteous and hypocritical breed, YerATrolls spend all their time pointing fingers at everyone but trolls, petulantly demanding that their opinions be granted the significance the YerATroll believes they deserve. YerATrolls often start threads excoriating others for troll-hunting, all the while completely oblivious to the fact that they're engaging in trolling by picking fights with everyone else. One of the most ill-tempered of troll species, YerATrolls are characterized by a childish need for attention disguised as cynical nobility and pretensions of being "above it all."

[http://ubuntuforums.org/showthread.php?p=1032102](http://ubuntuforums.org/showthread.php?p=1032102)

---

### Post by AllRadioisDead on 2009-10-20
> **Frak said:**
> XP has had the largest market share for the longest time considering OS's. Something can be learned from that.

I have a valid point, and you know it.
Isn't that what the LTS is for though?

---

### Post by Frak on 2009-10-20
> **ihermit said:**
> Isn't that what the LTS is for though?
Like LTS, but supported with updates every-so-often to the core system. Go from security and stability patches only to security, stability, and stable build updates. Put out a version of Firefox 3.5 that is stable.

---

### Post by Icehuck on 2009-10-20
I would love to see LTS releases be in development for 1 to 2 years with support for up to 7 years. If you really want a business to commit to your product then you are going to have to give them a stable platform to develop on for a few years.  

Three years of support is barely enough time to implement new systems for large corporation use. Hell, the last company I worked for took 1 year to upgrade all the older servers to new platforms.

---

### Post by Frak on 2009-10-20
> **Icehuck said:**
> I would love to see LTS releases be in development for 1 to 2 years with support for up to 7 years. If you really want a business to commit to your product then you are going to have to give them a stable platform to develop on for a few years.  

Three years of support is barely enough time to implement new systems for large corporation use. Hell, the last company I worked for took 1 year to upgrade all the older servers to new platforms.
I agree.

There's a mass multitude of systems where I work, servers and workstations. If we were using Ubuntu LTS, we would be halfway through the cycle already before the entire upgrade would be complete.

We use RedHat because it's nearly supported until the end of time.

---

### Post by SomeGuyDude on 2009-10-20
"Keep people interested"? Like if Ubuntu didn't update every six months no one would use it? People would uninstall it?

Ubuntu seems to entertain the notion that they'll break into the mainstream of OS's, and elevate to a level of Windows and OSX. Win7 is coming out three years after Vista and the world said that was proof that MS is admitting Vista was bad. OSX 10.5 was in 2007 and 10.6 was two months ago, they haven't even moved from 10 to 11 in the past ten years.

My point is that the "mainstream" computer user doesn't want a full upgrade of their system every six months. I've done tech on people's PC's that have NEVER run Windows Update. Not that long ago I had to help someone with a pre-SP2 version of XP. Linux users are more adventurous (it's how we got into Linux, after all) in a way that most non-Linux users aren't. I know lots of XP users who stuck with XP just because it worked and they didn't want to chance it.

What most people are looking for is a system that's reliable, and full system upgrades every six months do not scream "reliability" to the masses. It means the OS is constantly in motion and never "rests". OSX's complete lack of real motion sends the message that OSX is a complete product. The "only three years" between Vista and 7 struck many as proof that MS was scrambling to get away from Vista.

Imagine pre-installed Ubuntu becomes widespread. Do you realize that with the six-month release cycle, it's an inevitability that TONS of people are going to take their computers home and as soon as they plug it in they'll get a message that there's a whole new version of Ubuntu out? A computer pops off the assembly line in May with a brand new Jaunty on it, lands on Best Buy's lot in June, and in late September it finally gets bought by someone. Then a few weeks later they have to do a full system upgrade. Confident? Hardly.

EDIT: and semi-ninja'd by the above poster. The upgrade process for any large number of computers would become a nightmare. By the time you get all the kinks worked out of everyone's machine there'd be a new version already. At least IT guys would always have a job.

---

### Post by Icehuck on 2009-10-20
I forgot to also point out that my company won't upgrade to a new OS the first year it comes out. They will do about a year of testing on the OS to ensure stability and security.

---

### Post by 23meg on 2009-10-20
[QUOTE=SomeGuyDude]A computer pops off the assembly line in May with a brand new Jaunty on it, lands on Best Buy's lot in June, and in late September it finally gets bought by someone. Then a few weeks later they have to do a full system upgrade[/QUOTE]

No, they don't have to.

---

### Post by lovinglinux on 2009-10-20
> **23meg said:**
> No, they don't have to.

I have bought a notebook for my mother with Mandriva installed about two years ago. By that time, I was still a Windows user, so I have installed Windows XP over it as soon as I got home. A couple of months later I decided to install Ubuntu for her, since I had recently installed it for me. Unfortunately, I wasn't able to install Ubuntu because of some hardware incompatibility, due to motherboard tampering by the manufacturer (to get the Vista certification). The only Linux OS that I was able to install was the Mandriva from the rescue CD. So I tried that, but I wasn't able to upgrade, update or even install a single application, because the version wasn't supported anymore and wasn't experienced enough to figure out how to do it manually.

I don't know if Ubuntu would ask the user to upgrade if the version installed is not even supported anymore, but in the case with Mandriva I was pretty much screwed.

I also have a friend who bought a netbook with a Linux OS based on Ubuntu and the repository wasn't available anymore. I'm not sure if it actually use the Ubuntu repository, because I couldn't make it update by just giving instructions by IM (she lives on another town). Anyway, she bought it for traveling to Europe for a few months but end up leaving it at home and took the Windows laptop with her, because she couldn't even install emesene.

Since then, I have been noticing this OS, which is really bad BTW, being sold with notebooks on local supermarkets. So I wonder how would be the first impression about Linux for those who buys them.

---

### Post by adeypoop on 2009-10-20
Haven't read the whole thread so apologies if I'm repeating. I like the current model of a 6 month release cycle. If something is not ready in time, no need to postpone for X number of months waiting for it. Why should one module hold everything up? Take the example of the ext 4 file system, it wasn't part of the last release but will be in the next one. Its no big deal to wait for the next release or you can install from the repos if a feature is ready before the release. It ain't broke and don't need fixing. 

Comparisons to Windows and OSX are not relevant, they are closed source projects and a totally different kettle of fish to linux.

---

### Post by 3rdalbum on 2009-10-20
I'm a big fan of the idea of "give another eight weeks for LTS releases". Everything up until the (first) beta is exactly the same, but then have a long bugfix cycle.

Contrary to what the OP said, things are really shaping up in Karmic. My system is just as stable as it's ever been. Really, the only two things I want changed are: I want the "file-roller drag-to-nautilus causes crash" fix brought into the Ubuntu packagfes, and I think the Flash Plugin package on 32-bit should be fixed. Oh, and I want AAC built into libav again, but I understand that this is a licensing issue.

---

### Post by Tmi on 2009-10-20
As the previous speaker I haven't read it all and thus apologize if I'm repeating.

I'm quite fine with the release cycle - as long as you are aware of the potential problems it might bring it should be no problem. If you worry about initial buggyness due to rushing then just wait a month or so until most of it has been fixed. If you update a month or two out of sync it's pretty much like upgrading between stable versions on the same release cycle.

Of course thats not a working solution if your concern is the overall image that new users might get if they upgrade to a rushed release.

---

### Post by Gwasanaethau on 2009-10-20
Whilst I agree in essence with the idea of this thread (that is, I feel that the Ubuntu releases are rushed), I must point out that there are many other distributions that have flexible (or even rolling) release cycles. Ubuntu was set up to provide a new release every six months, and I think it's great that way (though if there are fairly important problems, then the release should be delayed for a short time). The newest releases tend to have new software that isn't available in any of the other distributions, and I look forward to seeing whatever's in the newest release. However, of late, I've needed to use something a little more stable, and as I couldn't get Hardy to work exactly the way I liked it, I tried out Arch (with its rolling release). However, every time a new Ubuntu release comes out, I have a good look at it and see what kind of nice stuff it has. ;)

That said, I believe the LTS releases really do need to be more of a consolidation of the previous releases (i.e. the end of a complete release cycle), with the following non-LTS release being the big one for bringing in all the new features, giving plenty of time to test for the next LTS. Each intervening release should still bring in new features, as that's what the community likes most, but they should be stabilised as much as possible by the LTS! LTS need not be bleeding edge, but it must be usable!

Just personal opinion, I really don't mind at all what (if anything) happens to the release cycle. ;)

---

### Post by K.Mandla on 2009-10-20
Perhaps I am in a minority, but I rather like the six-month system. I was under the impression the releases were paced because Debian at the time (if I remember right) had a "when it's ready" release schedule that didn't appeal to many people. Would Debian's release style qualify as a SUPER MEGA RELEASE?

Anyway, I don't know if you can really keep everyone happy with any release schedule at all. It seems like any time a release is slated, people want to know if Firefox 7.44 or Gnome 8.22.4 or KDE 3.14159 are going to be included. Something is always just over the horizon, and everybody always wants it.

The only way around that, as far as I know, is to go with a rolling release. Like ...

oh no, here it comes ...

Arch Linux! :lol:

Okay, that last part was just for fun. I apologize. Please continue. ;)

---

### Post by Xbehave on 2009-10-20
I don't think the 6month part needs to be changed but, if a release isn't ready keep working at it for a few more weeks and make it more stable. People are jumping to extremes here, thinking we would end up like debian but:
1) ubuntu has already held releases back when necessary, this is just suggesting doing this whenever a release isn't ready
2) Other 6month distros do this already, Fedora 11 was delayed significantly because it was not ready

As for windows/mac os X cycles, they generally update every 2-4 years, which is not unlike using LTS and slightly longer than holding on to non-LTS's (1.5 years)

---

### Post by longtom on 2009-10-21
As an LTS user for my mission critical machines, I like the 6 months cycle.  I mean - how many beta tester can one have?  And all tested in real live environment.  Great.

Having said that, I don't think the way the LTS editions are handled is as good as it could be.

There could be a sort of a delayed rolling release.  Not quite bleeding edge - but also not being offered OO 2.4 until 2011 (or whenever Hardy expires).
I reckon that applications could be upgraded in the repository once they are in circulation for a certain amount of time (3 months, 6 months..?) and they have proofed their worth.

---

### Post by NCLI on 2009-10-21
> **Frak said:**
> I agree.

There's a mass multitude of systems where I work, servers and workstations. If we were using Ubuntu LTS, we would be halfway through the cycle already before the entire upgrade would be complete.

We use RedHat because it's nearly supported until the end of time.
This is definitely a problem, but one that will hopefully be fixed when Canoniocal gets more resources and can afford to keep support for the LTS' going longer.
> **SomeGuyDude said:**
> "Keep people interested"? Like if Ubuntu didn't update every six months no one would use it? People would uninstall it?

Ubuntu seems to entertain the notion that they'll break into the mainstream of OS's, and elevate to a level of Windows and OSX. Win7 is coming out three years after Vista and the world said that was proof that MS is admitting Vista was bad. OSX 10.5 was in 2007 and 10.6 was two months ago, they haven't even moved from 10 to 11 in the past ten years.

My point is that the "mainstream" computer user doesn't want a full upgrade of their system every six months. I've done tech on people's PC's that have NEVER run Windows Update. Not that long ago I had to help someone with a pre-SP2 version of XP. Linux users are more adventurous (it's how we got into Linux, after all) in a way that most non-Linux users aren't. I know lots of XP users who stuck with XP just because it worked and they didn't want to chance it.

What most people are looking for is a system that's reliable, and full system upgrades every six months do not scream "reliability" to the masses. It means the OS is constantly in motion and never "rests". OSX's complete lack of real motion sends the message that OSX is a complete product. The "only three years" between Vista and 7 struck many as proof that MS was scrambling to get away from Vista.

Imagine pre-installed Ubuntu becomes widespread. Do you realize that with the six-month release cycle, it's an inevitability that TONS of people are going to take their computers home and as soon as they plug it in they'll get a message that there's a whole new version of Ubuntu out? A computer pops off the assembly line in May with a brand new Jaunty on it, lands on Best Buy's lot in June, and in late September it finally gets bought by someone. Then a few weeks later they have to do a full system upgrade. Confident? Hardly.

EDIT: and semi-ninja'd by the above poster. The upgrade process for any large number of computers would become a nightmare. By the time you get all the kinks worked out of everyone's machine there'd be a new version already. At least IT guys would always have a job.
The solution is extraordinarily simple: The manufacturers should install LTS', and make sure the default setting is to wait for the next LTS before prompting the user to upgrade. That means two years between every upgrade, plenty of time to give a sense of stability.

---

### Post by gn2 on 2009-10-21
> **evilaim said:**
> ~ are they rushing too many factors just to keep up with the time limits?  ~


Do you remember why 6.06 wasn't 6.04?

AFAIK the release dates are not set in stone and can be changed if required.

---

### Post by cascade9 on 2009-10-21
> **K.Mandla said:**
> Perhaps I am in a minority, but I rather like the six-month system. I was under the impression the releases were paced because Debian at the time (if I remember right) had a "when it's ready" release schedule that didn't appeal to many people. Would Debian's release style qualify as a SUPER MEGA RELEASE?

Anyway, I don't know if you can really keep everyone happy with any release schedule at all. It seems like any time a release is slated, people want to know if Firefox 7.44 or Gnome 8.22.4 or KDE 3.14159 are going to be included. Something is always just over the horizon, and everybody always wants it.

The only way around that, as far as I know, is to go with a rolling release. Like ...

oh no, here it comes ...

Arch Linux! :lol:

Okay, that last part was just for fun. I apologize. Please continue. ;)

Debian **STABLE** is always 'when its ready'. If your after new software, deb stable is not for you. Testing is pretty much a rolling release, freezing when its moving to stable, and Sid is rolling release.

---

### Post by snowpine on 2009-10-21
> **evilaim said:**
> The Ubuntu community is seemingly happy that the development team are releasing Ubuntu on a 6 month release cycle, but is this a feasible time frame to keep Ubuntu a solid Linux distribution or are they rushing too many factors just to keep up with the time limits?  Well, I've been beta testing 9.10 Beta.  It is 10 days before they are releasing it, and I'll tell you right now, this release is no where near being complete.  So, will they do what they always do, and release it on October 29th?  Of coarse, but with the issues at hand, such as the new Grub 2 beta having so many issues with compatibility, and the new Flash player for FireFox being about as stable as Charley Manson (which really isn't the Ubuntu team, but rumors said it might actually be included in 9.10, but I think that was scrapped), they will most likely just omit these new updates until 10.04.  Fully understandable, but would it not be a bit more efficient if the teams weren't constricted by time frames and releasing Ubuntu 9.10 without actually meeting the targets they set?  It seems that Ubuntu has been getting closer and closer with the amount of work that is needed and making a dash for the finish line and cutting code very close.

Would anyone really hurt from an open ended release cycle?

1. Unfair to base your conclusion on a "beta" release... it is not supposed to be "perfect" yet. :)
2. Have you tried Debian Stable (currently Lenny)? I think you would really like it (based on your post).

---

