---
title: "The mapper/vg00-lvroot (Ubuntu 12.04.1 LTS) partition is nearly full"
date: 2013-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by pramodvyas on 2013-04-23
Hi,
I am new member here. I got a problem while restoring ubuntu on m laptop. 
I have installed ubuntu 12.04  and GNU GRUB boot manager for booting in my laptop. Yesterday When I installed Windows, I lost ubuntu. Now I am trying to restore it.
I run ubuntu by USB and started boot repair and I got an error......

"The mapper/vg00-lvroot (Ubuntu 12.04.1 LTS) partition is nearly full. This can prevent to start it. Please use the file browser that just opened to delete unused files (or transfer them to another disk). Close this window when you have finished."

Now I am confused that which files I should delete or which not?

Please Help me....

---

### Post by oldfred on 2013-04-23
I do not know RAID nor LVM. Are you running those? Or full disk encryption?

Boot-Repair has difficulty telling RAID from LVM and may need help since both appear as /mapper. You may have to load drivers or mount partitions before running Boot-Repair or maybe just manually reinstall grub.

But Windows is not really compatible with Ubuntu RAID nor LVM, so how did you install?

---

