---
title: "Cleared /boot, but autoremove wants to remove ALL kernels."
date: 2017-07-03
forum: Server Platforms
---

### Post by ghughes on 2017-07-03
Good morning, all!

Just cleared the /boot of some of the obsolete kernels and reduced its size to something manageable. After you apt-get purge the kernels you want, you get a prompt to run autoremove.

However, autoremove says it's going to remove ALL the old kernels except the one that's currently booted. I want to keep a couple of older ones around "just in case."

How do I clear all the underbrush in /boot without nuking all the old kernels that I might need some dark night?

Thanks!

Gregg

---

### Post by monkeybrain20122 on 2017-07-03
Autoremove would usually keep two kernels. I usually run the new kernel for a few days if everything is ok then I manually remove the previous one and keep only one. Also I think a /boot partition is not necessary and tend to make things more complicated unless you want to encrypt your $HOME or maybe for dualboot with Windows? I never have a /boot partition, just root and home.

---

### Post by CatKiller on 2017-07-03
A /boot partition is necessary for UEFI installs.

I believe the autoremove algorithm for determining which kernels are "old" is a bit iffy. I, too, just manually remove the kernels that I don't want through the package manager. I normally just keep the latest if I've managed to boot into it a couple of times.

Edit: [This]("https://help.ubuntu.com/community/RemoveOldKernels") is how it's configured, if you want to tweak it.

> Note: This way will not remove all automatically installed old kernels;  the list of kept kernels is maintained in text file  /etc/apt/apt.conf.d/01autoremove-kernels as a list of matching regular  expressions.

---

### Post by ian-weisser on 2017-07-03
> **ghughes said:**
> However, autoremove says it's going to remove ALL the old kernels except the one that's currently booted.

If true (check the package names carefully), then that means you broke something.
From the limited information given, we cannot determine what you did.

The script that determines eligibility for autoremove works *very hard* to avoid precisely that situation.

One option you have is to run that eligibility script again - it's at /etc/kernel/postinst.d/apt-auto-removal

Another option is to make one older kernel ineligible for autoremoval using the apt-mark command (or apt install, for that matter).

---

### Post by ajgreeny on 2017-07-03
> **CatKiller said:**
> A /boot partition is necessary for UEFI installs.
No, that is incorrect.
A /boot partition is necessary and is automatically created if you use either LVM partitions or choose encryption at installation, but not simply because you use UEFI; perhaps you are confusing UEFI and LVM.

@ghughes
If you used apt or apt-get to remove or purge only the linux-image (kernel) of a particular version there will still normally be other packages of that same version remaining on the system, eg linux-headers, linux-image-extra, and maybe a few others, all of which should then be removed by the autoremove command if not automatically removed when the kernel goes.

---

### Post by CatKiller on 2017-07-03
> **ajgreeny said:**
> No, that is incorrect.
A /boot partition is necessary and is automatically created if you use either LVM partitions or choose encryption at installation, but not simply because you use UEFI; perhaps you are confusing UEFI and LVM.

Yes, possibly. I've only done two UEFI installs myself. They both got a /boot partition.

My understanding is that the ESP needs to be FAT32, which you wouldn't want to use for anything else.

---

### Post by ajgreeny on 2017-07-04
> **CatKiller said:**
> Yes, possibly. I've only done two UEFI installs myself. They both got a /boot partition.

My understanding is that the ESP needs to be FAT32, which you wouldn't want to use for anything else.
Do you choose LVM or encryption when you install? Both create a separate /boot partition automatically.

The ESP or EFI partition is not a /boot partition and can not be used for anything other than the UEFI boot system, but perhaps that is where you were being confused.

---

