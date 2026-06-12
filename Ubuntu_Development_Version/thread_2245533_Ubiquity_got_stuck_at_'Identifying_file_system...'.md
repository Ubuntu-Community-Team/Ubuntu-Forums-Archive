---
title: "Ubiquity got stuck at 'Identifying file system...' bug #1373365"
date: 2014-09-24
forum: Ubuntu Development Version
---

### Post by sudodus on 2014-09-24
Testing Lubuntu Utopic 32-bit beta manual partitioning failed for me if I was running other programs before starting the installer.

Test-case 1: Just after leaving the partitioning screen the system complained that  it could not unmount the target partition for the root file system.

Test-case 4: Just after leaving the partitioning screen the system complained that  it could not shut off the swap.

I had already done it manually  (including zRAM). I can turn swap on  and off manually (in the same live session after the install failure in  the 4th test). And I can mount and unmount the target device for the  root file system (manually with mount and umount). But for some reason Ubiquity has problems.
              

See this link where all 4 test cases are described.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1373365](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1373365)

It seems that Ubiquity is happy only when it is allowed to run first (not after other programs have been running).

---

### Post by Elfy on 2014-09-24
>  It seems that Ubiquity is happy only when it is allowed to run first (not after other programs have been running). When I'm running through tests for milestones I tend to open all the default favourite xubuntu menu items to test them prior to starting the install - not seen an issue like this.

---

