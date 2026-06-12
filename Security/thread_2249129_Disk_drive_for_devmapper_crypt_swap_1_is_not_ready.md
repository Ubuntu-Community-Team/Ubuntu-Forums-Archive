---
title: "Disk drive for /dev/mapper crypt swap 1 is not ready or not present on new install"
date: 2014-10-19
forum: Security
---

### Post by mat125 on 2014-10-19
Hi i have recently done a fresh install of Ubuntu 14.04 LTS and let it decide to install everything by itself. Now it says during boot disk drive 
for /dev/mapper crypt swap 1 is not ready or not present. I'm using x86 64

Can anyone explain what this means ?

Thanks.

---

### Post by oldfred on 2014-10-20
It sounds like you did an encrypted install and now it is having issues mounting swap which also is encrypted.

Post these:
sudo parted -l
cat /etc/fstab
       sudo blkid -c /dev/null -o list

---

### Post by mat125 on 2014-10-29
Thanks for your reply i will have to leave the problem as i have run out of time looking at my computer problems. I must say i thought a clean install over everything on my hard disk would be clean. Thought the install of 12.04 previously went alot smoother. Will have to put up with the funny messages on boot. Have noticed it is now harder to disconnect and reconnect my wifi connection aswell.
Still its now up and running after inital failed upgrade and days of head scratching but got there in the end.

Thanks again.

---

