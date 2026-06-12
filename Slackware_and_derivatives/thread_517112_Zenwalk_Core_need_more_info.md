---
title: "Zenwalk Core need more info"
date: 2007-08-04
forum: Slackware and derivatives
---

### Post by johnny4north on 2007-08-04
> Zenwalk's Core Edition is a Zenwalk system without X applications. Zenwalk-core is intended to be used as a starting point to build a custom desktop system or a server system, and for users with limited space on their disk, or great perfectionists wanting to build their personal desktop system themselves.  
will "Zenwalk Core"{min cd install} have pcCard/network support for FA 410? If not are there other CLI's installs that will work w/ this nic.  i have done a CLI install on my main game box, but i have concerns about doing it on a laptop.
i repaired my laptop by replacing cpu w/ amd k2 450mhz.  plays dvd's choppy(10 fps) w/ dsl, pup, and Zenwalk 4.6.1(which worked great w/ org. amd 550&cyberblade7 w/192 sys. mem).  This is why i want a custom install.  thanks in advance. :)very happy to have the ZenBox up and running.:)

---

### Post by bonzodog on 2007-08-04
Hrm....I'm not sure.

i have already installed zen core on a desktop machine, but did not have any awkward h/w to worry about.

Zen Core does have a lot of stuff driver wise, so if it worked by default in zenwalk default, then it should work, as zen core is pretty much zen with all the xap/x stuff stripped out, and nearly everything else left in.

---

### Post by johnny4north on 2007-08-04
thanks Bonzodog, i believe you are exactly correct, the fa 410 is working, but just now realized that it needs to be configured.:oops: i made the assumption that if the two lights where green{active and 100 Mbits}, it would be working.  i fought with router all night, and other issues lol.  i tried the xubuntu cli install [Sudo aptitude install xfce4 thunar xdm xorg synaptic dillo idesk], it installed easily, but was very slow(didn't like cyberblade7 i bet:([irq11 conflict]). im too excited, slow is fast in the terminal.  i made alot of mistakes, also learned a bunch.:-D

---

### Post by johnny4north on 2007-08-06
\\:D/ Success we are watching dvd(@20fps:) problem's; keyboard SIIG/numberlock caused cli errors, Cyberblade7=some distro's set as vesa, on top of it all was the soundcard/modem combo(M3/winmodem) which hogged IRQ11. The netgear FA 410 was @ irq 11, and when i configure it, the modem would default on during the netpkg cli command.  Solutions; format drive reiserts. Zenwalk 4.2(because it was easy to turn off services{esp numberlock}, and recognize the cyberblade7 vid card.)  the modem could also be turned off during the install. the netgear fa 410 works\\:D/. the ZenBox rocks on day and night.
the Zenwalk core didn't work for me(im sure i could have eventually figured out how to disable the winmodem) im currently happily locked in on Zenwalk 4.2.  here is some links that helped me w/ Zenwalk install to the HP N3350 - [http://wiki.zenwalk.org/index.php/Index:HOWTO](http://wiki.zenwalk.org/index.php/Index:HOWTO) 
near the bottom of page- [http://humanreadable.nfshost.com/journal/index.htm#journal_2006_2007](http://humanreadable.nfshost.com/journal/index.htm#journal_2006_2007)
i wanted a ultra lean Zenbox- ding. idea. maybe cli the mplayer?!  rebooted the computer back to the cli, then logged-in(i log into the cli, then run the startx command).  mplayer dev/dvd framedrop -fs  worked best for me.  you can play anything with the mplayer[@ the CLI] cd dvd vob files, etc. way cool.  here is the link to mplayer manual -   [http://www.mplayerhq.hu/design7/info.html#docs](http://www.mplayerhq.hu/design7/info.html#docs) :)

---

