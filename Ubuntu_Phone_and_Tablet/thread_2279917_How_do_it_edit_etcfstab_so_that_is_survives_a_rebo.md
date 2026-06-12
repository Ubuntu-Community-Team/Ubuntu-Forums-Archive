---
title: "How do it edit /etc/fstab so that is survives a reboot"
date: 2015-05-26
forum: Ubuntu Phone and Tablet
---

### Post by Filippo_Rusconi on 2015-05-26
Greetings fellow Ubuntu phone devs/users,

I have the Aquaris E45 phone by bq and I would like to have my sd card mounted at some specific location /home/phablet/sdisk. I edited /etc/fstab using adb shell and inserted the following line:

/dev/mmcblk1    /home/phablet/sdisk ext4 rw,user,auto   0       0

But, when I reboot the phone, the sd card is not mounted at all. I do not see it in the file manager, although I had formatted it in ext4. Upon looking into the system, I found a whole lot of /dev/<xxx> mounted in a large number of location (type 'mount' to list all of them). And I thus discovered that /etc/fstab is actually 'mounted' as a tempfs file. That means that my modification above did not survive the reboot. 

root@ubuntu-phablet:/etc# mount | grep etc
tmpfs on /etc/fstab type tmpfs (rw,nosuid,noexec,relatime,mode=755)


My question is : how can I modify /etc/fstab (the real one, that is the one that is used to make that tempfs item? I tried to search for the code bit that mounts that /etc/fstab as a tempfs item, but could not find it.
Any help ?

Cheers,
Filippo

PS I find the ubuntuphone (the bq's implementation) very pleasant and I am eager to start developing stuff for it...

---

