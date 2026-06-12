---
title: "boot hangs after random: &quot;nonblocking pool is initialised&quot;"
date: 2014-07-13
forum: Server Platforms
---

### Post by ashleydrees on 2014-07-13
Fresh install of 14.04 LTS, in a ESXi container - 8gig ram - 8vcpu - 250g disk - only thing that has been installed post base install is VirtualMIN Pro, system was working for 14 days before this issue - system was all up to date and just now "dpkg --configure -a" gives no error.

On friday, the ESXi Host rebooted and this install of Ubuntu has not been able to boot since then, not sure if this was because of an untidy reboot - or that something was broken before it happened which was not noticed as the machine had not been rebooted for a bit.

This is as far as it gets:- [http://screencast.com/t/1PV6XFQFav](http://screencast.com/t/1PV6XFQFav)

I can boot into recovery mode with break=init or an ISO, disks are clean, can install and re-install packages - have re-formatted swap. re-installed linux-generic, initramfs-tools, apparmor, initscripts and libpam-systemd and systems-services. ran "apt-get install --reinstall initramfs-tools" which rebuild the images. Installed bootchart - but there is nothing in /var/log/bootchart - so i guess it is not getting that far. I have trawled the net for something similar to give me some ideas, but nothing so far has had any effect. 

When leaving the shell post break=init, i get "Mount failed for selinuxfs on /sys/fs/selinux : no such file or directory" but only when resuming the boot from a break=init.

Most recent thing i have done is grub-install - which said successful and then i rebooted.. but ended up in the same place.

---

### Post by kwchun on 2014-07-31
Do you have any progress? I have exactly the same problem.

---

### Post by 3WrKB4C on 2014-11-26
Hi,
did any of you two find any solution? I think I had the same or very similar problem, posted [here]("http://ubuntuforums.org/showthread.php?t=2254373&p=13175288#post13175288")

---

