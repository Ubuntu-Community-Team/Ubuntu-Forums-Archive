---
title: "Re-Install 3.13.0-110?"
date: 2017-03-07
forum: Server Platforms
---

### Post by JSeymour on 2017-03-07
Hi All,

Had a problem with my server that I mistakenly thought was a driver issue.  (Problem coincidentally started on the same day as the update/upgrade to 3.13.0-110, so it seemed a reasonable suspicion.)  Turned out that wasn't it.

Out of an excess of caution, in case the server rebooted (power failure, whatever), I did an "apt-get purge" of linux-image-3.13.0-110-generic.  That uninstalled

[LIST]
[*]linux-image-3.13.0-110-generic:i386 (3.13.0-110.157), 
[*]linux-generic:i386 (3.13.0.110.118), 
[*]linux-image-extra-3.13.0-110-generic:i386 (3.13.0-110.157), 
[*]linux-image-generic:i386 (3.13.0.110.118) 
[/LIST]

Now, having identified the real culprit, I'd like to get that back, have the boot updated, initrd.img, vmlinuz updated - everything as if a regular apt-get update/apt-get dist-upgrade had been run.

It is unclear to me how to proceed.  Help, please?

Thanks,
Jim

---

### Post by DuckHook on 2017-03-07
Simply:```
sudo apt-get install linux-image-generic
```&#8230;then:```
sudo update-grub
```This should install the latest kernel back into your system, and continue to update thereafter.

---

### Post by JSeymour on 2017-03-08
Thanks, DuckHook!  I'll give it a try.

---

### Post by JSeymour on 2017-03-10
That did the trick, DuckHook!  Thanks again!

Only it was -112.  Got the notification.  Did the "dist-upgrade."  Noticed that none of the image stuff happened.  Followed your directions.  Fixed :)

---

### Post by DuckHook on 2017-03-10
Glad it worked.

*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

