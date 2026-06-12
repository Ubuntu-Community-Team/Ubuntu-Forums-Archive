---
title: "If your X broke, how dod you fix it?"
date: 2006-08-22
forum: The Cafe
---

### Post by greggh on 2006-08-22
I popped in a live Slax Popcorn CD. Surfed here and found the fix. Pretty quick and easy.

---

### Post by FISHERMAN on 2006-08-22
used an Ubuntu-live CD.

---

### Post by mostwanted on 2006-08-22
I immediately entered Aptitude and downgraded myself. If I hadn't remembered what the package was called, I wouldn't have been able to fix it myself.

---

### Post by christhemonkey on 2006-08-22
Command line, every time.

(unless its more serious, then ssh in and change it)

---

### Post by jdong on 2006-08-22
A friend of mine got a new 21" flat panel, and asked me to help set it up for him (as it takes some weird resolutions)

Prior to calling me over, he did a dist-upgrade (naturally he didn't tell me about it). So, I'm here trying to get his xorg.conf tweaked, and no matter what I try it always bombs out with "no screens found".


After around 30 minutes of screwing around and finally attempted a LiveCD (which worked flawlessly), I deduced it was some problem with updated packages. From there, a forum search revealed the problem.

--------

This was a pretty severe failure IMO, as it leaves users with a relatively unusable system. I consider myself a Linux "expert user", and it set me back 30 minutes. Fortunately I had nothing important to be doing at the time, but if I did, I would've been pretty ticked.

---

### Post by akniss on 2006-08-22
I didn't boot after the update until this morning, and the fix had already been posted.  So after muttering some choice words under my breath I gave ```
sudo aptitude update
sudo aptitude upgrade
```
a try.  When I saw that xserver-xorg-core was available to be upgraded, I assumed that must be the problem.  Only about 10 minutes out of my life was wasted.  Much better than many, I guess.  My fglrx driver was even still working after the fix!  Hooray!

---

### Post by siimo on 2006-08-22
switched to a different distro :-S

---

### Post by jdong on 2006-08-22
> **siimo said:**
> switched to a different distro :-S

Are you serious? Just curious, because an incident similar to this (but with mysql on the server side) was what made me abandon Gentoo.

---

### Post by slimdog360 on 2006-08-22
It seems as though a lot of poeple upgraded at the worst possible time, like just as they installed compiz or a new monitor, etc.

I upgradeed both my laptop and desktop computer with the bug, the laptop I was online before I restarted it so I was able to use the fix straight away. And the desktop, well I really dont feel like stuffing around fixing it so for the moment I booted into windows.

---

### Post by RedKrieg on 2006-08-22
sudo apt-get dist-upgrade did the trick for me.

---

### Post by leev on 2006-08-22
I just booted into Windows, and found the fix on the forums. Windows had to be updated anyway so it wasn't much of a problem.

---

### Post by vbt on 2006-08-22
sudo aptitude update
sudo aptitude upgrade

This one fixed it. I still love Ubuntu. :p

---

### Post by jimrz on 2006-08-22
update broke X on my desktop last night...tried to reconfigure, still hosed...fired up laptop, ignored the update, came here and found instructions (good previous ver #, etc) for downgrading to a known good ver...I love these forums...fixed X from command line then had to go make some corrections to stuff in xorg.conf that got hosed reconfiguring X.

sure hope today's upgrade works out better than yesterday's!!!
<fingers-crossed> gonna try it again.

EDIT: much better today, both boxes updated...no probs

---

### Post by Donnut on 2006-08-22
Could be if I wanted to get the fix from windoze I may have found it, but I stumbled along blindly trying to fix it with command line for a while then booted from a live CD and found the fix.

---

