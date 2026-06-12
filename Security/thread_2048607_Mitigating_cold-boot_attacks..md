---
title: "Mitigating cold-boot attacks."
date: 2012-08-26
forum: Security
---

### Post by Stonecold1995 on 2012-08-26
I heard that storing AES encryption keys in the debug registers of the CPU (or something like that) would mitigate cold-boot attacks because they keys are never stored in RAM (my disks are encrypted with AES).  If I'm right, the kernel patch is called TRESOR.  Is there a way I can install something like this without downgrading to an older kernel?  Like, is there a way to install TRESOR using a script or use an application to do that?

Also, I heard that another way to mitigate attacks is to monitor the memory temperature, and wipe the keys from memory if they are subject to a sharp drop in temperature.  Can all RAM cards monitor their temperature, and if so is the temperature value available to the operating system?

---

### Post by rookcifer on 2012-08-27
It boils down to physical security.  A cold boot attack is not the only way to steal your keys if an attacker has physical access to your machine.  For instance, he could perform the "evil maid" attack or install a camera or keylogger, etc.  There's even TEMPEST attacks if your adversary is sophisticated.  As you can see, there's lots you can be paranoid about, but the question is, how much do you really *need* to be paranoid about?

Disk encryption is only safe when you are sure no adversary has had physical access to your machine since you used it last.

As for cold boot attacks, the best way to deal with them is to make sure the power is off at least for a couple of minutes before the adversary gets access to the machine.  After the machine powers down, the RAM is slowly cleared (the speed at which is clears depends on the temperature.  Extremely cold temps will hold the data in the RAM longer, which is why forensics experts will use methods of cooling the RAM).

---

### Post by Stonecold1995 on 2012-08-27
I'm not too worried about Evil Maid attacks, because I'm using a script which monitors for changes in the MD5 sums of the files in /boot, along with the inodes where they are stored, and checks for changes in the MBR.  I'm not *too* worried about keyloggers.  Not hardware ones at least (I have a laptop so it would be a bit more difficult to install one).  As for software keyloggers I have chkrootkit, rkhunter, tiger, unhide, ClamAV, and OSSEC monitoring my system so I'm (hopefully) safe from that.

I know to stay with my computer for a few minutes after powering down, and every time I shut it down I'll stay with it for about 10 minutes.  I also run Folding@home on it and I'm pretty sure the heat it generates speeds up the process of clearing the RAM.  I do leave my computer on 24/7 most of the time to run Folding@home, but I only do that when I'm in my house.

I'm worried about high-sophistication attacks like this only because I am not good friends with nasty 3-letter acronyms, so physical security isn't really an option (or at least, it's not very effective).

And you can never be too paranoid...


I usually run Folding@home, which takes up 100% of the processor.  Would that reduce the effectiveness of TEMPEST attacks because it generates so much noise?

---

### Post by zaverivismay on 2013-02-20
Hi,
Sorry for starting this thread again, I have a question which I would like to know..what is the maximum time for which data can persist( DDR3 RAM ) after complete shut down.
If I remove the ram physically from the computer after power off, Till how much time can the data be retreived.(seconds or minutes.
Also if I am using truecrypt with Ubuntu Privacy Remix using live cd with out any other OS on my pc,is only truecrypt keys recovered from RAM or the contents of my file as well?

---

### Post by Stonecold1995 on 2013-02-20
> **zaverivismay said:**
> Hi,
Sorry for starting this thread again, I have a question which I would like to know..what is the maximum time for which data can persist( DDR3 RAM ) after complete shut down.
If I remove the ram physically from the computer after power off, Till how much time can the data be retreived.(seconds or minutes.
Also if I am using truecrypt with Ubuntu Privacy Remix using live cd with out any other OS on my pc,is only truecrypt keys recovered from RAM or the contents of my file as well?
IIRC, DDR3 RAM is cleared in under 10 seconds, rather than minutes as with other types.

---

