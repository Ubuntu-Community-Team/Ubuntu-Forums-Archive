---
title: "Ubuntu Privacy Rexmix (Swap ?)"
date: 2011-03-01
forum: Security
---

### Post by Savio2010 on 2011-03-01
Hi Everybody

I am using Locked Lynx 10.04r1 on my 

pentium D 3.0GHz
512 RAM

[https://www.privacy-cd.org/](https://www.privacy-cd.org/)

UPR does not access the HDD then from where am I getting Swap 245.3 MB in my System Monitor ??:confused: not only that it even uses it.

A big suspense.

Please Help..........

---

### Post by mikewhatever on 2011-03-01
If you have a swap partition on the hdd, linux live cd distros will usually use it. If you want to prevent them from doing so, use the swapoff command. Perhaps you could also tip off the creator of that particular cd.

---

### Post by Savio2010 on 2011-03-01
What ever you said applies to a normal Ubuntu CD/DVD Live session. Ubuntu Privacy Remix is designed with privacy in mind so..............

No HDD                                 .........................................To prevent attacts from HDD
No Network                           ....................................To prevent Network attacks 
noexec                                  ..........................................To prevent malicious programs to run.
Extended TrueCrypt Volumes  ...........To Save Application settings like persistence.

It is not intended for permanent installation.

In any case I have a 1GB swap partition and in the live session of UPR it shows me 1/4 of it.

Have a look at the site [https://www.privacy-cd.org/](https://www.privacy-cd.org/)

---

### Post by FuturePilot on 2011-03-01
> **Savio2010 said:**
> What ever you said applies to a normal Ubuntu CD/DVD Live session. Ubuntu Privacy Remix is designed with privacy in mind so..............

No HDD                                 .........................................To prevent attacts from HDD
No Network                           ....................................To prevent Network attacks 
noexec                                  ..........................................To prevent malicious programs to run.
Extended TrueCrypt Volumes  ...........To Save Application settings like persistence.

It is not intended for permanent installation.

In any case I have a 1GB swap partition and in the live session of UPR it shows me 1/4 of it.

Have a look at the site [https://www.privacy-cd.org/](https://www.privacy-cd.org/)

Perhaps they overlooked that little detail. Any live CD will use a swap partition if one is present. Your best bet would be to contact the developers of UPR and let them know about it.

---

### Post by mikewhatever on 2011-03-01
Well, it is supposed to be designed with privacy in mind, but is it the first time there is a gap between what the advertisement says and the product does? As already suggested, contact the devs and tell them.

---

### Post by Savio2010 on 2011-03-11
I got a reply from the developers of UPR. This is the reply


> Hello,

thanks for your mail and sorry for us taking so long to reply.
The screenshots attached to your mail show the gnome-system-monitor
using swap-space. I assume you are wondering, if UPR ist accessing
Swap-Partitions on your harddrive?

Not, it is not. UPR ist still completely taking away the possibility of
accessing the hard disks.  if you run swapon -s on commandline, you can
see, that the swap-space is provided via ramzswap. 

ramzswap creates RAM based block device (/dev/ramzswap) which acts as
swap disk. Pages swapped to this disk are compressed and stored in
memory itself. Compressing pages and keeping them in RAM virtually
increases its capacity. This allows more applications to fit in given
amount of memory.

You used the signing key to encrypt the files. Please use the
communication key in future - or even better, report bugs to our
bugtracker at launchpad
([https://www.privacy-cd.org/en/using-upr/report-a-bug](https://www.privacy-cd.org/en/using-upr/report-a-bug)).

best regards


Mark**


Thanks.

---

