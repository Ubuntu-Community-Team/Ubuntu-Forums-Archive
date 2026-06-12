---
title: "HU trouble with initramfs"
date: 2021-02-05
forum: Ubuntu Development Version
---

### Post by zika on 2021-02-05
**HU**: All the kernels that I've installed, refreshed or upgraded today are ending in kernel-panic. It happens on two machines on different places and very different per se. I've isolated it to just those kernels that were touched or installed today and have "destroyed", willfully, at least two "new" kernels by doing **update-initramfs** after I've located the possible source of trouble. It seems that I've located it into initramfs update process and it has to do with &#8222;init=&#8220;...
**Advise**: _postpone_ any upgrade that might include *update-initramfs*, especially one with *-ckall *switch. I've noticed that that switch was removed lately and that only first kernel is being processed. Maybe a blessing for this situation. Yes, it can be changed but, it seems that default has been changed.
Yes, I am on proposed/devel channel...

---

### Post by P-I H on 2021-02-05
The same to me and this created some extra work. 
I installed a new ssd today in my main computer and booted my test computer, which ended with kernel panic. 
Started the main computer made a new installation, set developer option as I need kernel 5.10, and booted to kernel panic.
Made a new installation set developer option, but only installed the 5.10 kernel. this worked OK.

---

### Post by VMC on 2021-02-05
I just installed the latest ISO and I don't have any issues. My standard install has kernel "5.8.0-36-generic".

---

### Post by zika on 2021-02-06
> **P-I H said:**
> The same to me and this created some extra work. 
I installed a new ssd today in my main computer and booted my test computer, which ended with kernel panic. 
Started the main computer made a new installation, set developer option as I need kernel 5.10, and booted to kernel panic.
Made a new installation set developer option, but only installed the 5.10 kernel. this worked OK.One of two kernels I've mentioned , the one that was &#8222;bricked&#8220; when I tried to make new initramfs, above is 5.10-xanmod so it does not seem to be version related. Daily and drmtip from Ubuntu Mainline are now being set up so I will see and report soon, this morning, if there is something new.
Report: No, newly made initramfs still boot in panic that states that there is no working init=. When I get some spare time I will invesigate more, now back to grandchildren and to act as real grandfather...

---

### Post by P-I H on 2021-02-06
Installed today's iso and booted. This work OK. Marked developer option and updated. The updated version didn't boot.

---

### Post by zika on 2021-02-07
It seems it got fixed. Not, yet, know what did fix it so I will not mark this thread as &#8222;Solved&#8220; for now...

---

### Post by P-I H on 2021-02-07
Yes worked OK after upgrade with Developer Option set.
However got this crash _usr_libexec_tracker-extract.126.crash

---

### Post by hoboy on 2021-03-02
The problem is I am stucked in initramfs .. can't even use sudo.

---

### Post by hoboy on 2021-03-02
can it be correct with liveDVD or all new install is required ?

---

### Post by zika on 2021-03-03
Try [https://askubuntu.com/questions/1274556/stuck-in-initramfs-at-boot](https://askubuntu.com/questions/1274556/stuck-in-initramfs-at-boot) first...

---

