---
title: "Thunar's 'tumblred' crashes affect audio ... Alternative desktop suggestion?"
date: 2015-08-10
forum: Ubuntu Studio
---

### Post by marseille2 on 2015-08-10
I have a crash problem with Tumblred that began escalating over the last week ... into a complete freeze/crash of XFCE. It's not that the desktop disappears... it's that it can disappear the file manager, access to any application, and mess with the quality of audio ... while I'm working in an audio program. 

The problem seems to date back some years, and I did see some work arounds ... so I replaced the default file manager with XFE. But I'm not sure this is a solution. Is that good enough, or is it better to change desktops ... and if so ... what's ideal for UbuntuStudio 14.04?

PS: Also see Launchpad [bug]("https://bugs.launchpad.net/ubuntu/+source/tumbler/+bug/1290041").

---

### Post by CrocoDuck on 2015-08-10
Hi!

I don't know how to help with your problem about Tumblred, but I can advise on alternative desktop environments. My suggestion for audio setups is "go as light as you can". Back in the Ubuntu Studio 10.04 days LXDE worked miracles on my old desktop computer. To be honest, that computer (512 Mb of ram, a 64 bit single core processor) is still working pretty good (although I never formatted it) and it is taking care of all my printing - scanning stuff but also of my signal analysis when I work on my electronics projects. On my laptop I don't even run a complete branded desktop environment, but I stacked on top of each other openbox, compton, tint2, conky and wbar. It looks cool and elegant for me ([check it out]("http://crocoduck-oducks.deviantart.com/art/Gray-ArchBang-Remix-485995317")) and it is X-TREMELY light, it really flies and feels a joy to work with, although someone may argue that it is old fashioned. Totally recommended. I was about to link to the [CrunchBang]("http://crunchbang.org/") Linux website for more... but I am shocked to see they ended the development :sad:... Well, you can still have a look at [ArchBang]("http://bbs.archbang.org/") (the distro I am using right now): it should be a good source of info for configuring openbox and its utilities if you are interested (most should work under ubuntu as well).

---

### Post by marseille2 on 2015-08-14
Thank-you, CrocoDuck:)

I did take LXDE for a test drive on Trusty, but it didn't play well PA's jack-sinks -- they wouldn't load. It might be due to a known [issue]("https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting"). Any other suggestions?

UPDATE: I installed the old school [JWM]("http://www.joewing.net/projects/jwm/"), and was nicely surprised. It's not pretty like LXDE but it's really light and I didn't really need to reconfigure anything (save for a few missing apps in the default menu). JWM also didn't mess with the sinks... and I retested LXDE against it (even changed /etc/pulse/default.pa), one more time just to see ... but nothing changed, so I probably have to wait til another update:(

---

### Post by CrocoDuck on 2015-08-15
> **marseille2 said:**
> I did take LXDE for a test drive on Trusty, but it didn't play well PA's jack-sinks -- they wouldn't load. It might be due to a known [issue]("https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting"). Any other suggestions?

Dang. I don't have any other suggestion for the issue since I stopped using pulseaudio years ago. My soundcards support hardware mixing, so I just don't need it.

> **marseille2 said:**
> [COLOR=#000000]I installed the old school [/COLOR][JWM]("http://www.joewing.net/projects/jwm/")[COLOR=#000000], and was nicely surprised.[/COLOR]

That sounds cool! I have a thing for old school light efficient interfaces.

---

### Post by vasa1 on 2015-08-15
> **CrocoDuck said:**
> ...
That sounds cool! I have a thing for old school light efficient interfaces.
1. Re. JWM, you may want to check out [https://lists.launchpad.net/torios/maillist.html](https://lists.launchpad.net/torios/maillist.html). They're using JWM.
2. Re. Crunchbang, there's a bunch of regular Crunchbang users who are taking things forward with "BunsenLabs": [http://crunchbang.org/forums/viewtopic.php?id=39994](http://crunchbang.org/forums/viewtopic.php?id=39994).

---

### Post by marseille2 on 2015-08-24
Thanks vasa1! I'm still dealing with this issue... I'm liking JWM a lot. I spent the weekend testing 3 desktops: JWM, ICEWM, and Fluxbox. So I thought I'd jot this down in case others have similar issues.

I love Fluxbox the most because the mouse rolls so smooth, and the desktop is feather - light. If I was a Firefox user, it would be a winner, but I'm stuck on Chrome ... which blew up the desktop, and sent me into a hard reboot. Come to find out... it's a known and unresolved bug from ages ago. Apparently the generic and commercial versions of Chrome can't redraw. The window stays maximized .... Why it crashed the computer, I dunno. But the Fluxbox packages for Trusty are also out-dated -- 1.3.5, and it's up to the user to compile from source ... since there are no up-to-date PPAs.


ICEWM ... not bad. But not as light as JWM. So it's user's choice here. Neither desktop needs too much reconfiguration ... mainly fine-tuning menus (really simple), but the default install won't get the user lost. I'd say about 90% of the programs installed will show up in the menu... *give or take*. They also both have the left-click desktop menu access which I really like. Just doesn't feel as smooth as Fluxbox. No biggie... the most important thing is that they both play well with PA's jack-sinks (so did Fluxbox ... whereas LXDE was an epic  fail).

---

