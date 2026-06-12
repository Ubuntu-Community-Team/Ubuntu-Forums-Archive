---
title: "Is using apt-get autoremove to delete old kernels safe?"
date: 2017-01-26
forum: Server Platforms
---

### Post by steve130 on 2017-01-26
I've been using Ubuntu server distros for awhile, but I consider myself a novice at command line stuff still.  When I run apt-get update, I get a message saying I have a lot of items that are no longer necessary.  Most of them seem to be kernel related. Is it safe to remove all these using apt-get autoremove?

```
libtidy-0.99-0 linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-39 linux-headers-3.19.0-39-generic
  linux-headers-3.19.0-41 linux-headers-3.19.0-41-generic
  linux-headers-3.19.0-43 linux-headers-3.19.0-43-generic
  linux-headers-3.19.0-47 linux-headers-3.19.0-47-generic
  linux-headers-3.19.0-49 linux-headers-3.19.0-49-generic
  linux-headers-3.19.0-51 linux-headers-3.19.0-51-generic
  linux-headers-3.19.0-56 linux-headers-3.19.0-56-generic
  linux-headers-3.19.0-59 linux-headers-3.19.0-59-generic
  linux-headers-3.19.0-65 linux-headers-3.19.0-65-generic
  linux-headers-3.19.0-66 linux-headers-3.19.0-66-generic
  linux-headers-3.19.0-68 linux-headers-3.19.0-68-generic
  linux-headers-3.19.0-69 linux-headers-3.19.0-69-generic
  linux-headers-3.19.0-73 linux-headers-3.19.0-73-generic
  linux-headers-3.19.0-74 linux-headers-3.19.0-74-generic
  linux-headers-3.19.0-75 linux-headers-3.19.0-75-generic
  linux-headers-3.19.0-77 linux-headers-3.19.0-77-generic
  linux-image-3.19.0-25-generic linux-image-3.19.0-39-generic
  linux-image-3.19.0-41-generic linux-image-3.19.0-43-generic
  linux-image-3.19.0-47-generic linux-image-3.19.0-49-generic
  linux-image-3.19.0-51-generic linux-image-3.19.0-56-generic
  linux-image-3.19.0-59-generic linux-image-3.19.0-65-generic
  linux-image-3.19.0-66-generic linux-image-3.19.0-68-generic
  linux-image-3.19.0-69-generic linux-image-3.19.0-73-generic
  linux-image-3.19.0-74-generic linux-image-3.19.0-75-generic
  linux-image-3.19.0-77-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-39-generic linux-image-extra-3.19.0-41-generic
  linux-image-extra-3.19.0-43-generic linux-image-extra-3.19.0-47-generic
  linux-image-extra-3.19.0-49-generic linux-image-extra-3.19.0-51-generic
  linux-image-extra-3.19.0-56-generic linux-image-extra-3.19.0-59-generic
  linux-image-extra-3.19.0-65-generic linux-image-extra-3.19.0-66-generic
  linux-image-extra-3.19.0-68-generic linux-image-extra-3.19.0-69-generic
  linux-image-extra-3.19.0-73-generic linux-image-extra-3.19.0-74-generic
  linux-image-extra-3.19.0-75-generic linux-image-extra-3.19.0-77-generic
  python-feedparser python-libxml2 python-utidylib
0 upgraded, 0 newly installed, 72 to remove and 9 not upgraded.
After this operation, 4,903 MB disk space will be freed.
```

---

### Post by wildmanne39 on 2017-01-26
*Thread moved to **Server Platforms for better support**.* 

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ajgreeny on 2017-01-26
Which version of Ubuntu are you using?
To the best of my knowledge **sudo apt-get autoremove** will remove old, unneeded kernels only in versions 16.04 and above.

It looks as if you are using an earlier version according to the kernel versions listed so you may have to remove those old versions either using **sudo apt-get remove** command or purge with **sudo apt-get remove --purge**

---

### Post by geeksmith on 2017-01-26
I've always found it safe to remove older kernels I no longer use. I generally keep at least one old kernel around in case I run into problems and need a failsafe kernel version.

---

### Post by ian-weisser on 2017-01-26
autoremove will indeed remove old kernels...that are marked as eligible for autoremove.

The script /etc/kernel/postinst.d/apt-auto-removal runs after each kernel install, and determines whether a kernel should be marked as eligible for autoremoval.
Header files, manual apt-marking, and other things may interfere with the script's work. Its just a script, neither perfect nor omniscient.

In 16.04 and later, you should not need to run autoremove manually. The unattended-upgrades package, included in all default *buntu desktops, will do an equivalent action to 'autoremove' daily. You can safely run autoremove in 16.04 in addition to the u-u daily scrub.

---

### Post by hydn79 on 2017-01-28
Overkill but just make sure to reboot first after kernel or other reboot required updates. The auto-remove if reboot is successful since you know you won't need to revert. There's also no harm in keeping them esp if you don't reboot often.

---

