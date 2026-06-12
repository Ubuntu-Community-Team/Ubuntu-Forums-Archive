---
title: "general strategy to avoid prompts on boot time"
date: 2012-10-21
forum: Server Platforms
---

### Post by perler on 2012-10-21
hi,

we are evaluating amazon AWS and there you don't have any access to the console of the machine you are running. so we need to make sure, that the machine boots always at least to the point where sshd is started (aside the case of catastrophic events like grub errors etc..).

so, no helpful fsck requests or expecially missing mounts "press S or C" messages, please.

how should we approach this? is there a gerneral option for this? or is there a way to start an sshd server very early in the boot chain?

PAT

---

### Post by sandyd on 2012-10-21
> **perler said:**
> hi,

we are evaluating amazon AWS and there you don't have any access to the console of the machine you are running. so we need to make sure, that the machine boots always at least to the point where sshd is started (aside the case of catastrophic events like grub errors etc..).

so, no helpful fsck requests or expecially missing mounts "press S or C" messages, please.

how should we approach this? is there a gerneral option for this? or is there a way to start an sshd server very early in the boot chain?

PAT

a) You can get Ubuntu to ignore that by adding 'nobootwait' to the options section in the fstab line.
b) It won't get stuck at grub unless there are actual problems with your EBS volume. In that case, contacting amazon is required.
c) FSCK - If it fails, there is no fix. You will have to mount the EBS volume onto another instance and run fsck there to see if that fixes it

---

