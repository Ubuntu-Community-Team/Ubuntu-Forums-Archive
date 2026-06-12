---
title: "Heh, more Gentoo fun!"
date: 2005-03-28
forum: The Cafe
---

### Post by jdong on 2005-03-28
I'm compiling a stage3 athlon-xp Gentoo 2005.0 install for my main desktop... There's still some aspects of Gentoo that I love, namely USE flags and flexible compiling.

I'm gonna go somewhat bleeding edge, using reiser4 + nptl + KDE 3.4, so it's probably gonna be a bumpy ride. Hopefully, it's worth it in the end.

---

### Post by paul cooke on 2005-03-28
gentoo is irrelevant. Ubuntu is the shape of the future for Linux.

yes I have done Gentoo... I'm not embarrassed to admit it... it was a diversion... but I didn't really feel empowered and just getting a basic system up and running from stage 3 was an adventure in itself...

I prefer the ease of updating Ubuntu over all my boxes overnight using a cron job.

---

### Post by poofyhairguy on 2005-03-28
[QUOTE=jdong]I'm compiling a stage3 athlon-xp Gentoo 2005.0 install for my main desktop... There's still some aspects of Gentoo that I love, namely USE flags and flexible compiling.

I'm gonna go somewhat bleeding edge, using reiser4 + nptl + KDE 3.4, so it's probably gonna be a bumpy ride. Hopefully, it's worth it in the end.[/QUOTE]

I hope you plan to give another full review...

---

### Post by Bilko on 2005-03-28
[QUOTE=jdong]I'm compiling a stage3 athlon-xp Gentoo 2005.0 install for my main desktop... There's still some aspects of Gentoo that I love, namely USE flags and flexible compiling.

I'm gonna go somewhat bleeding edge, using reiser4 + nptl + KDE 3.4, so it's probably gonna be a bumpy ride. Hopefully, it's worth it in the end.[/QUOTE]

Gentoo is great as a Desktop - got it here in addition to a Ubuntu machine - but reiser4 ...

---

### Post by jdong on 2005-03-28
[QUOTE=poofyhairguy]I hope you plan to give another full review...[/QUOTE]

Ok, I'm emerging qt right now, going for a KDE 3.4.0 desktop with HAL. If all goes smoothly, I'll give a nice, complete review that Gentoo deserves. Last time, I was ticked that a prerelease 2005.0 didn't work... *imagine that!*

As far as Gentoo vs Ubuntu -- I don't want to start a contest. Both are good distros, it's just that my desktop will turn into more of a heavy-duty server+desktop mix, and Gentoo seems more appropriate for such a setup...

---

### Post by bigzak on 2005-03-28
[QUOTE=jdong]As far as Gentoo vs Ubuntu -- I don't want to start a contest. Both are good distros, it's just that my desktop will turn into more of a heavy-duty server+desktop mix, and Gentoo seems more appropriate for such a setup...[/QUOTE]

I used Gentoo when my machine was part of a network of 20+ Gentoo machines, all running the distcc daemon. It's not so bad when you can share the build time across 2-10 machines for any particular package.

On my home machine, however, an update started to take hours. I much prefer Ubuntu for my home machine. It really does 'just work', and updates take about 10 minutes on my 2Mb connection (I am running hoary preview, so a dist-upgrade is usually relatively large at the moment).

---

### Post by jdong on 2005-03-28
With a big fat AMD64 machine, a full Gentoo install from stage1 to KDE takes about 12 hours of compiling, so it's not a big deal at all...

---

### Post by Randabis on 2005-03-28
[QUOTE=jdong]I'm compiling a stage3 athlon-xp Gentoo 2005.0 install for my main desktop... There's still some aspects of Gentoo that I love, namely USE flags and flexible compiling.

I'm gonna go somewhat bleeding edge, using reiser4 + nptl + KDE 3.4, so it's probably gonna be a bumpy ride. Hopefully, it's worth it in the end.[/QUOTE]
 I'm about to do the same myself within ubuntu if everything works out right. :)

---

### Post by jdong on 2005-03-28
I'm on kdelibs-3.4.0 right now (8 of 73). Once I get kdelibs, everything else after that's tiny.

---

### Post by TravisNewman on 2005-03-28
Good luck emerging openoffice! *L* That thing is a beast to compile. Probably took close to 24 hours itself on my athlon xp.

Good luck with everything! There are times when I miss gentoo, but then I realize that I want to stay up to date and I want to also use my computer. It's fantastic for those who want to install and leave it, or those running servers, but for me it was just too much, since I HAD to update every day ;)

---

### Post by jdong on 2005-03-28
```


jdong@omega:~$ uptime
 18:47:10 up 21:16,  6 users,  load average: 5.32, 5.32, 5.35

```

Yep, it's busy... ;)

Waiting patiently :)

---

### Post by jerome bettis on 2005-03-28
i finally installed it this weekend. i just made a 10 gig partition on the same disk, so i can share my /boot & /home partitions between gentoo and ubuntu.  i've wanted to do this for several weeks now, but i was hesitant as i knew i would screw something up.  but it turns out there was nothing to fear - the install doc works perfect if you read it carefully.

stage 1 install with xfce, firefox, thunderbird, eclipse and a few small apps i like from gnome took about 10 hours of compiling on my 1.7ghz pentium M w/ 512mb ram.  i'm going to back up this partition now with partimage so i don't have to do that again when i screw it up.

i'm actually debating starting over with a different set of cflags, namely -Os instead of -02 and some other stuff.  it's noticeably faster than ubuntu, but not as much as i was hoping for.  eclipse still takes a long time to start.

---

### Post by TravisNewman on 2005-03-28
OK, so is there an installer? It was posted somewhere that htere is. If it doesn't allow for the flexibility that Gentoo is famous for it's pointless.

Hopefully other distros (us, for example) will catch on to 32 bit in 64 bit soon.

---

### Post by kassetra on 2005-03-29
[QUOTE=jdong]Yep, it's busy... ;)

Waiting patiently :)[/QUOTE]

Just to take a small detour of our topic here...

I once worked for a nameless ISP whose server loads were just under *DOUBLE* what you were seeing there... And the head of this ISP simply *loved* the main server, it was his baby... so it's not like we could go in there and rip that puppy out in order to install something better... Yeah...  You can imagine the customers that were calling in because they couldn't get their email, out to the web, etc... heh.  Did I mention I also had to step in for tech support...?

good times, good times...

---

### Post by Whiffle on 2005-03-29
I just got off gentoo, had it for about a year.  Its got its place.  In fact I learned just about everything I know about linux through gentoo, which should help me in the future.  But, I got tired of waiting (1.6ghz p4) for everything, and having to configure everything.  I was absolutely stunned when I had ubuntu up and working in an hour or less without even having to touch my xorg.conf

---

### Post by jerome bettis on 2005-03-29
[QUOTE=Whiffle]I was absolutely stunned when I had ubuntu up and working in an hour or less without even having to touch my xorg.conf[/QUOTE]

yeah i have no idea what my refresh rate is so i just copied that file over from my ubuntu partition and it works just as well.

now what i'm wondering right now is can i copy and use the packages i compiled under gentoo over here in ubuntu?  i guess i could copy the files, make a .deb (however i do that) and upload them somewhere which i could put in my apt sources.  eh that might be more trouble than it's worth with frequent updates and such.  but i'm using the same kernel over here and it seems to be somewhat more responsive.

---

### Post by defkewl on 2005-03-29
Are we suppose to talk about Gentoo here?

Yeach Gentoo is great, but is it suitable under mission critical project?

---

### Post by TjaBBe on 2005-03-29
I like Gentoo. But I moved onto Debian and Ubuntu because of the time it takes to compile all updates for a gentoo system. They also keep their repository very up-to-date, resulting in me compiling again update after update.

On the other hand I probably learned most from Gentoo comparing to other distro's I've used. In my opinion it is a great distro if you want to learn more of Linux itself. 

So I agree with panickedthumb, Gentoo is great, but not if you want to actually use your computer for anything else but compiling ;).

---

### Post by defkewl on 2005-03-29
Me too admit that Gentoo is a great system. But I still would not use it for mission critical system. It's good for learning Linux, but it's not good for business. :P Just my opinion.

---

### Post by jdong on 2005-03-29
Well, here's my experience:

* **Portage Profile Problems** -- 2.6 headers/sources are still masked via the 2005.0 profile -- WTF? Issuing practically any emerge command tells you that gentoo-sources/linux-headers are masked. You have to manually unmerge & remerge gentoo-dev-sources and linux26-headers in order to continue.

* **Numerous Ebuild failures** -- From stage3 to KDE 3.4.0, I think I've had to go in to hand-patch ebuilds about 5 times, to prevent compile failures. And that's not just with ~x86 packages -- stable (x86) packages had sandbox violations, etc. Overall, it feels like Gentoo is getting very sloppy. I talked about it on the forums, and got the whole "~x86 is not stable" response. You'd think that after an ebuild hits Portage for a month, that it'd at the very least COMPILE? Nope.

* **Not very up-to-date** -- To get a fairly recent system, you have to manually accept a very sizeable number of ebuilds with the ~x86 keyword. It gets very bothersome to do by hand.

* **Portage becoming slower and slower** -- I could've sworn that metadata updates didn't take 2 minutes last year!

* **KDE doesn't boot up properly** -- KDE locks up X at bootup, because of some sort of ksplash issue. Had to edit KDE scripts by hand to bypass this.


In addition, I heard complaints on DSLR of many people ending up with broken systems after switching over to the 2005.0 profile. All in all, Gentoo is not ready for mainstream use, and should be treated as an experimental setup. Definitely do not go Gentoo unless you have plenty of time to spare.

---

### Post by jdong on 2005-03-29
Ok, a few issues resolved... Stuff is starting to get stable-masked recently. Excellent.

---

### Post by DJ_Max on 2005-03-29
[QUOTE=defkewl]Are we suppose to talk about Gentoo here?

Yeach Gentoo is great, but is it suitable under mission critical project?[/QUOTE]
 As long as you know your way around Linux, then it's one of the best OS's out there for you. I've used Gentoo, and never had a faster bootup time. I'll be installing Gentoo soon.

---

### Post by TravisNewman on 2005-03-29
Why shouldn't we talk about Gentoo here? We can talk about most anything else ;)

---

### Post by DJ_Max on 2005-03-29
[QUOTE=panickedthumb]Why shouldn't we talk about Gentoo here? We can talk about most anything else ;)[/QUOTE]
 I agree. Also, panickedthumb, what you having for dinner, why not send me some. :)

---

### Post by TravisNewman on 2005-03-29
um... I had macaroni and cheese for dinner. Why? *L* You confused me man.

---

### Post by DJ_Max on 2005-03-29
[QUOTE=panickedthumb]um... I had macaroni and cheese for dinner. Why? *L* You confused me man.[/QUOTE]
 Oh, just a side-joke, seeing as we can talk about anything here.

---

### Post by TravisNewman on 2005-03-29
oooohhhhhh
sorry, long, boring day at work today. Nothing happened all freakin' day, so my mind went to sleep long long ago.

---

### Post by DJ_Max on 2005-03-29
heh, I know what you're talking about, been there.

---

### Post by TravisNewman on 2005-03-29
Wow, the installer actually looks quite promising:
[http://dev.gentoo.org/~agaffney/gli/](http://dev.gentoo.org/~agaffney/gli/)

---

### Post by Randabis on 2005-03-30
[QUOTE=jdong]Well, here's my experience:

* **Portage Profile Problems** -- 2.6 headers/sources are still masked via the 2005.0 profile -- WTF? Issuing practically any emerge command tells you that gentoo-sources/linux-headers are masked. You have to manually unmerge & remerge gentoo-dev-sources and linux26-headers in order to continue.[/quote]
I thought you're supposed to use gentoo-sources now. :p

> * **Numerous Ebuild failures** -- From stage3 to KDE 3.4.0, I think I've had to go in to hand-patch ebuilds about 5 times, to prevent compile failures. And that's not just with ~x86 packages -- stable (x86) packages had sandbox violations, etc. Overall, it feels like Gentoo is getting very sloppy. I talked about it on the forums, and got the whole "~x86 is not stable" response. You'd think that after an ebuild hits Portage for a month, that it'd at the very least COMPILE? Nope.
I agree wholeheartedly. It got so bad for me that I just said screw it and wiped out the gentoo partition. Gentoo just keeps getting crappier and crappier imho. Too many of the devs are crack addicts or something.

> * **Not very up-to-date** -- To get a fairly recent system, you have to manually accept a very sizeable number of ebuilds with the ~x86 keyword. It gets very bothersome to do by hand.
Yeah that sucks. :/

> * **Portage becoming slower and slower** -- I could've sworn that metadata updates didn't take 2 minutes last year!
I KNOW. It ridiculous.

> * **KDE doesn't boot up properly** -- KDE locks up X at bootup, because of some sort of ksplash issue. Had to edit KDE scripts by hand to bypass this.
I wasn't able to get that far because of all the stupid compile failures. :( I couldn't even recompile glibc for ntpl or get gcc 3.4.3. I don['t know what they did in 2005.0 that screwed this up...I had that working just fine in 2004.3.


> In addition, I heard complaints on DSLR of many people ending up with broken systems after switching over to the 2005.0 profile. All in all, Gentoo is not ready for mainstream use, and should be treated as an experimental setup. Definitely do not go Gentoo unless you have plenty of time to spare.
Yeah, the main problem is portage has turned to shit for some reason. :/

---

### Post by jdong on 2005-03-30
[QUOTE=Randabis]I thought you're supposed to use gentoo-sources now. :p[/QUOTE]

Until about 5 days AFTER the release of 2005.0, every version of gentoo-sources and linux-headers was HARD MASKED or PROFILE MASKED.

If you're not ready to release 2005.0, DONT RELEASE IT. Sheesh, simple concept!

---

### Post by Randabis on 2005-03-30
[QUOTE=jdong]Until about 5 days AFTER the release of 2005.0, every version of gentoo-sources and linux-headers was HARD MASKED or PROFILE MASKED.

If you're not ready to release 2005.0, DONT RELEASE IT. Sheesh, simple concept![/QUOTE]
Wow, I didn't know that. :p I share your frustrations at any rate. I don't know what's going on with gentoo developers, but the way things are going now is really hurting the distro. :(

---

### Post by jdong on 2005-03-30
Well, now I got it fully set up.

Once you tweak with it for a while (unmasking/adding keywords, etc), Gentoo is a very pleasant distro.

It's just that the install process is very time-consuming and frustrating. You have to be "in the loop" (watching bugzilla, mailing lists, forums, like a hawk) in order to know what to install and what not to install.


KDE logo hangs were caused by a badly compiled NVidia driver -- it somehow got linked to a mystery kernel (?!? 2.6.2)

---

### Post by Randabis on 2005-03-30
[QUOTE=jdong]Well, now I got it fully set up.

Once you tweak with it for a while (unmasking/adding keywords, etc), Gentoo is a very pleasant distro.

It's just that the install process is very time-consuming and frustrating. You have to be "in the loop" (watching bugzilla, mailing lists, forums, like a hawk) in order to know what to install and what not to install.


KDE logo hangs were caused by a badly compiled NVidia driver -- it somehow got linked to a mystery kernel (?!? 2.6.2)[/QUOTE]
Yeah, I know...I've done more than one Gentoo install in my day (including a few stage 1s), but it's just not worth it to me anymore, especially after the numerous problems I had with 2005.0. But yeah, when everything is working right, it's a powerful distro.

---

### Post by jdong on 2005-03-30
One thing that really bugs me right now is how sucky Hoary Firefox is. Random hangs opening new tabs, segfaults usually accompanying the hangs, etc. It's definitely a Ubuntu problem, since my FC3 install has the same base Firefox (1.0.2) and doesn't exhibit any issues.

I'd like to keep some other distros at hand.

---

### Post by TravisNewman on 2005-03-30
*blinks*
I still have yet to have any trouble with any Firefox version on any Operating System/Distro. I am lucky, I know, and surely there are bugs, but I haven't seen any segfaulting unless its related to plugins, no hangs, etc. Very strange.

---

### Post by zenwhen on 2005-03-30
[QUOTE=panickedthumb]*blinks*
I still have yet to have any trouble with any Firefox version on any Operating System/Distro. I am lucky, I know, and surely there are bugs, but I haven't seen any segfaulting unless its related to plugins, no hangs, etc. Very strange.[/QUOTE]


You aren't alone. I have been using Firefox since EARLY in it's Phoenix days and have had like three crashes. :)

---

### Post by vassalle on 2005-03-30
taliking about firefox in hoary... mind is broken or something, i cant import bookmarks.. the fields are kinda empty.. the cancel, next tab on the bottom right corner is not even worded! but thankfully it doesnt hang..

---

### Post by ahmad on 2005-03-31
have any of you gotten synaptics drivers to work (for amd64) on gentoo or ubuntu?

a friend had installed ubuntu a weeks ago and he told me that the portage of ubuntu has only some basic applications. i love the fact that gentoo's portage rocks and is very big. but i cannot get synaptics drivers to work for amd64. 

 if ubuntu can make the touchpad work so i can have the advanced features like double-tap dragging, etc and hardware acceleration for ati 9700 mobile, i would switch to ubuntu.

---

### Post by jerome bettis on 2005-03-31
how do i "apt-get update" with gentoo?

i'm starting to like this distro better than ubuntu.  don't get me wrong, ubuntu is sweet, but everything over here is just a lot faster.  firefox shows up as soon as i click it, not a second or so later.  at first i was kind of disappointed with xfce and was contemplating emerging gnome-light.  but after i've used it for a few days i've realized it's actually pretty nice and can be made to look almost just as good.

personally i had no problems at all during the installation (except for one thing that was due to a careless mistake on my part).  but it sounds like i got lucky.  i could not imagine trying to install / use this system if i was a newbie coming from windows.  ubuntu is great because you don't have to do anything, but you can still go off and learn things if you want to.
 
i guess the biggest thing that i really like about gentoo is i know exactly what packages i have on this system, and there's not many at all.  my main gripe with ubuntu is there's tons of apps i don't / would never ever use.  the same thing for kde, there's 1000 stupid little apps that come with it that i don't want.  over here i have nothing more than xfce, firefox, thunderbird, xmms, gaim, gnome-terminal, gnome-calculator, gedit, gaim, xpdf, java 1.4.2 and eclipse.  and that's all i want =; anything else is considered unnecessary bloat.

---

### Post by DJ_Max on 2005-03-31
Gentoo doesn't use apt-get, it uses Portage. The command script is 'emerge'. Read the docs, they have plenty of them.

---

### Post by jerome bettis on 2005-03-31
LOL

i know that.  i'm asking what is the gentoo equlivant of debian's apt-get update.  is it emerge update or what?

thanks  .. i plan to read a lot in the coming weeks when i have the time.

---

### Post by Whiffle on 2005-03-31
[QUOTE=jerome bettis]LOL

i know that.  i'm asking what is the gentoo equlivant of debian's apt-get update.  is it emerge update or what?

thanks  .. i plan to read a lot in the coming weeks when i have the time.[/QUOTE]
 emerge -up world  --to see whats goign to be upgraded

emerge -u world --upgrades

---

### Post by Randabis on 2005-03-31
[QUOTE=jerome bettis]LOL

i know that.  i'm asking what is the gentoo equlivant of debian's apt-get update.  is it emerge update or what?

thanks  .. i plan to read a lot in the coming weeks when i have the time.[/QUOTE]
 emerge --sync

---

