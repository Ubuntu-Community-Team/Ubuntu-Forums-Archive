---
title: "Fixed bugs that are back - How is it possible? What causes it?"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-04-07
At this point I'm pretty used to the black magic that makes things that were fixed come back always a couple days before the RC, so we can have the pleasure of seeing bugs persisting from one cycle to another despite our work. Today however, thinks look extra special:

- Infinitesimal small window grabbing area: Back
- Impossible to grab overlaying scrollbar: Back
- No sound on ALC892 (wow, this one worked this entire cycle after I interacted with David Heningsson via LP, he found the bug and updated the kernel module. I have no idea how is it even possible to break it again?): Back
- nvidia-current delay when switching to VT-Any to VT-7 and back. Eventual screen corruption. Was reported by me in NN, OO, PP. Was fixed about a month ago annnnnd: Back
- Freezing touchpad. We discussed it in OO, it wen't directly to PP and was fixed. Now, of course, its: Back
- Virtual-Machine Window turns into non-interactive White-Square when switching screens. I haven't seen this one since OO. And it's Back.

And others, many others I thought were gone. (I mean they *were* fixed, I'm **sure** of it). It's really frustrating for me.

I'm beginning to be pretty sure that it happens every cycle, always when we are a couple days from release. I can't understand it. I'm not even sure how it would be possible. Does anyone have any idea?

Regards,
Effenberg

---

### Post by dino99 on 2012-04-07
i can add some more :(
- logged as gnome-classic, gnome-panel does not load, need to start it via terminal
- metacity fails too, same workaround

- feature removed (sadly, its critical): cant create a launcher with desktop right click

That's right that we have much more troubles now (b2, freezed time) than before. But its often the case: fix something, break an other. Fedora knows that too, it delay the roadmap !!! but canonical dont.

---

### Post by Pilot6 on 2012-04-07
I do not quite understand why people use Ubuntu with gnome, etc. The purpose of Ubuntu is to have everything out of the box. If you do not like default DE, why do not you install e.g. Debian and add any DE you like?

---

### Post by mc4man on 2012-04-07
I would guess unless your install has local issues what you're seeing then may be hardware based

For instance on couple of day old non modded install - 
- Infinitesimal small window grabbing area:no problem
- Impossible to grab overlaying scrollbar: can grab fine
-nvidia-current delay when switching to VT-Any to VT-7 and back. - 

With the 290.10 drivers all is fine, with the 295.XX I suffer from a 'corner case' & quite mysterious bug, works fine for a min. of 3 restart cycles, then get a complete failure to restart/shutdown or switch VT*'s somewhere between the 4th & 8th cycle. Happens like clockwork

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564)

- Freezing touchpad. We discussed it in OO, it wen't directly to PP and was fixed. Now, of course, its: no sign of issue here at all - when it happens to you are you seeing 2 syndaemon instances or is it another cause?

On the other hand I see some other issues not widely reported & still get this out of the blue breakdown in smooth scrolling - very obvious in gedit on large  files, scrolling becomes like sliding on ice.

---

### Post by effenberg0x0 on 2012-04-07
> **mc4man said:**
> I would guess unless your install has local issues what you're seeing then may be hardware based

For instance on couple of day old non modded install - 
- Infinitesimal small window grabbing area:no problem
- Impossible to grab overlaying scrollbar: can grab fine

It looks like it was 3 weeks ago here, when that was an active issue. it makes no sense. It shouldn't be hardware-related... (right?)

> **mc4man said:**
> 
-nvidia-current delay when switching to VT-Any to VT-7 and back. - 
 With the 290.10 drivers all is fine, with the 295.XX I suffer from a 'corner case' & quite mysterious bug, works fine for a min. of 3 restart cycles, then get a complete failure to restart/shutdown or switch VT*'s somewhere between the 4th & 8th cycle. Happens like clockwork
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564)

That's the "growing delay / performance decrease" we talked some times, right? 

> **mc4man said:**
> 
 - Freezing touchpad. We discussed it in OO, it wen't directly to PP and was fixed. Now, of course, its: no sign of issue here at all - when it happens to you are you seeing 2 syndaemon instances or is it another cause?
I don't see two instances so far, will check more often to make sure. synclient ToupadOff=0 fixes it immediately, which is why I'm assuming it's the same bug. Incredibly frequent, like 9 out of 10 times I turn the laptop on. I'm absolutely sure it had stopped happening maybe a month ago or so.

> **mc4man said:**
> 
On the other hand I see some other issues not widely reported & still get this out of the blue breakdown in smooth scrolling - very obvious in gedit on large  files, scrolling becomes like sliding on ice.
I haven't noticed this one... will check.

Regards,
Effenberg

PS: You know what, I'll just format all machines. At this point I need to be absolutely sure I am seeing default packages/settings, otherwise I'm going crazy or something.

---

### Post by ventrical on 2012-04-07
> **mc4man said:**
> I would guess unless your install has local issues what you're seeing then may be hardware based

For instance on couple of day old non modded install - 
- Infinitesimal small window grabbing area:no problem
- Impossible to grab overlaying scrollbar: can grab fine
-nvidia-current delay when switching to VT-Any to VT-7 and back. - 

With the 290.10 drivers all is fine, with the 295.XX I suffer from a 'corner case' & quite mysterious bug, works fine for a min. of 3 restart cycles, then get a complete failure to restart/shutdown or switch VT*'s somewhere between the 4th & 8th cycle. Happens like clockwork

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/940564)

- Freezing touchpad. We discussed it in OO, it wen't directly to PP and was fixed. Now, of course, its: no sign of issue here at all - when it happens to you are you seeing 2 syndaemon instances or is it another cause?

On the other hand I see some other issues not widely reported & still get this out of the blue breakdown in smooth scrolling - very obvious in gedit on large  files, scrolling becomes like sliding on ice.


 I haven't had any of  the touchpad problems (Dell Inspiron/AcerAspire/Acer Extensa). The scrollbar is working great here on my Dell Opti. (will soon check my NVidia tower)

The Dell problem I had was this: I was having cooling fan probs. The fan would work when I tested it out of the box but once it was installed back in the machine it would fail. The 2.80GHz P-4 was hot enough to fry an egg on but those chips have thermal shutdown protects (so I saved my P-4) The problem was also with the hdd-Seagate Baraccuda, EIDE Ultra. It was causing the Dell to be slow to start.

---

### Post by ventrical on 2012-04-07
On my NVidia machine I have impossible to grab windows for resizing. just no way, no how , even from the lower right-hand corner. (3.2.0-22) Unity 3D

Edit* But on Unity 2D there is no problem grabbing and resizing!!??  Unity Problem then ??

---

### Post by mc4man on 2012-04-07
> Quote:
Originally Posted by mc4man View Post
-nvidia-current delay when switching to VT-Any to VT-7 and back. -
With the 290.10 drivers all is fine, with the 295.XX I suffer from a 'corner case' & quite mysterious bug, works fine for a min. of 3 restart cycles, then get a complete failure to restart/shutdown or switch VT*'s somewhere between the 4th & 8th cycle. Happens like clockwork
[https://bugs.launchpad.net/ubuntu/+s...rs/+bug/940564](https://bugs.launchpad.net/ubuntu/+s...rs/+bug/940564)
That's the "growing delay / performance decrease" we talked some times, right?

This seems to affect only a small number of nvidia adapters (8400m here) or maybe only some adapters on some mobo's (Dell here

It's actually much worse - sometime after the 3rd restart/bootup & before the 8th restart/bootup,  when trying to shutdown or restart the display shuts down immediately & the machine never powers down or restarts.
Additionally no VT other than 7 can ever be started, just a black screen (Other Vt's can be opened till the shutdown/restart fail happens

I can reset the counter so to speak thru various means, then it starts over again - 3 good at a min, then it will fail again
Really wierd

As far as the cursor freeze - most occurances were found to be from 2 things - 
On a live session or the 1st login on a fresh install lightdm was starting a syndaemon instance. Additionally g-s-d does so the cursor would freeze. That was fixed in lightdm

The other most common was when g-s-d crashed & restarted or other such events,  it would then start up syndaemon again, this would cause 2 instances & a freeze in short order. This was fixed in g-s-d recently and then modified to go back to the  2 sec timeout but allow cursor movement, just no clicks (-t option

debian/patches/10_smaller_syndaemon_timeout.patch:
    - don't change delay, use -t option to block the clicks (lp: #962958)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/962958](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/962958)

---

### Post by ventrical on 2012-04-07
"- nvidia-current delay when switching to VT-Any to VT-7 and back.  Eventual screen corruption. Was reported by me in NN, OO, PP. Was fixed  about a month ago annnnnd: Back"

 I can't even get a terminal.. I get this exaggerated grey menu bar on top. Will try 3D.

Nope .. no VT with 3D either. Just VT-7. The rest , blank space.

---

### Post by keithpeter on 2012-04-07
Hello All

xeon HP desktop pc xw6200 with nvidia GT520 card and the proprietary drivers installed by jockey. Installed from Beta2 cd-rom on Thursday and updated daily including just now. Unity, Unity2d, Gnome-Shell/Classic and xfce4 (not Xubuntu) Sessions available.

In Unity;

Infinitesimal small window grabbing area: grab area extends to about the width of the shadow under the windows. Can grab and drag top, sides, bottom and corners ok

Impossible to grab overlaying scrollbar: Nautilus window made very small, can grab the scroll bar ok

Sound: not relevant its Intel ICH5/Analog Devices AD1981B according to alsamixer and seems to be working fine

VT7 switching: can get vt1 and can switch back with around 5 seconds delay. I have 2 users running, me as admin and 'default' as standard. Switching back to VT7 brings me to log-in screen and I have to switch to my user

---

### Post by ventrical on 2012-04-07
Ok.. I got VT switching back with 3.2.0-22 but not with 3.3.n-nRC.

---

### Post by ventrical on 2012-04-07
> **mc4man said:**
> This seems to affect only a small number of nvidia adapters (8400m here) or maybe only some adapters on some mobo's (Dell here

It's actually much worse - sometime after the 3rd restart/bootup & before the 8th restart/bootup,  when trying to shutdown or restart the display shuts down immediately & the machine never powers down or restarts.
Additionally no VT other than 7 can ever be started, just a black screen (Other Vt's can be opened till the shutdown/restart fail happens

I can reset the counter so to speak thru various means, then it starts over again - 3 good at a min, then it will fail again
Really wierd

As far as the cursor freeze - most occurances were found to be from 2 things - 
On a live session or the 1st login on a fresh install lightdm was starting a syndaemon instance. Additionally g-s-d does so the cursor would freeze. That was fixed in lightdm

The other most common was when g-s-d crashed & restarted or other such events,  it would then start up syndaemon again, this would cause 2 instances & a freeze in short order. This was fixed in g-s-d recently and then modified to go back to the  2 sec timeout but allow cursor movement, just no clicks (-t option

debian/patches/10_smaller_syndaemon_timeout.patch:
    - don't change delay, use -t option to block the clicks (lp: #962958)
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/962958](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/962958)


Same here .. Geforce G210. But I can get VTs now with 3.2.0-22 but not with 3.3.n-nRC

---

### Post by mcellius on 2012-04-07
Pilot6:

> I do not quite understand why people use Ubuntu with gnome, etc. The  purpose of Ubuntu is to have everything out of the box. If you do not  like default DE, why do not you install e.g. Debian and add any DE you  like?

It's interesting you should say that: I feel exactly the opposite.  I agree that one should use whatever DE one prefers, but I've never felt that the "purpose of Ubuntu is to have everything out of the box."  It's Linux.  It should be what I want it to be, not what someone else thinks it should be.  I'm limited by time and by my programming skills, of course, to using what's available, but within those limits I like to have choices.  And if someone comes up with a DE that I really like, I see nothing wrong with using it on whichever distro I prefer.

I guess I don't understand why people use a completely distro when all they want to do is change the DE.

---

### Post by sgage on 2012-04-07
> **Pilot6 said:**
> I do not quite understand why people use Ubuntu with gnome, etc. The purpose of Ubuntu is to have everything out of the box. If you do not like default DE, why do not you install e.g. Debian and add any DE you like?

For me, I stick with Ubuntu mostly because of the repos. I do like Fedora, but it's just a bit more fiddly, and I prefer dpkg to rpm. Ubuntu has a few other touches that make it worthwhile, even if one doesn't use Unity.

---

### Post by buzzmandt on 2012-04-07
> **Pilot6 said:**
> I do not quite understand why people use Ubuntu with gnome, etc. The purpose of Ubuntu is to have everything out of the box. If you do not like default DE, why do not you install e.g. Debian and add any DE you like?

You're so wrong, for everything out of the box you'd have to use linux mint or mepis or one of those that has all codecs and drivers installed by default.  youtube videos and dvd readers from a live session or straight from fresh install with nothing more to do.  That's everything out of the box.

We use ubuntu with non default de because we like the ubuntu base, we like the somewhat bleeding edge but we don't like something about unity.  not that it's bad we're just looking for something else.  Some of us even use something else with unity (different DE sessions for different reasons or different feels or what mood strikes us).

> why do not you install e.g. Debian and add any DE you like?
why not install ubuntu and add any DE we like, that's part of the fun. (unity fan boy alert. lol)

---

### Post by xyzzyman on 2012-04-09
White-screen issue with virtualbox and other apps:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938658)

This is the first time in awhile I've been able to switch between text and graphical VT's quickly for the first time in awhile though.

---

### Post by ronacc on 2012-04-09
@ effenberg0x0 I'm seeing some of those issues too on my test box (AMD64 + Nvida ) running G-S . more disconcertingly after an update 2 days ago some of them showed up on one of my work boxes running 10.04 . The absurdy small grab area and also likewise click area on desktop icons . Also even though I am set for single click to open it now takes a double click on desktop icons but not on folders in nautilus file manager . Only security updates were installed , I'll get the list and post it .

---

### Post by balloons on 2012-04-09
> **effenberg0x0 said:**
> At this point I'm pretty used to the black magic that makes things that were fixed come back always a couple days before the RC, so we can have the pleasure of seeing bugs persisting from one cycle to another despite our work. Today however, thinks look extra special:

- Infinitesimal small window grabbing area: Back
- Impossible to grab overlaying scrollbar: Back
- No sound on ALC892 (wow, this one worked this entire cycle after I interacted with David Heningsson via LP, he found the bug and updated the kernel module. I have no idea how is it even possible to break it again?): Back
- nvidia-current delay when switching to VT-Any to VT-7 and back. Eventual screen corruption. Was reported by me in NN, OO, PP. Was fixed about a month ago annnnnd: Back
- Freezing touchpad. We discussed it in OO, it wen't directly to PP and was fixed. Now, of course, its: Back
- Virtual-Machine Window turns into non-interactive White-Square when switching screens. I haven't seen this one since OO. And it's Back.

And others, many others I thought were gone. (I mean they *were* fixed, I'm **sure** of it). It's really frustrating for me.

I'm beginning to be pretty sure that it happens every cycle, always when we are a couple days from release. I can't understand it. I'm not even sure how it would be possible. Does anyone have any idea?

Regards,
Effenberg

Effenberg, i can confirm the VT switching issue on my box at least :-( 

Not to add fuel to the fire here; I want you to think seriously about this. Generally the idea with QA and testing is that once you fix a bug (since you apparently had a gap in your testing that allowed you to ship the bug!) you add it to the testing suite so that you never regress and ship that bug again (aka, if it comes back your build fails). 

Now, many of these issues are spread across interactions between codebases; some of which we don't even have access to. That said, how could we apply the same principles here to prevent regressions? Hardware specific bugs are tricky as well, but there are universal ones listed here.

As to why it happens.. well I'll toss some ideas out:

For the kernel patches, the team has to decide what patches to keep, why, etc. They probably dropped the patch that fixed your issue (since upstream changed), and likely assumed the underlying problem was fixed and the patch no longer needed. Additionally, the patch likely doesn't work with the newer kernel and would need to be updated. 

On the others like sound and video, again it's likely a patch thing. If the fixes are made on a distro level, it's easy for them to break when you pull the new upstream package. In upstream the bug is still existing, and if your patch fixes it in the old, it needs applied to the new also. This load of distro patching should be avoided and is not best practice. I have **NO KNOWLEDGE** that this is occurring in these case (please don't go harassing developers on this); ubuntu has a policy to keep the delta between it and debian as small as possible and debian has the same between it and the upstreams.

---

### Post by effenberg0x0 on 2012-04-09
Hi Nick, this is a really short/quick reply (from smartphone - check the email I sent to you earlier - bad day today). A quick look at threads from last two days here and at general help was enough for me to see that others are mentioning previously fixed bugs. You're right: If fixed bugs return (and I am convinced they eventually do) it's a processes failure. I'm not sure it's testing fault though, would like to consider the devs side of it. There are limits to testing. Lets talk it in details soon.
Thanks, Effenberg
> **guitara said:**
> Effenberg, i can confirm the VT switching issue on my box at least :-( 

Not to add fuel to the fire here; I want you to think seriously about this. Generally the idea with QA and testing is that once you fix a bug (since you apparently had a gap in your testing that allowed you to ship the bug!) you add it to the testing suite so that you never regress and ship that bug again (aka, if it comes back your build fails). 

Now, many of these issues are spread across interactions between codebases; some of which we don't even have access to. That said, how could we apply the same principles here to prevent regressions? Hardware specific bugs are tricky as well, but there are universal ones listed here.

As to why it happens.. well I'll toss some ideas out:

For the kernel patches, the team has to decide what patches to keep, why, etc. They probably dropped the patch that fixed your issue (since upstream changed), and likely assumed the underlying problem was fixed and the patch no longer needed. Additionally, the patch likely doesn't work with the newer kernel and would need to be updated. 

On the others like sound and video, again it's likely a patch thing. If the fixes are made on a distro level, it's easy for them to break when you pull the new upstream package. In upstream the bug is still existing, and if your patch fixes it in the old, it needs applied to the new also. This load of distro patching should be avoided and is not best practice. I have **NO KNOWLEDGE** that this is occurring in these case (please don't go harassing developers on this); ubuntu has a policy to keep the delta between it and debian as small as possible and debian has the same between it and the upstreams.

---

### Post by balloons on 2012-04-09
> **effenberg0x0 said:**
> Hi Nick, this is a really short/quick reply (from smartphone - check the email I sent to you earlier - bad day today). A quick look at threads from last two days here and at general help was enough for me to see that others are mentioning previously fixed bugs. You're right: If fixed bugs return (and I am convinced they eventually do) it's a processes failure. I'm not sure it's testing fault though, would like to consider the devs side of it. There are limits to testing. Lets talk it in details soon.
Thanks, Effenberg

Effenberg; feel better -- no rush and no worries. Agreed, this is another topic worth discussing a bit more. I also agree on where the work likely lies -- I'm using the word testing here, but devs should be running tests as well. This level of regression prevention testing should be occurring at there level, ala unit testing, etc. You reproduce the bug with a test, fix it, and add the junit or whatever to your unit testing suite. Build won't be published to the tree with that bug ever again :-)

---

