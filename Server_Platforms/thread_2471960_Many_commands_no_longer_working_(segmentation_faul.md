---
title: "Many commands no longer working (segmentation fault)"
date: 2022-02-14
forum: Server Platforms
---

### Post by herrb on 2022-02-14
I have an ubuntu server 20.04
Right now I cannot manage my server anymore. Plenty of commands such as `sudo mount ...` just return segmentation fault.
Even `sudo shutdown -r` returns segmentation fault.
`Sudo su` works. A `shutdown -r` then returns `Segmentation fault (core dumped)`

Any ideas what could be wrong? What can I do to debug?

LG,

Julian

---

### Post by #&amp;thj^% on 2022-02-14
> **herrb said:**
> I have an ubuntu server 20.04
Right now I cannot manage my server anymore. Plenty of commands such as `sudo mount ...` just return segmentation fault.
Even `sudo shutdown -r` returns segmentation fault.
`Sudo su` works. A `shutdown -r` then returns `Segmentation fault (core dumped)`

Any ideas what could be wrong? What can I do to debug?

LG,

Julian

Need to see the actual return from the terminal, to advise.
EDIT:check /var/logs as well

---

### Post by schragge on 2022-02-14
A shot in the dark. Both **shutdown** and **mount** are linked against **libblkid**. Try to reinstall [FONT=monospace]**libblkid1**[/FONT].

You might have to reboot into [uwiki]RecoveryMode[/uwiki]  or perform [uhelp]community/LiveCdRecovery[/uhelp] in order to do this as some required and important packages depend on **libblkid**:
```
[COLOR=green]$[/COLOR] aptitude search '~i~rnative~Dlibblkid1(~prequired|~pimportant)'|cat[COLOR=green]
i  e2fsprogs - ext2/ext3/ext4 file system utilities
i  libcryptsetup12 - disk encryption support - shared library
i  libfdisk1 - fdisk partitioning library
i  libmount1 - device mounting library
i  mount - tools for mounting and manipulating filesystems
i  systemd - system and service manager
i  udev - /dev/ and hotplug management daemon
i  util-linux - miscellaneous system utilities[/COLOR]
```

 I don't know if any tool from them may be used during the reinstall of [FONT=monospace]**libblkid1**[/FONT] (probably not), but if it does and is broken, you won't be able to complete the process from inside the running system.

---

### Post by #&amp;thj^% on 2022-02-14
> **schragge said:**
> A short in the dark. Both **shutdown** and **mount** are linked against **libblkid**. Try to reinstall [FONT=monospace]**libblkid1**[/FONT]

My exact first thought as well. :)

---

### Post by DuckHook on 2022-02-14
[LIST=1]
[*]Did everything go south after an update?
[*]Did you install/change any app/service/module just prior?
[*]Any HW changes? Added, subtracted, modified?
[*]Did you do a dirty shutdown before?
[*]Can you back up data without crash? If so, then backup right away. This can save your bacon if everything gets worse. Even a proposed fix could bork you system up completely.
[/LIST]
Then, as 1fallen advises, post log results prefiltered for relevance.

---

### Post by MAFoElffen on 2022-02-14
I'm with DuckHook and Fallen1 on this... We need to see logs first... but also needs to include the recent APT logs.

Segmentation Faults (A type of Memory Error) are when your system tries to access a page of memory  that doesn’t exist. Frequently those are when some instruction of code tries to  perform a read/write operation on a read-only or free location.  Segfaults are generally associated with certain files and generally happens during or after upgrades.

Just saying that just because it gets a segfault on those commands, it could be related to filelocks preventing access to certain files, or broken packages that occurred during a recent upgrade... Which would be resolved from a different perspective and approach... 

Saying this now, so that the OP doesn't start making changes to things that he might have to back out of to resolve the actual problem..

So yes, more information needed before recommending any kind of solution yet...

---

