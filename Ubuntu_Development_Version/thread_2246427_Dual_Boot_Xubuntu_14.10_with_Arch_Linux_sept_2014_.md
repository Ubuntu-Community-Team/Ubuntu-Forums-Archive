---
title: "Dual Boot Xubuntu 14.10 with Arch Linux sept 2014 ubuntu first"
date: 2014-09-30
forum: Ubuntu Development Version
---

### Post by harlock593 on 2014-09-30
Hi,

i searched on google to find a tutorial for making a dual boot with ubuntu already installed (no windows).

i found an old closed thread on this forum mentionning a youtube video but without the link to the video.

i think i have to get two swap partitions, but i need to resize my main ubuntu partition. i'm on a laptop with a 1 Tb hdd and ubuntu's swap is 7.9 Gb (i have 8gigs of ram).

i also have to say that this laptop has uefi and secure boot.

i already have succeeded installing arch linux only, then i installed ubuntu and erased it but now i'd like both of them.

i also know that there is an option to install arch from another distribution, but i don't see well what it consists of. but it could be an option. but i think arch is a bit faster than ubuntu.

because it is more minimal. although i have xubuntu (but i also installed MATE and Cinnamon).

---

### Post by yancek on 2014-09-30
> i think i have to get two swap partitions

No, you don't.  You can have as many distributions as you want and they will all use the same swap.
Just use GParted to create a partition for Ubuntu and one for Arch and leave space for separate data partitions that can be shared by both.  I don't see any questions?

---

### Post by Bucky Ball on 2014-09-30
*Thread moved to **Ubuntu Development Version**.*

Welcome. Unsure why you are using 14.10. It's not released yet. You don't need two swap partitions. The two installs will happily use the same one (and /home). Just choose 'Something Else' when installing Ubuntu (so maybe install Arch first) and mark the existing /home and /swap to use, but NOT to format. The system will know what you mean and assign accordingly without formatting so you won't lose data. Unsure of the procedure with Arch but sure you can choose something similar to 'Something Else' and manually partition there, too.

If you are just venturing in to Ubuntu/Linux, I suggest you use a released and stable version, 12.04 LTS or 14.04 LTS, both with five years support. Good luck. ;)

PS: To resize the partition Ubuntu is installed on you will need to boot from the install LiveDVD/USB, 'Try Ubuntu' and do it with Gparted. You can't resize a mounted partition and you can't unmount a Ubuntu OS partition if you are running Ubuntu, if you follow me. ;)

Having said all this, back up all valuable data before proceeding, regardless of how you go about this.

PPS: You can get more minimal with Ubuntu by installing Ubuntu mini.iso and adding only what you want, in your case, possible xfce4 for a desktop environment. Take it from there. 

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

After mini install, this is about all you need to get things up and running:

My example post-OS install line:
```
sudo apt-get install xfce4 synaptic lightdm
```

Add whatever else you might like to this install line, i.e. firefox, filezilla, vlc, whatever ... ;)

(* yancek ninja-ed me, but yes, what they said. ;))

PPS: I have edited the title of your thread as this - [HOW-TO] - is used for tutorials and how-tos, which this is not. This is a support request ...

---

### Post by harlock593 on 2014-10-01
i've installed ubuntu using all disk space and i think that / and /home are on the same partition. i didn't change what was proposed.

---

### Post by Bucky Ball on 2014-10-01
You haven't really responded to anything either yancek or myself have mentioned. 

In that case /home is a directory inside the partition / rather than a partition. What exactly did you want to know? Why are you using 14.10? Developer? Tester? Reporting bugs?

---

