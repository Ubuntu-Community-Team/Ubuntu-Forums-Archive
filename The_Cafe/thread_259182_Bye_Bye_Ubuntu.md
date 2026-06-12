---
title: "Bye Bye Ubuntu"
date: 2006-09-17
forum: The Cafe
---

### Post by hearnden on 2006-09-17
Well, I'm leaving Ubuntu for another distro, or perhaps Mac OS.

Why?  Because of the lack of regression testing in the updates, and lack of contemporary hardware support.

The xserver-xorg update hosed my machine last month, and it was pretty hard to recover from something that kills your interface.    And no, I can't use the Live CD, because Ubuntu hasn't caught up with my hardware (JMicron PATA controller).

The latest kernel updates have been more problematic.  Not only did it hose the 2.6.15.26 kernel, but also the other 2.6.15.23 'safe' kernel I had.  I don't know how it did it, but somehow all my initrd's are broken, and booting any of them results in a Kernel Panic while trying to mount the root file system.  It's not my file system that's the problem, because if I use the initrd from my laptop (copied onto a USB flash drive), it boots ok: so it's something to do with the initrd and the kernel modules.  I'm presuming the latest update fiddled with something outside of /lib/modules/<version>, because it must be common to all my kernels.  Maybe it broke mount?   I don't really care anymore.  I've tried everything short of a complete reinstall - I've upgraded, downgraded, purged, reinstalled kernels, but all the initrds that get made are broken.

Just boot from the Live CD or reinstall I hear you say?  I would, but Ubuntu can't read my DVD drive because it can't work the JMicron PATA controller!  It was a huge ordeal to get it installed in the first place (had to install using my laptop and an external hard drive enclosure), and I'm not going through that again.

A non-reversible update without tight regression testing is a recipe for disaster, and it appears that the Ubuntu team is not learning from these mistakes.  Or maybe I just have unrealistic expectations about Ubuntu working with new hardware.

---

### Post by aysiu on 2006-09-17
I hope you find what works for you.

---

### Post by coastdweller on 2006-09-17
This is a rant, nothing else.

Doesn't seem to be in the right forum.

> **hearnden said:**
> Well, I'm leaving Ubuntu for another distro, or perhaps Mac OS.

Why?  Because of the lack of regression testing in the updates, and lack of contemporary hardware support.

The xserver-xorg update hosed my machine last month, and it was pretty hard to recover from something that kills your interface.    And no, I can't use the Live CD, because Ubuntu hasn't caught up with my hardware (JMicron PATA controller).

The latest kernel updates have been more problematic.  Not only did it hose the 2.6.15.26 kernel, but also the other 2.6.15.23 'safe' kernel I had.  I don't know how it did it, but somehow all my initrd's are broken, and booting any of them results in a Kernel Panic while trying to mount the root file system.  It's not my file system that's the problem, because if I use the initrd from my laptop (copied onto a USB flash drive), it boots ok: so it's something to do with the initrd and the kernel modules.  I'm presuming the latest update fiddled with something outside of /lib/modules/<version>, because it must be common to all my kernels.  Maybe it broke mount?   I don't really care anymore.  I've tried everything short of a complete reinstall - I've upgraded, downgraded, purged, reinstalled kernels, but all the initrds that get made are broken.

Just boot from the Live CD or reinstall I hear you say?  I would, but Ubuntu can't read my DVD drive because it can't work the JMicron PATA controller!  It was a huge ordeal to get it installed in the first place (had to install using my laptop and an external hard drive enclosure), and I'm not going through that again.

A non-reversible update without tight regression testing is a recipe for disaster, and it appears that the Ubuntu team is not learning from these mistakes.  Or maybe I just have unrealistic expectations about Ubuntu working with new hardware.

---

### Post by HowardMM on 2006-09-17
I am in a similar position. I believed all the hype that ubuntu was something easy to instal and a real alternative to the M$. sadly after wasing a weekend on trying to instal it unsucessfully (didnt even even get to first base!) I feel that I have been ripped off not in a $ sense but claims made by ubuntu community. I have now rebooted my xp machine effortlessly and have gone back to business as usual, with a greater determination not to believe the geeks that a serious alternative to windows which can be installed by the lay person exists..farewell!!

---

### Post by wieman01 on 2006-09-17
> **coastdweller said:**
> This is a rant, nothing else.

Doesn't seem to be in the right forum.
No, he is not. He has got a point. Ubuntu's update process has been out of control for a while. The forum is full of similar posts. This kind of thing to me once (!) until I disabled automatic updates and "pinned" my kernel version.

So I understand his frustration. Ubuntu should learn from that (I like it nonetheless).

---

### Post by Lord Illidan on 2006-09-17
Somehow, I find I am in a similar position to the OP. Not to the person above me :  	
> 
I am in a similar position. I believed all the hype that ubuntu was something easy to instal and a real alternative to the M$. sadly after wasing a weekend on trying to instal it unsucessfully (didnt even even get to first base!) I feel that I have been ripped off not in a $ sense but claims made by ubuntu community. I have now rebooted my xp machine effortlessly and have gone back to business as usual, with a greater determination not to believe the geeks that a serious alternative to windows which can be installed by the lay person exists..farewell!!

as I believe that there is a serious alternative to windows...but I have a feeling that updates are not being tested as thoroughly as they should be. Posts are cropping up everywhere about kernel upgrades and the xserver-xorg debacle. I myself am experiencing the "cannot mount root" error in Ubuntu Dapper..and thanks to that I am now in Fedora.

Such a great distro should test its upgrades more. Let's be frank, if Microsoft released an update that didn't allow you to login or didn't boot, we would all be over it, screaming for blood. Why should Ubuntu be any different?

---

### Post by wieman01 on 2006-09-17
This supports "Lord Illidan's" and my statement:

[http://www.ubuntuforums.org/showthread.php?t=259245]("http://www.ubuntuforums.org/showthread.php?t=259245")

Actually this isn't fun because Ubuntu is on the verge of becoming a serious alternative to Windows. But if this continues it will put its credibility at stake and eventually lose market share.

---

### Post by Timal on 2006-09-17
wieman01

Am curious about your "...I disabled automatic updates and "pinned" my kernel version..." comment.

Reason?
Two wks ago motherboard dies big time, xp [for whatever reason] decides to waste a few 'crucial' [and BIG] info repositories in my docs&settings. 15yrs online biz life at this point became dead. Yes..... backups are sooo important and I have well and trully learned my lesson! [what a chump...]

So, I build new box, salvage what can from xp hd's.

Now start looking at all distros.
Nightmare... as such varying degrees of install complexity/user input requirements. Complexity leading all way up to OpenSUSE 10.1 [did net install - many hours!].
So I [again] do Dapper live CD and [of course] got blown away by smooth and effortless install - ie, near as damn it no user inputs needed...

I want to go 100percent xnix work setup... BUT your comment along with what others have said in this thread - well, gets me edgy regards stability!

PLEASE explain your comment because my install 'just appears' to work for me and not interested in messing about with upgrade issues.

A biz OS needs 'at least' to be stable and predictable, yes?

Could you also detail HOW to lock down my existing kernal [+other areas if needed?] setup???

BTW - what about security issues if disable updates?

I installed firestarter and unsure if need AntiVirus.

Many Thanks

---

### Post by wieman01 on 2006-09-17
Hello Timal, 

The only updates I left enabled are the security patches. Tell you what, I'll open another thread & try not to hijack this one. Get back to you in a minute.

Security patches/updates have not been an issue so far, thanks for that.

---

### Post by Timal on 2006-09-17
Thanks wieman01
Hope have not gone too far off topic [please say if I have and then I'll learn (hopefully -lol)]. It's just that so many things are going on at moment attempting to rebuild online life.. See a thread and get excited/worried/curious[always!]

---

### Post by coastdweller on 2006-09-17
It has since been moved from the forum it was posted to. It was off-topic when originally posted.

> **wieman01 said:**
> No, he is not. He has got a point. Ubuntu's update process has been out of control for a while. The forum is full of similar posts. This kind of thing to me once (!) until I disabled automatic updates and "pinned" my kernel version.

So I understand his frustration. Ubuntu should learn from that (I like it nonetheless).

---

### Post by nalmeth on 2006-09-17
#-o
ahh, you'll be back 
:biggrin:

---

### Post by Lord Illidan on 2006-09-17
So is anything being moved to counteract this trend? Dapper is supposed to be a LTS distro..if anything the updates do not prove this.

If Dapper cannot be maintained adequately and it's only a few months old, how will it be maintained 1 year more, when other distros are being worked on?

---

### Post by jdong on 2006-09-17
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

There is now a very strict procedure for introducing updates into stable releases in response to these update blunders.


To be perfectly honest, Dapper's LTS status (i.e. accepting bugfixes) has made it more **prone** to update breakages than other releases.


And also, let's be fair. Some of the problems described are not caused by the two updates. These few weeks I've heard quite a number of things blamed on the updates (grub errors, grub prompt, disappearing hard drives, weird looking fonts, and so on), but that simply is not accurate.

The first update failure ONLY causes a "No Screens Found" error starting X, and the second update only affects the -26 kernel (it does not even touch the -23 kernel), and causes nvidia/fglrx users to also get No Screens Found.

---

### Post by Bloodfen Razormaw on 2006-09-17
Mac OS X is far, far worse than Ubuntu with stability problems.  Not to mention how bad OS X usability is.  I'd suggest that if Ubuntu isn't working, try another distro that does more testing, e.g. Debian.  Debian testing will be as (if not more) up to date, but with excellent, strict testing.  And since Ubuntu is derived from Debian you won't need to learn new tools.

---

### Post by aysiu on 2006-09-17
> **HowardMM said:**
> I have now rebooted my xp machine effortlessly and have gone back to business as usual, with a greater determination not to believe the geeks that a serious alternative to windows which can be installed by the lay person exists..farewell!! If, in fact, people in the Ubuntu community told you that Ubuntu was to be installed by laypeople, you were definitely misinformed.

I wouldn't have laypeople installing Windows themselves either. Laypeople should always stay with what's preinstalled or installed for them.

That said, if you ever feel the urge to come back to Linux, I would recommend Mepis or PCLinuxOS instead of Ubuntu. Ubuntu's emphasis is on free software (for example, you have to install Flash and Java yourself), and it can still be very terminal-dependent for setup (for example, to mount your Windows partitions with the correct permissions, it's very likely you'll have to edit your /etc/fstab file).

Mepis and PCLinuxOS target ex-Windows users specifically, include proprietary software and codecs Windows users are used to having, and provide GUI frontends for things Ubuntu does not (well, at least Mepis does--I'm not too sure about PCLinuxOS on that one).

In any case, sorry people sold you the wrong bill. It's too bad they unstickied my [Is Ubuntu for You?](http://ubuntuforums.org/showthread.php?t=63315) thread.

---

### Post by spockrock on 2006-09-17
sorry but if you dont think ubuntu is up to date with your hardware, but the advantage of Mac OSX is the hardware is very strict, so yeah and I am assuming you have a new nice core duo 2 setup, with that jmicron pata controller, that you spent a good deal of money on that setup, and now gonna spend probably another 2k for a Mac for the exact same hardware.

I mean the easist solution I think is to use a pata to sata converter on your optical drive and install ubuntu update to a supported kernel and give it a shot.  Its alot cheaper then getting rid of that nice core duo 2 computer only to get the same thing for an OS.

I dunno if you were planning on getting a Macpro or just gonna try to hack osx to run on a pc, but OSX is worse for hardware compatibility, I think since the hardware is very controlled on apple machines.

---

### Post by jdong on 2006-09-17
The JMicron PATA controller is VERY new hardware -- and unfortunately its Linux support isn't stellar yet. I had the same problem with my Promise PATA controller when I first built my AMD64 (Ubuntu Hoary days).

---

### Post by jimmygoon on 2006-09-17
Ubuntu is not perfect. Stop expecting it to be. It is a better alternative to Windows. You guys can not honestly tell me that you have more problems with Linux's updates than you do with Window's update. **Note:** you may not know how to fix them as easily, but that is no the fault of ubuntu. Fixing that xorg problem was much easier than recovering hours of work that goes deleted when xp decides to randomly reboot. Tell me how to "solve" that one.

This is another case (as with the 3rd poster in this thread too [the one with only one post]) of a xp "poweruser" expecting to be able to dominate linux and upon being hit with one challenge gets defensive and blames the software.

You are looking for the wrong thing in Ubuntu and I guarentee you won't find it in XP either.

---

### Post by maniacmusician on 2006-09-17
people should be educated about linux instead of being harrassed. I know you're good intentioned, but still. The guy just needs to learn how to use a terminal-based web browser. Several people did that and used these fabulous forums to fix the xorg problem.

also, his post was not pointless...we **did** have problems with our updates. Our system wasn't working right. this is obvious, especially since it's being revamped, as jdong pointed out. All OS's have their fault, but that's life.

But at the same time, I don't agree with the OP in the sense that ubuntu should be abandoned because of these kinds of problem. Does he think other distros will be better? hell, most of them will be harder. he'll find himself missing sudo apt-get. going back to windows is even worse...and OSX, he would have to buy new hardware for that if he wants the same level of performance. Sure, Ubuntu's got issues but as you can clearly see, they're being worked on. 


ps. for a terminal based web browser, i'd recommend links

---

### Post by hearnden on 2006-09-17
> **jdong said:**
> [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

The first update failure ONLY causes a "No Screens Found" error starting X, and the second update only affects the -26 kernel (it does not even touch the -23 kernel), and causes nvidia/fglrx users to also get No Screens Found.

For the xserver-xorg failure, I was in the unfortunate situation that I had also just upgraded my BIOS, and so I was convinced that the problem had to be caused by a Taiwanese hardware company who only cares about testing on Windows.  It never occured to me that the semi-automatic update process of the Linux distro that is supposed to be as easy-to-use and as dumbed-down as possible could have been the cause.  I know I wasn't the only one who investigated many other possibilities before thinking that an Ubuntu upgrade caused the problem.

As for the second update, I know it doesn't touch anything in /lib/modules/2.6.15.23/..., but the initrd image contains many other things besides kernel-version-specific stuff, and I'd like to investigate more about what that upgrade did, but alas, without access to Linux and dpkg-deb etc, I went no further.

And using a capitalised ONLY does not diminish the severity of the xserver-xorg blunder.  I switched to Ubuntu from Red Hat then  SuSE and Solaris because I did not want to have to deal with these kind of issues.  The point I was making is that the only thing going for Ubuntu (and it is certainly a very valuable thing, if attainable) is ease-of-use and getting closer to the *it just works* phenomenon.  Imagine that: all the things you love about Linux without any of the dramas! However two major failures introduced via the update mechanism in a short interal severely tarnish that image, and it has been enough to make me seriously look elsewhere.

---

### Post by hearnden on 2006-09-17
> **spockrock said:**
> sorry but if you dont think ubuntu is up to date with your hardware, but the advantage of Mac OSX is the hardware is very strict, so yeah and I am assuming you have a new nice core duo 2 setup, with that jmicron pata controller, that you spent a good deal of money on that setup, and now gonna spend probably another 2k for a Mac for the exact same hardware.


Close but not really.  I wasn't going to buy a Mac, I was going to spend just as much time testing to see how Mac OS X (and the various hacks for using non-Mac hardware) liked my hardware as I have spend fiddling with Ubuntu.  My main motivation for looking at OSX is how much so many people rave about it.

> 
I mean the easist solution I think is to use a pata to sata converter on your optical drive and install ubuntu update to a supported kernel and give it a shot.  Its alot cheaper then getting rid of that nice core duo 2 computer only to get the same thing for an OS.


Thanks for the PATA->SATA suggestion, I'll investigate some more, although I've read some people with my mobo (Asus P5B) have tried that without success.  I'm not considering buying a new machine.

> 
I dunno if you were planning on getting a Macpro or just gonna try to hack osx to run on a pc, but OSX is worse for hardware compatibility, I think since the hardware is very controlled on apple machines.

It is, but just as with Linux, there are plenty of people willing to try and hack it for new non-Mac hardware and publish their findings.

However the most realistic alternative for me right now is (apart from XP, which unfortunately I haven't been able to fault on my new PC yet), is Debian.

---

### Post by GuitarHero on 2006-09-17
Can we have the mods immediatly close these threads from now on?  Not to be rude but I don't think anyone cares you're leaving.  We all wish you the best but theres no reason for everyone leaving ubuntu to make a thread about it.  As if switching distros gives them some credential to preach to us about whats wrong with ubuntu.

---

### Post by maniacmusician on 2006-09-17
> **GuitarHero said:**
> Can we have the mods immediatly close these threads from now on.  Not to be rude but I don't think anyone cares you're leaving.  We all wish you the best but theres no reason for everyone leaving ubuntu to make a thread about it.  As if switching distros gives them some credential to preach to us about whats wrong with ubuntu.
now there's some straight up, common sense logic

---

### Post by wieman01 on 2006-09-17
> **hearnden said:**
> For the xserver-xorg failure, I was in the unfortunate situation that I had also just upgraded my BIOS, and so I was convinced that the problem had to be caused by a Taiwanese hardware company who only cares about testing on Windows.  It never occured to me that the semi-automatic update process of the Linux distro that is supposed to be as easy-to-use and as dumbed-down as possible could have been the cause.  I know I wasn't the only one who investigated many other possibilities before thinking that an Ubuntu upgrade caused the problem.

As for the second update, I know it doesn't touch anything in /lib/modules/2.6.15.23/..., but the initrd image contains many other things besides kernel-version-specific stuff, and I'd like to investigate more about what that upgrade did, but alas, without access to Linux and dpkg-deb etc, I went no further.

And using a capitalised ONLY does not diminish the severity of the xserver-xorg blunder.  I switched to Ubuntu from Red Hat then  SuSE and Solaris because I did not want to have to deal with these kind of issues.  The point I was making is that the only thing going for Ubuntu (and it is certainly a very valuable thing, if attainable) is ease-of-use and getting closer to the *it just works* phenomenon.  Imagine that: all the things you love about Linux without any of the dramas! However two major failures introduced via the update mechanism in a short interal severely tarnish that image, and it has been enough to make me seriously look elsewhere.
I agree with you. But I'll give Ubuntu a second/third chance because I believe that the latest blunder will set them thinking... Mark Shuttleworth is a very commercial- & media-savvy guy so I have no doubt they will respond soon. And they have taken corrective action already as pointed out earlier in this thread.

So let's keep up confidence & hope for the best. I'll continue to use Ubuntu for a while & see if it gets any better anytime soon. If not, I'll drop Ubuntu like a hot potato by the end of the year. Hope this won't happen though. :-)

But again, I am convinced that the Ubuntu team will react and try to polish their image. This has been fairly bad marketing for them.

---

### Post by hearnden on 2006-09-17
> **jimmygoon said:**
> Ubuntu is not perfect. Stop expecting it to be. It is a better alternative to Windows. You guys can not honestly tell me that you have more problems with Linux's updates than you do with Window's update. **Note:** you may not know how to fix them as easily, but that is no the fault of ubuntu. Fixing that xorg problem was much easier than recovering hours of work that goes deleted when xp decides to randomly reboot. Tell me how to "solve" that one.

This is another case (as with the 3rd poster in this thread too [the one with only one post]) of a xp "poweruser" expecting to be able to dominate linux and upon being hit with one challenge gets defensive and blames the software.

You are looking for the wrong thing in Ubuntu and I guarentee you won't find it in XP either.

I don't expect Ubuntu to be perfect, but I thought that with such an emphasis on increasing marketshare, dumbing-down Linux, and easy-of-use, that they would have been ultra-conservative with stability, and hence on regression testing their updates.

I don't think I ever said that Windows was a better alternative to Ubuntu, and I certainly don't think that is the case (although I do have a dual-boot with XP, and we all know why).  That said, although I do not prefer XP, I know how to live 'safely' in XP; however with these update sagas I cannot say the same about Ubuntu (apart from disabling all updates).

---

### Post by GuitarHero on 2006-09-17
Ubuntu is not about dumbing down linux at all.  It organizes the tools you have to utilize linux's power better, but it is in no way "dumber" or "weaker".

---

### Post by hearnden on 2006-09-17
> **maniacmusician said:**
> people should be educated about linux instead of being harrassed. I know you're good intentioned, but still. The guy just needs to learn how to use a terminal-based web browser. Several people did that and used these fabulous forums to fix the xorg problem.


When I finally accepted that an Ubuntu update might have caused my xserver problem, I did use lynx to browse the forums and there found the unbelievable truth.  But when's the last time any of you used a terminal browser?  How many websites today (especially forums!) are readable when viewed in a 80-character-wide terminal?  The raw HTML is more understandable!

> 
But at the same time, I don't agree with the OP in the sense that ubuntu should be abandoned because of these kinds of problem. Does he think other distros will be better? hell, most of them will be harder. he'll find himself missing sudo apt-get. going back to windows is even worse...and OSX, he would have to buy new hardware for that if he wants the same level of performance. Sure, Ubuntu's got issues but as you can clearly see, they're being worked on. 


ps. for a terminal based web browser, i'd recommend links

Perhaps Ubuntu still wins in usability, but these update problems are cause to undertake a serious assessment of other alternatives.  But if I do come back to Ubuntu, updates will certainly be disabled for 6 months!

---

### Post by GuitarHero on 2006-09-17
So dont update.  Most of the time you dont need them, if you have a stable system let it be.  Security updates you may want but the number of viruses and malware that pose any threat to a linux system is negligible.

---

### Post by maniacmusician on 2006-09-17
The update problems you're going on and on about are already well on their way to being fixed. Much stricter rules are being implemented. A mistake was made, but we learned from it and now it won't happen again.

I havn't tried lynx for browsing, but i use _links_ and like it a lot. it's easy to use.

---

### Post by wieman01 on 2006-09-17
> **GuitarHero said:**
> Can we have the mods immediatly close these threads from now on?  Not to be rude but I don't think anyone cares you're leaving.  We all wish you the best but theres no reason for everyone leaving ubuntu to make a thread about it.  As if switching distros gives them some credential to preach to us about whats wrong with ubuntu.
I do think this kind of discussion is necessary & helpful. So why not have it? While I don't agree with polemic a balanced discussion based on facts does have a purpose. It'd be sad if these threads were closed by default.

---

### Post by maniacmusician on 2006-09-17
> **wieman01 said:**
> I do think this kind of discussion is necessary & helpful. So why not have it? While I don't agree with polemic a balanced discussion based on facts does have a purpose. It'd be sad if these threads were closed by default.
yes, but most of the time, we're discussing the same thing over and over. it gets tiring. I didnt really get much out of this thread. I knew about the update problems, and I knew they were being fixed. 

Why should it matter to me that it upset one person so much that he's going to switch distros? I already know the facts of the matter.

---

### Post by wieman01 on 2006-09-17
> **maniacmusician said:**
> yes, but most of the time, we're discussing the same thing over and over. it gets tiring. I didnt really get much out of this thread. I knew about the update problems, and I knew they were being fixed. 

Why should it matter to me that it upset one person so much that he's going to switch distros? I already know the facts of the matter.
True indeed. However, the good thing about this forum is that you have a choice: One either contributes or does not. So it's up to you to "discuss the same thing" again... or not - if you know what I mean. But I guess you're right, I am off as well.

---

### Post by hearnden on 2006-09-17
> **GuitarHero said:**
> Can we have the mods immediatly close these threads from now on?  Not to be rude but I don't think anyone cares you're leaving.  We all wish you the best but theres no reason for everyone leaving ubuntu to make a thread about it.  As if switching distros gives them some credential to preach to us about whats wrong with ubuntu.

Point taken.  The intent of my post was not to preach, but to get a sense of who else feels they are in a similar position.  And not to be rude, but if the goal of Ubuntu is to increase the popularity of Linux, then surely the sum of the justifications of all the people who leave Ubuntu is, almost by definition, exactly what is wrong with it?  ergo switching distros does give credence to publishing the motivation behind it, however I acknowledge that perhaps this is not the best place for it.  I apologise if you thought you were going to get more out of this thread than you did.

---

### Post by hearnden on 2006-09-17
> **GuitarHero said:**
> Ubuntu is not about dumbing down linux at all.  It organizes the tools you have to utilize linux's power better, but it is in no way "dumber" or "weaker".

By dumbing-down I do not mean weaker or dumber, I mean "require less technical knowledge to get the same results", i.e. utilise Linux's power without having to be very tech-savvy.  Perhaps I could have used a different phrase, but I view 'dumbing down' as a good thing: it is precisely why I have been more productive in Ubuntu than previous *nixes, because it has been easier to get the same things done.

---

### Post by Zyzzyx on 2006-09-18
Well, if nothing else, this thread got at least one more person checking out terminal/text browsers.  ;)

I just installed Links and tried it on a few websites I frequent. Interesting, and potentially very handy.

---

### Post by 3rdalbum on 2006-09-18
If you want a system that is going to be stable and relatively free of security flaws, then only upgrade when a new point version is released.

I thought that was basically the point of having 6.06.1: It's a release where all the security updates have been tested by many many users, and therefore have been deemed "safe to bundle".

---

### Post by jdong on 2006-09-18
To clarify, by ONLY, I was trying to emphasize what were the symptoms of the breakage. I didn't mean to downplay the significance of the breakage in any way -- having X fail to start is quite significant -- catastrophic even, a failure for Ubuntu.

As I said before, I've seen too many unrelated problems unfairly blamed on the update blunders, and as people try to apply the fixes for the update blunders to these unrelated problems, the fixes of course don't work, and they get more angry about the update blunders :)


The update issue is clearly being taken seriously now, with the new StableReleaseUpdate policy, which is absolutely the strictest guidelines for releasing updates that I've ever seen in any of the distributions that I've used (and believe me -- I've used A LOT of different distributions).


I know how frustrating and disappointing the xorg update was, and how even more disheartening it was when not a month later the mistake was repeated. But the problem is being solved, and there is no need to leave Ubuntu. Every distribution has had its share of mistakes like this... it's just important that we prevent this from happening again and move on -- and it seems like that's what Canonical is doing.

---

### Post by wieman01 on 2006-09-18
> **jdong said:**
> The update issue is clearly being taken seriously now, with the new StableReleaseUpdate policy, which is absolutely the strictest guidelines for releasing updates that I've ever seen in any of the distributions that I've used (and believe me -- I've used A LOT of different distributions).
Just hope the whole affair won't into the opposite now. One of the key advantages of Ubuntu over other distributions is their efficient management of security updates (cycle time of roughly 1.5 days as far as I remember). There needs to be a balance, that's for sure.

---

### Post by Brunellus on 2006-09-18
> **wieman01 said:**
> Just hope the whole affair won't into the opposite now. One of the key advantages of Ubuntu over other distributions is their efficient management of security updates (cycle time of roughly 1.5 days as far as I remember). There needs to be a balance, that's for sure.
the offending xserver update wasn't a security update...it was, as I understood it, an attempt to improve PCI-E support.

---

### Post by hockeyshifter on 2006-09-18
I have read and agree with about 90% of all that has been written. IMHO the need to remove the linux kernal from the hands of the educational/elitists who want to keep some kind of controll over the developement process. i have done 3 installs of the same dapper/ubuntu release . all three were updated to the most current release and any updates that were required were also installed. i have set up the box to be dual boot and guess what all have beed hosed by the grub boot loader . all attemptes to refresh the boot loader( i have   buddy who makes a living using redhat) have been usless. i would like to see a standard set of protocalls for the installation (installshield) of all linux based programs and better interoperatability between windose and linux. LINUX has come along way in only 2 years and it needs to get farther down the road to get wider appeal for the common end user to want to use it. 
LINUX will be come the dominate OS in the next 5 years ( read DRM    copy protection , dvd duplication etc) because the general population will get very disinfranchaised with mac OSX and Vista  because they will be told how to use it ( mp3 players) ](*,) 
        SO with post i announce that i will not be using a linux distro for at least 2 more years.

---

### Post by hockeyshifter on 2006-09-18
I have read and agree with about 90% of all that has been written. IMHO the need to remove the linux kernal from the hands of the educational/elitists who want to keep some kind of controll over the developement process. i have done 3 installs of the same dapper/ubuntu release . all three were updated to the most current release and any updates that were required were also installed. i have set up the box to be dual boot and guess what all have beed hosed by the grub boot loader . all attemptes to refresh the boot loader( i have   buddy who makes a living using redhat) have been usless. i would like to see a standard set of protocalls for the installation (installshield) of all linux based programs and better interoperatability between windose and linux. LINUX has come along way in only 2 years and it needs to get farther down the road to get wider appeal for the common end user to want to use it. 
LINUX will be come the dominate OS in the next 5 years ( read DRM    copy protection , dvd duplication etc) because the general population will get very disinfranchaised with mac OSX and Vista  because they will be told how to use it ( mp3 players) ](*,) 
        SO with this post i announce that i will not be using a linux distro for at least 2 more years.

---

### Post by Brunellus on 2006-09-18
> **hockeyshifter said:**
> I have read and agree with about 90% of all that has been written. IMHO the need to remove the linux kernal from the hands of the educational/elitists who want to keep some kind of controll over the developement process. i have done 3 installs of the same dapper/ubuntu release . all three were updated to the most current release and any updates that were required were also installed. i have set up the box to be dual boot and guess what all have beed hosed by the grub boot loader . all attemptes to refresh the boot loader( i have   buddy who makes a living using redhat) have been usless. i would like to see a standard set of protocalls for the installation (installshield) of all linux based programs and better interoperatability between windose and linux. LINUX has come along way in only 2 years and it needs to get farther down the road to get wider appeal for the common end user to want to use it. 
LINUX will be come the dominate OS in the next 5 years ( read DRM    copy protection , dvd duplication etc) because the general population will get very disinfranchaised with mac OSX and Vista  because they will be told how to use it ( mp3 players) ](*,) 
        SO with this post i announce that i will not be using a linux distro for at least 2 more years.
goodbye. 

The Linux kernel is actually in the hands of the people who want to improve it for the purpose of getting what they need to do...done.  That includes educational elitists who want to look down on mere mortals (although some of them have progressed to work on GNU/HURD, which is so 1337 it barely exists...ha!).  More often, though, that means corporations seeking to make a profit on Linux-powered solutions (IBM, Novell, RedHat, Canonical) and/or other people with an interest in an improved Free kernel.

Mass adoption is a secondary and wholly unintentional side effect, which will be driven more by economics than any technical considerations.  The price of software, worldwide, is going to fall.  Eventually, things will get to a point of indifference where the benefits of Free licensing will outweigh the burdens of EULA compliance.  This is [already happening]("http://www.networkworld.com/news/2006/091206-von-sam-houston.html?page=1") in other sectors.

The masses won't have a darn thing to do with any of this, since the people on which license compliance puts the greatest burden are corporate system administrators.

---

### Post by Lord Illidan on 2006-09-18
>  			 		 		 		 		I have read and agree with about 90% of all that has been written. IMHO the need to remove the linux kernal from the hands of the educational/elitists who want to keep some kind of controll over the developement process. i have done 3 installs of the same dapper/ubuntu release . all three were updated to the most current release and any updates that were required were also installed. i have set up the box to be dual boot and guess what all have beed hosed by the grub boot loader . all attemptes to refresh the boot loader( i have buddy who makes a living using redhat) have been usless. i would like to see a standard set of protocalls for the installation (installshield) of all linux based programs and better interoperatability between windose and linux. LINUX has come along way in only 2 years and it needs to get farther down the road to get wider appeal for the common end user to want to use it. 
LINUX will be come the dominate OS in the next 5 years ( read DRM copy protection , dvd duplication etc) because the general population will get very disinfranchaised with mac OSX and Vista because they will be told how to use it ( mp3 players) ](*,) 
        SO with this post i announce that i will not be using a linux distro for at least 2 more years.

Don't let the door hit you on your way out....silly announcement.

---

### Post by aysiu on 2006-09-18
> **hockeyshifter said:**
> LINUX has come along way in only 2 years and it needs to get farther down the road to get wider appeal for the common end user to want to use it. Don't make me laugh. The common end user will **never** install Linux, no matter how "easy" or "compatible" it gets.

Never.

The common end user doesn't even install Windows now. Shouldn't that tell you something?

Why do I have to repeat this... it feels like every week...?

---

### Post by Brunellus on 2006-09-18
> **aysiu said:**
> Don't make me laugh. The common end user will **never** install Linux, no matter how "easy" or "compatible" it gets.

Never.

The common end user doesn't even install Windows now. Shouldn't that tell you something?

Why do I have to repeat this... it feels like every week...?
average is once every 18 hours?

---

### Post by aysiu on 2006-09-18
> **Brunellus said:**
> average is once every 18 hours?
Could be more frequent than that...

---

### Post by Brunellus on 2006-09-18
> **aysiu said:**
> Could be more frequent than that...
each of us has a role.  You say "Users never install things anyway."

My job is to say "Users never chose their OSes to begin with".

---

### Post by aysiu on 2006-09-18
> **Brunellus said:**
> each of us has a role.  You say "Users never install things anyway."

My job is to say "Users never chose their OSes to begin with".
I think the two go hand-in-hand, though.

As more corporations force their users to use Linux workstations, more Linux-preloaded desktops and laptops will become available... and that's what people will buy for the home.

It all goes hand-in-hand--work, home, school, recreation, embedded, server. The real question is which one will push the hardest so that the others will benefit.

---

### Post by OffHand on 2006-09-18
> **GuitarHero said:**
> So dont update.  Most of the time you dont need them, if you have a stable system let it be.  Security updates you may want but the number of viruses and malware that pose any threat to a linux system is negligible.

Dude, are you serious. I get an alert in my upper left corner telling me to upgrade (hence the word upgrade) my system and you are telling me to ignore it. That's just plain stupid imo. The developpers of Ubuntu tell me that they have improved software to offer and I shouldn't trust it?

Anyways, they have already changed they way they deal with updates so stuff like this will not happen again.

p.s. Both updates did not affect.

---

### Post by tagra123 on 2006-09-18
Has a point. I am not in the habit of allowing an update the first time ubuntu reminds me there are updates availiable -- I didn't do this with Windows either. 

Ubuntu has been sloppy with more than 1 update. The first time: Shame on them -- The second time Shame on me for not knowing or being prepared.

I usually wait -- and look through the items being updated - especially with utilities I use like samba, cups, nfs, XORG --etc. I also keep an eye on the forums for the listed programs after an update is available.

I do a full system backup - even when I used Windows -- Once a month. I also do hourly, daily, and weekly backups of important files. If something wont let the computer start I break out the backups.

Having the latest and greatest hardware isn't everything. Having good hardware is. This goes for windows and linux.  Linux does need more hardware support and compatibility but this isn't the community's fault -- its the manufacturer's.

---

### Post by DoctorMO on 2006-09-18
> the need to remove the linux kernal from the hands of the educational/elitists who want to keep some kind of controll over the developement process

I quite supprised by the iggnorance of this section of the post, it assumes that the linux kernel is in someones hands, that you could control it in some way and that it's the educated bastards who are doing all this controling.

Some interesting socio facts for you about open source and free software:

1) If you don't like the way the Linux kernel is developed, then fork.
2) To have control is to control the minds of hundreds, maybe thousands of programmers who each want to do different things.
3) The lience is perpetual meaning that no 'one' could have control.
4) If there is something you want done, roll up your sleves because no one else will do it for you.

the above quote shows just what messed up human beings the corperate/political culture is producing. they have no understanding of outside process and things that happen by conssensus and structure. asuming that someone must be ording the armies to invade. =D>

---

### Post by Brunellus on 2006-09-18
> **OffHand said:**
> Dude, are you serious. I get an alert in my upper left corner telling me to upgrade (hence the word upgrade) my system and you are telling me to ignore it. That's just plain stupid imo. The developpers of Ubuntu tell me that they have improved software to offer and I shouldn't trust it?

Anyways, they have already changed they way they deal with updates so stuff like this will not happen again.

p.s. Both updates did not affect.
all 'upgrades' are essentially leaps of faith:  you are changing a running system to gain a set of promised benefits.  

If you want a 'stable' system, it's entirely possible to do that.  Debian's "stable" release hardly changes at all for YEARS, except for small security fixes.  

The continuum is like this

Stability >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>Novelty
Debian Stable>>>>>>>>>>>Ubuntu>>>>>>>>>>>>>Gentoo

---

### Post by .t. on 2006-09-18
Running Gentoo stable is not particularly novel, and running ~arch you'd have to be prepared for breakage. As to the OP; I hope your ignorance leads you down a long and educational path. And on that note: bye!

---

### Post by OffHand on 2006-09-18
> **Brunellus said:**
> all 'upgrades' are essentially leaps of faith:  you are changing a running system to gain a set of promised benefits.  

If you want a 'stable' system, it's entirely possible to do that.  Debian's "stable" release hardly changes at all for YEARS, except for small security fixes.  

The continuum is like this

Stability >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>Novelty
Debian Stable>>>>>>>>>>>Ubuntu>>>>>>>>>>>>>Gentoo

My point is that Ubuntu presents itself as being easy and noobfriendly.
You cannot break a system like that while at the same time tell people it is easy and solid.

---

### Post by Brunellus on 2006-09-18
> **OffHand said:**
> My point is that Ubuntu presents itself as being easy and noobfriendly.
You cannot break a system like that while at the same time tell people it is easy and solid.
The ubuntu breakages have been isolated incidents, and the maintainers have fixed their procedures since then.  Trust them.  

If not, then I encourage you to move on to Blag, MEPIS, Knoppix, or any number of other distributions.

---

### Post by OffHand on 2006-09-18
> **Brunellus said:**
> The ubuntu breakages have been isolated incidents, and the maintainers have fixed their procedures since then.  Trust them.  

If not, then I encourage you to move on to Blag, MEPIS, Knoppix, or any number of other distributions.

Quote from my first post...
> Anyways, they have already changed they way they deal with updates so stuff like this will not happen again.

p.s. Both updates did not affect.

I like Ubuntu and I am going to stay. Thanks for the suggestion though  :rolleyes:

EDIT: btw, I was just responding to the guy that said we shouldn't install updates which is bollocks imo and explaining why I thought it is bollocks. If that's the case there never should have been an update notifier.

---

### Post by bobbybobington on 2006-09-18
perhaps having update settings by default in the os so that it waits 24 hrs before installing updates. This way you can have a last defence of "testers" before the updates effect everyone else, and its 24 hrs since all major broken updates are solved in 24hrs. If you want to disable the 24 hr wait it will warn you that you might have update troubles. So devs and testers can disable the 24 hr wait, and they wont have to deal with the 24 wait to access the fix for it.

This of course would be one component of improving QA.

---

### Post by missmoondog on 2006-09-18
> **hearnden said:**
> For the xserver-xorg failure, I was in the unfortunate situation that I had also just upgraded my BIOS, and so I was convinced that the problem had to be caused by a Taiwanese hardware company who only cares about testing on Windows.  It never occured to me that the semi-automatic update process of the Linux distro that is supposed to be as easy-to-use and as dumbed-down as possible could have been the cause.  I know I wasn't the only one who investigated many other possibilities before thinking that an Ubuntu upgrade caused the problem.

As for the second update, I know it doesn't touch anything in /lib/modules/2.6.15.23/..., but the initrd image contains many other things besides kernel-version-specific stuff, and I'd like to investigate more about what that upgrade did, but alas, without access to Linux and dpkg-deb etc, I went no further.

And using a capitalised ONLY does not diminish the severity of the xserver-xorg blunder.  I switched to Ubuntu from Red Hat then  SuSE and Solaris because I did not want to have to deal with these kind of issues.  The point I was making is that the only thing going for Ubuntu (and it is certainly a very valuable thing, if attainable) is ease-of-use and getting closer to the *it just works* phenomenon.  Imagine that: all the things you love about Linux without any of the dramas! However two major failures introduced via the update mechanism in a short interal severely tarnish that image, and it has been enough to make me seriously look elsewhere.

this just about says it all! :frown: 

However two major failures introduced via the update mechanism in a short interal severely tarnish that image, and it has been enough to make me seriously look elsewhere.

---

### Post by hockeyshifter on 2006-09-18
>  I quite supprised by the iggnorance of this section of the post, it assumes that the linux kernel is in someones hands, that you could control it in some way and that it's the educated bastards who are doing all this controling. quoted from Doctor MO 

Mr. MO .. my brother in-law is a professor at U PENN at State college. he is working on a nasa funded space project looking for a certian type of gama rays. the team must pinch pennies at all cost. he has been on the project for almost 8 years. the team members on the is project are from all over the US and the World. i ask the question why dose the team NOT use LINUX . his response was complication in using the OS (most major distros) . The team writes all of the computation programs and they are written to work on windows because of the issues common to linux.how would  you like to take 6 months to write a program and it not be compatible; how would you like to have spent 2 years of your grant money only to have all the data corupted because when you started a program the system stalled or crashed. i have debated with the team leader who happens to be from ireland and worked on the linux kernal at dublin college his feeling are the same as mine.

---

### Post by jdong on 2006-09-19
You can seriously cut down on the number of updates (and therefore the perceived update risk) by turning off the dapper-backports and dapper-updates repositories, and leave only dapper-security. However, then you lose out on "bugfixes" from dapper-updates, which isn't a big deal if nothing feels broken to you anyway.


It's really not a great idea to skip dapper-security updates though... that could leave you vulnerable to attack.

---

### Post by mrgnash on 2006-09-19
> **HowardMM said:**
> I am in a similar position. I believed all the hype that ubuntu was something easy to instal and a real alternative to the M$. sadly after wasing a weekend on trying to instal it unsucessfully (didnt even even get to first base!) I feel that I have been ripped off not in a $ sense but claims made by ubuntu community. I have now rebooted my xp machine effortlessly and have gone back to business as usual, with a greater determination not to believe the geeks that a serious alternative to windows which can be installed by the lay person exists..farewell!!

Glad to see the back of you.

---

### Post by monktbd on 2006-09-19
> **hockeyshifter said:**
> The team writes all of the computation programs and they are written to work on windows because of the issues common to linux.how would  you like to take 6 months to write a program and it not be compatible; how would you like to have spent 2 years of your grant money only to have all the data corupted because when you started a program the system stalled or crashed.

oh how i like those vague "facts".
ad programming: be more specific about the "issues common to linux"
unless the libraries arent completly entirely different programs are easily recompileable for different versions. 

ad data corrpution: if someone fails to have a proper backup strategy it isnt the OS fault. and i have seen more data loss on windows machines by far.

just ask yourself why so many servers run on linux.

---

### Post by ago on 2006-09-19
> **hearnden said:**
> Why?  Because of the lack of regression testing in the updates, and lack of contemporary hardware support.
That is far more common with MS. See MS06-42 for instance. The X bug in Ubuntu was a one-off and was fixed within HOURS and there were clear instructions within minutes. The MS bug was released on 8th of August and introduced 2 new vulnerabilities. The 24th of August they managed to fix 1 out of 2 with a new patch. Only with the third patch after MORE THAN A MONTH they managed to get it right... And it was not an isolated case, by any means. Not to mention about the other surprises that they like to mix with updates... WGA anybody? And that was not even an error...

> And no, I can't use the Live CD, because Ubuntu hasn't caught up with my hardware (JMicron PATA controller).
So what? Why do you expect Ubuntu to work on unsupported hardware? I use the hardware required to make my OS tick, I choose the OS first, then the hardware, not the other way around. If you want to use Linux, buy Linux compatible hardware it is not that difficult these days.

> The latest kernel updates have been more problematic.  Not only did it hose the 2.6.15.26 kernel, but also the other 2.6.15.23 'safe' kernel I had.  I don't know how it did it, but somehow all my initrd's are broken, and booting any of them results in a Kernel Panic while trying to mount the root file system.  It's not my file system that's the problem, because if I use the initrd from my laptop (copied onto a USB flash drive), it boots ok: so it's something to do with the initrd and the kernel modules.  I'm presuming the latest update fiddled with something outside of /lib/modules/<version>, because it must be common to all my kernels.
There are no other reports about those issues (affecting both 26 AND 23 kernels) that I am aware of. It looks far more likely that you borked the system all by yourself, if you like to play root when you do not know what you are doing, do not complain. After the X problems people have been blaming the updates for things that have nothing to do with them. You are not even sure what the problem is, still you are pointingthe finger to the devs... That is a pretty lame attitude.

---

### Post by ago on 2006-09-19
> **hockeyshifter said:**
> his response was complication in using the OS (most major distros) .
What complication exactly? 

> The team writes all of the computation programs and they are written to work on windows because of the issues common to linux.
Which are?

> how would  you like to take 6 months to write a program and it not be compatible;
I have yet to see a piece of source code written for one linux system that cannot be compiled on another system...

> how would you like to have spent 2 years of your grant money only to have all the data corupted because when you started a program the system stalled or crashed.
Sure, they are concerned about crashes and therefore they use Windows.... On what movie? 

Maybe the program stalled or crashed. A userspace program will not crash Linux, you can write code with the sole purpose to try and crash Linux. And unless the program is executed with root privileges you will fail. Windows? I just need to put a matrix in memory that is large enough to require all the memory+vm and windows is dead for good. 

And by the way there are several NASA programs happily using Linux... Including their latest supercomputer... I guess you should inform them that having an unstable OS such as Linux on their most expensive iron might be a bad idea...

---

### Post by 3rdalbum on 2006-09-19
Mate, there are a number of ways where you can even write a program for Windows, and the source-code can be compiled and run on Linux.

As far as crashes go, you're reading the post of someone who can't remember when their computer last crashed. A huge number of supercomputers run Linux (it's well over 50%) or some form of BSD, and that's one application where you do anything to avoid having a crash or data corruption! Or do you think that your data is more important than finding a black hole or a cure for cancer?

---

### Post by ago on 2006-09-19
> **3rdalbum said:**
> A huge number of supercomputers run Linux (it's well over 50%)

73.4% to be precise. We reach 93.8% if we add the Linux cousins... And do not forget that most "mixed" systems have often some linux parts... Windows? It seems expensive iron is allergic to it... Probably because it is sooo stable and performs sooo well...

**Top 500 SuperComputers by OS Family**[list=1]
[*]Linux 73.40%
[*]Unix 19.60%
[*]Mixed 4.80%
[*]Mac OS 1.00%
[*]BSD Based 0.80%
[*]Windows 0.40%[/list]

[http://www.top500.org/stats/27/osfam/](http://www.top500.org/stats/27/osfam/)

---

### Post by markyb86 on 2007-12-12
He should try ubuntu again! I bet it wont give him the same trouble over a year later!

> how would you like to have spent 2 years of your grant money only to have all the data corupted because when you started a program the system stalled or crashed.

If you were doing anything that long, why wouldnt you have something called backup

---

### Post by meborc on 2007-12-12
> **markyb86 said:**
> If you were doing anything that long, why wouldnt you have something called backup

+1

good catch =D>

---

