---
title: "After upgrade the Terminal won't open"
date: 2015-09-23
forum: Ubuntu Development Version
---

### Post by awamunro on 2015-09-23
After the recent update to Kernel 4.2.11 I cannot open a terminal either from the dash or with ctrl>alt>t
The software updater reports "You have stopped the update. Try again or Quit"
Any ideas please?
The only way I can update and upgrade is via synaptic.
Sony viao laptop VGN-NR10E Ubuntu Wily Werewolf i386
It is OK on my 64bit desktop.

---

### Post by zika on 2015-09-23
> **awamunro said:**
> After the recent update to Kernel 4.2.11 I cannot open a terminal either from the dash or with ctrl>alt>t
The software updater reports "You have stopped the update. Try again or Quit"
Any ideas please?
The only way I can update and upgrade is via synaptic.
Sony viao laptop VGN-NR10E Ubuntu Wily Werewolf i386
It is OK on my 64bit desktop.[http://ubuntuforums.org/showthread.php?t=2295530](http://ubuntuforums.org/showthread.php?t=2295530) might have some answer(s) for You.
As for update/upgrade try```
sudo apt-get install-f
```in tty to remedy possible error in apt tree...

---

### Post by jimmy-frydkaer on 2015-09-25
Had the same problem on my wily install - worked around it by installing Terminator from synaptic. Now, when I press ctrl+alt+t I get the terminator terminal emulator which works just fine for me.

---

### Post by awamunro on 2015-10-04
The software updater still fails with "You have stopped the check for update" button for "Check Again" gives the same result.
64bit Kernel 4.2.0.14 and 32bit on laptop.

---

### Post by dino99 on 2015-10-05
if you have installed some ppa's packages, then downgrade (via ppa-purge)

---

### Post by zika on 2015-10-05
> **awamunro said:**
> The software updater still fails with "You have stopped the check for update" button for "Check Again" gives the same result.
64bit Kernel 4.2.0.14 and 32bit on laptop.What message do You get when/if You try [http://ubuntuforums.org/showthread.php?t=2296060&p=13361168#post13361168](http://ubuntuforums.org/showthread.php?t=2296060&p=13361168#post13361168) ...?

---

### Post by awamunro on 2015-10-05
That link is this post!!

---

### Post by awamunro on 2015-10-05
I have not installed ppa's. Upgrades can be invoked from the lxterminal which I have installed.

---

### Post by flocculant on 2015-10-05
> **awamunro said:**
> That link is this post!!

What zika is asking you is what you get if you run 

> **zika said:**
> [http://ubuntuforums.org/showthread.php?t=2295530](http://ubuntuforums.org/showthread.php?t=2295530) might have some answer(s) for You.
As for update/upgrade try```
sudo apt-get install-f
```in tty to remedy possible error in apt tree...

You've not responded to that.

---

### Post by zika on 2015-10-05
> **awamunro said:**
> That link is this post!!1. I am old but my hearing is 20/20.
2. No, that link is not to that post.
All the best.

---

### Post by awamunro on 2015-10-05
> **flocculant said:**
> What zika is asking you is what you get if you run 

sudo apt-get install-f
You've not responded to that.

I get 0 to upgrade, 0 to newly install, 0 to remove

---

