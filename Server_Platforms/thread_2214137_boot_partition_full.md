---
title: "/boot partition full"
date: 2014-03-30
forum: Server Platforms
---

### Post by Frank P on 2014-03-30
Ubuntu server 12.04 LTS
I have tried all the potential methods for deleting old kernels that I could find on Google - nothing worked
The partition has versions 23, 51-59.
60 wont update because of the full partition.

I tried to resize the partition using gparted from a live DVD but there didn't seem to be any way to free up space.

Can I safely delete some of the older - say 51 to 55, files or is there something else I can do

Thanks

Frank P

---

### Post by apohal9 on 2014-03-30
Simply check /boot for vmlinuz* System.map* initrd.img* config* and abi* files. Delete the old ones you do not need anymore. Be sure to delete all 5 files per Kernel-version. Afterwards run update-grub and reboot. This should free up space.

So if you'd like to delete 51 -> 55, remove all 5 for each version. E.g.:
> sudo rm vmlinuz*51* System.map*51* initrd.img*51* config*51* abi*51*

But anyways, be carefull to not delete all of them ;)

**Attention:** this is not a good solution. It works, but your omitting the package manager which is may lead to problems later. Please follow Bashing-om's solution.

---

### Post by Frank P on 2014-03-30
That fixed it
Thanks!!!

Frank P

---

### Post by apohal9 on 2014-03-30
> **ajgreeny said:**
> Please delete.

Wrong answer

My answer?
If yes, please help me too on how to free space on /boot. I've done it this way all times and never got issues with this.

---

### Post by Frank P on 2014-03-30
apohalo9

Your answer was perfectly correct - it freed up the space and allowed apt-get upgrade to run with no errors

Thanks again

Frank P

---

### Post by Bashing-om on 2014-03-30
et all;

The proper way to remove kernels  in the older releases is along these lines:
In this case perhaps "apt-get remove/purge" may have been effective.
- in a problematic situation - this has proved to be effective:
```

sudo dpkg -P linux-image-3.0.0-{12,13,14,15,16,17}-generic-pae

```
And the same commnad for the "linux-headers".
One should not ever avoid the package manager ! As the package manager takes care of a lot of behind the scene details.

Later releases, the package manager will remove those obsolete kernels with the "autoremove" command.

[INDENT][INDENT][/INDENT][/INDENT]My little bit to try and help

---

### Post by Frank P on 2014-03-30
Appreciate the reply but I tried that and a lot of other commands before I posted. I spent hours googling for solutions. Nothing worked except for the simple delete using Midnight Commander so I could see what I was deleting

Frank P

---

### Post by apohal9 on 2014-03-31
> **Bashing-om said:**
> et all;

The proper way to remove kernels  in the older releases is along these lines:
In this case perhaps "apt-get remove/purge" may have been effective.
- in a problematic situation - this has proved to be effective:
```

sudo dpkg -P linux-image-3.0.0-{12,13,14,15,16,17}-generic-pae

```
And the same commnad for the "linux-headers".
One should not ever avoid the package manager ! As the package manager takes care of a lot of behind the scene details.

Later releases, the package manager will remove those obsolete kernels with the "autoremove" command.
My little bit to try and help

Thank you Bashing-om.
You're completely correct. It's never a good way to avoid the package manager. Learned that now ;)

---

