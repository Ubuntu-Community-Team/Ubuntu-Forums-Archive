---
title: "Mdadm does not load at boot"
date: 2015-11-16
forum: Server Platforms
---

### Post by cryptz on 2015-11-16
Hello, 

I installed ubuntu 15.10 from scratch and all is working fine. The system boots from a non raid disk. I installed mdadm and attempted to create a 3 device raid 0. This device will not load at boot. After boot i can manually run mdadm -As and the array is assembled and works fine. I do not believe an attempt is even made to assemble the raid array at boot. I have tried searching dmesg for anything containing md or md0 and my search comes up emtpy. I have tried several variants of /etc/mdadm/mdadm.conf

currently i have the following:

AUTO -all
DEVICE /dev/rssda1 /dev/rssdb1 /dev/rssdc1
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/0  metadata=1.2 UUID=36e2a125:0cd2783c:08061ed2:1e96f656 name=SAN:0

note the md/0 this is a result of the [COLOR=#111111][FONT=Ubuntu]/usr/share/mdadm/mkconf script[/FONT][/COLOR]

Please note i have tried simply: ARRAY /dev/md0 UUID=36e2a125:0cd2783c:08061ed2:1e96f656

i have also ran update-initramfs -u as well.

i believe the issue is related to the fact that nothing is even trying to assemble the array at boot. can anyone tell me what logs to check or where i can look to see if this logic to build the array exists. i thought since i installed the server without raid maybe a core piece of the puzzle is missing.

---

### Post by darkod on 2015-11-17
The ARRAY definition should be enough to auto-assemble the array on boot. The fact that you added mdadm later should not matter. Although I am starting to doubt that since I had another case recently where mdadm added after the install was giving us issues.

You can also try to reconfigure the grub-pc package. You can keep the same options you have, just let it run through the procedure. I have read somewhere that that helps grub reconfigure with mdadm support (although in your case you are not booting from an array so I'm not sure you even need it).
```
sudo dpkg-reconfigure grub-pc
```

Otherwise it all looks good.

---

### Post by cryptz on 2015-11-17
sudo dpkg-reconfigure grub-pc
dpkg-query: package 'grub-pc' is not installed and no information is available

maybe the fact that I am booting in an efi env is related:

root@SAN:/# dpkg --list | grep grub
ii  grub-common                         2.02~beta2-29                   amd64        GRand Unified Bootloader (common files)
ii  grub-efi-amd64                      2.02~beta2-29                   amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version)
ii  grub-efi-amd64-bin                  2.02~beta2-29                   amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 binaries)
ii  grub-efi-amd64-signed               1.55+2.02~beta2-29              amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)
ii  grub2-common                        2.02~beta2-29                   amd64        GRand Unified Bootloader (common files for version 2)

shouldn't there be more output from md: at boot? if not what should I be looking for that would error out in re-creating the array:

root@SAN:/# dmesg | grep md:
[    8.314130] md: raid0 personality registered for level 0
[    8.325082] md: linear personality registered for level -1
[    8.333856] md: multipath personality registered for level -4
[    8.343637] md: raid1 personality registered for level 1
[    8.857690] md: raid6 personality registered for level 6
[    8.862505] md: raid5 personality registered for level 5
[    8.867224] md: raid4 personality registered for level 4
[    8.877135] md: raid10 personality registered for level 10

---

### Post by cryptz on 2015-11-18
I wanted to post a follow up to this. The issue is resolved now and I wanted to just post how it was resolved.

big shout to TJ from #Ubuntu on irc for his help.

Basically the issue was that udev did not regard the /dev/rssd* as a storage device during boot. The pciessds I have have this naming scheme vs say sdx with a normal drive. As a result they were slipping past the boot process and never triggering a mdadm assemble.

the file in question is /lib/udev/rules.d/60-persistent-storage.rules
3 edits had to be made:
1a -KERNEL!="loop*|mmcblk*[0-9]|msblk*[0-9]|mspblk*[0-9]|nvme*|sd*|sr*|vd*|xvd*|bcache*|cciss*|dasd*|ubd*", GOTO="persistent_storage_end"

to:

1b -KERNEL!="rs*|loop*|mmcblk*[0-9]|msblk*[0-9]|mspblk*[0-9]|nvme*|sd*|sr*|vd*|xvd*|bcache*|cciss*|dasd*|ubd*", GOTO="persistent_storage_end"

2a -KERNEL=="sd*|sr*|cciss*", ENV{DEVTYPE}=="disk", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"

to 

2b -KERNEL=="rs*|sd*|sr*|cciss*", ENV{DEVTYPE}=="disk", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"


3a -KERNEL=="sd*|cciss*", ENV{DEVTYPE}=="partition", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

to 

3b KERNEL=="rs*|sd*|cciss*", ENV{DEVTYPE}=="partition", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

the above changes fixed the problem by including rs* devices. however editing this file is not the best solution since it could be overwritten by a system update. it is advisable to instead create a custom rule under /etc/udev/rules.d/59-yourcustomrule.rules

---

