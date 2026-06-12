---
title: "Ubuntu 12.04 beta wont boot from new kernel"
date: 2012-03-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by agurkas on 2012-03-23
Hello dear friends,

upgrading from 11.10 to 12.04 beta went without error messages. (When asked to replace config files replaced with new ones).

After upgrade
Ubunto wont boot 3.2.0-20 kernel 

it stops after lines:
#start_kernel+0x3c7/0x3c7
#gs_change+0x13/0x13

still can boot into old kernel 3.0.0-17 with no problems though.

I wonder is it possible to somehow fix this without reinstalling 12.04 from scratch?
I have a lot of softwares installed on that workstation so that would be couple of days wasted to reinstall and configure everything.

I could work for some time with old kernel if there is a hope 12.04 official release will somehow fix that booting problem.

Anyone has any opinion why boot stops after gs_change+0x13/0x13 line ? Cannot find anything helpful on the Internet.

Help is very much appreciated.

---

### Post by grahammechanical on 2012-03-23
How did you get that kernel? I updated 17 hours ago and it was not there. I have just checked and Update Manager still doses not have it.

It seems that you have some packages relating to this new kernel but not others.

Do you have Synaptic Package Manager installed. You need it. You can get it through the Ubuntu software Centre.

The use it to search for all the packages relating to the 3.2.0-20 kernel and either un-install them or see if they can be upgraded.

I see from using Synaptic on my system that some packages relating to that kernel are ready to be updated.

This is why it is always good to keep at least one earlier kernel in the Grub menu. For just such occasions.

Regards.

P.S. Keep running the 17 kernel and do daily updates you might find that it gets corrected over the next few days.

---

### Post by Sarvatt on 2012-03-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/961482](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/961482)

---

### Post by Gregory Lee on 2012-03-23
I got that kernel a couple of days ago.  Seems okay, here.
```
~# ls -l /boot |grep 3.2.0-20
-rw-r--r-- 1 root root   789425 Mar 21 17:02 abi-3.2.0-20-generic
-rw-r--r-- 1 root root   140211 Mar 21 17:02 config-3.2.0-20-generic
-rw-r--r-- 1 root root 14158238 Mar 23 06:11 initrd.img-3.2.0-20-generic
-rw------- 1 root root  2884032 Mar 21 17:02 System.map-3.2.0-20-generic
-rw------- 1 root root  4965712 Mar 21 17:02 vmlinuz-3.2.0-20-generic
```

---

### Post by xebian on 2012-03-23
> **agurkas said:**
> Hello dear friends,

upgrading from 11.10 to 12.04 beta went without error messages. (When asked to replace config files replaced with new ones).

After upgrade
Ubunto wont boot 3.2.0-20 kernel 

it stops after lines:
#start_kernel+0x3c7/0x3c7
#gs_change+0x13/0x13

still can boot into old kernel 3.0.0-17 with no problems though.

I wonder is it possible to somehow fix this without reinstalling 12.04 from scratch?
I have a lot of softwares installed on that workstation so that would be couple of days wasted to reinstall and configure everything.

I could work for some time with old kernel if there is a hope 12.04 official release will somehow fix that booting problem.

Anyone has any opinion why boot stops after gs_change+0x13/0x13 line ? Cannot find anything helpful on the Internet.

Help is very much appreciated.

You don't have to re-install the whole 12.04.  All you have to do is uninstall that non-working kernel and then re-install later and hope it might work ( which works most of the time).

---

### Post by agurkas on 2012-03-23
> **Sarvatt said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/961482](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/961482)

Thank you very much Sarvatt.
workaround mentioned in that bugzilla worked for me.
I just had to add pcie_aspm=force into grub options and now I am enjoying the 3.2.0-20 kernel.

grahammechanical asked: >How did you get that kernel?

I just did apt-get dist-upgrade. the new kernel is in the repo.


Thank you all guys for the the help. Your support is absolutely fantastic.

---

