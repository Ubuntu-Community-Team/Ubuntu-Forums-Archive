---
title: "Have you ever removed all the extra packages from your system ?"
date: 2006-09-03
forum: The Cafe
---

### Post by xXx 0wn3d xXx on 2006-09-03
I'm just wondering if anyone ever did. I had nothing to do and I removed everything that I didn't need from a default base install and I was able to remove about 350-400 mb of stuff that I didn't use. Has anyone ever done this  ?

---

### Post by fuscia on 2006-09-03
yup. on my old desktop, i stripped it as bare as i could. it only has a 10gig hard drive.

---

### Post by kerry_s on 2006-09-03
Ohh yes, everytime i install i trim that install down, after i finish installing what i need i'll even delete the " /etc/doc " and " /etc/man " files cause i don't use them. I run a server install + fluxbox so it's not really all that much to trim to begin with, but i just don't like crap hanging around i'll never use.

---

### Post by meng on 2006-09-03
I never did strip down my Ubuntu installs, but I have been impressed by the latest PCLinuxOS MiniMe. Rather than start big and get smaller, you start small and add what you need. Some would argue that the default KDE is a bit of bloat to start with, but it runs okay on my hardware. The only other time I seriously did something like that was with a Debian (etch) install. I guess I also did the same when I dabbled with Gentoo and Arch, but I didn't keep those long enough to really count.

---

### Post by Omnios on 2006-09-03
Im pushing 160 gig so realy never bothered

---

### Post by greggh on 2006-09-03
I'd like to remove all the extra packages I don't need, but like most folks fairly new to Linux I don't know which ones they are. Maybe when I learn a bit more I can trim it down.

---

### Post by BrunoC on 2006-09-05
How about a good howto on that? =)

---

### Post by xXx 0wn3d xXx on 2006-09-05
> **BrunoC said:**
> How about a good howto on that? =)

I would write one but it would differ from person to person. (Most of the time) I'll look into it.

---

### Post by xhaan on 2006-09-06
I don't take stuff out unless I'm desperate to get rid of it, if I want a small system I'd rather stuff I don't need not be installed to begin with.

My Debian system takes up 615mb, which really isn't all that small, but I think most of that is taken by xfree86 and XFCE + dependencies... I find it to be just fine for the 2gb hard drive though.

---

### Post by blakegrover on 2006-09-18
I put ubuntu on a machine that only had a 2gb hard drive.  After the install I had only 40 mb of free space.  I removed the man pages and documentation, the example content, evolution, gimp, games, and any services that wasn't running on the computer (bluetooth, pcmcia, etc) and I have managed to get 180mb free now.  But I am still going to try to get some more space back but I don't know where yet.

---

### Post by Bezmotivnik on 2006-09-18
I think that would be a wonderful, Platonic ideal -- but I confess that I'm not 100% sure of what can safely go and what really needs to be there.

Is *anyone*? :-k

---

### Post by mips on 2006-09-18
I think it might be easier doing a server install and then adding only what you need.

---

### Post by henriquemaia on 2006-09-18
Never bothered with that, but I'm a bit curious and willing to try. Maybe I'll do that on a test machine.

---

### Post by bruce89 on 2006-09-18
Thankfully the Edgy ubuntu-desktop allows the removal of various packages (fonts, hplip etc.), so I did remove them.

---

### Post by missmoondog on 2006-09-18
> **mips said:**
> I think it might be easier doing a server install and then adding only what you need.

i might have to try that on the next install. :-)

---

### Post by kerry_s on 2006-09-18
I still trim, even on the server install. I usually get rid of the extra xorg drivers for video cards i don't have, i only keep vesa as a backup, i use the nvidia-glx for my video. I also get rid of all the vim's, i only use nano. I also remove all the remote access stuff, i don't connect remotely. I get rid of that contest thing and report bug. I get rid of the raid stuff and lvm, also as much laptop stuff as can be removed with out uninstalling other stuff. Then i reboot to make sure i still have a working system. Then i install the stuff i want to use right away. After all that then i'll clean up again by deleting the doc and man files. Synaptic i always set up to delete after install so i don't have to worry about that.

---

### Post by brucevangeorge on 2006-09-27
> **mips said:**
> I think it might be easier doing a server install and then adding only what you need.

I trim the server install too. I get rid of alot of crap like the extra xorg drivers that aren't used, floppy utilities, some fat16 support pack... etc. About 50mb total off the server install.


Good apps to use: debfoster & deborphan.

---

### Post by rfruth on 2006-09-27
Lots of free hard disk space here+I'm lazy/busy+the if it ain't broke don't fix it theory seems to apply so no never trimmed mine down.

---

