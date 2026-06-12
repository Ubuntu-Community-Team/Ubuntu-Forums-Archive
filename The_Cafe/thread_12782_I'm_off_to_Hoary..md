---
title: "I'm off to Hoary."
date: 2005-01-26
forum: The Cafe
---

### Post by jdong on 2005-01-26
Since I'm setting up a fancy RAID5 array next month, and would need a complete reinstall (probably Hoary) to do so, I figured that I might as well migrate the system to Hoary now. So, off I am to do so. I'll test the Backports-to-Hoary transition in the process... Already, I'm seeing sections that could need improvement in the guide.

---

### Post by jdodson on 2005-01-26
[QUOTE=jdong]Since I'm setting up a fancy RAID5 array next month, and would need a complete reinstall (probably Hoary) to do so, I figured that I might as well migrate the system to Hoary now. So, off I am to do so. I'll test the Backports-to-Hoary transition in the process... Already, I'm seeing sections that could need improvement in the guide.[/QUOTE]

the backports guide or ubuntuguide?

---

### Post by jdong on 2005-01-26
The Backports "Upgrading To Hoary" guide, with the apt-show-version .... awk.... command. I'm finding it better to first upgrade to Hoary, then force all leftover backports to Hoary packages, rather than trying to "Roll back" backports to Warty, then upgrade everything to Hoary.

---

### Post by akurashy on 2005-01-26
Good luck :D
and i hope this time hoary dont mess up my linux when you finish :D

---

### Post by Quest-Master on 2005-01-26
I tried to upgrade to Hoary yesterday; totally killed my Ubuntu. No X, failed startups, and so on. 

Did a full reinstall today, and won't touch Hoary till it is fully stable after last night's experience. :(

---

### Post by akurashy on 2005-01-26
well quest i had the same problem
no X and startup problems >_<
and only a terminal

---

### Post by Randabis on 2005-01-26
[QUOTE=Quest-Master]I tried to upgrade to Hoary yesterday; totally killed my Ubuntu. No X, failed startups, and so on. 

Did a full reinstall today, and won't touch Hoary till it is fully stable after last night's experience. :([/QUOTE]

Bummer. I have it running smoothly on 3 machines.

---

### Post by mark on 2005-01-26
I've got Warty running smoothly and Hoary (Array 3) running semi-smoothly (dual-booting, thanks to *grub* - although the Hoary install initially clobbered my Warty *grub* entries...

I'm having some odd sound problems with Hoary (no sound on boot, have to diddle mute/unmute & volume settings via the Volume Control) & the Array 3 install enabled some *apt* repositories that apparently won't go "live" until the April release, but otherwise I'm encouraged.  Things seem quite a bit quicker (boot, Web access (after I disabled IPv6)), just generally more responsive.

I plan on maintaining both installations until *Der Tag* in April.  If I encounter any real problems, I'll try to post here (somewhere)....

---

