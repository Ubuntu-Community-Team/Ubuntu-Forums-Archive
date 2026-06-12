---
title: "Returning from the land of the Gentoo"
date: 2006-09-03
forum: Testimonials &amp; Experiences
---

### Post by .t. on 2006-09-03
As some of you may know, I recently installed, rather built, a Gentoo to compare video performace. I was fed up of Edgy's slow Mesa implementation: only 600FPS in glxgears (I know it's not a benchmark). However, I spent four days getting the programs I wanted built, and everything "working". I was getting 1500FPS on versions equivalent to those in Edgy; except for one: Mesa, which was newer.

I soon became fed up with old GNOME 2.14, so I upgraded to Gentoo unstable; that is, "~x86" keyworded. Things broke during the upgrade, and for two more days I was trying to get things happy. I still hadn't built OpenOffice.org 2.

When I was fed up of partially working "ebuilds" and applications, I decided that stable ("x86" keyworded) was the way to go, notwithstanding its older packages. So. I changed my ACCEPT_KEYWORDS line in /etc/make.conf, removing the tilda. I ran emerge --sync, then emerge --DNuva world, to get the latest Portage tree and "upgrade" the system. Of course, this didn't work. However, I persisted. I ran "emerge -e system && emerge -e world" to rebuild first the base system and then all packages I had opted for completely from scratch, according to their newest allowed version. This didn't work either, and soon I was having trouble, completelty unprecedented, with "coreutils". As you can probably guess, this is a bit of an important package. I rebooted - dunno why - and got many, many udev errors, so I thought, "Hey, I'll rebuild udev". I did, and that didn't fix the problem. I ran emerge -DNuva world again, and it tried and failed to build coreutils. I resumed the process, skipping the package, and everything else was alright. Just not that.

I decided it wasn't worth wasting more time, so I spent another two days building a stable Gentoo. 24 hours to build; 24 hours to configure. Still no OpenOffice.org, and GEdit was refusing to open files. Of course, I hadn't built it with debugging symbols, and I wasn't going to rebuild it. I lived with it, using nano for everything. By the way, NEdit is no good. It works, but Motif is about twenty years old. I suppose if you like that retro look, it's fine.

Later, I left OpenOffice to build overnight. In the morning it was still running, so I decided I would use the computer anyway. I opened up a terminal to build a small something else that I needed, and decided against it once the process had begun. I switched out of Firefox, which was also acting up, closing randomly because of "X errors", and hit Ctrl-C in the terminal. Noooooooo!!! I had killed the OpenOffice build. I couldn't bear to wait so long again; this was the last straw. I was crazed with the amount of wasted time building and configuring, but also obsessed with the power it gave me - both of processing and configurablity.

Nonetheless, I decided I was coming back to Ubuntu. I could live with slow rendering - after all, I was running the testing distribution. Of course, I love Gentoo: it's power and people are wonderful. But I don't really have the time to put in the amazing effort that I now see the Ubuntu and Debian developers do. And I now greatly appreciate that, and, having learnt so much with Gentoo, I understand that it is not easy. It's bloddy difficult, to get a working system: for all of the Ubuntu/Debian users' hardware. So, everybody; stop wingeing, and learn either to wait, to fix it yourselves, or, either way, to appreciate the great favour that you are being done by Canonical, and Debian. It's just awesome.

---

### Post by _tuxman_ on 2006-09-07
It's true that gentoo is indeed a time-consuming distro, but at times, the user may waste even more time than it is necessary by getting a little too much involved with the recompiling thing.

> 
(I know it's not a benchmark).

right, not a benchmark

> 
I soon became fed up with old GNOME 2.14, so I upgraded to Gentoo unstable; that is, "~x86" keyworded.

Changing all system to "~x86" is not such a good idea for new users, it'll get you in more trouble to begin with.
> 
I still hadn't built OpenOffice.org 2.

The binary openoffice package would have saved you some time.
> 
I persisted. I ran "emerge -e system && emerge -e world"

Not a good way of persisting.

> 
 rebooted - dunno why - and got many, many udev errors, so I thought, "Hey, I'll rebuild udev".

Yes, rebooting at that time was probably not a good idea(especially if config files were not consistent and etc-update was needed)

---

### Post by .t. on 2006-09-07
Firstly I must give this advice: do not assume someone a fool unless you know them to be.

Actually I did a lot of research (look for user .t. on the forums), asked whether using ~x86 was a good idea, and I thought (after a smooth install to stable) that I could handle it. I'm generally quite proficient. I used glxgears as it does show some degree of performance, and now I must say I am getting almost the 1500FPS that I did in Gentoo in Edgy. I know, also, how to use /etc/portage/package.keywords. I must reiterate that I did indeed do plenty of research. I had decided to build OOo2 after reading on the Gentoo Wiki that I would not get the full GTK widget set bindings for the application if I emerge'd openoffice-bin, and Firefox wasn't taking too long to build on my Pentium M 725.

I rebuilt system and world to clear up all dependency problems, making sure that system worked, and then that anything different would also get taken account of during the second build of system, and the first build of world. This was my reasoning. Once again, research was key (I remembered this command after reading the GCC Upgrade Guide).

Finally, I do actually know of etc-update and used it plenty. I rebooted after doing to system-world rebuild to make sure all running applications on the system were using the newest build, to try and eliminate any problems. There were no threads on the forum describing my particular problem, and I know that my configuration files were correct. I am not a "n00b". I thought that it may have been a problem with an updated ebuild, or newer code, and that a sync and rebuild was in order to fix the problem.



My original post was made as a synopsis to two weeks of working with the distribution. A lot of that time was spent with a working system. I wrote this post after deciding that I didn't have the time on my CPU to build and configure the system, and only when I was doing that did I realise the amount of work that the Ubuntu devs have put in. The thread was made as a thanks to them, and not a call for abuse.

---

