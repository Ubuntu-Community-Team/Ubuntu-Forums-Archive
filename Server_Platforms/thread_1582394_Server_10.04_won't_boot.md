---
title: "Server 10.04 won't boot"
date: 2010-09-26
forum: Server Platforms
---

### Post by flycast on 2010-09-26
On a brand new 1Tb drive I installed Ubuntu 10.04 Server LTS, added a lightweight gui, set up samba and have been using it for a couple of weeks. I am liking it! When I installed I had an old NTFS drive in as well. I am repurposing an XP machine in a home/small business network by taking an older XP machine and installing Ubuntu server. When I installed Ubuntu I instructed the install to add grub to the NTFS drive as well.

The Grub failed on the NTFS drive - it does not boot. That is OK as all I want to do is get old files off before I turn that into the system drive. It seemed to boot OK on the Ubuntu install and I set up Samba and have been serving files since. I was in the slow process of moving files off the old XP drive.

I lost power in a storm yesterday and now my system won't boot. I get the ureadahead-other status 4 message (which is good) and then it just sits. I have tried booting by having one of both disks installed physically:

1Tb Ubuntu volume connected and powered alone
1Tb Ubuntu/250Gb NTFS both connected and powered

My boot hangs either way and I don't know how to fix. I am a linux noob...any help would be appreciated.

---

### Post by mariuszwar on 2010-09-27
Hi,
Try to boot LiveCD again any Linux distro, and then do:
# sudo fdisk -l (to show partitions on your disk)
and then 
# sudo fsck /dev/sdax (x for partition number) for any linux partitions (ext2-ext4)

If You'll have to umount  /dev/sdax before doing fsck

---

### Post by flycast on 2010-09-27
Thanks mariuszwar:

What I was trying to avoid is transferring the data to a temporary drive over the network as it is much slower that transferring from drive to drive in the same machine. I finally just transferred the data off the smaller drive and set it up as my final OS install and then mounted the larger drive.

Thanks for the tips.

---

