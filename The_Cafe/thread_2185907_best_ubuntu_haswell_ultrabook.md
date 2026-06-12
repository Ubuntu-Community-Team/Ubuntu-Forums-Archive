---
title: "best ubuntu haswell ultrabook"
date: 2013-11-04
forum: The Cafe
---

### Post by nerdcommander on 2013-11-04
I hate to be "that guy" that asks a gearhead harware question, but...
I'm in the market for hardware and I want something powerful (haswell i7) and light and thin with a 13"ish screen - therefore an "ultrabook". 
Budget is palm-sweatingly maxed at $2000US. 
Not a linux noob, but not super experienced either so I want this new machine to run Ubuntu (and maybe another Ubuntu based distro later) smoothly out of the box.
Considering a Dell XPS13 developer when/if the new version is released (supposedly Nov), and have considered the new System76s (reviews of quality make me think), but thought I'd gather opinions while I wait.
What do folks think?

PS - I'm not buying an apple, mostly cause they don't support their expensive, niche hardware for the 4+ years I want out of a $2K laptop, but why do they have such nice stuff and many other manufacturers can't put together a nice machine? Is it really just market share? Maybe that is a topic for a different post...

---

### Post by Miguel on 2013-11-05
In my experience, enterprise Dells are well supported. I've got a fully souped-up E6220 that runs Ubuntu (and RHEL 6) like a charm. Both the haswell based Latitude E7240 (12.5", 1.3 kg) and the E7440 (14", 1.6 kg) are ubuntu certified, and would expect nothing but flawless compatibility. There are two caveats: first, I don't think the Dells are worth the standard price. And second, it seems the screen in the E7240 is the same godawful panel as in my E6220, which is by far the worst part of it (low res, low brighntess, lower contrast, horrible viewing angles). 

You could also go the thinkpad way. The X240s looks extremely interesting, with the IPS screen (may want the 1080p touch one, but I don't get touch) and the dual battery system. It's a shame they got rid of the seven-row keyboard layout, and whether the new trackpoint system will work well is an open question. These systems should accept linux without issues, just make sure you get as many intel components as possible.

I'm personally pretty fed up with the hardware industry, and have just gotten through my employer a new 13" retina MBP. I don't like macports, I don't like apple, and I don't like having to deal with Escape sequencies instead of Alt+. on the terminal (UK layout). But still, I'm not 20 anymore, and there's no chance in hell I'm going through the nightmare 1366x768 ****** quality panels. I'll run a Debian VM as a compromise and be done with it.

---

### Post by nerdcommander on 2013-11-06
Miguel-
Thanks for the two suggestions, I'll look into them for sure. I've got a "corporate" Lenovo T420s right now and don't like it much - like everything, there are pros and cons...
Currently considering an ASUS UX302-LA with some upgrades (more ram and ssd).

---

### Post by sideaway on 2013-11-08
I'm not an expert on Ubunu compatibility, but have you considered the HP Folio series? I love the build quality on them... However I do wish my Elitebook was better supported with Ubuntu, not sure how well the folios fare? I can steal my GFs one and try it? :P

---

### Post by scythian.trigon on 2013-11-08
Dell E6220 - is it Haswell or Ivy Bridge ?
Redhat kernel is not cutting edge and some Haswell features are not available on older kernels 
[http://www.centos.org/forums/viewtopic.php?t=7553](http://www.centos.org/forums/viewtopic.php?t=7553)

---

### Post by nerdcommander on 2013-11-11
got two different Asus UX302s (in series) from best buy and returned them both since  the cut out plate that goes between the keys would pucker up and never  stick down. Key board also felt pretty flexy even on the display model in the store but that one  didn't have the pucker problem. Other than that, I liked the machine  just fine - good looking, quiet, seemed to run pretty cool and battery  was pretty good on the full cycle I got. Don't want to drop $1K for a  machine with questionable build quality. YMMV.
Never did get to test linux to see how it would do, which is a bummer.
The HP Folio Haswell version doesn't appear to be out yet, will keep an eye on it, thanks.
Still on the hunt for a haswell ultrabook, now considering a lenovo yoga 2 pro...

---

### Post by help_me2 on 2013-11-11
I have a Dell Latitude E5520 which is about 3 yrs old, and runs ubuntu flawlessly. They're decent machines, and built for the long haul. A little bit pricy, but good.

---

### Post by Miguel on 2013-11-13
> **scythian.trigon said:**
> Dell E6220 - is it Haswell or Ivy Bridge ?
Redhat kernel is not cutting edge and some Haswell features are not available on older kernels 
[http://www.centos.org/forums/viewtopic.php?t=7553](http://www.centos.org/forums/viewtopic.php?t=7553)

The E6220 is actually Sandy Bridge (released Fall 2011). The Ivy Bridge equivalent is the E6230. They're identical except the chipset and a slightly brighter panel. There's no full-voltage Haswell ultraportable in Dell's lineup. The haswell ultraportables Dell has are the E7240 and the E7440. Very sadly, the matte panel in the E7240 is as horrible as in the E6220. 

FWIW, RHEL 6.2 ran fine on the E6220 for the week I had it installed there, as long as one disabled VT-d on the BIOS.

---

### Post by Xtyn on 2013-11-14
I'd say Samsung ativ book 9 plus, but I haven't seen it with haswell, just an i7 ivy bridge. They are both 22nm anyway, so who cares, really?

Edit: they are available with haswell too.

---

### Post by nerdcommander on 2013-11-16
in the end, i decided on the lenovo yoga 2 pro:
i7 processor, 8 gigs RAM, 240 gig ssd
wiped windoze and installed ubuntu 13.10
the screen resolution is INSANE (3200 x 1800) so i reduced it to 1920 x 1080 which is the same ratio (16x9) and followed the instructions from the first post in this blog (actually about arch linux) - [http://keithcu.com/wordpress/?p=3270](http://keithcu.com/wordpress/?p=3270)

the commenter "Eric" on the above link says:
after installing Ubuntu I permanently enabled WIFI with this…
sudo vi /etc/modprobe.d/blacklist.conf
and add this to the file –> blacklist ideapad-laptop
 to enable screen brightness with working +/- buttons i did this…
 sudo vi /etc/default/grub
change this –> GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
to this –> GRUB_CMDLINE_LINUX_DEFAULT=”acpi_backlight=vendor quiet splash”
then run this –> sudo update-grub2

i followed these instructions and the thing works great for me now. the touchpad is insanely sensitive and i'm working on that, otherwise, there us ubuntu joy for me.

@Xtyn I considered that but it is more expensive and samsung doesn't generally work as well with ubuntu as far as i could tell - but thanks for the suggestion!

---

### Post by v1k1ng1001 on 2013-11-17
Lenovos are awesome.  Good choice!

---

### Post by Xtyn on 2013-11-17
> **nerdcommander said:**
> @Xtyn I considered that but it is more expensive and samsung doesn't generally work as well with ubuntu as far as i could tell - but thanks for the suggestion!
I had to decide between a thinkpad and a samsung series 9. I chose the samsung and it's working fine with ubuntu and other distributions.
Anyway, good luck with your new laptop. :)

---

### Post by Warpnow on 2013-11-17
They just upraded the Dell XPS 13 to haswell, which comes with ubuntu by default.

---

### Post by nerdcommander on 2013-11-21
> **Warpnow said:**
> They just upraded the Dell XPS 13 to haswell, which comes with ubuntu by default.

that looks tasty. not shipping til 12/19 and $400 more, but i'm super curious! so far the lenovo is doing well - it's fast, only annoyance is some trackpad issues and the screen resolution is so high that i had to reset it to lower res since some things are so small.

---

### Post by Kaijday on 2013-11-21
Lenovo's are nice.

Recently got myself a Z500 for uni work, runs Ubuntu flawlessly and with a 7 hour battery life.

---

### Post by mi117 on 2014-01-05
@nerdcommander : how is the battery backup going for you ..?

---

### Post by shawn22 on 2014-10-24
> **nerdcommander said:**
> in the end, i decided on the lenovo yoga 2 pro:
i7 processor, 8 gigs RAM, 240 gig ssd
wiped windoze and installed ubuntu 13.10
the screen resolution is INSANE (3200 x 1800) so i reduced it to 1920 x 1080 which is the same ratio (16x9) and followed the instructions from the first post in this blog (actually about arch linux) - [http://keithcu.com/wordpress/?p=3270](http://keithcu.com/wordpress/?p=3270)

the commenter "Eric" on the above link says:
after installing Ubuntu I permanently enabled WIFI with this…
sudo vi /etc/modprobe.d/blacklist.conf
and add this to the file –> blacklist ideapad-laptop
 to enable screen brightness with working +/- buttons i did this…
 sudo vi /etc/default/grub
change this –> GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
to this –> GRUB_CMDLINE_LINUX_DEFAULT=”acpi_backlight=vendor quiet splash”
then run this –> sudo update-grub2

i followed these instructions and the thing works great for me now. the touchpad is insanely sensitive and i'm working on that, otherwise, there us ubuntu joy for me.

@Xtyn I considered that but it is more expensive and samsung doesn't generally work as well with ubuntu as far as i could tell - but thanks for the suggestion!


I was hoping to get some input on how that laptop has treated you in the year since you got it and tried to run ubuntu on it. I was considering getting the yoga laptop. 

Thanks.

---

