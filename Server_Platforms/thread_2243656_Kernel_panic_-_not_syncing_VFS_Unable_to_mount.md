---
title: "Kernel panic - not syncing: VFS: Unable to mount"
date: 2014-09-10
forum: Server Platforms
---

### Post by m3rtijn on 2014-09-10
Yes, this issue has passed through the forums a number of times, I realize that. And I have read through all of them as far as I could find them. But none were able to resolve my issue.

Here's a screenshot to get started:
[ATTACH=CONFIG]256327[/ATTACH]

For search engines:
**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)**

This appears to be a fairly complete topic that describes on how to get it fixed:
[http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](http://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)

But I bump into problems as soon as I get into the live CD. The problem is mainly that my ubuntu isn't simply on /dev/sda1, that is only the /boot partition, if I recall. I let the installer do its thing (long ago) and it worked, so joy. Now it's apparently giving me problems. Anyway, the rest of the filesystem (the root) is on /dev/sda5. But that is an LVM partition...

I did find how to mount LVM's:
[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)

Can I fix it with that? Not really. After getting all the mounts working, I did the update-initramfs and the update-grub2, and then rebooted. Same error again.

So now I'm stuck.

This is Ubuntu 14.04.1 LTS server on a ESXi box. I'm vaguely familiar with linux things, but no expert by any measure. So please try to be complete if you have suggestions on what I should do.

---

### Post by m3rtijn on 2014-09-11
Got it fixed. I forgot to mount the /boot partition that is outside the LVM, on /dev/sda1.
I'll try to remember to post the full set of commands I executed shortly. I'm in a hurry atm.

---

