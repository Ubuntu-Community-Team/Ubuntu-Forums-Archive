---
title: "siftfox iceweasel or firefox?"
date: 2007-10-01
forum: The Cafe
---

### Post by maduranga on 2007-10-01
hello... can someone tell me what is best to use? and what do you? post  any advantage or disadvantage of your preferred browser.  and any useful guidance to get iceweasel is also welcome

---

### Post by pay on 2007-10-01
They are all based on the same source code by mozilla. Iceweasel has some artwork and other things removed so that it can be distrubuted with debian. Swiftfox is firefox with a few performance optimisations compilled into it (you could compile your own firefox with these extras). Swiftfox is not free software. You have probably already heard about firefox. 
 
I would recommend firefox (unless you have philosophical reasons for using iceweasel) as it gets updated with Ubuntu.

---

### Post by kerry_s on 2007-10-01
that's so funny, those are all firefox. iceweasel is a change of name & icon to make it free. swiftweasel is firefox optimized to your cpu.

---

### Post by maduranga on 2007-10-01
thanks :)   I like firefox, but like to try swiftfox or swiftweasel. is it neccessory to remove firefox before install swiftfox? where i can get it?

---

### Post by pay on 2007-10-01
I think that swiftfox installs to /usr/lib64/swiftfox and /usr/bin/swiftfox so it shouldn't be needed to remove firefox. You can find swiftfox here [http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by GSF1200S on 2007-10-01
> **pay said:**
> I think that swiftfox installs to /usr/lib64/swiftfox and /usr/bin/swiftfox so it shouldn't be needed to remove firefox. You can find swiftfox here [http://getswiftfox.com/](http://getswiftfox.com/)

Ive always meant to ask whether or not one can run Swiftfox on a core2duo (2.16)? Obviously I wouldnt notice much difference, but im the kind that will spend 3 hours to make my OS boot 5 seconds faster (ha, I should install Gentoo :))

---

### Post by glotz on 2007-10-01
I use Swiftfox and I think it is a bit faster. It's also available in the repos. The actual quarrel over the icons which gave birth to Iceweasel has already blown over.

---

### Post by pay on 2007-10-01
You would probably want this one [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_2.0.0.7-1_prescott.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_2.0.0.7-1_prescott.deb) but i severly doubt that you would notice any difference. Besides, I would recommend using the real firefox for updates or if you wanted to have the processor improvements, compile it yourself as swiftfox isn't free software.

---

### Post by GSF1200S on 2007-10-01
> **pay said:**
> You would probably want this one [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_2.0.0.7-1_prescott.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_2.0.0.7-1_prescott.deb) but i severly doubt that you would notice any difference. Besides, I would recommend using the real firefox for updates or if you wanted to have the processor improvements, compile it yourself as swiftfox isn't free software.

Well, in that case, I will just compile it myself. Might be fun- I know in a 64bit OS you can install a 32bit variant in a temp directory (/opt ?).. Ill prolly compile a new Fox in that location so I can see if there is any difference.

---

### Post by meho_r on 2007-10-01
Well, if you want to avoid plugins mess (Java and Flash) maybe Swiftfox is the best choice - it can be easy installed through Automatix together with java, flash, mplayer... plugins. Although, I noticed that Swiftweasel is faster than Swiftfox which is faster than Firefox. The problem with Swiftweasel is that some extensions don't work and I have problem with plugins :( For Swiftweasel, maybe you want to check [http://tghc.org/forum/viewforum.php?id=3]("http://tghc.org/forum/viewforum.php?id=3")

Sad thing is that Swiftfox 2.0.0.7 doesn't work for me :(

---

### Post by pay on 2007-10-01
It's probably best to install it to /usr/lib32 or /usr/local/lib32... /usr/local is normally the folder that software that you compilled goes to (without telling the compiller a different path ie ---prefix=/usr)

---

### Post by mrgnash on 2007-10-01
I've had problems with crashing and slowdown with all of them, so I use Epiphany for the most part... and only resort to Swiftweasel when I need to use a particular extension, or site that checks for the Firefox user-agent.

---

