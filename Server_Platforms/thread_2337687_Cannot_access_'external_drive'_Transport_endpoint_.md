---
title: "Cannot access 'external drive': Transport endpoint is not connected"
date: 2016-09-20
forum: Server Platforms
---

### Post by ehamdja on 2016-09-20
I need help figuring out on mounting my external drive through fstab. Before upgrading to 16.04.1 LTS i never have problem with this. It won't auto mount at boot and when i tried to access the drive it gave me "Cannot access '/media/serverSeagate1': Transport endpoint is not connected" error even though it says it's mounted. I have to manually unmount and remount it. The first 2 lines are okay, only the ntfs-3g type are the problem.

my fstab is as follow:

```
/dev/mmcblk0p1 / vfat defaults 0 0
/dev/mmcblk0p2    /    ext4    defaults    0    1


# UNCONFIGURED FSTAB FOR BASE SYSTEM


/dev/sda1    /media/serverSeagate1    ntfs-3g    auto,uid=1000,gid=1000,umask=007,x-systemd.automount    0    2
/dev/sdb1    /media/serverSeagate2    ntfs-3g    auto,uid=1000,gid=1000,umask=007,x-systemd.automount    0    2
/dev/sdc1    /media/serverWD-Black    ntfs-3g    auto,uid=1000,gid=1000,umask=007,x-systemd.automount    0    2
/dev/sdd1    /media/serverWD-Green    ntfs-3g    auto,uid=1000,gid=33,umask=007,x-systemd.automount    0    2

```
Is there anything i could do to have permanent fix rather than manually fix it? I tried researching it and couldn't find any fix. Please help. Thank you.

---

### Post by darkod on 2016-09-20
Have you tried mounting by UUID not /dev/sdXY? Especially with removable devices, I'm not sure you can depend on /dev/sdXY that much. I would use UUID.

Another thing, are you sharing the drives with windows? If not, make them linux filesystem, much better...

---

### Post by ehamdja on 2016-09-20
I am sharing it with windows by using samba. I am using it for my Owncloud setup.
Yes, it finally got mounted automatically after following your suggestion. 

```

/dev/mmcblk0p1 / vfat defaults 0 0
/dev/mmcblk0p2    /    ext4    defaults    0    1

# UNCONFIGURED FSTAB FOR BASE SYSTEM

UUID="BED08759D0871735"    /media/serverSeagate2    ntfs-3g      auto,uid=1000,gid=1000,umask=007,x-systemd.automount    0    2
UUID="8264C97C64C97407"    /media/serverSeagate1    ntfs-3g    auto,uid=1000,gid=1000,umask=007,x-systemd.automount    0    2
UUID="7064857264853C3A"    /media/serverWD-Black    ntfs-3g    auto,uid=1000,gid=1000,umask=007,x-systemd.automount    0    2
UUID="E4102C82102C5DB4"    /media/serverWD-Green    ntfs-3g    auto,uid=1000,gid=33,umask=007,x-systemd.automount    0    2

```

Thank you Darko!!!


On the down side, now on my webmin it shows they are not mounted even though they are (I can access it) (i attached pic). Do you think it's a glitch? or somthing wrong?
I tried to enable it from webmin just to test, it gives me [COLOR=#333333]mount: can't find UUID=""8264C97C64C97407"" with double quotes "" on each end. I am confused now [/COLOR]:confused:

---

### Post by darkod on 2016-09-21
1. Using samba does not mean you need to have ntfs partitions. On the contrary, linux (and samba in it) will work more naturally with linux filesystem on the partitions. Samba is taking care to offer the shares to windows clients using the correct format (CIFS), and windows client do not care about the actual filesystem on the partitions. 
If you still don't have too much data on the shares I would consider switching them to ext4.
But if you do take the disks and plug them into windows machine sometimes, in that case you need the partitions to be ntfs otherwise windows will not be able to use them.

2. Webmin is not supported and not recommended. You should stop using it ASAP. Try starting to learn CLI control of the linux servers, not to depend on webmin. Sometimes it modified files in different way unexpected for the OS and it might be only question of time when it will break something without you knowing it was webmin.
As for the double quotes issue, probably webmin is adding quotes so you need to put in the UUID without any quotes. But I would really not use it, especially for important things like mounting and fstab. The choice is yours...

---

### Post by ehamdja on 2016-09-21
1. I will try the other two of the drives to make them ext4, as the other two i already have some datas and some for my owncloud data. So i will leave it as it is.
2. I am trying to learn CLI control but having hard time as i am still new and learning the whole linux command. Sometimes webmin provide me some kind of clue what to do and how to do in graphical sense (i don't know if it makes sense) But yes ultimately my goal is to do at least comfortable with CLI control, that's why i am using webmin and shellinabox side by side to learn for now. But thank you and i appreciate your advice and help. I guess we can mark this thread as solved.

---

### Post by darkod on 2016-09-22
If you want to mark the thread as Solved you can do that in Thread Tools above the first post. Cheers.

---

