---
title: "Kernel panic after installing desktop"
date: 2006-11-11
forum: Sun Sparc Users
---

### Post by mahy on 2006-11-11
Hi y'all,

Last nite i did apt-get install xubuntu-desktop on my Ultra 5. 567 packages. After reboot, just when the bootsplash was about to disappear, the kernel panicked. So i booted the installation CD, mounted the /boot partition and edited silo.conf to display verbose boot instead of the 'quiet splash'. Then i saw the whole process. It even reached the login: prompt, then something about Gnome flashed (probably gdm) and a split second later my screen went blank.

My first question is how to tell SILO to boot into runlevel 3. I tried putting number 3 to the 'append' line, but it didn't help. Next question is quite obvious: how do i fix the kernel panic? ;)

BTW, a friend of mine's got the same type of machine. He installed Debian stable and everything went fine (XFree86). But when he tried to upgrade to testing (Xorg), the very same kernel panic greeted him. I'd've said it's a bug between Xorg and something in Ultra 5, but i saw some posts about resolution out of sync, so i guess it *can* be run without kernel panic. Anyone having an idea? TIA

---

### Post by mahy on 2006-11-12
Sigh! After much pain and suffering, i installed Debian Stable. XFree86 rocks (at least on SPARC :cool: )!

---

### Post by netced on 2006-11-12
I had exactly the same problem and I had to go back to Debian Sarge and XFree, even Debian Etch did not work because of Xorg. If you find a solution later do not forget to post it there cause I would be happy to know.

By the way, I replaced recently my Sarge with Solaris 10 and I'm QUITE happy with it. If you have enough memory it's a system to consider for your Ultra 5.

Old runlevel 3 no more exists and it's a shame, people are too confident with Xorg... (btw if someone knows how to return to something like the runlevel 3 of Linux 2.4, I'm interested)

---

### Post by Cuis on 2006-11-13
There is a problem with the Xorg server. I´ve found in the forums that is related to the PCI bus management. Some guy make it work by removing his PCI Cards from the U5.

What I do is to mount / using the installer disk, then edit /boot/silo.conf and replaced the line
"quiet splash" 
with 
"video=atyfb:1024x768@60"

Then run silo and reboot. The X server does not start, but al least  the kernel dont panic.
I'm still looking for a solution to this problem.

---

### Post by mahy on 2006-11-13
I believe Xorg developers need to find a solution. What on earth should i do when Debian shifts to Etch (which uses Xorg)? Install NetBSD or Solaris? AFAIK, no other Linux distro uses XFree86 anymore :(

---

