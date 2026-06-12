---
title: "Ubuntu 14.4 updates"
date: 2014-07-05
forum: Ubuntu, Linux and OS Chat
---

### Post by wolfen10862 on 2014-07-05
Ok peopel I came here from windows so everytbody knows the whole M/S update procedure, heres my thing, anybody use windows 8? try updateing to 9.1 and watch the fun
I dumped windows at Vista SP1 after a forced update that crashed the whole O/S and installed Ubuntu 12, Now I'm at 14, still a little terminal Phobic, but I AM learning.
Heres my thing about Ubuntu, every time I turn the computer on theres some sort of update available for 14.4, some require my password, some don;t but every time i click install, and every time when its done I STILL have a working computer (unlike Windows), I think I had to actualy restart once. I was duel booting with vista so I could pay one game that I loved which on ths old thiong just doesn't run at all through wine or POL, but after that last vista crash and reinstalling wiondows with Linux already there and the whole grunb thing, I now have only Ubuntu 14.4 I completely formatted the entire hard drive includeing the boot sector to a slicked out of the box stats installed it used the hard drive disk utility and started with Ubuntu only.
Even though I am by no means a Linux expert, or anywhere close I now recomend only Linux on every computer, people at work say they have problems with windos, I tell them theres one word to fix all their windows problems.
This operateing system is so good I wish I had started back when I was in eth Navy and saw a box that said Red Hat on it back in eth 80's. Had I dont that I'd be developing with you guys now

---

### Post by deadflowr on 2014-07-05
Not Support.
More like a testimonial.

But since testimonials are closed.

Moved to Ubuntu, Linux, and OS Chat

---

### Post by wolfen10862 on 2014-07-08
Ok thanks, I didn;t mean for it to sound liek a testmonial, but I jst started raveing about Ubuntu.
But it happened again today, turned it on and theres an update, so what do yall do sit around in the spare time and create updates, or what:)

---

### Post by Jonor on 2014-07-08
Go into the Software and Updates application and adjust for less frequent reminders about updates.

---

### Post by grahammechanical on 2014-07-08
> [COLOR=#000000] in the spare time[/COLOR]

That's about it. A lot of Ubuntu development work is done by people employed by a company called Canonical but there is also a lot of development work done by Community volunteers. I would included maintaining the software packages in Ubuntu in this community work. Also to be included is testing of the next Ubuntu release under development.

Do you have some spare time?

[http://community.ubuntu.com/](http://community.ubuntu.com/)

Regards.

---

### Post by Bucky Ball on 2014-07-08
I personally have update notifications set for once a week, but do it manually fairly regularly anyway. You could switch notifications off completely and:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... to update every week or so.

The fact there are regular updates is a good thing; bug fixes, general improvements, and things get better and more stable. Not to mention the importance of regular security updates being rolled out. I'm more than happy about that. ;)

---

### Post by 3rdalbum on 2014-07-09
Red Hat wasn't out in the 80s! The Linux kernel (the bit that talks directly to your computer) has only been around since the early 90s.

Linux was not user-friendly in the 1990s. I wasn't on Linux then, but I hear that you needed to hand-craft your own Xorg.conf configuration file. If you got it wrong, you might blow up your computer monitor! A bit primitive back then and you probably wouldn't have liked it. Linux has definitely come a long way since then, though, and I'm glad you like it today.

---

### Post by mastablasta on 2014-07-09
> **3rdalbum said:**
> 
Linux was not user-friendly in the 1990s. I wasn't on Linux then, but I hear that you needed to hand-craft your own Xorg.conf configuration file. If you got it wrong, you might blow up your computer monitor! A bit primitive back then and you probably wouldn't have liked it. .

i think even in first redhats. i was so happy when i got the KDE to load...

and also for devices you need to find them recognise them and then set it up to load them etc.

i abandoned Linux quite fast as i couldn't get the dial up modem to work. it was supposed to work but i couldn't get it to work no matter what. had the book and all.. even internet access. and at the time there wasn't so much documentation on the web.

---

### Post by cariboo on 2014-07-10
> **3rdalbum said:**
> Red Hat wasn't out in the 80s! The Linux kernel (the bit that talks directly to your computer) has only been around since the early 90s.

Linux was not user-friendly in the 1990s. I wasn't on Linux then, but I hear that you needed to hand-craft your own Xorg.conf configuration file. If you got it wrong, you might blow up your computer monitor! A bit primitive back then and you probably wouldn't have liked it. Linux has definitely come a long way since then, though, and I'm glad you like it today.

My first distro was RedHat 5.2 Desktop in 1998, it had a whole suite of ncurses based tools to help you set things up.There was a message during graphics setup, that warned if you set the vertical and horizontal refresh rates to high, you could blow up your CRT monitor, but I never heard of anyone doing that.

As for updates, there is a 14.04.1 point release coming up on July 24th, so doing a:

```
sudo apt-get update
sudo apt-get dist upgrade
```

should get you into the point release.

I'm running Utopic Unicorn (14.10) so I do upgrades at least twice a day, and except for weekends there are always quite few every time I open up synaptic.

That's actually one of things I like about running a Linux distribution, you can do updates and the system is still usable, and they usually don't take very much time. For example I have a system in my garage that doesn't get turned on very often, this afternnon I fired it up to look for parts for my weed trimmer, and I got a notification that therw were 77 updates available. I mentioned this to my brother-in-law who is your typical Windows user, and isn't aware of any other operating systems, except for those on his tablet and smart phone. He was very surprised that the 77 updates and their installation only took about 5 minutes. He was expecting the system to be the same as Windows, and be virtually unusable for at least the rest of the day, and would need to be rebooted several times in order to complete things.

---

