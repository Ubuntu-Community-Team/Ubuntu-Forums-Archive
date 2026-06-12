---
title: "Debian advice"
date: 2010-03-22
forum: The Cafe
---

### Post by Shpongle on 2010-03-22
Hey all , Im installing a minimal debian system in vb to become more familiar with linux and just so i have a sandbox to try stuff out, Its my first time setting up a minimal install , so i was just wondering are there any essential packages / libraries i should install ? 

i plan to have a no login manager and openbox and il see where i go from there ? , 

I have done dns nfs and samba on cli debian installs in college but that was just one aspect and it was using umllinux ,

any advice is welcomed :-)

---

### Post by Shpongle on 2010-03-22
so far i have installed xorg , iceweasel and openbox

---

### Post by Zoot7 on 2010-03-22
That's about all you need really, it's possible to keep things pretty minimal if you don't go installing a DE.

What branch of Debian are you running? Stable/Testing/Unstable?

---

### Post by Irihapeti on 2010-03-22
OK, this is for Ubuntu, but it should give you some ideas:
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

---

### Post by mkvnmtr on 2010-03-22
I do minimal Ubuntu installs quite often. The first things I install are xorg, xdce4 and synaptic. You choose open box so you probably not be using xfce4. You will find that most of the libraries are downloaded with the programs. As you do your research for sound and such you will find that synaptic makes it easy to see what else will be downloaded.

---

### Post by Irihapeti on 2010-03-22
I have an installation with Openbox, ROX-filer (because it doesn't have many dependencies) and xfce4-panel. I've found that running aptitude with the -R option (no recommended packages) is very handy, because then only the minimum of stuff gets pulled in, rather than lots of unrelated packages.

---

### Post by earthpigg on 2010-03-22
> **Irihapeti said:**
> I've found that running aptitude with the -R option (no recommended packages) is very handy, because then only the minimum of stuff gets pulled in, rather than lots of unrelated packages.

interesting. you found this needed in *debian*?

---

### Post by Irihapeti on 2010-03-23
> **earthpigg said:**
> interesting. you found this needed in *debian*?

No, sorry, I didn't make myself clear: ubuntu. (Shouldn't post when feeling tired.)

---

