---
title: "HOWTO: migrate wubi install to partition"
date: 2010-06-28
forum: Tutorials
---

### Post by bcbc on 2010-06-28
The information in this thread have been moved to [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012400](http://ubuntuforums.org/showthread.php?t=2012400)

Thread closed.


[COLOR="Blue"]**This HOWTO has been moved to a community-maintained Wiki**[/COLOR]: [https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")

For the reason why, see [here]("http://ubuntuforums.org/showthread.php?t=1949027").
=============================================================

This HOWTO describes how to migrate a Wubi install to partition. The partition(s) must be created already - this is not covered in this guide (but see [here]("http://ubuntuforums.org/showpost.php?p=11021363&postcount=418")). The examples shown below assume the target partition is [COLOR=Red]/dev/sda5[/COLOR] and the swap partition (if required) is [COLOR=Blue]/dev/sda6[/COLOR].

**_Automatic migration_**
The migration supports Wubi installs from 8.04 to 12.04, with Grub2 or grub-legacy. 
First download the attached file **wubi-move-2.2.tar.gz** to your Downloads directory, right-click and choose "Extract here". 
The rest of the migration is run from the terminal. See [How to migrate in pictures]("http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html")

To migrate to [COLOR=red]/dev/sda5[/COLOR] with swap on [COLOR=blue]/dev/sda6[/COLOR]
```
sudo bash wubi-move-2.2.sh [COLOR=red]/dev/sda5[/COLOR] [COLOR=Blue]/dev/sda6[/COLOR]

```To migrate to [COLOR=Red]/dev/sda5[/COLOR] without swap
```
sudo bash wubi-move-2.2.sh [COLOR=red]/dev/sda5[/COLOR]

```If you **don't** want to install the grub bootloader, use the --no-bootloader option. You can boot from the Wubi install's grub menu temporarily and manually install the grub bootloader later.
```
sudo bash wubi-move-2.2.sh --no-bootloader [COLOR=Red]/dev/sda5[/COLOR] [COLOR=Blue]/dev/sda6[/COLOR]
```To migrate from the root.disk when running from a live CD/USB:
```
sudo bash wubi-move-2.2.sh --root-disk=/media/win/ubuntu/disks/root.disk [COLOR=red]/dev/sda5[/COLOR] [COLOR=blue]/dev/sda6[/COLOR]
```The path to the root.disk is case-sensitive and if it contains spaces they must be escaped e.g.
```
sudo bash wubi-move-2.2.sh --root-disk=/media/New\ Volume/ubuntu/disks/root.disk [COLOR=red]/dev/sda5[/COLOR] [COLOR=blue]/dev/sda6[/COLOR]
```
You can migrate to separate partitions for /boot, /usr and /home
```
sudo bash wubi-move-2.2.sh [COLOR=red]/dev/sda5[/COLOR] [COLOR=blue]/dev/sda6[/COLOR] --boot=/dev/sda1 --usr=/dev/sda7 --home=/dev/sda8
```
For full usage instructions and notes:
```
bash wubi-move-2.2.sh --help
bash wubi-move-2.2.sh --notes
```The code is now hosted on GitHub. You can keep track of new development or contribute. See [https://github.com/bcbc/Wubi-move](https://github.com/bcbc/Wubi-move)

Known issues with script:
1. Running "update-grub" in the chroot doesn't pick up other linux installations on the same drive (same running the script or manual commands listed above). This is unlikely an issue for wubi users. Run sudo update-grub after booting the new install for the first time.
2. Only the current kernel's initrd.img is updated on the migrated install; if you require others you can update them with "sudo update-initramfs -u -k <kernel version>".
3. [End of life releases]("https://help.ubuntu.com/community/EOLUpgrades") that have grub-legacy must be upgraded to a supported release before migrating.

Other known issues:
1. Many older BIOSes cannot address more than 137GB from the start of the disk. If you try migrating to a partition that falls outside of this, then Grub2 will fail to load it's boot files. Even if only a part of the partition falls outside this range there is a possibility of grub failure in the future. Therefore, either confirm your BIOS is unaffected prior to partitioning, or ensure your target partition falls within this limit, or migrate to a separate boot partition within this limit.
2. The process that Wubi uses to boot (wubildr.mbr) cannot read ext3/4 partitions prior to release 11.10. It reads partitions in BIOS order looking for the wubildr file, so if finds an ext3/4 partiton before it finds the wubildr file - it will hang up. So, make sure you install the grub2 bootloader if you migrate to a partition lower than the one containing wubildr i.e. if Windows is on /dev/sda2 and you migrate to /dev/sda1

_A note on hibernation_:
The migration script will enable hibernation automatically, provided you migrate with a swap partition **and** the swap partition is large enough (must be > the size of your RAM).

For those interested, I've included the steps required to manually migrate in another [post]("http://ubuntuforums.org/showpost.php?p=11828696&postcount=675").

---

### Post by SteveGoTex on 2010-07-03
I used this to migrate an installation on a Dell Inspiron 9400. Worked with no problems.
Thanks very much for this, especially since the LVPM approach does not work for 10.04.

Will be trying this on an MSI Wind next..

Steve

---

### Post by SteveGoTex on 2010-07-03
The MSI WInd worked as well. It has netbook edition installed, with Win7 as the other OS.

In both cases, I had to manually install grub to the MBR after booting up the new installation. Other than that it worked as advertised.

Thanks again.
Steve

---

### Post by bcbc on 2010-07-03
> **SteveGoTex said:**
> The MSI WInd worked as well. It has netbook edition installed, with Win7 as the other OS.

In both cases, I had to manually install grub to the MBR after booting up the new installation. Other than that it worked as advertised.

Thanks again.
Steve

Great - thanks for the feedback. :)

Regarding needing to install grub afterwards, are you saying that the command 'grub-install /dev/sda' didn't work (if you ran it manually) or that the script failed to install it (and you didn't specify --no-bootloader)?

---

### Post by SteveGoTex on 2010-07-03
It did not work from the script, while i was still running in the Wubi installation. Once I had rebooted the new installation (from the Wubi boot list), was able to install grub to the MBR.

---

### Post by bcbc on 2010-07-04
> **SteveGoTex said:**
> It did not work from the script, while i was still running in the Wubi installation. Once I had rebooted the new installation (from the Wubi boot list), was able to install grub to the MBR.

It seems to be working for me... you should have been prompted:
```
wubi-move.sh: The grub2 bootloader will be installed to drive (/dev/sda)
wubi-move.sh: If you select no, you have to boot your new install
wubi-move.sh: from the wubi menu and install it later manually.
wubi-move.sh: Install the grub bootloader to /dev/sda? (Y/N)

```
Then, unless, you enter 'n' or 'N' it proceeds to install it. 

Note, if you migrate your wubi to a partition on another drive, the script will only permit installing the bootloader on that drive, which may not necessarily be the drive you boot from.

The only exception to this is if you use the --no-bootloader option. But I'll run some more tests anyway to make sure.

EDIT:
After further testing I've discovered that the package lupin-support (required for Wubi installs) modifies the grub-install command, but this isn't consistent across releases. For 10.04 the command 'grub-install --root-directory=xxx /dev/sda' was not actually updating the MBR, whereas on a 9.10 install it works fine. So I've modified the script to run grub-install within the target install (using chroot) as the lupin-support is already removed and the results should be consistent across releases.

Thanks again for the feedback.

Further EDIT: 
In fact there is a bug in lupin-support in 10.04 Ubuntu that makes grub-install act differently depending on whether the wubi is installed on the same partition as windows or not. In my case, the --root-directory option was working, but when I tried the same command on a more typical install on the same partition as windows, it did not work. 

It's not relevant for the migration anymore as the script is doing grub-install in chroot, however, might impact other wubi users. Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417)

---

### Post by sav25 on 2010-07-07
Hi
 
Apologies, I'm very new to Ubuntu and terminology etc.
 
I have a hard drive that is partitioned into 2 seperate partitions i.e. looks like 2 seperate drives. I'll call these drive 1 and drive 2.
 
Drive 1 is where my XP is installed, and I believe my Ubuntu 'wubi' is installed here too. Drive 2 is literally just used as a store for all my pictures, music and videos.
 
What I want to do is remove XP, merge the partitions into a single drive and use Ubuntu only (migrate away from wubi?).
 
Can this be done using the method above?
 
I can copy all of the files in 'Drive 2' to and external HD so after that, I dont mind deleting everything on the drive.
 
Thanks,
 
Rich

---

### Post by bcbc on 2010-07-07
> **sav25 said:**
> Hi
 
Apologies, I'm very new to Ubuntu and terminology etc.
 
I have a hard drive that is partitioned into 2 seperate partitions i.e. looks like 2 seperate drives. I'll call these drive 1 and drive 2.
 
Drive 1 is where my XP is installed, and I believe my Ubuntu 'wubi' is installed here too. Drive 2 is literally just used as a store for all my pictures, music and videos.
 
What I want to do is remove XP, merge the partitions into a single drive and use Ubuntu only (migrate away from wubi?).
 
Can this be done using the method above?
 
I can copy all of the files in 'Drive 2' to and external HD so after that, I dont mind deleting everything on the drive.
 
Thanks,
 
Rich

The method here is a straightforward migration of wubi to a new partition. It's intended for users who want to keep all the customization they've done on a wubi install, but would like to move to a 'traditional' dual boot.

It's possible to use it as part of a strategy to accomplish what you want, but I think you should create a separate thread for this as it's going beyond the scope of the topic. You can edit your post above with a link to the thread and I'll find it.

---

### Post by fbtb on 2010-07-13
Thank you sooo much! Awesome Guide! Finally i could migrate my Kubuntu 10.04!
I only had to reinstall my nvidia (proprietary) drivers. Everything else worked perfectly!
Thank you!

---

### Post by bcbc on 2010-07-14
> **fbtb said:**
> Thank you sooo much! Awesome Guide! Finally i could migrate my Kubuntu 10.04!
I only had to reinstall my nvidia (proprietary) drivers. Everything else worked perfectly!
Thank you!

Great, you're welcome :)

I'll take a look at the driver issue when I get a moment. I don't use proprietary graphics drivers, but I don't see any reason why this wouldn't be included in the migration.

---

### Post by rainazure on 2010-07-14
can I re-publish your guide with my native language and share it to my friends? 

:D

---

### Post by bcbc on 2010-07-14
> **rainazure said:**
> can I re-publish your guide with my native language and share it to my friends? 

:D

Feel free :)

Note that the script is under GNU GPL, as it is based on the original wubi-move-to-partition from the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How do I migrate to a real partition, and/or get rid of Windows entirely?")

---

### Post by lucastrike on 2010-07-20
Just want to say thanks for this thread. I migrated a wubi partition a year or two ago and it was hectic, but this method was astonishingly easy. For anyone that's interested, here is what I did:

1. Started with a single partition with windows.
2. Used an old version of Partition Magic to resize windows partition, leaving a large part of the drive unallocated.
3. Installed Wubi and got ubuntu up and running.
4. In ubuntu, installed gparted via synaptic manager.
5. Using gparted, made a 1gb swap (for 512 ram) on the end of the unallocated space, and in the middle between windows and swap, I created an ext4 partition.
6. Downloaded wubi-move.sh, opened terminal, navigated to my download folder, and typed "sudo bash wubi-move.sh /dev/sda2 /dev/sda3" being sure to say "Y" to grub
7. It finished, and I now have a full ubuntu installation on my broken-floppy, broke-cd, no-usb-boot laptop. 

Thank you again.

---

### Post by bcbc on 2010-07-20
> **lucastrike said:**
> Just want to say thanks for this thread. I migrated a wubi partition a year or two ago and it was hectic, but this method was astonishingly easy. For anyone that's interested, here is what I did:

1. Started with a single partition with windows.
2. Used an old version of Partition Magic to resize windows partition, leaving a large part of the drive unallocated.
3. Installed Wubi and got ubuntu up and running.
4. In ubuntu, installed gparted via synaptic manager.
5. Using gparted, made a 1gb swap (for 512 ram) on the end of the unallocated space, and in the middle between windows and swap, I created an ext4 partition.
6. Downloaded wubi-move.sh, opened terminal, navigated to my download folder, and typed "sudo bash wubi-move.sh /dev/sda2 /dev/sda3" being sure to say "Y" to grub
7. It finished, and I now have a full ubuntu installation on my broken-floppy, broke-cd, no-usb-boot laptop. 

Thank you again.
Great, you're welcome :)

That's a good workaround - I was considering doing this on my netbook the other day.

---

### Post by dieter1 on 2010-08-02
Hi bcbc,

Just followed your manual instructions and successfully moved my wubi onto a new partition without a hitch. Excellent work. I'm really pleased!

A question I still have: Now when I boot I don't get the option of going into Windows. Instead, I get the Ubuntu option of the new partition (sda7) and the wubi option (or so I think, as it says Ubuntu sda1). However, when I click on the wubi option it directs me to the screen I used to have when I booted, which was Ubuntu (wubi) and Windows. When I click on Windows, it opens just fine. (I'd like to get rid of XP, but I still need it for Geosetter and to get at my Bible commentaries in Libronix).

I'm just wondering what will happen if I uninstall wubi-Ubuntu within Windows: Will Windows still show up when I boot? I'm a bit scared to experiment: Before I installed wubi I tried to install Ubuntu on a new partition parallel to Windows with the net result that the computer refused to boot at all. Wubi worked fine as has this migration. In all fairness, I think it was my Windows setup that caused things to go awry the first time.

Thanks again for your help!

---

### Post by dieter1 on 2010-08-02
ok, I uninstalled ubuntu in Windows XP without a hitch and deleted wubildr.mbr='Ubuntu' in boot.ini. No problem! A slight cosmetic issue: The last option on the bootscreen says Ubuntu but boots Windows when entered. But Windows and Ubuntu now boot without a hitch.

Great!

---

### Post by dieter1 on 2010-08-02
> **dieter1 said:**
> ok, I uninstalled ubuntu in Windows XP without a hitch and deleted wubildr.mbr='Ubuntu' in boot.ini. No problem! A slight cosmetic issue: The last option on the bootscreen says Ubuntu but boots Windows when entered. But Windows and Ubuntu now boot without a hitch.

Great!

Ok, got the cosmetic issue sorted out. sudo update-grub was all I needed to do. :D

---

### Post by bcbc on 2010-08-02
> **dieter1 said:**
> ok, I uninstalled ubuntu in Windows XP without a hitch and deleted wubildr.mbr='Ubuntu' in boot.ini. No problem! A slight cosmetic issue: The last option on the bootscreen says Ubuntu but boots Windows when entered. But Windows and Ubuntu now boot without a hitch.

Great!

That's interesting... I've never seen grub from a regular install pick up a wubi install within windows before. Maybe it's a new thing. Are you running 10.04 with the latest updates?

Good you got it resolved. It's always a good idea to run sudo update-grub after the migration... I've seen some minor oddities when running update-grub within the chroot.

UPDATE: If the Wubi Ubuntu was set as the default OS in Windows Boot Manager, grub will use it to identify your Windows install. This can be solved by changing the default OS in Windows Startup & Recover settings and rerunning "sudo update-grub"

---

### Post by Ziggy72 on 2010-08-06
Thank you. The script worked well. The only issue now is with grub. When booting from grub, I now don't get any splash screen. In fact, after choosing to boot from a kernel of choice the screen remains blank for about 15 seconds before it springs to life with a fully-formed Lucid display screen. I suppose that's ok but I would like to see something happening during the boot. I've enabled everything I think I should in startup manager. I'm using an x64 installation. I've done sudo update-grub several times

---

### Post by bcbc on 2010-08-06
> **Ziggy72 said:**
> Thank you. The script worked well. The only issue now is with grub. When booting from grub, I now don't get any splash screen. In fact, after choosing to boot from a kernel of choice the screen remains blank for about 15 seconds before it springs to life with a fully-formed Lucid display screen. I suppose that's ok but I would like to see something happening during the boot. I've enabled everything I think I should in startup manager. I'm using an x64 installation. I've done sudo update-grub several times

I'm not sure that this has anything to do with the migration. There is a known issue with the boot splash showing. [This thread]("http://ubuntuforums.org/showthread.php?t=1469475") has a short description and fix, and this is the full [bug report]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801").

---

### Post by mercurius80 on 2010-08-07
Thank you very much bcbc!!! Your script has worked wonderly on my old toshiba satellite.

I want republish your fantastic guide in italian on my blog.

Excuse my bad english... Good look!:wink:

---

### Post by bcbc on 2010-08-07
> **mercurius80 said:**
> Thank you very much bcbc!!! Your script has worked wonderly on my old toshiba satellite.

I want republish your fantastic guide in italian on my blog.

Excuse my bad english... Good look!:wink:

Great you're welcome :) Feel free to republish.

---

### Post by k2filter on 2010-08-11
Exactly, what I was looking for.
Thanks a lot for such an awesome post :popcorn:

---

### Post by maskiepop on 2010-08-15
Hi. Add me to your growing fan base. 

Finding your script and this article solved a number of headaches for me. I have spent weeks getting LVPM to work, and when it seemed to me that I won't be able to, I thought I was in serious trouble. I have tried other tools as well, not just LVPM.

It started way way back. There is something between the CD/DVD device on my computer and ubuntu/linux distros. It's not media; it is not hardware. My WinXP, running on the same computer, reads, checks and verifies these distros without any problem. The same with my son's Ubuntu machine. But for whatever reason, my computer simply won't run those distros live from the cd the way they were meant to. 

My machine does not boot from a USB stick, either.

A few years back, the only way I was able to dual boot a winxp and an ubuntu 8.04 on my machine was via wubi, and then onto separate partitions with lvpm afterwards. I am not a techie; the pc/linux/win world is alien territory to me. So you could very well imagine how difficult and painful this was for me. Even days afterwards, I still dreaded the thought that I may have to go through it again.

To cut this short: it's been a great relief to me when I saw your script worked.

Thank you very much.

---

### Post by bcbc on 2010-08-16
> **k2filter said:**
> Exactly, what I was looking for.
Thanks a lot for such an awesome post :popcorn:

> **maskiepop said:**
> 
Thank you very much.

I'm glad to hear it's helping out :D

---

### Post by jaycee23 on 2010-08-17
Nice work bcbc

Don't need to use it but happy to appreciate some clever scripting
;)

---

### Post by bcbc on 2010-08-18
> **jaycee23 said:**
> Nice work bcbc

Don't need to use it but happy to appreciate some clever scripting
;)

Thanks - I appreciate the complement :)

(I have to reiterate that I just patched and enhanced Agostino Russo's original script. I don't want to take credit for his work.)

---

### Post by ULTRAM4X on 2010-08-21
Hello,

Thanks a lot for the HOWTO!

my question:

when im at this step

root@ubuntu:/# grub-install /dev/sda

i get the following

/dev/loop0 does not have any corresponding BIOS drive.

can u help me please?

Thanks again!

---

### Post by bcbc on 2010-08-21
> **ULTRAM4X said:**
> Hello,

Thanks a lot for the HOWTO!

my question:

when im at this step

root@ubuntu:/# grub-install /dev/sda

i get the following

/dev/loop0 does not have any corresponding BIOS drive.

can u help me please?

Thanks again!
Did you notice any other errors before this? Post the terminal output between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.


Try: 
```
grub-install --recheck /dev/sda
```

---

### Post by ULTRAM4X on 2010-08-21
well, when i was here

```
root@ubuntu:~# apt-get -y remove lupin-support
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete lupin-support no esta instalado, no se eliminará
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-amd64_Packages)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

```i get that error.

trying

```

root@ubuntu:~# grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
/dev/loop0 does not have any corresponding BIOS drive.
```

---

### Post by bcbc on 2010-08-21
> **ULTRAM4X said:**
> well, when i was here

```
root@ubuntu:~# apt-get -y remove lupin-support
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete lupin-support no esta instalado, no se eliminará
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-amd64_Packages)
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

```i get that error.

trying

```

root@ubuntu:~# grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
/dev/loop0 does not have any corresponding BIOS drive.
```

So from my limited translation skills, it looks like you don't have lupin-support installed? This is strange since you should have booted into a wubi install before migrating.

Can you run grub-install with the --debug option?

i.e. grub-install --debug /dev/sda

EDIT:
if you're having issues, you can complete the migration - all the steps to exit the chroot (just ignore grub-install and update-grub). Then reboot and try again. You haven't changed the wubi install at this point, so you can just rerun the migration (and reformat the target partition). I am a bit concerned about the missing lupin-support, so think it's safer to try again.

---

### Post by ULTRAM4X on 2010-08-21
yes, i had lupin-support before!

but in this step

```
apt-get -y remove lupin-support
```was uninstalled.

trying

root@ubuntu:~# grub-install --debug /dev/sda

```
+ bootdir=/boot
+ grubdir=/boot/grub
+ device_map=/boot/grub/device.map
+ set /usr/sbin/grub dummy
+ test -f /usr/sbin/grub
+ :
+ test -f /usr/lib/grub/x86_64-pc/stage1
+ :
+ test -f /usr/lib/grub/x86_64-pc/stage2
+ :
+ test -d /boot
+ test -d /boot/grub
+ test no = yes
+ test -f /boot/grub/device.map
+ :
+ sed -n /^([fh]d[0-9]*)/s/\(^(.*)\).*/\1/p /boot/grub/device.map
+ uniq -d
+ sort
+ sed -n 1p
+ tmp=
+ test -n 
+ find_device
+ df /
+ sed -n s%.*\(/dev/[^  ]*\).*%\1%p
+ tmp_fname=/dev/loop0
+ test -z /dev/loop0
+ resolve_symlink /dev/loop0
+ tmp_fname=/dev/loop0
+ test -L /dev/loop0
+ echo /dev/loop0
+ tmp_fname=/dev/loop0
+ echo /dev/loop0
+ root_device=/dev/loop0
+ find_device /boot
+ df /boot/
+ sed -n s%.*\(/dev/[^  ]*\).*%\1%p
+ tmp_fname=/dev/loop0
+ test -z /dev/loop0
+ resolve_symlink /dev/loop0
+ tmp_fname=/dev/loop0
+ test -L /dev/loop0
+ echo /dev/loop0
+ tmp_fname=/dev/loop0
+ echo /dev/loop0
+ bootdir_device=/dev/loop0
+ resolve_symlink /dev/sda
+ tmp_fname=/dev/sda
+ test -L /dev/sda
+ echo /dev/sda
+ install_device=/dev/sda
+ convert /dev/sda
+ test -e /dev/sda
+ :
+ sed -e s%\([vsh]d[a-z]\)[0-9]*$%\1% -e s%\(d[0-9]*\)p[0-9]*$%\1% -e s%\(fd[0-9]*\)$%\1% -e s%/part[0-9]*$%/disc% -e s%\(c[0-7]d[0-9]*\).*$%\1% -e s%\(e[0-9]\.[0-9]*\).*$%\1%
+ echo /dev/sda
+ tmp_disk=/dev/sda
+ echo /dev/sda
+ sed -e s%.*/[vsh]d[a-z]\([0-9]*\)$%\1% -e s%.*d[0-9]*p%% -e s%.*/fd[0-9]*$%% -e s%.*/floppy/[0-9]*$%% -e s%.*/\(disc\|part\([0-9]*\)\)$%\2% -e s%.*c[0-7]d[0-9]*p*%% -e s%.*e[0-9]\.[0-9]*p%% -e s%.*e[0-9]\.[0-9]*$%%
+ tmp_part=
+ grep -v ^# /boot/grub/device.map
+ sed s%.*\(([hf]d[0-9][a-z0-9,]*)\).*%\1%
+ grep /dev/sda *$
+ tmp_drive=(hd0)
+ test x(hd0) = x
+ test x != x
+ echo (hd0)
+ install_drive=(hd0)
+ test x(hd0) = x
+ test x/dev/loop0 != x/dev/loop0
+ convert /dev/loop0
+ test -e /dev/loop0
+ :
+ echo /dev/loop0
+ sed -e s%\([vsh]d[a-z]\)[0-9]*$%\1% -e s%\(d[0-9]*\)p[0-9]*$%\1% -e s%\(fd[0-9]*\)$%\1% -e s%/part[0-9]*$%/disc% -e s%\(c[0-7]d[0-9]*\).*$%\1% -e s%\(e[0-9]\.[0-9]*\).*$%\1%
+ tmp_disk=/dev/loop0
+ echo /dev/loop0
+ sed -e s%.*/[vsh]d[a-z]\([0-9]*\)$%\1% -e s%.*d[0-9]*p%% -e s%.*/fd[0-9]*$%% -e s%.*/floppy/[0-9]*$%% -e s%.*/\(disc\|part\([0-9]*\)\)$%\2% -e s%.*c[0-7]d[0-9]*p*%% -e s%.*e[0-9]\.[0-9]*p%% -e s%.*e[0-9]\.[0-9]*$%%
+ tmp_part=/dev/loop0
+ sed s%.*\(([hf]d[0-9][a-z0-9,]*)\).*%\1%
+ grep /dev/loop0 *$
+ grep -v ^# /boot/grub/device.map
+ tmp_drive=
+ test x = x
+ echo /dev/loop0 does not have any corresponding BIOS drive.
/dev/loop0 does not have any corresponding BIOS drive.
+ mdadm --detail /dev/loop0
+ exit 1
+ root_drive=
+ test x = x
+ exit 1
```

EDIT:

Well, I think the best thing is to run the script
but it appears the following:

```
root@ubuntu:/# sudo bash wubi-move.sh /dev/sda4 /dev/sda3
wubi-move.sh: Grub (legacy) is installed - this code supports grub2
```

---

### Post by bcbc on 2010-08-21
> **bcbc said:**
> These are the steps required to migrate a wubi 9.10 or 10.04 install to partition (grub2 only). The first part shows how to do a manual migration, and the second how to use the attached script to do an automated migration.

> **ULTRAM4X said:**
> Well, I think the best thing is to run the script
but it appears the following:

```
root@ubuntu:/# sudo bash wubi-move.sh /dev/sda4 /dev/sda3
wubi-move.sh: Grub (legacy) is installed - this code supports grub2
```

If you notice, my script only support grub2. This doesn't mean that you can't convert an install with grub-legacy, but not using the above commands (either manual or with the script). The script has that additional error check, because it's automated, but the onus is on you to do your own validation for the manual conversion (otherwise it would be too confusing to follow).

give me a couple of minutes to check it out...

---

### Post by bcbc on 2010-08-21
The best I can offer is to remove grub-legacy and install grub2 (in the chroot). 

So you'll have to run the following (first exit chroot, and then reenter because you need resolve.conf to have net access)
```
Edit commands erased - see post 38
```

I will take a look at including a section to convert using grub-legacy in the future, but I'll need some time to figure it out and test it.

---

### Post by ULTRAM4X on 2010-08-21
[COLOR=#000000]sorry for my ignorance (and for my English) but I am new at this,

how [/COLOR]exit chroot, and then reenter? :oops:


[COLOR=#000000]

[/COLOR]

---

### Post by bcbc on 2010-08-21
> **ULTRAM4X said:**
> [COLOR=#000000]sorry for my ignorance (and for my English) but I am new at this,

how [/COLOR]exit chroot, and then reenter? :oops:


[COLOR=#000000]

[/COLOR]

No worries - you can just enter the commands as I wrote them.
```
EDIT:commands erased - see post 38
```

If you get any error or something looks incorrect just post back.

---

### Post by ULTRAM4X on 2010-08-21
typing exit closes the terminal :(

and 
```

ultram4x@ubuntu:/$ cp /etc/resolv.conf /tmp/wubimove/etc
cp: no se puede crear el fichero regular «/tmp/wubimove/etc»: No existe el archivo o directorio
```

im using Kubuntu 10.04

---

### Post by bcbc on 2010-08-21
> **ULTRAM4X said:**
> typing exit closes the terminal :(

and 
```

ultram4x@ubuntu:/$ cp /etc/resolv.conf /tmp/wubimove/etc
cp: no se puede crear el fichero regular «/tmp/wubimove/etc»: No existe el archivo o directorio
```im using Kubuntu 10.04

If you were still in the chroot, then exit would take you out of it. Also it looks like /tmp/wubimove doesn't exist. Did you unmount and delete it? It's difficult for me to know exactly what you've done, but it looks like you exited the chroot and unmounted the target partition. At this point I think it's safer to forget about migrating and try again later, when I can give explicit, tested instructions start to finish. And/or include a script that will do it - which is safer for most users.

EDIT: I haven't been able to successfully migrate a wubi install with legacy-grub - I'm removing instructions until such time as I have it working.

UPDATE: See [http://ubuntuforums.org/showpost.php?p=9894476&postcount=92](http://ubuntuforums.org/showpost.php?p=9894476&postcount=92) for migrating wubi with legacy-grub.

---

### Post by bcbc on 2010-08-21
Before you reboot, run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here. I just want to make sure you don't have grub in your MBR.

---

### Post by ULTRAM4X on 2010-08-21
ok i run the last that u post and had no errors


Here is the report made by bootinfoscript 

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Paragon is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/home.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   245,762,047   245,760,000   7 HPFS/NTFS
/dev/sda2         245,762,048   578,033,663   332,271,616   7 HPFS/NTFS
/dev/sda3         578,034,765   582,131,339     4,096,575  82 Linux swap / Solaris
/dev/sda4         582,131,340   625,137,344    43,006,005  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros, 390721968 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   179,777,535   179,775,488   7 HPFS/NTFS
/dev/sdb2         179,783,415   390,716,864   210,933,450   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 82.0 GB, 81964302336 bytes
255 cabezas, 63 sectores/pista, 9964 cilindros, 160086528 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   160,081,714   160,081,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       899deaa9-ce2b-47c4-9937-b8d32e159d33   ext4                                     
/dev/loop1       bc326b68-a05b-4e35-a8ef-9a7e350c60f9   ext3                                     
/dev/sda1        5E68AF0868AEDE51                       ntfs       AnimE                         
/dev/sda2        687402E07402B13C                       ntfs       Música y PeliS               
/dev/sda3        bb7214ba-7a93-4e4f-9937-9b86e54c87ce   swap                                     
/dev/sda4        56ac17b8-be0b-4250-bfcc-83efb9b44b71   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4E0849B80849A037                       ntfs       APPZ & DescargaS              
/dev/sdb2        AE10873510870395                       ntfs       JuegoS                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F8289C1B289BD74A                       ntfs       RaiZ                          
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/loop1       /home                    ext3       (rw)
/dev/sdb2        /media/JuegoS            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /media/APPZ & DescargaS  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /media/AnimE             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1        /media/RaiZ              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


======================== sda2/Wubi/boot/grub/menu.lst: ========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=687402E07402B13C loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=687402E07402B13C

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        687402E07402B13C
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=687402E07402B13C loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        687402E07402B13C
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=687402E07402B13C loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic
uuid        687402E07402B13C
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=687402E07402B13C loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        687402E07402B13C
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=687402E07402B13C loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        687402E07402B13C
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 687402e07402b13c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 687402e07402b13c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 687402e07402b13c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 687402e07402b13c
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set f8289c1b289bd74a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/host/ubuntu/disks/home.disk    /home    ext3    loop    0    0

================= sda2/Wubi: Location of files loaded by Grub: =================


   2.8GB: boot/grub/grub.cfg
   6.7GB: boot/grub/menu.lst
   1.8GB: boot/initrd.img-2.6.32-21-generic
   5.6GB: boot/initrd.img-2.6.32-24-generic
   3.4GB: boot/vmlinuz-2.6.32-21-generic
   4.1GB: boot/vmlinuz-2.6.32-24-generic
   5.6GB: initrd.img
   1.8GB: initrd.img.old
   4.1GB: vmlinuz
   3.4GB: vmlinuz.old

=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
set locale_dir=($root)/boot/grub/locale
set lang=es
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, con Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=56ac17b8-be0b-4250-bfcc-83efb9b44b71 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-24-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
    echo    'Cargando Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=56ac17b8-be0b-4250-bfcc-83efb9b44b71 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=56ac17b8-be0b-4250-bfcc-83efb9b44b71 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
    echo    'Cargando Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=56ac17b8-be0b-4250-bfcc-83efb9b44b71 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 56ac17b8-be0b-4250-bfcc-83efb9b44b71
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0



UUID=56ac17b8-be0b-4250-bfcc-83efb9b44b71    /    ext4    errors=remount-ro    0    1
UUID=bb7214ba-7a93-4e4f-9937-9b86e54c87ce    none    swap    sw    0    0

=================== sda4: Location of files loaded by Grub: ===================


 307.1GB: boot/grub/core.img
 307.2GB: boot/grub/grub.cfg
 298.1GB: boot/initrd.img-2.6.32-21-generic
 306.7GB: boot/initrd.img-2.6.32-24-generic
 306.7GB: boot/vmlinuz-2.6.32-21-generic
 306.7GB: boot/vmlinuz-2.6.32-24-generic
 306.7GB: initrd.img
 298.1GB: initrd.img.old
 306.7GB: vmlinuz
 306.7GB: vmlinuz.old
```

now i will reboot

---

### Post by ULTRAM4X on 2010-08-21
i boot the wubi installation again

---

### Post by bcbc on 2010-08-21
> **ULTRAM4X said:**
> ok i run the last that u post and had no errors

<snip>

now i will reboot

OK that looks good. Did it work alright?

EDIT: I just noticed that windows isn't in your grub2 menu. Boot into the new target and run "sudo update-grub" and see whether it picks it up.

---

### Post by barnesk9 on 2010-08-23
I have an issue with my migration to a partition. I used the script from [wubiGiude.org]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") and the shell script wubi-move-to-partition, 

everything seemed to go well except there was no entry for the new ubuntu partition in grub when the computer started, I have already uninstalled wubi via windows. I now have a ubuntu partition that I can't access can some please help me out?

---

### Post by bcbc on 2010-08-23
> **barnesk9 said:**
> I have an issue with my migration to a partition. I used the script from [wubiGiude.org]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?") and the shell script wubi-move-to-partition, 

everything seemed to go well except there was no entry for the new ubuntu partition in grub when the computer started, I have already uninstalled wubi via windows. I now have a ubuntu partition that I can't access can some please help me out?

That script doesn't work - I don't know why they haven't removed it yet. It assumes grub-legacy is installed, and uses commands that are deprecated. However, the copying of all your data should have been ok... so should be fixable.

Please create a new thread and edit your above post with a link to it, and include the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). I'll come and find it.

---

### Post by barnesk9 on 2010-08-24
> **bcbc said:**
> That script doesn't work - I don't know why they haven't removed it yet. It assumes grub-legacy is installed, and uses commands that are deprecated. However, the copying of all your data should have been ok... so should be fixable.

Please create a new thread and edit your above post with a link to it, and include the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). I'll come and find it.


Should I run it from a live CD?

---

### Post by bcbc on 2010-08-24
> **barnesk9 said:**
> Should I run it from a live CD?

Yes. Instructions are in the link I provided.

---

### Post by barnesk9 on 2010-08-24
I couldn't find the edit button but here are the results
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,335,439   224,333,392   7 HPFS/NTFS
/dev/sda2         224,347,725   303,226,874    78,879,150  83 Linux
/dev/sda3         303,226,875   312,576,704     9,349,830   5 Extended
/dev/sda5         303,226,938   312,576,704     9,349,767  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       d7069958-9bd6-41f6-80a0-244dbad7267b   ext4                                     
/dev/sda1        CA5AADC05AADAA21                       ntfs                                     
/dev/sda2        c1c77d74-af08-42b2-9c7b-968c416a370c   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        5a88ddb2-3b5b-4577-a9ff-3e1bcccc5fab   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="IBM Client for e-business Windows XP v3.01" /noexecute=alwaysoff /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

C:\wubildr.mbr = "Xubuntu"


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ca5aadc05aadaa21
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro single
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   6.6GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.32-21-generic
   6.5GB: boot/vmlinuz-2.6.32-21-generic
    .1GB: initrd.img
   6.5GB: vmlinuz

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=c1c77d74-af08-42b2-9c7b-968c416a370c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set c1c77d74-af08-42b2-9c7b-968c416a370c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0



UUID=    /    ext3    errors=remount-ro    0    1
UUID=    none    swap    sw    0    0

=================== sda2: Location of files loaded by Grub: ===================


 117.6GB: boot/grub/grub.cfg
 117.5GB: boot/initrd.img-2.6.32-21-generic
 117.6GB: boot/initrd.img-2.6.32-24-generic
 117.6GB: boot/vmlinuz-2.6.32-21-generic
 117.6GB: boot/vmlinuz-2.6.32-24-generic
 117.6GB: initrd.img
 117.5GB: initrd.img.old
 117.6GB: vmlinuz
 117.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  8e a6 27 0d db 97 a2 4c  7a fc ad d6 3f 99 df 93  |..'....Lz...?...|
00000010  e3 4f 36 82 b3 2f dc 3b  e8 7a c7 ab ff 64 fc 9b  |.O6../.;.z...d..|
00000020  29 3f fb 6b 03 d6 0f da  df 83 4c 79 ce f8 94 fe  |)?.k......Ly....|
00000030  d8 aa 1e d5 6f 0e 58 c8  39 60 b1 cc 01 65 02 68  |....o.X.9`...e.h|
00000040  77 b7 c1 f9 da 64 2e b0  30 cb 5c 98 63 2e cc 33  |w....d..0.\.c..3|
00000050  b9 32 33 51 e2 24 09 8f  f2 51 b4 84 50 52 27 12  |.23Q.$...Q..PR'.|
00000060  42 29 3f c1 dc d9 99 46  7c e3 3d 2e 3c da b7 be  |B)?....F|.=.<...|
00000070  8d 26 a5 ba e2 3e eb 77  f1 8f 18 ff 8f 1b c4 5f  |.&...>.w......._|
00000080  72 de 48 e9 a9 12 fe c2  f5 b4 6d 4c 3c 45 12 db  |r.H.......mL<E..|
00000090  d3 da 52 76 6e 06 1b ff  98 64 44 5a 79 b6 bb 77  |..Rvn....dDZy..w|
000000a0  e0 eb bb be 78 0b f9 0f  94 65 aa 6f eb bd 7e a1  |....x....e.o..~.|
000000b0  7f 3f 7f 1e c9 f4 4f 66  4a 9f b4 bf f2 a4 a7 f7  |.?....OfJ.......|
000000c0  a6 ce 50 06 f2 cf 57 f7  d3 fe 65 e9 f2 ef 1a 78  |..P...W...e....x|
000000d0  fd 9f fc 17 9d 44 f9 a1  5e c7 1b 64 7e 34 8d f9  |.....D..^..d~4..|
000000e0  ed b9 f6 a4 fd 79 c1 9e  41 fd 39 fe 21 ed 3f 48  |.....y..A.9.!.?H|
000000f0  7e f6 da dd 83 f4 17 5b  98 7e 52 5a 7a fb fc b7  |~......[.~RZz...|
00000100  52 aa b2 2e 65 3e 9c 6b  df 4f fe 11 d7 3a f3 e1  |R...e>.k.O...:..|
00000110  3c ab d2 cb 26 a0 06 22  1b fd a1 33 99 fd 72 1f  |<...&.."...3..r.|
00000120  e7 0a 91 e0 e5 d6 50 76  bd c5 12 a0 3c e2 04 28  |......Pv....<..(|
00000130  cd f6 6f c4 e1 cc ce f4  60 4c 55 9b 65 3c c5 d8  |..o.....`LU.e<..|
00000140  00 1b 26 c6 08 35 be 7b  2c 4e f1 bd 76 e4 75 e9  |..&..5.{,N..v.u.|
00000150  ae 8d 02 e7 2e 1a c7 4b  ef 60 6e 1f 7b 3e f3 7e  |.......K.`n.{>.~|
00000160  e6 7b 1f 70 fd ff 1a 35  fe 5e f7 e6 60 fb 9f 8c  |.{.p...5.^..`...|
00000170  6b 97 6c bf 4a 98 ed ec  f7 4f ae 3d 2c 66 92 61  |k.l.J....O.=,f.a|
00000180  d7 9c 70 be 6b 3f da 3e  98 7f 8e 49 f4 ff cc 6f  |..p.k?.>...I...o|
00000190  7d e9 c9 ef df 14 9b a9  fb 37 98 ad 27 76 0c ed  |}........7..'v..|
000001a0  29 af a7 b4 fc cc eb a1  5b de a7 fd 33 97 a7 fc  |).......[...3...|
000001b0  67 42 7b a6 fe 43 12 47  ca 7c 4e bc 16 af 00 fe  |gB{..C.G.|N.....|
000001c0  ff ff 82 fe ff ff 3f 00  00 00 87 aa 8e 00 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by bcbc on 2010-08-24
barnesk9, please edit your previous post and put [[SIZE="1"] [/SIZE]CODE] at the top, and [/CODE] at the bottom. It makes it more readable. Also I'd like you to create a new thread. You can add a link to it here or I will - so people can follow if they're interested, but it's not an issue with this particular howto and belongs in a different thread.

Thanks.

---

### Post by barnesk9 on 2010-08-24
I finally found the edit button and made the change

edit - here is the link for the new thread 

[http://www.ubuntuforums.org/showthread.php?p=9760624#post9760624](http://www.ubuntuforums.org/showthread.php?p=9760624#post9760624)

---

### Post by sighfi on 2010-08-24
Thanks, bcbc, your automated migration worked very well for me.
sighfi

---

### Post by bcbc on 2010-08-24
> **sighfi said:**
> Thanks, bcbc, your automated migration worked very well for me.
sighfi

Awesome :)

---

### Post by FlameReaper on 2010-08-28
Currently reading through this guide. Just wondering: is it possible for me to migrate a wubi installation just by having the root.disk from it?

---

### Post by bcbc on 2010-08-28
> **FlameReaper said:**
> Currently reading through this guide. Just wondering: is it possible for me to migrate a wubi installation just by having the root.disk from it?

Yes it's possible, with some minor modifications to the manual conversion instructions I supplied above. But I wouldn't try it if the wubi isn't booting, i.e. if it's the broken one you mentioned in the other thread.

---

### Post by zooster on 2010-08-30
Hello, I'm new in ubuntu, I installed ubuntu 10.04 through wubi and I'd like to move it to a real partition. I've attached the screenshot of gparted, where it's possible to see my partitions. My questions are:
1) is this script good for my configuration? Should I leave the unallocate space as it is now, also in case to create the swap partition?
2) is this script good considered that the "unknown" ntfs partition in sda4 is encrypted with bitlocker?
3) since I want the boot managed by windows bootloader I guess I have to use the command - no bootloader as stated in the first post... but I haven't understood well the part about the grub loader, why and when I should install it? Is not enough the windows bootloader?
Thanks.

---

### Post by myChucky on 2010-08-30
I has some questions about boot, anyway I has using Windows OS. Then I has install Ubuntu 9.10 before this. Then I uninstall it for install new Ubuntu 10.04. After that, in my boot menu has display two Ubuntu boot. But only first Ubuntu boot can load, the 2nd one cannot load. Why and how to remove it?

---

### Post by bcbc on 2010-08-30
> **zooster said:**
> Hello, I'm new in ubuntu, I installed ubuntu 10.04 through wubi and I'd like to move it to a real partition. I've attached the screenshot of gparted, where it's possible to see my partitions. My questions are:
1) is this script good for my configuration? Should I leave the unallocate space as it is now, also in case to create the swap partition?
2) is this script good considered that the "unknown" ntfs partition in sda4 is encrypted with bitlocker?
3) since I want the boot managed by windows bootloader I guess I have to use the command - no bootloader as stated in the first post... but I haven't understood well the part about the grub loader, why and when I should install it? Is not enough the windows bootloader?
Thanks.

1. You can only create 4 primary partitions, so that extra space will be unusable. It is better to create an extended partition in the space from /dev/sda4 and the extra, and then you can create multiple logical partitions within that.

2. I don't know enough about bitlocker to help you with that - never used it. I do know that if you run the script it will assume the partition is empty because it sees it as "unknown". (It will ask to format it, or if you supply -y/--assume-yes it will just format it. Normally if you try and migrate to a partition with existing data it won't let you).

3. As far as booting from windows, you can use [easybcd]("http://neosmart.net/wiki/display/EBCD/Ubuntu") on Vista/7 to boot ubuntu, but I haven't done this myself so can't advise. You can keep booting it from the wubi install grub menu until you figure out a replacement. I'd search the forums or create a separate thread for this.

---

### Post by bcbc on 2010-08-30
> **myChucky said:**
> I has some questions about boot, anyway I has using Windows OS. Then I has install Ubuntu 9.10 before this. Then I uninstall it for install new Ubuntu 10.04. After that, in my boot menu has display two Ubuntu boot. But only first Ubuntu boot can load, the 2nd one cannot load. Why and how to remove it?

It's best to create a separate thread in [this forum]("http://ubuntuforums.org/forumdisplay.php?f=326") - this thread is about migrating wubi installs to partition.

---

### Post by zooster on 2010-08-31
> **bcbc said:**
> 1. You can only create 4 primary partitions, so that extra space will be unusable. It is better to create an extended partition in the space from /dev/sda4 and the extra, and then you can create multiple logical partitions within that.

2. I don't know enough about bitlocker to help you with that - never used it. I do know that if you run the script it will assume the partition is empty because it sees it as "unknown". (It will ask to format it, or if you supply -y/--assume-yes it will just format it. Normally if you try and migrate to a partition with existing data it won't let you).

3. As far as booting from windows, you can use [easybcd]("http://neosmart.net/wiki/display/EBCD/Ubuntu") on Vista/7 to boot ubuntu, but I haven't done this myself so can't advise. You can keep booting it from the wubi install grub menu until you figure out a replacement. I'd search the forums or create a separate thread for this.

1) the swap partition has to be primary as well? If so I still need another one primary partition free (is it adviceable to create a swap partition in linux?)

2) If I got it right the unknown encrypted partition shouldn't be a problem as far as I do not add the command -y/--assume-yes to the script, it will proceed leaving it there untouched...

3) If I set -no bootloader option I will have windows bootloader (wubi one) right? So why would I need grub or easy bcd or others?

---

### Post by bcbc on 2010-08-31
> **zooster said:**
> 1) the swap partition has to be primary as well? If so I still need another one primary partition free (is it adviceable to create a swap partition in linux?)

2) If I got it right the unknown encrypted partition shouldn't be a problem as far as I do not add the command -y/--assume-yes to the script, it will proceed leaving it there untouched...

3) If I set -no bootloader option I will have windows bootloader (wubi one) right? So why would I need grub or easy bcd or others?

I think I misunderstood you. I thought you wanted to migrate to /dev/sda4. If that is not the case, it's not possible to migrate.

Because you already have 4 primary partitions (the maximum possible). You cannot create any more (that 39GB extra space is unusable right now). 


FYI, linux doesn't require primary partitions. You can use logical partitions for the swap or / root.
If you had created an extended partition, then you could have defined any number of logical partitions. 
But the only way to create an extended partition now is to delete a primary partition - obviously not a trivial task as you have to backup the data prior to partitioning and restore it afterwards.

You can't boot linux directly from the windows boot manager. The only reason you can boot wubi is that a version of grub4dos is installed with it.

---

### Post by zooster on 2010-08-31
> **bcbc said:**
> I think I misunderstood you. I thought you wanted to migrate to /dev/sda4. If that is not the case, it's not possible to migrate.

Because you already have 4 primary partitions (the maximum possible). You cannot create any more (that 39GB extra space is unusable right now). 


FYI, linux doesn't require primary partitions. You can use logical partitions for the swap or / root.
If you had created an extended partition, then you could have defined any number of logical partitions. 
But the only way to create an extended partition now is to delete a primary partition - obviously not a trivial task as you have to backup the data prior to partitioning and restore it afterwards.

You can't boot linux directly from the windows boot manager. The only reason you can boot wubi is that a version of grub4dos is installed with it.
Ok, then I have to create manually logical partition inside extended sda4? Before to run the script?

And about the bootloader if I set option - no bootloader I'll still have  wobi bootloader?

---

### Post by bcbc on 2010-08-31
> **zooster said:**
> Ok, then I have to create manually logical partition inside extended sda4? Before to run the script?

And about the bootloader if I set option - no bootloader I'll still have  wobi bootloader?

Yes - this script does not delete/create/resize partitions. It just migrates wubi installs to existing empty partitions.

Yes using --no-bootloader will not install the grub bootloader. It will leave the windows bootloader in place. You can use the wubi grub menu to boot the new install temporarily - but this is not a good long term solution because you have to boot the wubi install to update the grub menu e.g. every time you get a kernel update on your migrated install. 

If you are happy that the migration worked well, I recommend either installing the grub bootloader, or using an alternative method.

---

### Post by zooster on 2010-09-01
> **bcbc said:**
> Yes - this script does not delete/create/resize partitions. It just migrates wubi installs to existing empty partitions.

Yes using --no-bootloader will not install the grub bootloader. It will leave the windows bootloader in place. You can use the wubi grub menu to boot the new install temporarily - but this is not a good long term solution because you have to boot the wubi install to update the grub menu e.g. every time you get a kernel update on your migrated install. 

If you are happy that the migration worked well, I recommend either installing the grub bootloader, or using an alternative method.

But how can the old wubi bootloader point to new migrated partition? Does this script edit the wubi loader?

---

### Post by bcbc on 2010-09-01
> **zooster said:**
> But how can the old wubi bootloader point to new migrated partition? Does this script edit the wubi loader?
The wubi-move.sh script runs while you are booted in the wubi install. The last step updates the wubi grub menu, and adds the migrated install. 

But after that, the wubi grub menu will never update unless you boot into it and do it manually, or take extraordinary measures (loop mount the root.disk and edit it yourself).

---

### Post by zooster on 2010-09-01
Thank you man, but can you tell me pro and contra to use grub loader to boot w7 or ubuntu instead the windows one?

---

### Post by bcbc on 2010-09-01
> **zooster said:**
> Thank you man, but can you tell me pro and contra to use grub loader to boot w7 or ubuntu instead the windows one?

That is something you'll want the broader community to answer, so I suggest you create a new thread.

---

### Post by rreyes3713 on 2010-09-02
bcbc

I'm ready to do this "migration". In Windows, I shrunk the partition and then added a new partition (sdev5 according to Linux, its called "New Volume"). I'm going to run your shell script but just a few questions.

bash wubi-move.sh
Does this script unmounts and formats the new partition or do I have to do that before running this script? I only glanced at the script with so maybe the answers is within the script.

Then what happens to the Wubi in Windows? Does it still exist in Windows or do I have to remove it like removing an installed application?

Please excuse me if there's posts on this thread that already answered my questions.

---

### Post by bcbc on 2010-09-02
> **rreyes3713 said:**
> bcbc

I'm ready to do this "migration". In Windows, I shrunk the partition and then added a new partition (sdev5 according to Linux, its called "New Volume"). I'm going to run your shell script but just a few questions.

bash wubi-move.sh
Does this script unmounts and formats the new partition or do I have to do that before running this script? I only glanced at the script with so maybe the answers is within the script.

Then what happens to the Wubi in Windows? Does it still exist in Windows or do I have to remove it like removing an installed application?

Please excuse me if there's posts on this thread that already answered my questions.

The script won't attempt to migrate to a mounted partition - it will tell you to unmount it first. It will format it with the ext4 filesystem (and this also removes the label).

The script is designed to do nothing to the wubi install - except update the wubi grub menu so you can boot the migrated install. The wubi will continue to exist until you uninstall it: Add/Remove programs, and select Ubuntu. Note, once you uninstall it's gone including all your data etc. so make sure the migration worked, and consider keeping a back up of your root.disk.

Before you migrate consider whether you want a swap partition (required if you want to enable hibernation). It's easier to get the partitions right before migrating than afterwards.

---

### Post by rreyes3713 on 2010-09-02
Thanks bcbc
> **bcbc said:**
> ... Before you migrate consider whether you want a swap partition (required if you want to enable hibernation). It's easier to get the partitions right before migrating than afterwards.
I'm looking at your example for swap and you have
[quote=""] 
sudo bash wubi-move.sh /dev/sda5 /dev/sda6 [/quote]is dev/sda6 a virtual partition because I don't know if this exist when I check with my KDE Partition Manager.

What do you mean by "enable hibernation"? then you mentioned "swap must be as big as RAM to hibernate". I think my RAM is 4 Gig. Is this big enough.

Sorry if I'm dummy in terminology.:(

---

### Post by bcbc on 2010-09-02
> **rreyes3713 said:**
> Thanks bcbc

I'm looking at your example for swap and you have
is dev/sda6 a virtual partition because I don't know if this exist when I check with my KDE Partition Manager.

What do you mean by "enable hibernation"? then you mentioned "swap must be as big as RAM to hibernate". I think my RAM is 4 Gig. Is this big enough.

Sorry if I'm dummy in terminology.:(

You have to create the partitions - they are not virtual. If you don't want a swap partition, you don't require it. 

If you want to hibernate with 4GB ram you'll require at least a 4GB swap partition (some people say 1.5 x RAM i.e. 6GB, I'd guess 5GB is plenty). Hibernate means to save the current state but power off your computer - when you restart it will restore all the open programs, files etc. you were working on.

Note - hibernation is a bit of a mystery in Ubuntu - I've found no definitive rules on swap size, but I know with karmic I could hibernate with swap=ram, but with Lucid I needed a bigger swap.

---

### Post by rreyes3713 on 2010-09-02
thanks for your patient answering my questions bcbc. Now I have a better "feel and understanding" what I am doing (I think) [ lol ]

I'm gonna do it. :p

---

### Post by bcbc on 2010-09-02
> **rreyes3713 said:**
> thanks for your patient answering my questions bcbc. Now I have a better "feel and understanding" what I am doing (I think) [ lol ]

I'm gonna do it. :p

No problem... let me know how it goes :)

---

### Post by rreyes3713 on 2010-09-03
I think I was successful on the "migration". 

Thanks bcbc. ):P

---

### Post by bcbc on 2010-09-03
> **rreyes3713 said:**
> I think I was successful on the "migration". 

Thanks bcbc. ):P

You're welcome. 

If you're unsure whether the migration was successful or not, feel free to post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") (between [[SIZE="1"] [/SIZE]CODE][/CODE] tags) or let me know if you have any questions.

---

### Post by possible181 on 2010-09-05
Hey,
Thanks...it works!!

and one more thing...is it safe to run the wubi uninstaller from windows or shd i just delete the ubuntu folder from my ntfs partition?

---

### Post by bcbc on 2010-09-05
> **possible181 said:**
> Hey,
Thanks...it works!!

and one more thing...is it safe to run the wubi uninstaller from windows or shd i just delete the ubuntu folder from my ntfs partition?

Provided you've installed the grub bootloader, used it to boot the migrated install and verified that everything is OK, you can safely uninstall wubi by going to Add/Remove programs and removing "Ubuntu" - or by running the uninstaller from the *x*:\ubuntu\ directory. If you don't fully uninstall wubi, you'll always be prompted with the windows boot manager when booting windows.

If you want to be extra cautious, backup the root.disk file (outside of the ubuntu directory) before uninstalling.

---

### Post by zooster on 2010-09-05
Since the partition of windows7 (C: ) where wubi was installed was too small, I decided to reinstall wubi into another larger partition (E: ), keeping the old root.disk. Sadly when I replaced the root.disk ubuntu cannot boot, the loader says that there is no root.disk file, although it's there...
I guess there is some kind of checksum about the virtual disk toward the loader is poiting... So how can I have my old ubuntu installation back?? I still have the old root.disk.

---

### Post by bcbc on 2010-09-05
> **zooster said:**
> Since the partition of windows7 (C: ) where wubi was installed was too small, I decided to reinstall wubi into another larger partition (E: ), keeping the old root.disk. Sadly when I replaced the root.disk ubuntu cannot boot, the loader says that there is no root.disk file, although it's there...
I guess there is some kind of checksum about the virtual disk toward the loader is poiting... So how can I have my old ubuntu installation back?? I still have the old root.disk.

The grub menu in the old root.disk is referring to the C: partition. When you see the menu, just hit 'e' on the first entry and change the references. For this you'll need to know what partition the E: drive references. 

e.g. assuming your root.disk was installed on /dev/sda3 before, and if E: is now /dev/sda4, then change (hd0,3) to (hd0,4) and /dev/sda3 to /dev/sda4. Also delete the line that says 'search -floppy etc.' Then CTRL+X to boot.

Once booted run "sudo update-grub" to correct.

I'm a little confused how your decision to migrate ended up becoming a reinstall of wubi - but either way, this should work fine. Just don't get rid of that backup root.disk.

---

### Post by zooster on 2010-09-05
> **bcbc said:**
> The grub menu in the old root.disk is referring to the C: partition. When you see the menu, just hit 'e' on the first entry and change the references. For this you'll need to know what partition the E: drive references. 

e.g. assuming your root.disk was installed on /dev/sda3 before, and if E: is now /dev/sda4, then change (hd0,3) to (hd0,4) and /dev/sda3 to /dev/sda4. Also delete the line that says 'search -floppy etc.' Then CTRL+X to boot.

Once booted run "sudo update-grub" to correct.

I'm a little confused how your decision to migrate ended up becoming a reinstall of wubi - but either way, this should work fine. Just don't get rid of that backup root.disk.

I'm confused as well :)
Well I don't see any menu.lst, I searched windows but there is no such file...

---

### Post by bcbc on 2010-09-05
> **zooster said:**
> I'm confused as well :)
Well I don't see any menu.lst, I searched windows but there is no such file...
When you see the Windows boot manager, select Ubuntu, then you see the grub menu. There is no menu.lst anywhere anymore.

EDIT: I see you have another [thread]("http://ubuntuforums.org/showthread.php?t=1568655") for this - that's a good idea. Why don't you post any follow up there and I'll do the same.

---

### Post by zooster on 2010-09-05
> **bcbc said:**
> When you see the Windows boot manager, select Ubuntu, then you see the grub menu. There is no menu.lst anywhere anymore.

EDIT: I see you have another [thread]("http://ubuntuforums.org/showthread.php?t=1568655") for this - that's a good idea. Why don't you post any follow up there and I'll do the same.

Sorry, I posted there forgetting this thread, so I posted here...
Well I did what you said, and actually I could boot into old root.disk, I also did a grub update, but rebooting again in ubuntu it is still unbootable. And if I edit the grub hitting E key I see still there hd0,3 and sda3... it's like it didn't store the changes...

---

### Post by bcbc on 2010-09-05
> **zooster said:**
> Sorry, I posted there forgetting this thread, so I posted here...
Well I did what you said, and actually I could boot into old root.disk, I also did a grub update, but rebooting again in ubuntu it is still unbootable. And if I edit the grub hitting E key I see still there hd0,3 and sda3... it's like it didn't store the changes...

I've replied there.

---

### Post by zooster on 2010-09-05
me too

---

### Post by Trynthlas on 2010-09-15
bcbc - ran the automated migration script, which gave a green light on everything, but am having an issue getting back in to my linux installs via the wubi grub loader.

- Have wubi 10.04 installed on Windows 7 (upgraded from XP, which is actually installed on a different hard drive than 7 is)
- Used free space on the XP drive to create sda2 and sda3 (ext4 and swap, respectively) for the migrated install. I'm not sure why the wubi install sees that drive as sda instead of the drive which is actually used for /host under wubi (sdb where windows 7 is), but not sure if that is an actual issue.
- checked grub version under wubi (1.98 ), so good there.
- ran script with --no-bootloader option. All green, no errors, the grub update at the end added the new linux to the wubi grub list.
- rebooted to check the new install. Went from windows bootloader to Ubuntu, and then got the following:

```
Try (hd0,0): NTFS5: No wubildr
Try (hd0,1): EXT2: 
```

With a blinking cursor at the end of that, and stuck. I'm thinking it is a problem with the wubi grub loader, but ??? Any help is appreciated.

---

### Post by bcbc on 2010-09-15
@Trynthlas,
I would guess that when you installed Win7 it used the XP install as the boot partition for winxp/win7 (that's what Windows tends to do by default: it adds the newer version's boot files to the old version's partition). And so the choice to boot Ubuntu may actually be originating on /dev/sda1.
 
Perhaps copying wubildr from /dev/sdb1 (or the partition where wubi is actually installed) to the XP partition will fix this. I'm not sure why it would give up looking for wubildr just because it encountered an ext4 partition, but that part of wubi is largely undocumented so it's hard to be definitive.

If copying wubildr doesn't work, post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and this should give a clearer picture of what's going on.

---

### Post by Trynthlas on 2010-09-16
Alright, well after making a new Live CD to run the bootinfoscript I've got it here. The output is rather large!

First, I did copy the contents of C: (win 7 install)/ubuntu/winboot (which has wubildr, wubildr.cfg, and wubildr.mbr) to (win XP install)/ubuntu/winboot

Attempting to enter the Ubuntu option from the windows boot loader after that produced the same as my last post.

Here's the script output:
```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   134,317,439   134,317,377   7 HPFS/NTFS
/dev/sda2         134,318,080   606,710,789   472,392,710   7 HPFS/NTFS
/dev/sda3         606,710,790   625,137,344    18,426,555  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   586,070,015   586,067,968   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3bb085ab-8449-4fc2-a795-2e095e6c9b64   ext4                                     
/dev/sda1        6454A72954A6FD44                       ntfs       WinXP                         
/dev/sda2        11449c5b-701a-4ef2-bee0-9b657e523262   ext4                                     
/dev/sda3        a322bf0b-a998-4ac0-8629-979a02009b84   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D848DAB248DA8E9E                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	echo	'Loading Linux 2.6.32-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sda2 when wubi migrated
UUID=11449c5b-701a-4ef2-bee0-9b657e523262    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sda3 when wubi migrated
UUID=a322bf0b-a998-4ac0-8629-979a02009b84    none    swap    sw    0    0

=================== sda2: Location of files loaded by Grub: ===================


 159.2GB: boot/grub/grub.cfg
 193.4GB: boot/initrd.img-2.6.32-22-generic-pae
 193.4GB: boot/initrd.img-2.6.32-23-generic-pae
 193.5GB: boot/initrd.img-2.6.32-24-generic-pae
 193.5GB: boot/vmlinuz-2.6.32-22-generic-pae
 193.5GB: boot/vmlinuz-2.6.32-23-generic-pae
 193.5GB: boot/vmlinuz-2.6.32-24-generic-pae
 193.5GB: initrd.img
 193.4GB: initrd.img.old
 193.5GB: vmlinuz
 193.5GB: vmlinuz.old

======================== sdb1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic-pae" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d848dab248da8e9e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-24-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d848dab248da8e9e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-23-generic-pae" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d848dab248da8e9e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic-pae root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-23-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d848dab248da8e9e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic-pae root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-22-generic-pae" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d848dab248da8e9e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic-pae root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Ubuntu, Linux 2.6.32-22-generic-pae (recovery mode)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d848dab248da8e9e
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic-pae root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6454a72954a6fd44
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro single
	initrd /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro single
	initrd /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode) (on /dev/sda2)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 11449c5b-701a-4ef2-bee0-9b657e523262
	linux /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=11449c5b-701a-4ef2-bee0-9b657e523262 ro single
	initrd /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sdb1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sdb1/Wubi: Location of files loaded by Grub: =================


   8.9GB: boot/grub/grub.cfg
  14.2GB: boot/initrd.img-2.6.32-22-generic-pae
   6.1GB: boot/initrd.img-2.6.32-23-generic-pae
  14.3GB: boot/initrd.img-2.6.32-24-generic-pae
  13.9GB: boot/vmlinuz-2.6.32-22-generic-pae
   5.4GB: boot/vmlinuz-2.6.32-23-generic-pae
  14.2GB: boot/vmlinuz-2.6.32-24-generic-pae
  14.3GB: initrd.img
   6.1GB: initrd.img.old
  14.2GB: vmlinuz
   5.4GB: vmlinuz.old
```

I am confused why it seems to indicate that sda2 is still NTFS formatted, when the migrate script should have re-formatted it to ext4, correct? 
> sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab
vs
> Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   134,317,439   134,317,377   7 HPFS/NTFS
/dev/sda2         134,318,080   606,710,789   472,392,710   7 HPFS/NTFS

---

### Post by bcbc on 2010-09-16
I meant to copy \wubildr from the root directory on /dev/sdb1 to the root directory on /dev/sda1. 

If that still doesn't work, you could install grub2's bootloader instead (that's eventually what you'll have to do unless you're planning on booting your migrated ubuntu using something like easybcd.) It's not a real risk since you're just going to overwrite the MBR. Which you can easily replace again using the live CD.

To install grub2 bootloader from live CD:
```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

To reinstall a windows equivalent bootloader if you're not happy with grub2 (ignore warnings - they refer to different use of lilo):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

PS Yes it's puzzling that fdisk sees /dev/sda2 as ntfs and blkid sees it as ext4. Must be an anomaly in mkfs or fdisk. Everything else looks exactly the way I'd expect it.

---

### Post by Trynthlas on 2010-09-16
> **bcbc said:**
> I meant to copy \wubildr from the root directory on /dev/sdb1 to the root directory on /dev/sda1. 

PS Yes it's puzzling that fdisk sees /dev/sda2 as ntfs and blkid sees it as ext4. Must be an anomaly in mkfs or fdisk. Everything else looks exactly the way I'd expect it.

Oops. Well, that (copying the correct wubildr) worked and I was able to load into the new /dev/sda2 partition-installed ubuntu, from which I am posting! I'll have to work on the grub or lilo bootloader later, but seems like I'm in better shape. Thank you!

On the /dev/sda2 oddity, I attached a screenshot of what the Disk Utility program sees it as. I have a way to edit the partition type (and label), and there is also a checkbox for 'Bootable' - not sure what if any of these things I want to mess with?

---

### Post by bcbc on 2010-09-16
> **Trynthlas said:**
> Oops. Well, that (copying the correct wubildr) worked and I was able to load into the new /dev/sda2 partition-installed ubuntu, from which I am posting! I'll have to work on the grub or lilo bootloader later, but seems like I'm in better shape. Thank you!

On the /dev/sda2 oddity, I attached a screenshot of what the Disk Utility program sees it as. I have a way to edit the partition type (and label), and there is also a checkbox for 'Bootable' - not sure what if any of these things I want to mess with?
Cool! Glad that worked.

Regarding the partition type, now's the time to mess with it before you diverge from the existing wubi install. But messing with partitions has some risks so take appropriate backup measures. There are a number of tools that can change partition types.

---

### Post by Praetor77 on 2010-09-26
So how should I proceed if I have grub-legacy? Is there any way to upgrade grub to grub2 before proceeding with scripts?

Thanks in advance....

---

### Post by bcbc on 2010-09-26
> **Praetor77 said:**
> So how should I proceed if I have grub-legacy? Is there any way to upgrade grub to grub2 before proceeding with scripts?

Thanks in advance....
I haven't had the time to figure this out. I've run a few tests but haven't achieved a consistent result so I don't want to publish it yet. And then I got busy doing other stuff.

Don't try upgrading to grub2. That will just break your wubi. There are some other differences between the older wubis that use grub-legacy e.g. the fstab, boot files, file system type.

I'll try and spend some more time on this...

---

### Post by Praetor77 on 2010-09-26
I´m actually reading up on all the problems when upgrading to grub2, but it seems a patched wubildr found in comment #90 here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/+index?comments=all)

Fixes the boot problem when upgrading grub-legacy to grub2. Still, will not trry  it yet, though I might read up some more and go ahead and do it, since I really need to move my wubi to dedicated partition soon, actually VERY soon.

Cheers!

---

### Post by bcbc on 2010-09-27
> **Praetor77 said:**
> So how should I proceed if I have grub-legacy? Is there any way to upgrade grub to grub2 before proceeding with scripts?

Thanks in advance....
Try this. _The following is only for wubi installs with grub-legacy_.

I used it to migrate a Jaunty (9.04) wubi install.  It's a vanilla install (with all updates applied) and so I make no  guarantees - not tested on 9.10/10.04. Also, since the commands are manual you have to be very  careful. Take backups before hand, especially the wubi files (the  \ubuntu directory).

Also, note, I do not try and use grub-legacy on the migrated install as a  matter of preference - I remove and replace it with grub2 (grub-pc),  and this behaves differently depending on the version. With Jaunty it's  version 1.96 and it's very different to the version on 10.04 (I'll  describe the differences you might see).

Following example migrates a wubi install to an external drive  (/dev/sdb) - root is /dev/sdb10 and swap is /dev/sdb7 - change as  appropriate _before_ cut-and-pasting  (as you can easily paste a newline and then the command executes immediately).
```

sudo -i
mkfs.ext3 **/dev/sdb10**

mkdir /tmp/wubimove
mount **/dev/sdb10** /tmp/wubimove
rsync  -av --exclude=/host --exclude=/mnt/* --exclude=/home/*/.gvfs   --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/*  --exclude=/sys/*  / /tmp/wubimove
      
mkswap **/dev/sdb7**
echo "RESUME=UUID=$(blkid -o value -s UUID **/dev/sdb7**)" > /tmp/wubimove/etc/initramfs-tools/conf.d/resume

sed -i 's:/.*[\.]disk .*::' /tmp/wubimove/etc/fstab    
sed -i 's:/.*/disks/boot .*::' /tmp/wubimove/etc/fstab
echo "UUID=$(blkid -o value -s UUID **/dev/sdb10**)    /    ext3    errors=remount-ro    0    1" >> /tmp/wubimove/etc/fstab
echo "UUID=$(blkid -o value -s UUID **/dev/sdb7**)    none    swap    sw    0    0" >> /tmp/wubimove/etc/fstab
      
mkdir /tmp/wubimove/host
cp /etc/resolv.conf /tmp/wubimove/etc
for i in dev proc sys dev/pts host; do mount --bind /$i /tmp/wubimove/$i; done
chroot /tmp/wubimove
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get -y remove lupin-support
apt-get -y purge grub grub-common
mv /boot/grub /boot/grubold

#... continues below

```This part installs grub2 - if you are on 10.04 it will  automatically generate grub.cfg and prompt you where to install the  bootloader. If you are on 9.04 and probably 9.10 you have to do it  yourself (lines in italics).  
```

apt-get -y install grub-pc grub-common
[I]update-grub
[/I][I]grub-install **/dev/sdb**
[/I]
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in host dev/pts dev proc sys; do umount /tmp/wubimove/$i; done
rmdir /tmp/wubimove/host
umount /dev/sdb10

update-grub
exit
exit

```

---

### Post by Praetor77 on 2010-09-27
It kinda worked! I got a grub rescue console, booted up with a Live USB, did:

sudo mount /dev/sda6 / mnt (I moved my wubi installation to an ext4 sda6 partition)
sudo grub-install --root-directory=/mnt/ /dev/sda

reboot and done! will post again after sudo update-grub and reboot...

---

### Post by bcbc on 2010-09-27
> **Praetor77 said:**
> It kinda worked! I got a grub rescue console, booted up with a Live USB, did:

sudo mount /dev/sda6 / mnt (I moved my wubi installation to an ext4 sda6 partition)
sudo grub-install --root-directory=/mnt/ /dev/sda

reboot and done! will post again after sudo update-grub and reboot...

OK... if you have problems, you just need to reinstall the windows bootloader and you should be back where you started. It's strange you got grub rescue - that means you installed grub but it couldn't find the Ubuntu partition when you booted! Unless you did this by accident from the wubi install - not in chroot - then it's unusual.

PS. The reason I used ext3 is that wubi installs prior to 9.10 were on ext3.

---

### Post by Praetor77 on 2010-09-27
Thanks for everything, worked perfectly. I had a 9.10 installation, but had grub-legacy for some reason, I suppose I upgraded from 9.04, don't really remember.

Thanks again!

---

### Post by bcbc on 2010-09-27
> **Praetor77 said:**
> Thanks for everything, worked perfectly. I had a 9.10 installation, but had grub-legacy for some reason, I suppose I upgraded from 9.04, don't really remember.

Thanks again!

OK cool. Glad it worked out!

---

### Post by elrics_fate on 2010-10-10
Would like to pop in to say thank you very much for the script. Worked great and with a little bit of work on the Windows 7 side I managed to transition smoothly. Keep up the awesome work.

---

### Post by bcbc on 2010-10-11
> **elrics_fate said:**
> Would like to pop in to say thank you very much for the script. Worked great and with a little bit of work on the Windows 7 side I managed to transition smoothly. Keep up the awesome work.

Great :) I appreciate the feedback... enjoy!

---

### Post by rneuls on 2010-10-13
Worked like a charm. I used your script

---

### Post by bcbc on 2010-10-14
> **rneuls said:**
> Worked like a charm. I used your script

Great :)

Yeah I expect most people would use the script. The manual commands are good if you want to know what the script is doing without having to wade through all the bumph (additional error checks, decision making, variable substitution) that makes it hard to read.

---

### Post by pariksheetsharma on 2010-10-21
And it worked like a charm. There is a problem though this page is not indexed properly on google. It should come as the first post on internet. 

Let me know how I can help with you that.

---

### Post by bcbc on 2010-10-22
> **pariksheetsharma said:**
> And it worked like a charm. There is a problem though this page is not indexed properly on google. It should come as the first post on internet. 

Let me know how I can help with you that.

You just give lots of money to google and it's sorted :)

---

### Post by Ragnar! on 2010-10-30
As soon as I quit skipping the first step (changing to root..lol), this worked flawlessly for me! Thank you so much.\\:D/

---

### Post by bcbc on 2010-10-31
> **Ragnar! said:**
> As soon as I quit skipping the first step (changing to root..lol), this worked flawlessly for me! Thank you so much.\\:D/

You're welcome :)
Yeah - being root works better ;)

---

### Post by ettostra on 2010-11-05
Hi everybody, I'm new to the forum and also to ubuntu.
On my pc I have win xp and wubi, no partitions (right?), so, can I use your script?

Thankyou very much!

---

### Post by bcbc on 2010-11-05
> **ettostra said:**
> Hi everybody, I'm new to the forum and also to ubuntu.
On my pc I have win xp and wubi, no partitions (right?), so, can I use your script?

Thankyou very much!
You need to create the target partition(s) before running the script, which isn't covered in this howto as there are already a lot of existing resources dedicated to partitioning.

If you would like specific help on this for your particular setup, you can create a new thread and you'll get lots of advice from forum members.

Good luck!

PS here're are a couple of links. I can't vouch for everything in them, but they have some good info.
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning](https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by ettostra on 2010-11-07
Good, so I will do that partition..!

Thankyou...!

---

### Post by rreyes3713 on 2010-11-10
ettostra, you may have to use a 3rd party partition app for XP unless you know how to partition hard drives at the "bios" level. Vista and Window 7 have the utility 'Disk Management". 

I recommend you do a defrag before adding a new partition. Then again, depending on the partition app, maybe its not needed. I don't know.

Identify the new partition. If you never had a partition it is probably dev5. I don't know.

Depend on the speed of your computer, be patient. I was not patient because I thought nothing was happening at the command line so I press 'enter' and message popped up "This may take a while ..."

I had no hang ups (thanks bcbc! for this script)

Its great to have your computer to dual booth. My girlfriend caught me with some border line explicit (but not that obscene) images on my Window side. So I moved these images to my Linux side which has two users. Besides password locked, she doesn't like to meddle in Linux too complicated even though Ubuntu is fairly "Window" like. ... even in Window, remove a couple of tool bars off the menu of MS Word or Excel, my girlfriend is already lost like a fish out of water.

Good luck ettostra. Cool thing about Linux on its own partition, you could browse the Window partition but not visa-versa. Maybe you can, but I can't on my computer.

---

### Post by dougadew on 2010-11-25
hey complete noob at all of this. i have four mb left and need to partition, obviously. i have downloaded the      [wubi-move.sh]("http://ubuntuforums.org/attachment.php?attachmentid=162615&d=1278440721") file but donot know what to do with it. when i open the terminal and try going through the non-manual steps it comes up that it cannot find the bash file? Please help

---

### Post by bcbc on 2010-11-25
> **dougadew said:**
> hey complete noob at all of this. i have four mb left and need to partition, obviously. i have downloaded the      [wubi-move.sh]("http://ubuntuforums.org/attachment.php?attachmentid=162615&d=1278440721") file but donot know what to do with it. when i open the terminal and try going through the non-manual steps it comes up that it cannot find the bash file? Please help

Likely you downloaded it to your Downloads folder.
So you'd either change to that directory:
```
cd ~/Downloads
``` and then run it from there or just run ```
sudo bash ~/Downloads/wubi-move.sh /dev/sdXY /dev/sdXZ
``` 
where /dev/sdXY is the prepared target partition and /dev/sdXZ the prepared swap partition (optional)

Let me know if you have any other questions.

---

### Post by Tridun on 2010-11-27
Hello All , I speak not a good English .
I have a question : 
For the last party ( Grub2 Installation ) , Do I overwrite the MBR of Windows, because I do not want to overwrite it, booting Ubuntu from NTLDR.

:popcorn::KS

---

### Post by sinha1612 on 2010-11-27
This was amazingly helpful and painless. I went through the manual steps and migrated my wubi installations on two machines to partition. A big thank you!
Also I read through the entire thread and was particularly impressed by the way you reply to each and every query, even the ones from newbies. It's people like you who keep the open-source ecosystem going. You deserve a big round of digital applause!! =D>

---

### Post by bcbc on 2010-11-27
> **Tridun said:**
> Hello All , I speak not a good English .
I have a question : 
For the last party ( Grub2 Installation ) , Do I overwrite the MBR of Windows, because I do not want to overwrite it, booting Ubuntu from NTLDR.

:popcorn::KS

If you are running the script, and you answer "Y" to installing the grub bootloader, then it will overwrite the Windows bootloader in the MBR.
If you are running manual instructions, then the command 'grub-install' will also overwrite the Windows bootloader.

How do you intend to boot if you're not using grub? Windows doesn't natively give you the ability to boot Ubuntu, and using the Wubi install is not recommended.

---

### Post by bcbc on 2010-11-27
> **sinha1612 said:**
> This was amazingly helpful and painless. I went through the manual steps and migrated my wubi installations on two machines to partition. A big thank you!
Also I read through the entire thread and was particularly impressed by the way you reply to each and every query, even the ones from newbies. It's people like you who keep the open-source ecosystem going. You deserve a big round of digital applause!! =D>

Thanks for the compliment :)

I think it's important for Wubi users to have a decent exit strategy without having to completely reinstall.

---

### Post by Tridun on 2010-11-28
```
**Ajout d’une entrée de menu pour Ubuntu dans l’amorceur de Windows XP**

     Une fois l'installation d'Ubuntu complétée, choisissez de rester dans le système du live CD. Nous allons maintenant copier le secteur d'amorçage de Grub :  Ouvrez un terminal et tapez : 
 sudo dd if=/dev/sdxY of=~/grub.bs bs=512 count=1   où sdxY doit être remplacé par la partition sur laquelle vous avez installé Ubuntu (exemple sda2). Le fichier grub.bs apparait maintenant dans le dossier utilisateur. Pour un live CD ubuntu, c'est sous "Ubuntu". 
   Possibilité 1 : Copiez le fichier grub.bs sur une clé USB et redémarrez. 

```

Sorry for the french response ^^

I dare not overwrite for fear of being unable to recover Windows, I do not Live-CD Ubuntu or Windows Restore CD

---

### Post by bcbc on 2010-11-28
> **Tridun said:**
> ```
**Ajout d’une entrée de menu pour Ubuntu dans l’amorceur de Windows XP**

     Une fois l'installation d'Ubuntu complétée, choisissez de rester dans le système du live CD. Nous allons maintenant copier le secteur d'amorçage de Grub :  Ouvrez un terminal et tapez : 
 sudo dd if=/dev/sdxY of=~/grub.bs bs=512 count=1   où sdxY doit être remplacé par la partition sur laquelle vous avez installé Ubuntu (exemple sda2). Le fichier grub.bs apparait maintenant dans le dossier utilisateur. Pour un live CD ubuntu, c'est sous "Ubuntu". 
   Possibilité 1 : Copiez le fichier grub.bs sur une clé USB et redémarrez. 

```

Sorry for the french response ^^

I dare not overwrite for fear of being unable to recover Windows, I do not Live-CD Ubuntu or Windows Restore CD
OK so you're using something like easyBCD. That's fine not to install grub to the drive MBR, but I believe that you need to install grub to the bootsector on the target partition instead (this is what that dd command is copying). This cannot be done without forcing it (an option on the grub-install command). I'll assume you have instructions to do this (but it's not currently supported by the script). If you use the manual migration it's quite easily done just by modifying the target from /dev/sda to /dev/sda5 and supplying the force option (change partition as appropriate).

---

### Post by motrengaw on 2010-12-04
Your wubi-move.sh performed flawlessly for me and my Vista-encumbered Acer 4420 laptop.   Thank you so much for your clear, concise documentation of your clear, concise code.  Deeply appreciated and very impressive.

I have a follow-on question/concern that may apply to only my box, and the Vista side of that to boot (oops. sorry).

On startup, the new grub menu posts the list of linux updates and a 'Windows Boot Loader' and 'Windows Recovery' option.   When I select the Windows Boot Loader, Vista begins to boot, then switches to a 'Recovery Mode' with an Acer marque posting and a Windows login prompt.  I can select my existing administrator account and enter my password.  I'm then taken to a Windows recovery splash.  The only tempting option there is 'Startup Repair' which promises to automatically fix 'problems that are preventing Windows from starting normally.'  I'm leery of this for obvious reasons.  I haven't tried the 'Windows Recovery' option for the same reason.

The Grub menu listed the 'Windows Boot Loader' on sda1.  The Windows Recovery splash gives its location as 'C:\Acer'  These entries correspond to the labels for the Vista install partition prior to the wubi-move event.  Is it possible that the 'Startup Repair' option will confine its efforts to the sda1 partition and leave the newly Grub-ed MBR on sda alone?  I assume this would allow me to go ahead and boot my Vista install as before but preserve the true dual boot environment your script gave me.

Any further light you can shed would be much appreciated.   Thanks again for your time and effort on this polished tool.

---

### Post by bcbc on 2010-12-04
> **motrengaw said:**
> Your wubi-move.sh performed flawlessly for me and my Vista-encumbered Acer 4420 laptop.   Thank you so much for your clear, concise documentation of your clear, concise code.  Deeply appreciated and very impressive.
...
Thanks for the compliments. 

Regarding the Windows entries in Grub... Grub doesn't always identify the Windows partitions well. Probably because many of the same boot files exist on the recovery partition. The easiest way to figure out which is 'normal' windows, is by identifying the physical partition that has the boot flag set. Then always select the grub entry that mentions that partition, regardless of desciption.
e.g. on my one computer I have two entries:
menuentry "Windows NT/2000/XP (**on /dev/sda1**)" { 
and 
menuentry "Microsoft Windows XP Professional (**on /dev/sda2**)" { 

The one with the boot flag set is /dev/sda2. I've never tried the first one, and don't recommend playing around with it unless you know what you are doing.

PS you can edit these if they bug you - *drs305* wrote a good guide on this. [Grub2 title tweaks thread]("http://ubuntuforums.org/showthread.php?t=1287602")

---

### Post by motrengaw on 2010-12-04
Of course.  Stumped me as to how to see the boot flags until I remembered the column in the 'parted' output---I'm still a relative newbie to Linux as I'm sure you could tell.

It was in fact the sda2 partition with the scary 'Windows Recovery' label that was flagged and sure enough held my intact Vista boot.  Roaring along with the top down and the wind in my hair now on both systems (Ubuntu being the Corvette and Vista being the Edsel).

Thanks again, so much!  Best of the Season to you and yours!!

---

### Post by bcbc on 2010-12-05
> **motrengaw said:**
> Of course.  Stumped me as to how to see the boot flags until I remembered the column in the 'parted' output---I'm still a relative newbie to Linux as I'm sure you could tell.

It was in fact the sda2 partition with the scary 'Windows Recovery' label that was flagged and sure enough held my intact Vista boot.  Roaring along with the top down and the wind in my hair now on both systems (Ubuntu being the Corvette and Vista being the Edsel).

Thanks again, so much!  Best of the Season to you and yours!!

I had to look up 'Edsel' :)

Anyway... glad you got it all sorted.  Seasons greetings to you too!

---

### Post by dwachtel on 2010-12-15
Thanks for the script and the help you give to the community. The very clear comments in the script were very helpful in refreshing my ancient (ca. 1982 ) shell scripting knowledge.
 
 I made one change to the script before running it. I changed ext4 to ext3 as ext3 is purportedly more reliable and I don't really need huge files or faster file operations. I also had an additional virtual disk defined (in WUBI) and the script copied the contents over to the “native” file system with no problem! 

 The first boot picked up the new Linux installation but not the Windows XP one. After doing a “grub-update” then a reboot, XP was found and everything works properly.
 
 The “native” install seems to be quite a bit faster than the WUBI installation. If anyone is hesitant to make the change they should do it. It's quit painless and the results are well worth it. Plus it's a lot easier to change the size of real partitions using a gparted live CD than it is to enlarge a version 10+ WUBI installation or add a new virtual drive.  
 
 Unfortunately, I didn't have to look up 'Edsel' :rolleyes:.

Thanks again
 Dave

---

### Post by bcbc on 2010-12-15
@dwachtel,

You're welcome! Re. the filesystem, I haven't heard of any issues with ext4 - it has been used since 9.10 with Wubi installs. I know that the script that adds virtual disks uses ext3 (as does lvpm), but this is probably because they haven't been updated since the 8.04 release. I don't think it makes a lot of difference either way. 
I'm glad you found the script clear and were able to modify it as needed.

---

### Post by Angelbrand on 2010-12-19
> **bcbc said:**
> 
This example assumes the new install will be on [COLOR="Red"]/dev/sda5[/COLOR] and that there will be a swap on [COLOR="Blue"]/dev/sda6[/COLOR]. If there is no swap, just ignore lines containing [COLOR="Blue"]/dev/sda6[/COLOR]. If there is a swap partition it must be of type 'swap'. Change the device names as appropriate.



i have no partition called [COLOR="Red"]/dev/sda5[/COLOR]

here is a screen shot from gparted.

---

### Post by Angelbrand on 2010-12-19
> **Angelbrand said:**
> i have no partition called [COLOR="Red"]/dev/sda5[/COLOR]

here is a screen shot from gparted.

ignore above as i worked that issue out but the code isnt working on my sytem it keeps comming up operation denied.

---

### Post by bcbc on 2010-12-19
> **Angelbrand said:**
> ignore above as i worked that issue out but the code isnt working on my sytem it keeps comming up operation denied.

what exactly are you doing and what is the full error message?

---

### Post by Angelbrand on 2010-12-19
i think i must have restarted terminal or something after entering pass word and it was because i hadnt entered sudo -i before entering code from step two. sorry blonde moments today. 
il make sure im logged in next time. sorry!

---

### Post by bcbc on 2010-12-19
> **Angelbrand said:**
> i think i must have restarted terminal or something after entering pass word and it was because i hadnt entered sudo -i before entering code from step two. sorry blonde moments today. 
il make sure im logged in next time. sorry!

That' ok :) Just be careful with those commands... if you're not sure I advise you to use the script. Good luck.

---

### Post by tweezak on 2010-12-22
Great guide and handy script. Very helpful. Thank you very much.

Now...that I've done it all and have rebooted, how do I know that I'm in the "parition" linux and didn't boot back into WUBI? What's an easy way to tell? The boot process looks the same as before.

Thanks again!

---

### Post by bcbc on 2010-12-22
> **tweezak said:**
> Great guide and handy script. Very helpful. Thank you very much.

Now...that I've done it all and have rebooted, how do I know that I'm in the "parition" linux and didn't boot back into WUBI? What's an easy way to tell? The boot process looks the same as before.

Thanks again!

You're very welcome :)

The boot process should be different (unless you chose to not install grub). Instead of the Windows boot manager, you'll see the grub menu first.

You can tell what you have booted in a number of ways... go to a terminal and see what root is mounted on: 
```
mount
#or 
mount | grep ' / '
```

It should say something like:
> /dev/sda5 on / type ext4 (rw,errors=remount-ro)
You're still on Wubi if it says > /dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)

You can also check the fstab:
```
cat /etc/fstab
```
You're on Wubi if it says:
> /host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1

If you skipped the grub install, you have to boot your new install by choosing Ubuntu from the Windows boot manager, and then looking near the bottom of the grub menu where it should say something like "Ubuntu xxxxx (on /dev/sda5)"
If this is the case, don't uninstall Wubi without first installing the grub bootloader from your migrated install.

---

### Post by tweezak on 2010-12-22
> **bcbc said:**
> You're very welcome :)

The boot process should be different (unless you chose to not install grub). Instead of the Windows boot manager, you'll see the grub menu first.

You can tell what you have booted in a number of ways... go to a terminal and see what root is mounted on: 
```
mount
#or 
mount | grep ' / '
```It should say something like:


That told me what I needed to know. I'm now on /dev/sda2

You da man!

umm...or da woman. In either case, thanks!!

---

### Post by Telos3K on 2010-12-23
Hi,

I've followed the above to migrate from wubi, creating sda6 and sda 7 (as I already had an sda5 and didn't want to accidentally erase data).

when rebooting, I get the grub prompt.

I enter

grub> root (hd0,6)

then

grub> kernel /boot/vmlinuz-2.6.32-24-generic

and get 
error: unknown command 'kernel'.

what am I doing wrong?

---

### Post by bcbc on 2010-12-23
> **Telos3K said:**
> Hi,

I've followed the above to migrate from wubi, creating sda6 and sda 7 (as I already had an sda5 and didn't want to accidentally erase data).

when rebooting, I get the grub prompt.

I enter

grub> root (hd0,6)

then

grub> kernel /boot/vmlinuz-2.6.32-24-generic

and get 
error: unknown command 'kernel'.

what am I doing wrong?
So first off - did you use the script or run it manually?

Assuming you successfully migrated to /dev/sda6, and you have a grub prompt (not a grub rescue) then the following should boot it:
```
insmod ext2
set root=(hd0,6)
linux /vmlinuz root=/dev/sda6 ro 
initrd /initrd.img
boot
```

PS /vmlinuz links to the latest installed kernel, or you can use /boot/vmlin (and hit the Tab key to see available kernels)

Once you boot into your new install, reinstall the grub bootloader:
```
sudo grub-install /dev/sda
```

If you're not sure, boot an Ubuntu CD in 'Live CD' mode and run [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post back the results.

---

### Post by Telos3K on 2010-12-23
I ran it manually.
Since my last post I ran windows recovery (since one problem I had was that Win7 stopped running when I had wubi set up). So, looking in windows disk management, Isee that my partitions are still set up (a Recovery, a winOS (C: drive), DATA (D:, and with all the data files still intact) and three additional partitions, which I assume are the sda6, 7 and 8 I set up for the migration. In theory, Ubuntu is now on sda6, but of course I can't see anything from windows -- all the space is given as "free."
 
So how do I get back over to sda6? Can I just reboot the machine and run the above command, or do I have to reboot from a LiveCD, or....? (This is a case where I'd rather ask first.)
 
Thanks!

---

### Post by bcbc on 2010-12-23
> **Telos3K said:**
> I ran it manually.
Since my last post I ran windows recovery (since one problem I had was that Win7 stopped running when I had wubi set up). So, looking in windows disk management, Isee that my partitions are still set up (a Recovery, a winOS (C: drive), DATA (D:, and with all the data files still intact) and three additional partitions, which I assume are the sda6, 7 and 8 I set up for the migration. In theory, Ubuntu is now on sda6, but of course I can't see anything from windows -- all the space is given as "free."
 
So how do I get back over to sda6? Can I just reboot the machine and run the above command, or do I have to reboot from a LiveCD, or....? (This is a case where I'd rather ask first.)
 
Thanks!
If you boot to a grub prompt you can just enter those commands I showed. 
To be honest, the simplest way for me to help you is if you post the results of the bootinfoscript.

If it turns out that there was a problem with the migration, your wubi install should remain untouched and reinstalling the windows bootloader (or lilo from an ubuntu cd) will get that booting again. But let's get the bootinfoscript first so we can see.

---

### Post by Telos3K on 2010-12-23
The results from bootinfoscript.  FWIW, accessing sda6 from the LiveCD seems to indicate that all the wubi files are in there.....
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,716,279    30,714,232  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,716,280   274,904,279   244,188,000   7 HPFS/NTFS
/dev/sda3         274,904,280   976,768,064   701,863,785   f W95 Ext d (LBA)
/dev/sda5         274,904,343   378,781,695   103,877,353   7 HPFS/NTFS
/dev/sda6         378,783,744   583,583,743   204,800,000  83 Linux
/dev/sda7         583,585,792   788,828,159   205,242,368  83 Linux
/dev/sda8         788,830,208   892,948,479   104,118,272  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        BCB68218B681D376                       ntfs       OS                            
/dev/sda5        B19401CA6A583703                       ntfs       DATA                          
/dev/sda6        b610e25d-4073-487b-abc3-db17a16dea91   ext2       /dev/sda6                     
/dev/sda7        89a1b68b-20dd-4897-b826-92ba8adeb48d   ext2       /dev/sda7                     
/dev/sda8        10746ca2-a741-45e3-8a23-814b27967f4e   ext2       /dev/sda/8                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=b610e25d-4073-487b-abc3-db17a16dea91 ro acpi_backlight=vendor  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=b610e25d-4073-487b-abc3-db17a16dea91 ro single acpi_backlight=vendor
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b610e25d-4073-487b-abc3-db17a16dea91 ro acpi_backlight=vendor  quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=b610e25d-4073-487b-abc3-db17a16dea91 ro single acpi_backlight=vendor
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b610e25d-4073-487b-abc3-db17a16dea91 ro acpi_backlight=vendor  quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=b610e25d-4073-487b-abc3-db17a16dea91 ro single acpi_backlight=vendor
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b610e25d-4073-487b-abc3-db17a16dea91
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c98-ac5d
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set cc624cd7624cc842
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/dev/sda5    /media/DATA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0


UUID=b610e25d-4073-487b-abc3-db17a16dea91    /    ext4    errors=remount-ro    0    1
UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d    none    swap    sw    0    0

=================== sda6: Location of files loaded by Grub: ===================


 232.6GB: boot/grub/grub.cfg
 232.5GB: boot/initrd.img-2.6.32-24-generic
 232.5GB: boot/initrd.img-2.6.32-25-generic
 232.4GB: boot/initrd.img-2.6.32-26-generic
 232.5GB: boot/vmlinuz-2.6.32-24-generic
 232.5GB: boot/vmlinuz-2.6.32-25-generic
 232.5GB: boot/vmlinuz-2.6.32-26-generic
 232.4GB: initrd.img
 232.5GB: initrd.img.old
 232.5GB: vmlinuz
 232.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 d8 b4 62 10  |........?.....b.|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 e9 0a 31 06 00 fe  |......?.....1...|
000001d0  ff ff 05 fe ff ff 28 0b  31 06 00 08 35 0c 00 00  |......(.1...5...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by bcbc on 2010-12-23
> **Telos3K said:**
> The results from bootinfoscript:
...


You need to edit your fstab. 
```
sudo mount /dev/sda6 /mnt
gksu gedit /mnt/etc/fstab

```
Comment out the following lines by adding a '#':
```
#/dev/sda2    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
#/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
#/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0
#UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d    none    swap    sw    0    0
```
The first one is the old /host from Windows (which doesn't require an entry in fstab anyway - not sure why that's there). The next two are the root.disk and swap.disk from Wubi. 
The fourth is your /dev/sda7 marked as swap but in fact it's an ext2 partition so won't work as swap. You'll have to go into gparted later and change it to type "swap" and then run "mkswap" on it before adding it back to /etc/fstab (with the updated UUID as it changes when you run mkswap)

After you've finished editing it, then you need to install grub's bootloader to the MBR:
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot. Should work.

Is there any reason you went with "ext2" partitions instead of "ext4"?  I'm not aware of any problems with this, but haven't tried it myself.

PS did you totally recover Windows, because your wubi install is gone? Do you have a backup of your old wubi files?

---

### Post by Telos3K on 2010-12-23
I had backed up my data files but not my wubi files before I ran into this problem.
I chose ext2 rather than ext4 because I didn't know better
When I run 

sudo mount /dev/sda6 /mnt
gksu gedit /etc/fstab
in the terminal off of the LiveCD (as I know no other way of accessing Ubuntu at this point), the text I get in gedit is:

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```So clearly I'm doing something wrong......
And now, in the Places list, sda6 is missing -- did mounting it remove it from this list?

---

### Post by bcbc on 2010-12-24
Oh sorry about that: should be 
```
gsku gedit /mnt/etc/fstab
```

---

### Post by Telos3K on 2010-12-24
made the changed and saved the file, and ran the grub install.

What do I need to know before I reboot?  Do I reboot from the LiveCD, or do I disconnect that and just reboot from nthe machine? Will I be getting the grub prompt?  If so, do I then run the code that you suggested a while back, or is that no longer necessary?

---

### Post by bcbc on 2010-12-24
> **Telos3K said:**
> made the changed and saved the file, and ran the grub install.

What do I need to know before I reboot?  Do I reboot from the LiveCD, or do I disconnect that and just reboot from nthe machine? Will I be getting the grub prompt?  If so, do I then run the code that you suggested a while back, or is that no longer necessary?

Tell it to restart, it will tell you to remove the CD, boot it up (while crossing your fingers). If you end up at a grub prompt... you can try the manual boot. If that fails too, boot from the Live CD and post back here.

---

### Post by Telos3K on 2010-12-24
Rebooted and looks like everything is working great -- Many thanks!

To complete the process, I'd like to optimize the partitioning.
First, in GParted, can I change the file system type (for example ext2 to ext4 for sda6 and 8, and change to linux-swap for sda7), without damaging the data?


As to the sizing, 

sda2, the windows OS drive, is sized at 116 GB and using 19.  If I'm not going to be using adding to it much, I assume I can drop it to say, 30 GB?

sda6, I assume this is the Ubuntu OS?  It is sized at 100GB and using 11.  So I can drop that to, say 30 as well?

sda7 is now 100GB -- what should it be?

sda8 -- do I even need this, or did I make one too many partitions?

sda5 -- this is where all my data is.  I assume I should make this as large as possible, after making the above reductions

Many thanks for your guidance.

---

### Post by bcbc on 2010-12-24
> **Telos3K said:**
> Rebooted and looks like everything is working great -- Many thanks!

To complete the process, I'd like to optimize the partitioning.
First, in GParted, can I change the file system type (for example ext2 to ext4 for sda6 and 8, and change to linux-swap for sda7), without damaging the data?


As to the sizing, 

sda2, the windows OS drive, is sized at 116 GB and using 19.  If I'm not going to be using adding to it much, I assume I can drop it to say, 30 GB?

sda6, I assume this is the Ubuntu OS?  It is sized at 100GB and using 11.  So I can drop that to, say 30 as well?

sda7 is now 100GB -- what should it be?

sda8 -- do I even need this, or did I make one too many partitions?

sda5 -- this is where all my data is.  I assume I should make this as large as possible, after making the above reductions

Many thanks for your guidance.

OK... Great that it's working.

Now... slow down and back up all your data before messing with your partitions.  

1. Don't change ext2 to ext4 using gparted. There probably is a way but that's not it. I'd just copy your install to an ext4 partition or backup, modify, restore. I suggest you create a new thread for that. (Or just leave it as ext2 for now).
2. Your swap should be approx the size of your RAM + about 1GB to be safe - and that's only if you want to hibernate. 

Other than that - I can't really advise what you should do with your partitions. Just note that modifying the partitions will likely require updates to grub.

I'm glad the migration (finally) worked, despite the customizations. :)

---

### Post by Telos3K on 2010-12-24
OK, I'll research and check the appropriate threads for the best way to back up and then  optimize the partitons.
 
Thanks for all your help!

---

### Post by chauncy22 on 2010-12-29
Hello, I am new to this and put a lot of work into customizing my Ubuntu 10.4. will I loose my wubi if this doesn't work. Thank you for the time you put into this and also for sharing. I have a dual boot set up...Windows 7 and Vista. Wubi  is installed in the vista partition.

---

### Post by bcbc on 2010-12-29
> **chauncy22 said:**
> Hello, I am new to this and put a lot of work into customizing my Ubuntu 10.4. will I loose my wubi if this doesn't work. Thank you for the time you put into this and also for sharing. I have a dual boot set up...Windows 7 and Vista. Wubi  is installed in the vista partition.
Hi, the migration is designed to leave the wubi install untouched. 

The only thing it does is to run "update-grub" in order to add the migrated install to the wubi grub menu. 

The idea is that you check the migrated install and only when you're happy, you can remove the wubi install. (But of course you can keep and continue to use both if you choose to.)

---

### Post by bilkay on 2011-01-01
I migrated a couple of weeks ago, using this guide, after running wubi for several months. I don't see ANY difference, other than one less boot menu. Why go to all the trouble?

---

### Post by bcbc on 2011-01-01
> **bilkay said:**
> I migrated a couple of weeks ago, using this guide, after running wubi for several months. I don't see ANY difference, other than one less boot menu. Why go to all the trouble?

People have different reasons for migrating. Maybe they're running out of space on Ubuntu... they want to be able to hibernate ... more stability... ...

Without a migration procedure most people end up reinstalling which can be a pain if you've spent a long time tweaking things and can't remember everything you've done.

Why did you migrate?

---

### Post by hopper333 on 2011-01-02
Another satisfied customer, thanks a lot for this bcbc. :KS

Converted a quite involved wubi 10.10 amd64 installation with custom kernel and restricted hardware drivers on a Dell Inspiron 14R laptop (not the most Linux-friendly device initially) from Windows 7 loop drive to dual-boot on an ext4 file system with zero problems.

Excellent, this should be made an official part of wubi somehow.

---

### Post by bcbc on 2011-01-02
> **hopper333 said:**
> Another satisfied customer, thanks a lot for this bcbc. :KS

Converted a quite involved wubi 10.10 amd64 installation with custom kernel and restricted hardware drivers on a Dell Inspiron 14R laptop (not the most Linux-friendly device initially) from Windows 7 loop drive to dual-boot on an ext4 file system with zero problems.

Excellent, this should be made an official part of wubi somehow.

Great! You're welcome.

I think there was always supposed to be an official migration tool - the vision was for one that could partition as well. I think that's all on the back burner as the chief maintainer for Wubi doesn't seem to be involved anymore, and Canonical hasn't assigned anyone to replace him.

---

### Post by bilkay on 2011-01-02
> **bcbc said:**
> People have different reasons for migrating. Maybe they're running out of space on Ubuntu... they want to be able to hibernate ... more stability... ...

Without a migration procedure most people end up reinstalling which can be a pain if you've spent a long time tweaking things and can't remember everything you've done.

Why did you migrate?
a. Time to spare (golf courses closed - snow)
b. Hibernation

I can't seem to get hibernation working. I migrated with a swap file rather than a partition. My /etc/initramfs-tools/conf.d/resume looks like this:
```
RESUME=UUID=95b5d034-f19b-4f3d-b509-f7eec40748a5 resume_offset=4063232
```The UUID is /dev/sda4 (my root). The resume_offset is the number from:

```
$ sudo filefrag -v /swap/swap1.file
Filesystem type is: ef53
File size of /swap/swap1.file is 3174400000 (775000 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0  4063232           32768 
   1   32768  4098048  4095999  32768 
 ...
```[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946) (** HOWTO: Use swapfile instead of partition and hibernate  **) gives instructions for updating grub, but they don't seem relevant to the current version of grub. But I don't see how that would prevent it from going INTO hibernation.

---

### Post by bcbc on 2011-01-03
> **bilkay said:**
> a. Time to spare (golf courses closed - snow)
b. Hibernation

I can't seem to get hibernation working. I migrated with a swap file rather than a partition. My /etc/initramfs-tools/conf.d/resume looks like this:
```
RESUME=UUID=95b5d034-f19b-4f3d-b509-f7eec40748a5 resume_offset=4063232
```The UUID is /dev/sda4 (my root). The resume_offset is the number from:

```
$ sudo filefrag -v /swap/swap1.file
Filesystem type is: ef53
File size of /swap/swap1.file is 3174400000 (775000 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0  4063232           32768 
   1   32768  4098048  4095999  32768 
 ...
```[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946) (** HOWTO: Use swapfile instead of partition and hibernate  **) gives instructions for updating grub, but they don't seem relevant to the current version of grub. But I don't see how that would prevent it from going INTO hibernation.
Yeah I remember seeing this sometime back. I tried it without success. Maybe if you post on that thread they can help you.

If you can create a new partition (e.g. your ubuntu is on a logical), just use gparted to resize and then create a swap file. It might be easier. Take suitable backups before resizing - but it seems to work well - at least resizing from the end of the partition.

---

### Post by bilkay on 2011-01-03
> **bcbc said:**
> Yeah I remember seeing this sometime back. I tried it without success. Maybe if you post on that thread they can help you.

If you can create a new partition (e.g. your ubuntu is on a logical), just use gparted to resize and then create a swap file. It might be easier. Take suitable backups before resizing - but it seems to work well - at least resizing from the end of the partition.
Thanks for your help.

I really don't want to go the swap partition route - there are so many advantages to using swap files, and gparted already trashed one partition for me.

I just have one question about your HOWTO: That older thread I referenced makes grub changes so that the pre-hibernate condition is restored, rather than going through the boot process. You don't seem to be doing that. How is that so?

---

### Post by bcbc on 2011-01-03
> **bilkay said:**
> Thanks for your help.

I really don't want to go the swap partition route - there are so many advantages to using swap files, and gparted already trashed one partition for me.

I just have one question about your HOWTO: That older thread I referenced makes grub changes so that the pre-hibernate condition is restored, rather than going through the boot process. You don't seem to be doing that. How is that so?The swap uuid is placed in /etc/initramfs-tools/conf.d/resume:
> echo "RESUME=UUID=$(blkid -o value -s UUID /dev/sda6)" > /tmp/wubimove/etc/initramfs-tools/conf.d/resume
You normally have to run "update-initramfs -u" after modifying this, but that happens as a result of uninstalling lupin-support anyway, so I don't bother repeating it.

---

### Post by Telos3K on 2011-01-04
I'm back because even though I haven't resolved how to best partition my disk, I at least want to have my swap partition working so I can hibernate. As I described above, I set it up in gParted as /dev/sda7, with the file system as linux-swap.

My /etc/initramfs-tools/conf.d/resume file reads:

```
RESUME=UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d
```

what changes do I have to make? Anything else I have to do?

Many thanks!

---

### Post by hreinhardk on 2011-01-04
I'm am old chap but new in Linux. Wubi 9.10 on xp for 6 month. Want to move my wubi to partition but  grub legacy 0.97)
Went through your informative forum. Am I right your commands on #92 sep 27 10  will do for my migration? (including the lines in Italic) (I changed your  partition no. in mine.)
I'd like to ask first to avoid ending up in a mess (although you always find a way out. Great. )

My wubi is on a separate (logical) partition (sda6, 13.2 GB, 11.5 GB used). Sda7  formated ext4 (13.1 GB)the new ubuntu partition,  sda8 swap-format 1.5 GB (1GB RAM) (somewhere I read I'd need sufficient unallocated space for swap. Is that necessary?)

Wubi back up in xp. done. works.

Something more to do before I start?

One last question: your second line in #92 is  "mkfs.ext3 /dev/sdb10" Does it mean the main partition is formatted in ext3. Is that necessary? You recommend throughout the forum to use ext4.

---

### Post by bcbc on 2011-01-04
> **Telos3K said:**
> I'm back because even though I haven't resolved how to best partition my disk, I at least want to have my swap partition working so I can hibernate. As I described above, I set it up in gParted as /dev/sda7, with the file system as linux-swap.

My /etc/initramfs-tools/conf.d/resume file reads:

```
RESUME=UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d
```

what changes do I have to make? Anything else I have to do?

Many thanks!
Confirm the UUID, fstab and resume settings match, then update initial ram disk:
```
$ sudo blkid /dev/sda7
/dev/sda7: UUID="**89a1b68b-20dd-4897-b826-92ba8adeb48d**" TYPE="swap"

$ cat /etc/fstab | grep swap
UUID=**89a1b68b-20dd-4897-b826-92ba8adeb48d** none            swap    sw              0       0

$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=**89a1b68b-20dd-4897-b826-92ba8adeb48d**

# if that's all good
$ sudo update-initramfs -u
```

---

### Post by bcbc on 2011-01-04
> **hreinhardk said:**
> I'm am old chap but new in Linux. Wubi 9.10 on xp for 6 month. Want to move my wubi to partition but  grub legacy 0.97)
Went through your informative forum. Am I right your commands on #92 sep 27 10  will do for my migration? (including the lines in Italic) (I changed your  partition no. in mine.)
I'd like to ask first to avoid ending up in a mess (although you always find a way out. Great. )

My wubi is on a separate (logical) partition (sda6, 13.2 GB, 11.5 GB used). Sda7  formated ext4 (13.1 GB)the new ubuntu partition,  sda8 swap-format 1.5 GB (1GB RAM) (somewhere I read I'd need sufficient unallocated space for swap. Is that necessary?)

Wubi back up in xp. done. works.

Something more to do before I start?

One last question: your second line in #92 is  "mkfs.ext3 /dev/sdb10" Does it mean the main partition is formatted in ext3. Is that necessary? You recommend throughout the forum to use ext4.

Yes, those instructions should work fine - and you've taken all the necessary precautions. But you're not leaving a lot of room to grow with the new partition, since you've already used 11.5GB.

For Karmic you should be fine with 1.5GB ram (I could hibernate with swap size = ram on karmic). I found Lucid requires more swap to hibernate. I'm not sure what you mean by requiring sufficient unallocated space for swap - as long as you have that swap partition that should be all you need.

Regarding the file system, I don't think it makes a big difference in terms of the migration. I tend to stick with the file system on the originating system, but there's no real reason for that. So, you should be fine to use ext4 - just update everywhere that I reference ext3 in the commands. Some people still think ext4 isn't as reliable as ext3 - I don't have an opinion on this.

Good luck and feedback is always welcome - I have the feeling that wubi + grub legacy is very uncommon these days, but if I hear different I might just add it to the script or provide a separate one.

---

### Post by hreinhardk on 2011-01-05
Thanks for your quick reply.
Rg. the space, the old wubi partition (sda6) is just in front of the new ubuntu, after migration. 
As soon as the new ubuntu works well I want to delete the old wubi and expand the new partition in this space. Should be possible to move the new ubuntu installation, shouldn't it?

Rg the format. Instead of changing your commands I just formated back  to ext3

---

### Post by bcbc on 2011-01-05
> **hreinhardk said:**
> Thanks for your quick reply.
Rg. the space, the old wubi partition (sda6) is just in front of the new ubuntu, after migration. 
As soon as the new ubuntu works well I want to delete the old wubi and expand the new partition in this space. Should be possible to move the new ubuntu installation, shouldn't it?

Rg the format. Instead of changing your commands I just formated back  to ext3
I haven't had a problem resizing partitions in gparted, but I haven't done it a lot either - mostly shortened or lengthened from the right side - and made sure I had a backup. I think it should work either way but probably takes a lot longer doing what you want to do. Maybe get some opinions from other people on the forum on the best way to do this.

---

### Post by hreinhardk on 2011-01-05
migration work very well. It was a great experience after having looked for a working migration tool quite long time.  Thanks a lot.
Ubuntu now boots much faster. 

The  boot menue seems to be strange (or perhaps only unfamiliar) 
This issue is frequentlydiscussed in this forum. I'll go through that again to work out what's on.  If I get lost, I'll ask you again for help.

---

### Post by rsearjeant on 2011-01-05
Just wanted to add my own note of thanks for this excellent script.  It worked perfectly. My Acer laptop is now dual-booting Win7 / Xubuntu 10.10.  Thanks for creating and maintaining this superb utility.

Because of bad experiences in the past (not with your script, I should add!) I chickened-out and went for the --no-bootloader option, but I'd like to tidy things up by installing the grub2 bootloader manually and getting rid of the Wubi install. 

I'm still a bit worried about screwing-up access to Windows. If I run "grub-install /dev/sda" from the newly-moved Xubuntu, can I assume Windows will be added to the Grub menu and all will be well when I restart? (I'm 75% confident ... just need a little reassurance!)

Roger

---

### Post by bcbc on 2011-01-05
> **hreinhardk said:**
> migration work very well. It was a great experience after having looked for a working migration tool quite long time.  Thanks a lot.
Ubuntu now boots much faster. 

The  boot menue seems to be strange (or perhaps only unfamiliar) 
This issue is frequentlydiscussed in this forum. I'll go through that again to work out what's on.  If I get lost, I'll ask you again for help.

Great! And thanks for the feedback too. 

There are some who feel strongly about Grub2 and remain - or move back to - Grub. It tends to work fine for me (except on Wubi installs of course).

---

### Post by bcbc on 2011-01-05
> **rsearjeant said:**
> Just wanted to add my own note of thanks for this excellent script.  It worked perfectly. My Acer laptop is now dual-booting Win7 / Xubuntu 10.10.  Thanks for creating and maintaining this superb utility.

Because of bad experiences in the past (not with your script, I should add!) I chickened-out and went for the --no-bootloader option, but I'd like to tidy things up by installing the grub2 bootloader manually and getting rid of the Wubi install. 

I'm still a bit worried about screwing-up access to Windows. If I run "grub-install /dev/sda" from the newly-moved Xubuntu, can I assume Windows will be added to the Grub menu and all will be well when I restart? (I'm 75% confident ... just need a little reassurance!)

Roger
It should be there already... try the following:
Boot your computer, select Ubuntu from the Windows boot manager, when you see the Wubi grub menu hit 'c'. This drops you to a grub prompt. 
Now load up your migrated Ubuntu's grub menu (assuming /dev/sda5):
```
configfile (hd0,5)/boot/grub/grub.cfg
```

This is exactly what you will see when you install the grub bootloader. You can then test out the Windows option and the rest before installing grub.

If you're still nervous then backup your MBR before installing the grub bootloader. But reinstalling the windows bootloader is very simple - I just use lilo even though I have the windows disks because I can install it from Ubuntu, and I've never had an issue using it.

---

### Post by hreinhardk on 2011-01-05
back again to bcbc.
I've got the same boot menue problem as post 18.
Top Ubuntu (boots the migrated  partition ubuntu)
bottom line ubuntu sda1, boots to (the old wellknown) windows boot menue from there i can access wubi as well as xp. 

the solution for post 18, sudo update-grubI did, but it didn't change the situation. 
In a similar (I think) problem, post 86, you suggested to change  MBR with lilo (write to sda I think). 

sudo apt-get install lilo
sudo lilo -M/dev/sda MBR   

would these commands fit for me too? 

You too suggested to go back to grub instead of grub2. I don't know how.

My next step would be to upgrade to 10.04 and then to uninstall wubi. 
Is it necessary to fix the "cosmetic" with the boot menue first or will they be fixed by upgrading and uninstall anyhow?

many questions sorry.

---

### Post by bcbc on 2011-01-05
> **hreinhardk said:**
> back again to bcbc.
I've got the same boot menue problem as post 18.
Top Ubuntu (boots the migrated  partition ubuntu)
bottom line ubuntu sda1, boots to (the old wellknown) windows boot menue from there i can access wubi as well as xp. 

the solution for post 18, sudo update-grubI did, but it didn't change the situation. 
In a similar (I think) problem, post 86, you suggested to change  MBR with lilo (write to sda I think). 

sudo apt-get install lilo
sudo lilo -M/dev/sda MBR   

would these commands fit for me too? 

You too suggested to go back to grub instead of grub2. I don't know how.

My next step would be to upgrade to 10.04 and then to uninstall wubi. 
Is it necessary to fix the "cosmetic" with the boot menue first or will they be fixed by upgrading and uninstall anyhow?

many questions sorry.
Actually I believe that's caused by having Ubuntu as the default OS in the Windows Boot Manager - boot.ini. Not confirmed, but maybe you can confirm it by booting Windows and changing the default OS back to Windows (in the Windows Startup & Recovery settings, under the advanced tab of System Properties).
After that boot back into the migrated Ubuntu and run "sudo update-grub"

Don't reinstall lilo. I think it's counterproductive at this point unless you intend to keep Wubi.

UPDATE: Yeah just confirmed that. I don't remember when I clued in to that, but obviously some time after that post #18.

---

### Post by hreinhardk on 2011-01-05
Thanks it worked fine. 
I then tried to uninstall wubi, but it was not on the add/remove list of xp. 
I read somewhere there's a command to uninstall wubi from ubuntu new. I don't remember.
Otherwise I just delete the partition wubi was on with gpart and clean windows directory for wubi and partition installation do not depend on each other, do they?

---

### Post by bcbc on 2011-01-05
> **hreinhardk said:**
> Thanks it worked fine. 
I then tried to uninstall wubi, but it was not on the add/remove list of xp. 
I read somewhere there's a command to uninstall wubi from ubuntu new. I don't remember.
Otherwise I just delete the partition wubi was on with gpart and clean windows directory for wubi and partition installation do not depend on each other, do they?

They're independent - you can delete it [manually]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi%3F") if there's no \ubuntu\uninstall-wubi.exe (in add/remove it's listed as Ubuntu not Wubi).

---

### Post by hreinhardk on 2011-01-05
Thanks. I found the uninstall ubuntu-wubiexe in Ubuntu directory. It didn t work.
In add remove it was not listed. I once installed with live ubuntu on stick.
 I tried in xp to delete the partition where only wubi was installed. But there was some problem with the file system.   Anyway. I can deal with this kind of problems. 
Thanks for your help performing the migration.

I couldn't deal with the problem. Pls see the next post several hours later...

---

### Post by hreinhardk on 2011-01-06
at the end I messed up the whole migration. Sorry.

I deleted the wubi partition (sda6) and expanded the migrated ubuntu partition (sda7) into the free space. (swap was sda8).
(I did that by using a live CD...) 
As a result the ubuntu partition became sda6, swap sda7 and when I booted  I ended up on the <rescue grub> prompt. 

I looked around in the forums but found no good solution. 
with xp repairconsole  "fixmbr" I could reset mbr to boot back into xp. And then? How to fix (reinstall) the grubloader for the ubuntu installation on sda6?

---

### Post by bcbc on 2011-01-06
> **hreinhardk said:**
> at the end I messed up the whole migration. Sorry.

I deleted the wubi partition (sda6) and expanded the migrated ubuntu partition (sda7) into the free space. (swap was sda8 ).
(I did that by using a live CD...) 
As a result the ubuntu partition became sda6, swap sda7 and when I booted  I ended up on the <rescue grub> prompt. 

I looked around in the forums but found no good solution. 
with xp repairconsole  "fixmbr" I could reset mbr to boot back into xp. And then? How to fix (reinstall) the grubloader for the ubuntu installation on sda6?
Boot from a live CD, go to terminal:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

More info:
when it boots, it'll present you with the grub menu, hit 'e', change references of (hd0,7) to (hd0,6), delete the line beginning "search --floppy...", change /dev/sda7 to /dev/sda6, hit CTRL+X to boot.
Then run "sudo update-grub" when booted.

---

### Post by hreinhardk on 2011-01-06
oh, what a wonderful morning...
while getting up I saw your reply tried immediately and... 
it worked!!
there was no line to change /dev/sda7 to /dev/sda6,
it nevertheless bootet into ubuntu.
after sudo update-grub no boot problems anymore. 

Are there tutorials to learn about the "inside" of ubuntu and the terminal commands to influence it?

your help was very generous for I knew my problem was a bit off topic of this forum. Thanks.

---

### Post by bcbc on 2011-01-06
> **hreinhardk said:**
> oh, what a wonderful morning...
while getting up I saw your reply tried immediately and... 
it worked!!
there was no line to change /dev/sda7 to /dev/sda6,
it nevertheless bootet into ubuntu.
after sudo update-grub no boot problems anymore. 

Are there tutorials to learn about the "inside" of ubuntu and the terminal commands to influence it?

your help was very generous for I knew my problem was a bit off topic of this forum. Thanks.

OK Great. I guess Grub used the UUID instead of /dev/sda7 - I wasn't entirely sure whether the UUID would be changed when Gparted did it's resize. So I guess the only thing required was to update the MBR.

Anyway - bit of a workout - but you got it working in the end!

Regarding learning Ubuntu... not really sure. You can learn a lot from ubuntuforums.org. And google. I don't have a 'Linux Bible' if that's what you're looking for :)

---

### Post by hreinhardk on 2011-01-06
So many believers and no bible. I like this kind of churches.
bye.

---

### Post by r00t4rd3d on 2011-01-07
Im curious , what are the benefits of doing this ? I did the wubi install from win7 and everything seems fine. Ive read that disk performance could be affected by going the wubi route but for me atleast that doesnt seem to be an issue.

---

### Post by bcbc on 2011-01-07
> **r00t4rd3d said:**
> Im curious , what are the benefits of doing this ? I did the wubi install from win7 and everything seems fine. Ive read that disk performance could be affected by going the wubi route but for me atleast that doesnt seem to be an issue.

Reliability - having everything on a single file is a risk. This can be mitigated by backups. Also lately Grub2 updates have been breaking Wubi booting, which can be a pain for new users to handle.

Support - Wubi is probably used by a minority of Ubuntu users and they tend to be newer - so you won't get as good support. Also developers probably consider Wubi issues lower priority.

I think migration was always intended to be part of Wubi. But there's no reason to rush into it. If you want to keep using Wubi, just make sure you have data backups - and back up the entire root.disk before major updates.

---

### Post by dom96 on 2011-01-09
Worked perfectly, no problems at all(At least so far). Awesome job bcbc :D Thank you!

---

### Post by chauncy22 on 2011-01-09
I forgot the last step in Installing the boot loader. I used the automated script.
Ubuntu shows in the boot menu but when I click on it I get this :

Error: unknown command 'Load Front'
Error: file not found

---

### Post by bcbc on 2011-01-09
> **dom96 said:**
> Worked perfectly, no problems at all(At least so far). Awesome job bcbc :D Thank you!

Glad to hear! Enjoy.

> **chauncy22 said:**
> I forgot the last step in Installing the boot loader. I used the automated script.
Ubuntu shows in the boot menu but when I click on it I get this :

Error: unknown command 'Load Front'
Error: file not found

So you have the Wubi booting issue - and since you didn't install grub2's bootloader... you can't boot either now. But you have a live CD so I'd just use it to install grub2 (as I described in that other thread) - that will get the migrated install booting. 

If you would prefer to fix the Wubi problem, see the [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #2, Solution#1 and then the Permanent Fix after you've booted it.

---

### Post by chauncy22 on 2011-01-09
OK,  I was able to boot into my ubuntu with advise from the other thread.
Thank you bcbc very much. Now...how can I get my windows boot loader back because I can only see my Win 7 and not my Vista. Please advise.

Thank you very much again for the quick response.

---

### Post by chauncy22 on 2011-01-09
Sorry, I will try the advise from the link you provided and let you know how it turned out. You are awesome man!!!:P

---

### Post by bcbc on 2011-01-09
> **chauncy22 said:**
> OK,  I was able to boot into my ubuntu with advise from the other thread.
Thank you bcbc very much. Now...how can I get my windows boot loader back because I can only see my Win 7 and not my Vista. Please advise.

Thank you very much again for the quick response.

You're welcome! Did you sort out booting Vista and 7? When you install a new windows OS over an old one, it combines the boot files... so I suspect that you just need to select the "Windows 7 (loader) (on /dev/sda1)" entry and then you should get the Windows boot manager with your two windows entries and the old Wubi Ubuntu.

---

### Post by chauncy22 on 2011-01-09
Hi bcbc,

Thought I would not push mu luck and leave the grub boot loader as is. Thank you very much!! I can finally get rid of my Vista partition...it was holding my Ubuntu hostage:P:P:P!!

---

### Post by bcbc on 2011-01-09
> **chauncy22 said:**
> Hi bcbc,

Thought I would not push mu luck and leave the grub boot loader as is. Thank you very much!! I can finally get rid of my Vista partition...it was holding my Ubuntu hostage:P:P:P!!

You should probably hold your horses... until you figure this out. If you get rid of Vista you'll probably be removing your win 7 boot files. As I explained before, windows combines the boot files of newer and older installs - and it always places them on the older install. So delete it, and your new one won't boot.

---

### Post by wilee-nilee on 2011-01-09
> **chauncy22 said:**
> Hi bcbc,

Thought I would not push mu luck and leave the grub boot loader as is. Thank you very much!! I can finally get rid of my Vista partition...it was holding my Ubuntu hostage:P:P:P!!

Is sda2 the W7 partition? hey wubi master bcbc.;)

---

### Post by bcbc on 2011-01-09
> **wilee-nilee said:**
> Is sda2 the W7 partition? hey wubi master bcbc.;)

Hey wilee-nilee ;) Thanks for stopping by and helping out.

---

### Post by wilee-nilee on 2011-01-10
> **bcbc said:**
> Hey wilee-nilee ;) Thanks for stopping by and helping out.

no problem we can get the  /bootmgr /Boot/BCD into the W7 so it boots on it own.

It just needs the boot flag on the W7 partition and the W7 recovery booted to the command terminal and 
bootrec.exe /fixboot

---

### Post by OptimusS on 2011-01-12
Perfect! 10x!
(btw i didn't know you can chroot in script :))

---

### Post by Telos3K on 2011-01-12
bcbc,

You wrote:

> Confirm the UUID, fstab and resume settings match, then update initial ram disk:

the last two lines of my fstab file read:
```

UUID=b610e25d-4073-487b-abc3-db17a16dea91    /    ext4    errors=remount-ro    0    1
#UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d    none    swap    sw    0    0
```

so I should first uncomment the last line and then update the initial ram disk?

When you say ```
Confirm the UUID, fstab and resume settings match
```

do you mean the UUID setting in the fstab and resume files? Or is there a third file I need to check as well?

(Sorry for the delay in res[ponding to your help -- I somehow missed the email alert...)

---

### Post by bcbc on 2011-01-12
> **OptimusS said:**
> Perfect! 10x!
(btw i didn't know you can chroot in script :))
Great!

> **Telos3K said:**
> bcbc,

You wrote:



the last two lines of my fstab file read:
```

UUID=b610e25d-4073-487b-abc3-db17a16dea91    /    ext4    errors=remount-ro    0    1
#UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d    none    swap    sw    0    0
```

so I should first uncomment the last line and then update the initial ram disk?

When you say ```
Confirm the UUID, fstab and resume settings match
```

do you mean the UUID setting in the fstab and resume files? Or is there a third file I need to check as well?

(Sorry for the delay in res[ponding to your help -- I somehow missed the email alert...)

Yes... I meant you should confirm what the UUID of the swap was and then make sure the entries in fstab and resume matched it. So if that's the correct UUID then uncomment it, then check it right away:
```
sudo swapon -a
free

#and then
sudo update-initramfs -u
```

And then you might as well hibernate and see how that goes. If you have any issues hibernating, check the syslog for errors with the prefix PM:
```
grep 'PM:' /var/log/syslog
```

---

### Post by Telos3K on 2011-01-12
OK, I uncommended that line and saved it.  Then I ran the code to update ram, and got:

```

bwbloch@ubuntu:~$ $ sudo blkid /dev/sda7
$: command not found
bwbloch@ubuntu:~$ /dev/sda7: UUID="89a1b68b-20dd-4897-b826-92ba8adeb48d" TYPE="swap"
bash: /dev/sda7:: No such file or directory
bwbloch@ubuntu:~$ 
bwbloch@ubuntu:~$ $ cat /etc/fstab | grep swap
$: command not found
bwbloch@ubuntu:~$ UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d none            swap    sw              0       0
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
none: command not found
bwbloch@ubuntu:~$ 
bwbloch@ubuntu:~$ $ cat /etc/initramfs-tools/conf.d/resume
$: command not found
bwbloch@ubuntu:~$ RESUME=UUID=89a1b68b-20dd-4897-b826-92ba8adeb48d

```

what am I doing wrong?

---

### Post by bcbc on 2011-01-12
> **Telos3K said:**
> OK, I uncommended that line and saved it.  Then I ran the code to update ram, and got:
Run the following:
```

sudo blkid /dev/sda7
```
This will output something like:
> /dev/sda7: UUID="89a1b68b-20dd-4897-b826-92ba8adeb48d" TYPE="swap"

Then note the UUID, confirm that it is type "swap" and then ensure that the UUID matches that in the fstab and resume file by running the following two commands:
```

cat /etc/fstab | grep swap
cat /etc/initramfs-tools/conf.d/resume
```

If the UUID you see is different, correct it. If they all match the uuid of your swap, then run:
```

sudo update-initramfs -u
```

---

### Post by Telos3K on 2011-01-13
I ran:
```
sudo blkid /dev/sda7
```

and got:
```
/dev/sda7: LABEL="Swap" UUID="24622487-0dd5-4c54-bd7f-724c9bf66979" TYPE="swap"
```

I then changed my fstab and resume files to match it:
```
bwbloch@ubuntu:~$ cat /etc/fstab | grep swap
#/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0
UUID=24622487-0dd5-4c54-bd7f-724c9bf66979    none    swap    sw    0    0
bwbloch@ubuntu:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=24622487-0dd5-4c54-bd7f-724c9bf66979
bwbloch@ubuntu:~$ 
```

I then run:
```
sudo update-initramfs -u
```
and get:
```
update-initramfs: Generating /boot/initrd.img-2.6.32-27-generic
bwbloch@ubuntu:~$ 
```

Then reboot, and got to hibernate, and the system freezes up, then shuts down and performs a disk check on rebooting.

Per bcbc's suggestion, this is now a [new thread]("http://ubuntuforums.org/showthread.php?t=1652522")....

---

### Post by bcbc on 2011-01-13
Telos3k,
There are many reasons that hibernation may not work. At this point it's best to create a new thread (because we're getting off topic for this one) and include the following info in it.

Machine brand/model - full specs

Post the result of:
```
grep 'PM:' /var/log/syslog
```
and 
```
free
```

I'll find your new thread, or you can just edit your previous post with the address.

---

### Post by dtx4 on 2011-01-24
kool, thanks, this is by far the easiest way to install ubuntu i believe. 
for all those windows users, who have a problem partitioning hard-drive and dont wanna go through all of this mammoth of a thread, here's a quick recap:
>get wubi on your windows box
>[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) Go through this link
>follow the steps on page 1
:KS
peace

now i need to install kernel updates and hope that it doesnt break my ubuntu! :O

---

### Post by robst on 2011-01-24
Hi bcbc,
I congratulate you for this tool, it worked all fine and I am happy with the results, in my case i got rid of my Vista, and now I am solely on Ubuntu, I did the move basically because the available resources were getting scarce working in Windows.  

Now I want to uninstall Wubi, I have seen all uninstall tools are for windows, I wonder how do i do it from the migrated Linux.  I am wondering if I just reformat the partition on which it was installed first (I install it in a small 10G primary partition).

I would appreciate your comments.  Best of luck.

---

### Post by bcbc on 2011-01-25
> **robst said:**
> Hi bcbc,
I congratulate you for this tool, it worked all fine and I am happy with the results, in my case i got rid of my Vista, and now I am solely on Ubuntu, I did the move basically because the available resources were getting scarce working in Windows.  

Now I want to uninstall Wubi, I have seen all uninstall tools are for windows, I wonder how do i do it from the migrated Linux.  I am wondering if I just reformat the partition on which it was installed first (I install it in a small 10G primary partition).

I would appreciate your comments.  Best of luck.

Hi Robst, yes - if you no longer have windows the 'uninstall' of wubi on the 10GB is a simple format. Or you could just delete the /ubuntu directory on this partition and keep whatever else is on it (if anything).

Once you remove the root.disk then you no longer have the wubi backup (which is still bootable, even without windows), so it's a good idea to have a backup of your migrated install in place. 

Good luck!

---

### Post by bcbc on 2011-01-25
> **dtx4 said:**
> kool, thanks, this is by far the easiest way to install ubuntu i believe. 
for all those windows users, who have a problem partitioning hard-drive and dont wanna go through all of this mammoth of a thread, here's a quick recap:
>get wubi on your windows box
>[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) Go through this link
>follow the steps on page 1
:KS
peace

now i need to install kernel updates and hope that it doesnt break my ubuntu! :OThanks for the feedback. You're right this thread has got fairly long, however I don't think it's required to read the whole thing unless you're interested in other people's experiences. If I hear of any bugs I'll update post #1 and following that try and get it fixed asap, so technically Post #1 should contain everything you need to know about the migration.

I though about including links to partitioning guides there, but some of them contain old information - and the resulting discussions could easily end up dominating a thread such as this.

Good luck with those update ;)

---

### Post by WeFY-KVQqr on 2011-01-28
I'm baffled...
I've tried this nice script to copy a wubi install to a partition. I've decided to stick with the bootloader chaining into wubi grub for the moment.
It worked flawlessly except one problem. The new install won't appear in the grub menu and what's more the previous available options to boot into windows 7 and the option of memtest86 are gone too. So one could say that all os-prober options of grub won't stick.
I've tried to run the bootinfo script and that one indeed detects windows and the new linux install. 

So I've decided to boot into the regular wubi install and tried to perform a grub update.
During that process it is shown that windows is detected and the new linux install but unfortunately the grub menu is STILL not updated.

In the meantime I've invested so much time in this that I could easily have installed a fresh ubuntu version at least 3 times, so for now I've done some nice tweaking and edited the wubi grub menu in order to make it boot the new linux install. However I guess that will be automatically reverted back by a future grub update.

Does someone know why the os-prober entries are not picked up?
Or is there somehow a limit in the number of entries the wubi grub menu will display?
Currently there are 8 entries in it (4 kernels and 4 recovery options of the same kernels).

---

### Post by bcbc on 2011-01-28
> **WeFY-KVQqr said:**
> I'm baffled...
I've tried this nice script to copy a wubi install to a partition. I've decided to stick with the bootloader chaining into wubi grub for the moment.
It worked flawlessly except one problem. The new install won't appear in the grub menu and what's more the previous available options to boot into windows 7 and the option of memtest86 are gone too. So one could say that all os-prober options of grub won't stick.
I've tried to run the bootinfo script and that one indeed detects windows and the new linux install. 

So I've decided to boot into the regular wubi install and tried to perform a grub update.
During that process it is shown that windows is detected and the new linux install but unfortunately the grub menu is STILL not updated.

In the meantime I've invested so much time in this that I could easily have installed a fresh ubuntu version at least 3 times, so for now I've done some nice tweaking and edited the wubi grub menu in order to make it boot the new linux install. However I guess that will be automatically reverted back by a future grub update.

Does someone know why the os-prober entries are not picked up?
Or is there somehow a limit in the number of entries the wubi grub menu will display?
Currently there are 8 entries in it (4 kernels and 4 recovery options of the same kernels).
What release are you on?

You mentioned that the "it is shown that windows is detected and the new linux install". Can you confirm that the auto-generated grub.cfg contains all the correct entries. Just backup your edited one first.

UPDATE:
I've duplicated this on 10.04.1 with the latest grub-pc update applied. This is somehow related to the grub bug that causes boot failures in wubi 10.04.1. The fix is the same (see [here]("http://ubuntuforums.org/showthread.php?t=1639198")):
```
sudo mv /boot/grub /boot/grubold
sudo mkdir /boot/grub
sudo cp /boot/grubold/grubenv /boot/grub
sudo update-grub
```

---

### Post by WeFY-KVQqr on 2011-01-28
Yeah, message #200 in this thread. This is a very successful and useful thread.  =D>
 
Anyway...
 
Thanks bcbc for your very quick response.
 
I'm using the dreaded Ubuntu 10.04.1 version.
I'm familiar with the thread you mention, but I can't exactly link my problem to one of the examples mentioned there.
 
Does my Windows boot? I should say yes because it is bootable with its own bootloader, but I can't boot it from the grub menu, because is not listed there anymore.
Does my Ubuntu boot? Well, that's probably a "yes" too, but I can't boot the particular version I want too because it isn't listed in the menu, but the other entries in the grub menu boot perfectly.
 
Furthermore I don't know exactly what to do with your suggestion. If I look it up in the thread you mentioned, it looks to me as a "partial" solution. Do you mean I've only to do these four actions to solve the problem?
If not do I have problem 1 or problem 2 according to you?
In the meantime I blew the edited grub menu and I had to repair it with a Live CD so I'm back to the "original" grub menu and I'm a bit more cautious now before performing more actions.
 
 
I found out that when I go to the command line in the grub menu and I do the following three actions I can boot the new ubuntu installation too:
 
 
```
linux /boot/vmlinuz-2.6.32-27-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro quiet splash
initrd /boot/initrd.img-2.6.32-27-generic
boot

```

 
You asked about grub.cfg. Well I don't know if it contains the correct entries.
It looks like this:
 
 
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
 
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi
 
function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
 
function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
 
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
 
### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-27-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-27-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set dc1a10b21a108ba0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set c4e2d2cde2d2c2ba
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 82deb960deb94d63
    chainloader +1
}
menuentry "Ubuntu, met Linux 2.6.32-27-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, met Linux 2.6.32-27-generic (herstelmodus) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, met Linux 2.6.32-26-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, met Linux 2.6.32-26-generic (herstelmodus) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, met Linux 2.6.32-25-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, met Linux 2.6.32-25-generic (herstelmodus) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, met Linux 2.6.32-24-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, met Linux 2.6.32-24-generic (herstelmodus) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 843f3473-a806-431f-a33f-45be9e8ce14c
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=843f3473-a806-431f-a33f-45be9e8ce14c ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/30_os-prober ###
 
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ### 
```
 
The migrated installation is the one on /dev/sda6.
 
You see a few times "herstelmodus" that's the Dutch translation of "recovery mode".

---

### Post by bcbc on 2011-01-28
@WeFY-KVQqr, first off, congrats on being #200 ;)

So, this grub problem is still largely a mystery. It doesn't always affect everyone the same way. And I've had installs where it boots fine for a while, but then later stops booting. This latest problem you've found is a new wrinkle... there's nothing wrong with the grub.cfg, but it only shows a partial list of entries. But if you hit 'c' - drop to a grub command line - and manually load grub.cfg (configfile /boot/grub/grub.cfg) you'll probably see it reboot (mine does).

Unfortunately the grub developers have declined to take an interest, so the best we can do is workaround the problem. That permanent fix I describe is to restore the /boot/grub to what it looks like on a fresh Wubi install (prior to any grub-pc updates). This does fix your problem, because - even though you don't have the 'classic' symptoms mentioned in the Wubi megathread, I believe it's still part of the same problem.

Since you can still boot Wubi, you should boot it, go to terminal and apply the fix (those four commands I showed). Then also go into Synaptic and lock packages grub-pc and grub-common (locking is only required if you intend to keep using wubi).

PS I didn't examine your grub.cfg in detail, but in my tests I did compare the before and after - and there was nothing wrong that I could see to explain it. Luckily I was able to reproduce the problem quickly so it makes it easier to diagnose/fix.

Thanks for the feedback 
PS I updated post #1 to add it to the known issues.

---

### Post by WeFY-KVQqr on 2011-01-29
bcbc, thanks man! It did the trick.
However I had to deviate a little bit from your advise.
 
The third command
 
```
 
sudo cp /boot/grubold /boot/grub

```
 
refuses to work because boot/grub has been created in the previous command and after all this command would not make much sense because it boils down to copying the contents of grubold back to boot/grub which is the location where the contents did come from and which would mean no different situation than it was before.
So I've looked it up in the original thread. There I saw this command:
 
```
 
sudo cp /boot/grubold/grubenv /boot/grub

```
 
and that one does work although I don't quite understand why it works because the original grub folder has a lot of files and after this operation it misses most of them.
 
 
This brings me to some other questions:
 
- There are many updates for Ubuntu 10.04.1 including a new Linux kernel version (2.6.32-28 this time). Is it save to apply them or will they (and especially the new kernel version) once again not make it to the grub menu?
I'm not planning to do this with the wubi installation but only with the new migrated installation.
- Looking back on this complicated business. I rather get rid of the whole wubi stuff after all. Is it safe to perform a regular grub-install command now as pointed out in your first post and will it still be possible to boot into Windows after doing this?

---

### Post by bcbc on 2011-01-29
> **WeFY-KVQqr said:**
> bcbc, thanks man! It did the trick.
However I had to deviate a little bit from your advise.
 
The third command
 
```
 
sudo cp /boot/grubold /boot/grub

```
 
refuses to work because boot/grub has been created in the previous command and after all this command would not make much sense because it boils down to copying the contents of grubold back to boot/grub which is the location where the contents did come from and which would mean no different situation than it was before.
So I've looked it up in the original thread. There I saw this command:
 
```
 
sudo cp /boot/grubold/grubenv /boot/grub

```
 
and that one does work although I don't quite understand why it works because the original grub folder has a lot of files and after this operation it misses most of them.
 
 
This brings me to some other questions:
 
- There are many updates for Ubuntu 10.04.1 including a new Linux kernel version (2.6.32-28 this time). Is it save to apply them or will they (and especially the new kernel version) once again not make it to the grub menu?
I'm not planning to do this with the wubi installation but only with the new migrated installation.
- Looking back on this complicated business. I rather get rid of the whole wubi stuff after all. Is it safe to perform a regular grub-install command now as pointed out in your first post and will it still be possible to boot into Windows after doing this?
Sorry about that typo - I swear I checked it more than a couple of times ;)
Anyway... that command just copies the grubenv file to the new /boot/grub. That's the same as on a default wubi install.

There's no issue I am aware of with running kernel updates etc. in wubi other than kernel updates automatically regenerate grub.cfg. But since you've made that permanent fix - it has no negative effect - and I'd be surprised if you see that same problem again.

Yes it is safe to install grub2 - you can first boot into the migrated install, run "sudo update-grub" and confirm that it sees the windows install from the output or by looking at /boot/grub/grub.cfg. 
Then install it to the drive MBR as described.

---

### Post by fubar65 on 2011-01-30
using Ubuntu 10.10, I also tried this, I came up with several roadblocks.
When I rebooted I got a grub> prompt only.
after some searching I used my win XP cd to fixmbr and then I got my boot menu back..
however Windows refused to boot and I ultimately wanted to get rid of wubi on the windows partition. I was able to boot to the wubi install or the newly created copy on sda5.
I edited the boot loader and then it only tried to boot into Windows, which it wouldn't, I got a black screen and it locked up.. I said screw that and am cloning it back to the way it was right now..

I assume the Ubuntu will still be on sda5, so my question is, how do I disable wubi without uninstalling it (until I get this working), and how do I go about getting the grub loader to pick up Ubuntu and XP so I can then uninstall wubi.

I am sorry I used wubi now.. nice to tinker with but updates cause unending problems..
If it wasn't such a pain to get my print server working I would just get the data and do a fresh install..

Th@nX

---

### Post by bcbc on 2011-01-30
> **fubar65 said:**
> using Ubuntu 10.10, I also tried this, I came up with several roadblocks.
When I rebooted I got a grub> prompt only.
after some searching I used my win XP cd to fixmbr and then I got my boot menu back..
however Windows refused to boot and I ultimately wanted to get rid of wubi on the windows partition. I was able to boot to the wubi install or the newly created copy on sda5.
I edited the boot loader and then it only tried to boot into Windows, which it wouldn't, I got a black screen and it locked up.. I said screw that and am cloning it back to the way it was right now..

I assume the Ubuntu will still be on sda5, so my question is, how do I disable wubi without uninstalling it (until I get this working), and how do I go about getting the grub loader to pick up Ubuntu and XP so I can then uninstall wubi.

I am sorry I used wubi now.. nice to tinker with but updates cause unending problems..
If it wasn't such a pain to get my print server working I would just get the data and do a fresh install..

Th@nX

Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results. Did you do the manual conversion?

---

### Post by fubar65 on 2011-01-30
I used the script, not manual, it seemed to go fairly quickly and it looked like it worked..
I cloned it back and Windows and Wubi are both working now, everything is on sda5 but when I try to update grub and reboot, even windows is gone from the loader, I get several versions of kernel for my wubi install to choose from, nothing more..

thanks for the reply


I ran the boot info script and this is the output
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   167,782,859   167,782,797   7 HPFS/NTFS
/dev/sda2         167,782,860   312,576,704   144,793,845   f W95 Ext d (LBA)
/dev/sda5         167,782,923   305,395,649   137,612,727  83 Linux
/dev/sda6         305,395,713   311,259,374     5,863,662  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       4d505caa-8c37-42a3-ad2a-397560ff7dd9   ext4                                     
/dev/sda1        B874B77674B735CA                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79   ext4                                     
/dev/sda6        8810c3fc-2171-426a-99ee-c3b56dcccc96   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

======================== sda1/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b874b77674b735ca
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set b874b77674b735ca
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b874b77674b735ca
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b874b77674b735ca
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b874b77674b735ca
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, Linux 2.6.35-23-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b874b77674b735ca
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b874b77674b735ca
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro quiet splash
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux /boot/vmlinuz-2.6.35-23-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro single
    initrd /boot/initrd.img-2.6.35-23-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


  15.4GB: boot/grub/grub.cfg
  16.9GB: boot/initrd.img-2.6.35-23-generic
    .6GB: boot/initrd.img-2.6.35-25-generic
   4.6GB: boot/vmlinuz-2.6.35-23-generic
   4.5GB: boot/vmlinuz-2.6.35-25-generic
    .6GB: initrd.img
  16.9GB: initrd.img.old
   4.5GB: vmlinuz
   4.6GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set b874b77674b735ca
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sda5 when wubi migrated
UUID=e263e0ab-c60d-4ed3-8fa8-ec82a5e71d79    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sda6 when wubi migrated
UUID=8810c3fc-2171-426a-99ee-c3b56dcccc96    none    swap    sw    0    0

=================== sda5: Location of files loaded by Grub: ===================


  88.2GB: boot/grub/core.img
  94.6GB: boot/grub/grub.cfg
  86.0GB: boot/initrd.img-2.6.32-26-generic
  87.0GB: boot/initrd.img-2.6.35-23-generic
  86.1GB: boot/initrd.img-2.6.35-25-generic
  88.1GB: boot/vmlinuz-2.6.32-26-generic
  88.1GB: boot/vmlinuz-2.6.35-23-generic
  88.2GB: boot/vmlinuz-2.6.35-25-generic
  86.1GB: initrd.img
  87.0GB: initrd.img.old
  88.2GB: vmlinuz
  88.1GB: vmlinuz.old
```

the  biggest reasons for doing this is stability with updates, I don't want slow downs due to fragmentation and wireless has a lot of problems connecting, but I think that is the b43 driver..

Th@nX

---

### Post by bcbc on 2011-01-30
> **fubar65 said:**
> I used the script, not manual, it seemed to go fairly quickly and it looked like it worked..
I cloned it back and Windows and Wubi are both working now, everything is on sda5 but when I try to update grub and reboot, even windows is gone from the loader, I get several versions of kernel for my wubi install to choose from, nothing more..

thanks for the reply


I can't see any problems with either the wubi or the migrated install, although it seems like you upgraded your wubi to 10.10 from 10.04.1 - is this correct?
The reason is that you have the 'extended wubi grub menu' and one of the symptoms of this as has recently been discovered is the 'missing' menu items on the Wubi grub menu. (Read back a few posts in this thread).

But this shouldn't affect the normal Ubuntu... 

So if I understand you correctly, the migration seemed to go ok, but you ended up at a grub prompt when you rebooted.
You restored back, but now the Windows and migrated install from the Wubi grub menu doesn't show? Is this correct?

First thing I'd do is do the "Permanent Fix" shown (see post 1, known issues, or as described one or two posts back). That should get all your Wubi grub menu entries showing again. Then boot the migrated install from the wubi menu and check it's working fine.

Then try and install the grub2 bootloader again - see if there is any error output from it. Sometimes Grub2 detects the presence of other software using the space between the master boot record and the first partition and outputs a message. In that case, it doesn't always work. But it's hard to know this during the migration as I believe the script suppresses that output (a newer version coming soon handles chroot errors better).

So to do this, boot your migrated install from the Wubi grub menu (after applying that fix) and run:
```
sudo grub-install /dev/sda

```

If you see any weird output or errors, then likely it won't boot - so just fix the MBR with lilo before restarting:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
or boot from your windows repair disc and just run fixmbr (fixboot not required). If you use lilo, ignore the big warning screen.

If everything looked good, then try booting it again.

---

### Post by fubar65 on 2011-01-31
how odd, I just booted it up and there it was in the boot menu, the install on sda5..

I did indeed upgrade from 10.04 to 10.10 in the hopes it would fix the long login times to the wireless network.. it didn't help at all.

I am not sure why this showed up in the boot menu but it did..
first thing I did was edit my boot.ini file to remove the wubi reference, then I moved the 2 wubi boot files to another folder, then I ran the sudo update-grub and sudo install-grub /dev/sda

then I rebooted and the proper boot menu showed up, I am now in Ubuntu 10.10 with a true dual boot system, thanks, the guide does work, I just had a few hiccups along the way!

now if I can get the damn wireless to work better I'd be all set..


Th@nX for the guide and info!


edit - I uninstalled the network manager and am just using Wicd and it is working much better, 5 reboots and it logs right in to the wireless!
it's the wife's laptop so she will be happy too, brownie points for me!!

---

### Post by Jack-87 on 2011-02-06
So i figured I would upgrade my wubi 10.04 to 10.10 in the process I found that I will need more disk space as my 30gig wubi just isn't cutting it.

Extending the virtual disk for wubi requires making a larger virtual disk and migrating it over to that. So I figured I might as well just migrate to a real partition.

My upgrade has already started and can not be stopped.

My question is will I be able to migrate a 10.10 version of ubuntu to a actual partition on the physical disk using this script or not?

Also... As it stands the computer has two physical disks. 500 gigs each.

The first disk has windows and a few default partitions from manufacturer. 

Second disk has about 150 gigs free and my wubi virtual disk is on this disk.

Is there anyway I can repartion this disk while booted into my wubi install to have 120 gigs for ubuntu and 2 gigs swap.

Sorry i know I asked many questions. I just need to know if these are possible and i will hunt down appropriate threads for the off topic ones.

Thanks!!!!

---

### Post by bcbc on 2011-02-06
@Jack-87
Yes you can migrate 10.10 with the script.

No you cannot split a partition while the partition is mounted. You should do it while booted from a live CD. If you don't have an ubuntu cd (or usb) yet you should get one.

It's also a good idea to back up your data, prior to upgrading, prior to partitioning.

---

### Post by NARGB on 2011-02-11
Thanks a lot, It worked fine!

---

### Post by aym_74 on 2011-02-11
Hello everybody!

I'm using a wubi from now 7 month and will try now to go on a std partition! I've prepared the ext3 and the swap and was going to use a "wubi move to partition" found on the official ubuntu website, but I saw that there could be some bug about the grub so I'm going to download (I hope!) the scrip I found in this thread :D

I'll let You know, but let me thank You for the job You do for us

---

### Post by aym_74 on 2011-02-12
> **aym_74 said:**
> Hello everybody!

I'm using a wubi from now 7 month and will try now to go on a std partition! I've prepared the ext3 and the swap and was going to use a "wubi move to partition" found on the official ubuntu website, but I saw that there could be some bug about the grub so I'm going to download (I hope!) the scrip I found in this thread :D

I'll let You know, but let me thank You for the job You do for us

transfer complete perfectly!

Thank's a lot!

Just one more question:

I saw that in the partition i used to install wubi, there still is the "ubuntu" folder that was created before, can I delete it? Must I uninstall the wubi from winXP?

Thak You for any answer

---

### Post by bcbc on 2011-02-12
> **NARGB said:**
> Thanks a lot, It worked fine!
Good to hear.

> **aym_74 said:**
> transfer complete perfectly!

Thank's a lot!

Just one more question:

I saw that in the partition i used to install wubi, there still is the "ubuntu" folder that was created before, can I delete it? Must I uninstall the wubi from winXP?

Thak You for any answer
Once you're happy everything is working, you can boot Windows and uninstall Wubi normally - either through the Control Panel Add/remove (entry Ubuntu) or run program \ubuntu\Uninstall-Ubuntu.exe

---

### Post by aym_74 on 2011-02-16
> **bcbc said:**
> Good to hear.


Once you're happy everything is working, you can boot Windows and uninstall Wubi normally - either through the Control Panel Add/remove (entry Ubuntu) or run program \ubuntu\Uninstall-Ubuntu.exe

Hi!

i'm happy and everything seems to work in a good way :D

But....

i can't find in the grub's list window xp! That is I can only charge ubuntu and not xp. I could even not be a big problem but I would like to access to it in order to uninstall the wubi version of ubuntu.

any suggestion?

---

### Post by bcbc on 2011-02-16
> **aym_74 said:**
> Hi!

i'm happy and everything seems to work in a good way :D

But....

i can't find in the grub's list window xp! That is I can only charge ubuntu and not xp. I could even not be a big problem but I would like to access to it in order to uninstall the wubi version of ubuntu.

any suggestion?

If running "sudo update-grub" doesn't add it, then post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

I haven't come across cases in my tests where windows wasn't added to the grub menu.

---

### Post by enid on 2011-02-16
Hi bcbc,

Thank you for this great HowTo.
It worked pretty well for me, firstly I tried to execute the script inside the running wubi-ubuntu, but then I realised that I should use sth like a liveCD, and I boot-ed Puppy Linux from my usb, and ran the script from there. Worked like a charm ;) Now Ubuntu has gained independence on my comp :D

This HowTo should be on the wubi FAQ or the default method for migrating.

BR

---

### Post by bcbc on 2011-02-16
> **enid said:**
> Hi bcbc,

Thank you for this great HowTo.
It worked pretty well for me, firstly I tried to execute the script inside the running wubi-ubuntu, but then I realised that I should use sth like a liveCD, and I boot-ed Puppy Linux from my usb, and ran the script from there. Worked like a charm ;) Now Ubuntu has gained independence on my comp :D

This HowTo should be on the wubi FAQ or the default method for migrating.

BR
Hi enid, 
That --root-disk=... option is a new feature that was introduced with version 2.0: to do a migration from a live CD/USB. You could also have run it from the booted Wubi install, which is the simplest approach for most. It can also migrate a normal (non-wubi) Ubuntu install.

I have added a link to this how to in the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How do I migrate to a real partition, and/or get rid of Windows entirely?").

Thanks for the feedback!

---

### Post by enid on 2011-02-17
> **bcbc said:**
> Hi enid, 
That --root-disk=... option is a new feature that was introduced with version 2.0: to do a migration from a live CD/USB. You could also have run it from the booted Wubi install, which is the simplest approach for most. It can also migrate a normal (non-wubi) Ubuntu install.

I have added a link to this how to in the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?").

Thanks for the feedback!

Hi bcbc,
Sorry for not getting right this part (--root-disk=... option). Indeed firstly I added this option also on the booted wubi install.
Great you've added the link to Wubi Guide.

You have my congratulations on this.

BR

---

### Post by bcbc on 2011-02-17
> **enid said:**
> Hi bcbc,
Sorry for not getting right this part (--root-disk=... option). Indeed firstly I added this option also on the booted wubi install.
Great you've added the link to Wubi Guide.

You have my congratulations on this.

BR
Ah that makes sense. I put in checks to prevent using --root-disk= when it's mounted, but I was thinking 'mounted for browsing' rather than 'running the wubi at the time'. So perhaps the message should have been clearer. 

I'll modify post #1 to clarify. 

Thanks again for the feedback. You can see how important it is, because otherwise I'm limited to my own experience and assumptions on how it will be used.

---

### Post by ubuntuforums on 2011-02-17
Worked perfectly. Now if I uninstall Wubi from Windows, how will I boot into Ubuntu? Right now I'm using the Windows boot menu which allows me to select Ubuntu and then it brings me to the grub menu. Do I need to install the grub menu first?

The reason I chose not to install the grub menu, is I have more than one boot option for Windows 7. One is regular, another has DEP disable, etc. So if install the grub menu I believe it will only display the regular Windows 7 boot option... ?

---

### Post by bcbc on 2011-02-17
> **ubuntuforums said:**
> Worked perfectly. Now if I uninstall Wubi from Windows, how will I boot into Ubuntu? Right now I'm using the Windows boot menu which allows me to select Ubuntu and then it brings me to the grub menu. Do I need to install the grub menu first?

The reason I chose not to install the grub menu, is I have more than one boot option for Windows 7. One is regular, another has DEP disable, etc. So if install the grub menu I believe it will only display the regular Windows 7 boot option... ?

Well, you can use EasyBCD. I haven't used it myself so can't offer any advice on that. That's one option.

But if you install the grub2 bootloader, you should still be able to get to  the same windows boot manager, and it will show the choice between regular and DEP disable, and Wubi (until you uninstall it). 

You can test this already from the wubi grub menu...look below the entries for memtest and you'll see an entry (or entries) for Windows. That's the same as you'd see if grub2 was installed. By selecting the correct one* you'll then see the Windows boot manager again.

* *Grub2 isn't good identifying vista/7 installs and will often mix up which one is the recovery. So choose the one that refers to the partition with the boot flag set*.

Anyway, once you're confident that you can get to Windows from Grub, then you can do one final test:
Press 'c' from the grub menu to get to a grub prompt, then enter "configfile (hd0,5)/boot/grub/grub.cfg"  (this will bring up the grub menu on the migrated install - assuming you installed to /dev/sda5 - or change (hd0,5) accordingly) and that's the exact grub menu that you'd see on startup.

If all is good, boot the migrated install and enter (assuming you boot from /dev/sda):
sudo grub-install /dev/sda

---

### Post by bou3lam on 2011-02-19
tell me please something, this will not move the whole wubi files but just the personal files ? because when i applied , ubuntu stayed in E and since its a fresh install D was empty ! excuse me how i said before im a total dumby

---

### Post by bcbc on 2011-02-19
> **bou3lam said:**
> tell me please something, this will not move the whole wubi files but just the personal files ? because when i applied , ubuntu stayed in E and since its a fresh install D was empty ! excuse me how i said before im a total dumby
The script migrates everything on the Wubi install (root.disk) to the target partition. Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by bou3lam on 2011-02-20
please someone explain what the swap function mean :confused:

---

### Post by bou3lam on 2011-02-20
same as yesterday, ubuntu folder stayed in E  , and dev sd5 which is D is empty !  here are the results of boot info script

---

### Post by bcbc on 2011-02-20
> **bou3lam said:**
> please someone explain what the swap function mean :confused:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
If you need to hibernate you need a swap partition, otherwise you can create a swap file. That link explains how to do that. 
Note for hibernation the swap partition must be > size of RAM (add about .5 to 1 GB to be safe e.g. 2GB RAM = 3GB swap)

> **bou3lam said:**
> same as yesterday, ubuntu folder stayed in E  , and dev sd5 which is D is empty !  here are the results of boot info script
Ok, from the bootinfsocript results it looks like everything migrated normally. What was previously your D: 'drive' in windows (/dev/sda5) contains 10.04.1 Ubuntu. 

You didn't install the Grub2 bootloader so to boot it you have to use your Wubi grub menu:  select Ubuntu from the windows boot manager, then look towards the bottom of the grub menu, AFTER the Windows entry you'll see an "*Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda5)*" entry. Select that and it will boot your migrated install.

At some point you'll need to make a provision for booting the migrated install without Wubi - e.g. installing grub2's bootloader to the MBR. Make sure you do that before removing Wubi.

---

### Post by bou3lam on 2011-02-20
please, a step by step what to do :(

---

### Post by bcbc on 2011-02-20
> **bou3lam said:**
> please, a step by step what to do :(

What do you want help with?

---

### Post by bou3lam on 2011-02-21
> 

At some point you'll need to make a provision for booting the migrated install without Wubi - e.g. installing grub2's bootloader to the MBR. Make sure you do that before removing Wubi.
i must uninstall wubi or what ? if i do it will remove ubuntu also

---

### Post by bou3lam on 2011-02-21
but D or sda5 is empty !please take a look [[IMG]http://img691.imageshack.us/img691/1526/screenshotmb.png[/IMG]](http://img691.imageshack.us/i/screenshotmb.png/)

---

### Post by bcbc on 2011-02-21
> **bou3lam said:**
> i must uninstall wubi or what ? if i do it will remove ubuntu also
You don't have to uninstall Wubi. 
If you uninstall Wubi it will remove the Wubi Ubuntu, not the migrated Ubuntu. But you don't have the ability to boot the migrated Ubuntu yet, except through the Wubi grub menu.

Also, /dev/sda5 is not empty. The disk utility isn't a good place to see whether it contains files or not.

To get the migrated install booting on its own do the following:
1. boot into it using the wubi grub menu
2. run 
```
sudo grub-install /dev/sda
```
That will replace the Windows bootloader with the grub2 bootloader. After that your computer will boot via the ubuntu install on /dev/sda5

PS you should change the partition type of /dev/sda5 to '83' - linux. Since you migrated to what was an ntfs partition. That's one thing the script doesn't do.
You can boot the **Wubi** install and use the following command:
```
sudo sfdisk -c /dev/sda 5 83
```

(Do it from Wubi when it's unmounted).

---

### Post by bou3lam on 2011-02-21
thanks alot, but i had very bad experience with grub in the past and was unable to boot :(

---

### Post by bcbc on 2011-02-21
> **bou3lam said:**
> thanks alot, but i had very bad experience with grub in the past and was unable to boot :(

OK... how do you want to boot the new install?

---

### Post by bou3lam on 2011-02-21
arent there any alternatives else than grub please ?

---

### Post by bcbc on 2011-02-21
> **bou3lam said:**
> arent there any alternatives else than grub please ?
I guess you could use Lilo. I know that on vista/7 you can use EasyBCD to boot Ubuntu (it still uses grub2, but it's installed to the partition boot sector, not the master boot record) - but you're on XP anyway?

But this thread is more about the wubi migration. For most people Grub2 is OK. If you need specific help with Grub2 and its alternatives drs305 is the person to ask: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jagannathahm on 2011-02-22
HI 
Thanks for the script It worked like a charm.  I like to use a third party boot loader e.g.GAG4.10 which has worked very well for me when linux is installed directly via cd or dvd .  migarted partition is not recognized by the bootloader says : boot sector not found"  Any suggestions for this?  If this can be done then we can delete wubi and use it again on another partition in future.

---

### Post by tejjammy on 2011-02-22
Hi im trying to migrate this on my new dell laptop but unfortunately i cannot create a new primary partition.
I have attached a pic showing my HDD map can you suggest what to do ?
Thank you

---

### Post by bcbc on 2011-02-22
> **jagannathahm said:**
> HI 
Thanks for the script It worked like a charm.  I like to use a third party boot loader e.g.GAG4.10 which has worked very well for me when linux is installed directly via cd or dvd .  migarted partition is not recognized by the bootloader says : boot sector not found"  Any suggestions for this?  If this can be done then we can delete wubi and use it again on another partition in future.
This is not done by default on any install, unless you select to install grub2 to the partition boot record. You can do it manually, but you'll have to use the --force option to get grub2 to allow it.
> bcbc@ubuntu:~$ sudo grub-install /dev/sda1
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.


PS: don't do this from the Wubi install. Wubi has overrides for "grub-install" that instead try to update the wubildr. If you boot the migrated install you can do this. Be very careful, if you install grub2 to the partition boot record (boot sector) of a Windows partition by accident, it will break Windows.

---

### Post by bcbc on 2011-02-22
> **tejjammy said:**
> Hi im trying to migrate this on my new dell laptop but unfortunately i cannot create a new primary partition.
I have attached a pic showing my HDD map can you suggest what to do ?
Thank you
You cannot create any new primary partitions (maximum allowed is 4). But you could split one of your logical partitions and created a couple more for Ubuntu (it doesn't require a primary partition). In your case, one of those logicals is the /host partition so you couldn't modify it while running Wubi, but you could from a live CD.

Be careful though - if you were to split /dev/sda5 for instance, you will find that the /host that is currently /dev/sda6 would become e.g. /dev/sda8. In that case, Wubi will need some help to boot (not a big deal, but you need to 'e'dit the grub menu and modify the "root=/dev/sdaY" parameter). 
If instead you split /dev/sda6 and created new /dev/sda7 and /dev/sda8 you wouldn't have any issues.

---

### Post by tejjammy on 2011-02-22
> **bcbc said:**
> You cannot create any new primary partitions (maximum allowed is 4). But you could split one of your logical partitions and created a couple more for Ubuntu (it doesn't require a primary partition). In your case, one of those logicals is the /host partition so you couldn't modify it while running Wubi, but you could from a live CD.

Be careful though - if you were to split /dev/sda5 for instance, you will find that the /host that is currently /dev/sda6 would become e.g. /dev/sda8. In that case, Wubi will need some help to boot (not a big deal, but you need to 'e'dit the grub menu and modify the "root=/dev/sdaY" parameter). 
If instead you split /dev/sda6 and created new /dev/sda7 and /dev/sda8 you wouldn't have any issues.

So should i run using a live CD and split the last drive? I won't need to edit GRUB2 menu then.
Also if i choose not to write GRUB to MBR, how will ubuntu boot?

---

### Post by bcbc on 2011-02-22
> **tejjammy said:**
> So should i run using a live CD and split the last drive? I won't need to edit GRUB2 menu then.
Also if i choose not to write GRUB to MBR, how will ubuntu boot?
Yes, use the live CD to partition. I should caution that with partitioning there are always risks, so backing up beforehand is a good idea.

Regarding whether or not to install Grub to the MBR, my personal recommendation is to install it. But I understand that some people are not comfortable with this and there are some alternatives - e.g. for Win7/vista you can use EasyBCD. I just can't offer any advice, because I've never used them. If you create a new thread, you'll probably get responses from people who have used them.

As an interim measure you can boot the migrated install from the Wubi grub menu, but that's only good in the short term.

---

### Post by tejjammy on 2011-02-22
> **bcbc said:**
> Yes, use the live CD to partition. I should caution that with partitioning there are always risks, so backing up beforehand is a good idea.

Regarding whether or not to install Grub to the MBR, my personal recommendation is to install it. But I understand that some people are not comfortable with this and there are some alternatives - e.g. for Win7/vista you can use EasyBCD. I just can't offer any advice, because I've never used them. If you create a new thread, you'll probably get responses from people who have used them.

As an interim measure you can boot the migrated install from the Wubi grub menu, but that's only good in the short term.

I have no problems in installing GRUB on MBR. Only thing is that my Dell laptop has 3 yrs warranty which i don't want to void... I paid about 12% of the laptop's cost for it. 
Thank you again!

---

### Post by oglipogli on 2011-02-25
Dear bcbc,
Can u please help me out the partitions are confusing me a lot I have upgraded to Ubuntu 10.04 LTS right now running under WUBI its in the main partition along with Windows XP.
Apart from that i have three logical partitions one of which contains Win 7 now can we make ubuntu take over the entire partition thereby wiping XP out without disturbing the other 3 partitions. 
I may be short in tech details but please reply.
I have customised my UBUNTU n i like it this way can it be migrated?

---

### Post by bcbc on 2011-02-25
> **oglipogli said:**
> Dear bcbc,
Can u please help me out the partitions are confusing me a lot I have upgraded to Ubuntu 10.04 LTS right now running under WUBI its in the main partition along with Windows XP.
Apart from that i have three logical partitions one of which contains Win 7 now can we make ubuntu take over the entire partition thereby wiping XP out without disturbing the other 3 partitions. 
I may be short in tech details but please reply.
I have customised my UBUNTU n i like it this way can it be migrated?

Usually when you install Windows 7 after an earlier version of Windows, it places the Windows 7 boot files on the earlier versions partition - and then sets up both options in the windows boot manager. If you then format the partition containing XP, windows 7 doesn't boot. So that's one thing to look for.

Also you have Wubi in the same partition as XP so you cannot migrate directly from Wubi over the partition it is on. It is possible to migrate from just the root.disk (new option --root-disk=xxx) but you'd have to copy it off the partition first and then migrate it back on using a live CD.

But your biggest issue is probably that Windows 7's boot files are on your XP partition. Take a look at [this]("http://www.multibooters.co.uk/system.html") and/or [this]("http://www.multibooters.co.uk/multiboot.html").

---

### Post by oglipogli on 2011-02-27
> **bcbc said:**
> This guide is broken into two parts... the first shows how to manually migrate a Wubi 9.10, 10.04 or 10.10 install to partition (grub2 only). The second part shows how to use the attached script to do an automated migration (this also supports grub-legacy).

The partition(s) must be created already - there are plenty of guides on how to do this. 


**_Manual migration_** (see below for automated migration)

*[COLOR="Red"]Please don't use the manual migration unless you fully understand what you are doing. The automated migration has many additional safeguards and will protect you from errors.[/COLOR]*

This example assumes the new install will be on [COLOR="Red"]/dev/sda5[/COLOR] and that there will be a swap on [COLOR="Blue"]/dev/sda6[/COLOR]. If there is no swap, just ignore lines containing [COLOR="Blue"]/dev/sda6[/COLOR]. If there is a swap partition it must be of type 'swap'. Change the device names as appropriate.

Most of these commands are best cut-and-pasted to avoid typos. If you need to change the device names, I recommend doing it in a text editor before pasting to terminal. Otherwise, if you paste a linefeed by accident the command will run before you have a chance to change it.


1. Do this all as root
```
sudo -i
```

1.a. Ensure you do not have grub-legacy. If the output of the following shows version 0.97 then please do not continue. These instructions only work with grub versions 1.96 and greater. You can use the attached script *wubi-move-2.0.sh* instead.
```
grub-install --version
```

2. Format new partition if not done so already - make sure it's empty, large enough and unmounted
[COLOR="Red"]WARNING[/COLOR] -- the next command will wipe all existing data on [COLOR="Red"]/dev/sda5[/COLOR]
```
mkfs.ext4 [COLOR="Red"]/dev/sda5[/COLOR]
```

3. Mount new partition and copy files. 
```
mkdir /tmp/wubimove
mount [COLOR="Red"]/dev/sda5[/COLOR] /tmp/wubimove
rsync -av --exclude=/host --exclude=/mnt/* --exclude=/home/*/.gvfs --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/* --exclude=/sys/* / /tmp/wubimove
chmod -x /tmp/wubimove/etc/grub.d/10_lupin
```
    
4. Setup swap partition and enable hibernation (swap must be at least as big as RAM to hibernate)
```
mkswap [COLOR="Blue"]/dev/sda6[/COLOR]
echo "RESUME=UUID=$(blkid -o value -s UUID [COLOR="blue"]/dev/sda6[/COLOR])" > /tmp/wubimove/etc/initramfs-tools/conf.d/resume
```
    
5. Edit fstab (blank out wubi mounts with sed and add new partitions)
```
sed -i 's:/.*[\.]disk .*::' /tmp/wubimove/etc/fstab    
echo "UUID=$(blkid -o value -s UUID [COLOR="Red"]/dev/sda5[/COLOR])    /    ext4    errors=remount-ro    0    1" >> /tmp/wubimove/etc/fstab
echo "UUID=$(blkid -o value -s UUID [COLOR="blue"]/dev/sda6[/COLOR])    none    swap    sw    0    0" >> /tmp/wubimove/etc/fstab

```

6. Remove lupin support and update grub (all in chroot). Note that this step installs the grub bootloader to /dev/sda and will replace your windows bootloader (the line 'grub-install  /dev/sda') -- see note below
```
mkdir /tmp/wubimove/host
for i in dev proc sys dev/pts host; do mount --bind /$i /tmp/wubimove/$i; done
chroot /tmp/wubimove
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get -y remove lupin-support
update-grub
*grub-install /dev/sda*
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in host dev/pts dev proc sys; do umount /tmp/wubimove/$i; done
rmdir /tmp/wubimove/host
umount [COLOR="red"]/dev/sda5[/COLOR]
```

7. Update wubi grub menu to pick up new install and exit sudo
```
update-grub
exit
```    
You're done. When you reboot, you should see a grub menu instead of the windows boot menu. Select the first entry. If you didn't run 'grub-install' you can boot from the wubi menu, select your new install from the bottom after the Windows entry.

NOTE on installing the grub bootloader: you can try out the new installation by booting it from the wubi grub menu first - if you want to make sure everything is working before replacing the windows bootloader. To do this, bypass the line 'grub-install /dev/sda' (in step 6.). You can then install the grub2 bootloader manually later after booting into the new install.
I also recommend updating the grub menu after booting into the target partition ```
sudo update-grub
```

==================================================

**_Automated migration_**

[COLOR="Blue"]wubi-move-2.0.sh[/COLOR] is the latest release of the migration script. The previous script wubi-move.sh only supports Wubi with Grub2, whereas the new script adds the following features:
[LIST=1]
[*]Supports migration of a normal (non-wubi) Ubuntu install. This can be useful to create a working backup, move your installation between computers, or create a working copy to experiment with.
[*]Supports migration of a Wubi install from just the root.disk file (new option --root-disk= ). This can be performed from an Ubuntu live CD/USB or another Ubuntu install. The named root.disk must be a fully-contained, working Wubi install (this excludes grub-legacy Wubi where the /boot folder is always on the Windows partition).
[*]It supports migration of a Wubi or Normal install that uses grub-legacy - however it will replace grub-legacy with Grub2 (only on the migrated install). It does **not** update the current install's menu.lst so it is recommended to always install the Grub2 bootloader (or modify menu.lst manually).
[*]It has a new option --shared-swap to be used if you will be sharing an existing swap partition with another install. It bypasses the 'mkswap' command to avoid modifying the UUID.
[/LIST]
Usage instructions and notes:
```
bash wubi-move-2.0.sh --help
bash wubi-move-2.0.sh --notes
```
To migrate Wubi/normal install to /dev/sda5 without swap
```
sudo bash wubi-move-2.0.sh /dev/sda5

```
To migrate Wubi/normal install to /dev/sda5 with swap on /dev/sda6
```
sudo bash wubi-move-2.0.sh /dev/sda5 /dev/sda6

```
If you **don't** want to install the grub bootloader i.e. you want to leave the existing bootloader in place, use the --no-bootloader option. In this case, you will have to manually install the grub bootloader later.
```
sudo bash wubi-move-2.0.sh **--no-bootloader** /dev/sda5 /dev/sda6

```
To migrate from the root.disk when running from a live CD/USB:
```
sudo bash wubi-move-2.0.sh --root-disk=/media/win/ubuntu/disks/root.disk /dev/sda5 /dev/sda6
```
To share a swap partition with an existing install:
```
sudo bash wubi-move-2.0.sh --shared-swap /dev/sda5 /dev/sda6
```

PS I had to compress the latest script as it's too large for the forum limits. Download, right-click, then click "Extract here".

Warning - while I have tested this numerous times and every attempt has been made to ensure there are no bugs, use it at your own risk.

Please note - it takes some time to copy all the data from wubi to the target partition. e.g. on my computer it takes about 5-10 minutes for a small install (5GB).

Known issues:
1. For some reason, running "update-grub" in the chroot doesn't pick up other linux installations on the same drive (same running the script or manual commands listed above). This is unlikely an issue for wubi users. Run sudo update-grub after booting the new install for the first time.
2. If you have updated packages grub-pc or grub-common there is a bug in Grub that can result in the migrated install not showing up in the Wubi grub menu. This only affects you if you are not installing the Grub2 bootloader. The fix is described under the **Permanent Fix** of the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198").
Thanks a lot!!! successfully migrated removed win7 enjoying..!!!

---

### Post by bou3lam on 2011-02-28
bcbc thanks alot for the script its worked great, i will maybe keep the other (wubi) installed until there will be a stable grub relase, how i saw there is alot of bugs and people have problems with it , again many thanks for the great script and your kindly help

---

### Post by bcbc on 2011-02-28
> **oglipogli said:**
> Thanks a lot!!! successfully migrated removed win7 enjoying..!!!

> **bou3lam said:**
> bcbc thanks alot for the script its worked great, i will maybe keep the other (wubi) installed until there will be a stable grub relase, how i saw there is alot of bugs and people have problems with it , again many thanks for the great script and your kindly help

Great! You're welcome :)

---

### Post by oglipogli on 2011-03-01
> **oglipogli said:**
> Thanks a lot!!! successfully migrated removed win7 enjoying..!!!
 Was using Ubuntu 10.04 successfully after migration , then thought of upgrading. Upgrade files installed successfully but after restarting my laptop ..... nothing appears just blank screen & a blinking cursor. Tried pressing Shift key while start but nothing happens...!!! please help..!!!

---

### Post by bcbc on 2011-03-01
> **oglipogli said:**
> Was using Ubuntu 10.04 successfully after migration , then thought of upgrading. Upgrade files installed successfully but after restarting my laptop ..... nothing appears just blank screen & a blinking cursor. Tried pressing Shift key while start but nothing happens...!!! please help..!!!
Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

### Post by bcbc on 2011-03-04
> **oglipogli said:**
> Was using Ubuntu 10.04 successfully after migration , then thought of upgrading. Upgrade files installed successfully but after restarting my laptop ..... nothing appears just blank screen & a blinking cursor. Tried pressing Shift key while start but nothing happens...!!! please help..!!!
I've run a few tests - 10.04 wubi migration followed by a 10.10 upgrade - and I haven't had any problems. From your description, it sounds like your problem is related to grub; so reinstalling the grub2 bootloader will probably fix it - but it's hard to say exactly unless you provide the bootinfoscript results I requested earlier.

One thing I did notice is that - with the 10.10 upgrade Grub2 tries to reinstall it's bootloader to the device it was originally installed on. You can see this value with the command *debconf-show grub-pc* (it's the 'grub-pc/install_devices:' entry). For Wubi installs this is set to /dev/loop0.

The 2.0 version of the migration script updates this,  so grub will know where to update itself (or not if it's blank). The old script does not (it remains set to /dev/loop0). 
So for those people who used the old script and try to upgrade to 10.10, you might see a message prompting you that grub failed to install to /dev/loop0. Then it offers a check box to continue without installing - make sure you leave that box unchecked and click Forward, then select the correct drive device on the next screen e.g. /dev/sda, and it will continue correctly.
You can also proactively update the value with the following command (change /dev/sda as appropriate):
```
echo SET grub-pc/install_devices [COLOR=Blue]/dev/sda[/COLOR] | sudo debconf-communicate
```I hope that helps - please post the bootinfoscript results if you still need help.

---

### Post by milkywayfarer on 2011-03-08
Great thx, it works! (:

---

### Post by bcbc on 2011-03-12
> **milkywayfarer said:**
> Great thx, it works! (:

Great - thanks for the feedback :)

---

### Post by boroborolama on 2011-03-12
I'm ready to migrate my wubi install to a partition.  (I've actually been asking about this on the forums for a month.  I just didn't have the search term "migrate" until now!)

This laptop came with Windows 7 pre-installed, but I have no use for it anymore.  Ubuntu is great.  Can you help me understand my partition table well enough to run the script?  Do I use the partition in which the wubi virtual partition is mounted? ([FONT=Courier New]/dev/sda3[/FONT] I think)  Or do I need a new partition first?  Please advise.

Here's the output of [FONT=Courier New]df -h[/FONT]:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   13G  2.5G  84% /
none                  1.8G  292K  1.8G   1% /dev
none                  1.8G  468K  1.8G   1% /dev/shm
none                  1.8G  372K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda3             290G   50G  240G  18% /host

```

---

### Post by bcbc on 2011-03-12
boroborolama,
you haven't showed your partition table, just the space on your currently mounted file systems. Please run "sudo fdisk -l" (lowercase -L) to show the partition table.

The typical way to migrate requires new partitions or an existing, empty partition. This is recommended as you retain your working Windows (and the separate Wubi install). So this rules out /dev/sda3, but it does have a lot of free space, so it's a candidate for partitioning.

There are a number of partitioning guides out there. With Windows 7 you can partition using the disk manager - just make sure you don't convert your partitions to 'dynamic drives'.

---

### Post by boroborolama on 2011-03-12
Output of [FONT=Courier New]fdisk -l[/FONT]:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd64e292

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1146     9203712   27  Unknown
/dev/sda2   *        1146        1159      102400    7  HPFS/NTFS
/dev/sda3            1159       38914   303263064    7  HPFS/NTFS

```

---

### Post by daUnion on 2011-03-12
I just did this migrating a 10.10 install and on boot it says failed to load /lib/modules/2.6.35-25-generic/modules.dep then it boots into the graphical interface and I don't notice any differences(all drivers that should be loaded are loaded) between wubi and this install should I be worried or not?

---

### Post by bcbc on 2011-03-12
> **boroborolama said:**
> Output of [FONT=Courier New]fdisk -l[/FONT]:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd64e292

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1146     9203712   27  Unknown
/dev/sda2   *        1146        1159      102400    7  HPFS/NTFS
/dev/sda3            1159       38914   303263064    7  HPFS/NTFS

```
Split /dev/sda3 and create an extended partition (/dev/sda4) in the free space. Within that you can create the logical partitions you need. You cannot split it while booting your wubi install, but you should be able to do it from Windows. Once it's split you can install GParted on the Wubi install and create the ext4 and swap partitions from there.

Partitioning carries a small risk - so make sure your backups are current beforehand.

---

### Post by bcbc on 2011-03-12
> **daUnion said:**
> I just did this migrating a 10.10 install and on boot it says failed to load /lib/modules/2.6.35-25-generic/modules.dep then it boots into the graphical interface and I don't notice any differences(all drivers that should be loaded are loaded) between wubi and this install should I be worried or not?
That sounds like this bug [https://bugs.launchpad.net/linux/+bug/642421](https://bugs.launchpad.net/linux/+bug/642421)
I had a quick read and it doesn't seem very clear what is causing it except for the fact that it appears harmless - and difficult to solve.

My advice is to rerun the migration if you haven't changed much - or if you find a solution in the bug report you can try that (no harm in trying and then rerunning the migration either). I'll look into it further and see if I can find more information - and maybe a way to prevent this from happening in the future (with the migration).

Thanks for the feedback!

---

### Post by bcbc on 2011-03-12
> **daUnion said:**
> I just did this migrating a 10.10 install and on boot it says failed to load /lib/modules/2.6.35-25-generic/modules.dep then it boots into the graphical interface and I don't notice any differences(all drivers that should be loaded are loaded) between wubi and this install should I be worried or not?

Okay I read that [bug report]("https://bugs.launchpad.net/linux/+bug/642421") in detail and two things seem to be clear. 1) it's a cosmetic issue and 2) it's fixed with the latest maverick kernel updates. So if you are running 2.6.35-25 try updating to the latest kernel and it should be resolved.

It also seems to be rather random who is affected (even some Wubi users apparently), so while migrating the Wubi again may result in a 'fix' it's probably totally unnecessary to do this. Instead simply update your kernel.

Hope that helps.

---

### Post by boroborolama on 2011-03-13
> **bcbc said:**
> Split /dev/sda3 and create an extended partition (/dev/sda4) in the free space. Within that you can create the logical partitions you need. You cannot split it while booting your wubi install, but you should be able to do it from Windows. Once it's split you can install GParted on the Wubi install and create the ext4 and swap partitions from there.

Partitioning carries a small risk - so make sure your backups are current beforehand.

So, I split [FONT=Courier New]/dev/sda3[/FONT] from Windows 7 using Disk Management, and then I created the extended partition [FONT=Courier New]/dev/sda4[/FONT], per your instructions.  Then, from Ubuntu 10.04 using Gparted, I created the ext4 and linux-swap partitions from that (they became [FONT=Courier New]/sda5[/FONT] and [FONT=Courier New]/sda6[/FONT], resp.)

At some point I had to reboot, and now Ubuntu won't boot.  I have this error:  [http://ubuntuforums.org/showthread.php?t=1474253](http://ubuntuforums.org/showthread.php?t=1474253)

I'm writing from Windows.  I'm thinking about throwing this all away and doing a fresh install of Ubuntu from USB stick (I have 10.10 Maverick already, but I'm thinking that I may make a 10.04 LTS Lucid install since I can always upgrade later).

Here are my questions:

1.  I have a backup of my home directory on an external hard drive, but that's it.  I orginally made an enormous tarball out of the linux root directory (with a few exceptions like /proc, etc.) but it accidentally also included ALL of WINDOWS since that is hiding in the filesystem on account of wubi.  Ahhh!).  *What do I lose by doing a fresh install and just copying back my home directory?*  (Things that come to mind:  email contacts in Evolution, old emails, extra software from the repositories)

2.  *Can I keep Windows 7 but create a dual boot in grub?*

3.  *Should I try to follow your instructions anyway.  How?*

I realize that this has gotten slightly off-topic, but you have been very helpful [FONT=Arial Black]bcbc[/FONT], so maybe you can offer some advice.

---

### Post by bcbc on 2011-03-13
If I understand correctly you have the wubi/grub problem (and that is unrelated to your partitioning.) This is a common problem, although it's unclear what you might have done to trigger it from what you described (e.g. updating a kernel could trigger it).

So I wouldn't throw in the towel just yet. There is a well documented fix in the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"): Problem #2, Solution #1, and then the Permanent Fix once it's booting. Then migrate after that. You could also migrate using the --root-disk= option since this is wubi-related and doesn't affect a migrated Ubuntu. But I think it's cleaner to first confirm and resolve the problem.

---

### Post by boroborolama on 2011-03-13
> **bcbc said:**
> If I understand correctly you have the wubi/grub problem (and that is unrelated to your partitioning.) This is a common problem, although it's unclear what you might have done to trigger it from what you described (e.g. updating a kernel could trigger it).

So I wouldn't throw in the towel just yet. There is a well documented fix in the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"): Problem #2, Solution #1, and then the Permanent Fix once it's booting. Then migrate after that. You could also migrate using the --root-disk= option since this is wubi-related and doesn't affect a migrated Ubuntu. But I think it's cleaner to first confirm and resolve the problem.

Thank you **so much**.

I've resolved the grub boot issue (which probably had to do with upgrading to the [FONT=Courier New]2.6.32-29-generic[/FONT] kernel--I actually usually boot into [FONT=Courier New]2.6.32-28[/FONT] kernel because of compatibility issues for [FONT=Courier New]alsa[/FONT]).  And, now, I've migrated away from the wubi install.  I feel liberated!

Can I go and shrink the original Windows partition now and reclaim that space with my new linux partition or should I have done that before?
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1146     9203712   27  Unknown
/dev/sda2   *        1146        1159      102400    7  HPFS/NTFS
/dev/sda3            1159       21816   165927256    7  HPFS/NTFS
/dev/sda4           21816       38914   137335808    5  Extended
/dev/sda5           21816       38276   132215874   83  Linux
/dev/sda6           38277       38913     5116671   82  Linux swap / Solaris
```Thanks again, **bcbc**.

---

### Post by bcbc on 2011-03-13
> **boroborolama said:**
> Thank you **so much**.

I've resolved the grub boot issue (which probably had to do with upgrading to the [FONT=Courier New]2.6.32-29-generic[/FONT] kernel--I actually usually boot into [FONT=Courier New]2.6.32-28[/FONT] kernel because of compatibility issues for [FONT=Courier New]alsa[/FONT]).  And, now, I've migrated away from the wubi install.  I feel liberated!

Can I go and shrink the original Windows partition now and reclaim that space with my new linux partition or should I have done that before?
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1146     9203712   27  Unknown
/dev/sda2   *        1146        1159      102400    7  HPFS/NTFS
/dev/sda3            1159       21816   165927256    7  HPFS/NTFS
/dev/sda4           21816       38914   137335808    5  Extended
/dev/sda5           21816       38276   132215874   83  Linux
/dev/sda6           38277       38913     5116671   82  Linux swap / Solaris
```Thanks again, **bcbc**.
Great, you're welcome!

Regarding resizing the windows partition now - if you split /dev/sda3 you'd have to first resize the extended partition /dev/sda4 to absorb that free space before you could use it. And expanding /dev/sda5 after that may be time consuming. 

I'm not sure what the best approach would be for this... I tend to move my Ubuntu installs around between my internal drive and an external drive when I do things like that (the 2.0 script handles normal migrations as well), but I see others have used Gparted to do it with the install in place.
Whatever method you use, make sure your backups are current.

---

### Post by faz. on 2011-03-14
OK I am a fairly new user to Linux.

I have a 16gb drive. There is XP Pro on it, and Ubuntu 10.10. The Ubuntu is a Wubi installation from Windows. 

I want to completely remove Windows, to save space, and have Ubuntu as the only operating system.

How would I go about doing this?

I downloaded the wubi-move-2.0.sh, placed it on the desktop and tried to just run the help file, but I got "no such file or directory". I am obviously an idiot, someone help me out??

If it's a lot of work I won't risk it, I don't fancy installing Linux all over again.

Thanks

---

### Post by bcbc on 2011-03-14
> **faz. said:**
> OK I am a fairly new user to Linux.

I have a 16gb drive. There is XP Pro on it, and Ubuntu 10.10. The Ubuntu is a Wubi installation from Windows. 

I want to completely remove Windows, to save space, and have Ubuntu as the only operating system.

How would I go about doing this?

I downloaded the wubi-move-2.0.sh, placed it on the desktop and tried to just run the help file, but I got "no such file or directory". I am obviously an idiot, someone help me out??

If it's a lot of work I won't risk it, I don't fancy installing Linux all over again.

Thanks
There's no way to migrate a wubi onto it's host i.e. to migrate over the current partition where it is installed. It is possible to copy the root.disk to an external drive, then boot a live CD and convert from that root.disk but that only works if 
(a) you only have a single virtual disk i.e. you haven't created a separate home.disk or usr.disk, and 
(b) you don't have your /boot partition on the windows host i.e. wubi with grub legacy - originally installed on 9.04 or earlier.

On top of this, I don't recommend this for general use because the script won't migrate to a partition that contains data, and so you have to wipe your windows + existing wubi beforehand.

My personal recommendation is to create a separate target partition either on the internal hard drive or another drive, and then migrate to that. Confirm that it's working. At that point you can migrate the install back again over Windows.
In your case, having only 16GB (that seems way too small for XP plus Wubi) - you don't have much option for partitioning the internal drive.

---

### Post by faz. on 2011-03-14
That's the thing, it is way too small!! Hence the literally now, 100mb space left!! Though it is odd how it says I have 4gb left... Anyway, I have an SD card slot, can easily put another 16gb into that cheaply. Maybe you could point me in the direction of somehow moving my "home" folder to the SD card, as opposed to the main drive?

I will leave it be for now.

Is there any way I can modify the boot order so Ubuntu appears on top, saves me having to press "down" :D :D

Thanks for your good information

---

### Post by bcbc on 2011-03-15
> **faz. said:**
> That's the thing, it is way too small!! Hence the literally now, 100mb space left!! Though it is odd how it says I have 4gb left... Anyway, I have an SD card slot, can easily put another 16gb into that cheaply. Maybe you could point me in the direction of somehow moving my "home" folder to the SD card, as opposed to the main drive?

I will leave it be for now.

Is there any way I can modify the boot order so Ubuntu appears on top, saves me having to press "down" :D :D

Thanks for your good information
I wouldn't recommend you put /home on an SD card.

Right-click on My Computer, Properties, Advanced tab, Startup & Recovery, change the Default Operating System to Ubuntu. Do NOT set the timeout lower - if you set it to zero Windows will not boot anymore.

---

### Post by faz. on 2011-03-15
Ok, what I did was this:

****** the whole idea, put Ubuntu netbook on a flash drive, and am reinstalling now!

MUCH BETTER :)

no doubt I will have problems though :P

---

### Post by geiroffenberg on 2011-03-20
Automated script worked beautifully! I'm a total newbie to linux, so im very thankful.

Big thanks to bcbc for being awsome. never seen a better help guy anywhere.

BTW, just in case someone runs into the same problem.
Before running the migration script, i had to shrink my win xp partition. NONE of the win tools worked, easeus didnt even find the partition. i dont know why and now i dont care, lol. Finally i did the whole shrink, create extended, create logical, create swap, in one swoop in gparted live from a usb stick. Everything worked out great from then on, no problems whatsoever. (i think it is necesary to boot into windows one time right after shrinking, it will run some automated updating stuff)
:guitar:

---

### Post by bcbc on 2011-03-20
> **geiroffenberg said:**
> Automated script worked beautifully! I'm a total newbie to linux, so im very thankful.

Big thanks to bcbc for being awsome. never seen a better help guy anywhere.

BTW, just in case someone runs into the same problem.
Before running the migration script, i had to shrink my win xp partition. NONE of the win tools worked, easeus didnt even find the partition. i dont know why and now i dont care, lol. Finally i did the whole shrink, create extended, create logical, create swap, in one swoop in gparted live from a usb stick. Everything worked out great from then on, no problems whatsoever. (i think it is necesary to boot into windows one time right after shrinking, it will run some automated updating stuff)
:guitar:
Great :) Thanks for the feedback and the compliment!

---

### Post by Wallace Duffy on 2011-03-28
Hi bcbc, all,

First I admit that I am relatively new to Ubuntu/Linux...

I must also be honest and tell you I've been having a hard time with this. I consider myself fairly intelligent but I've been reading/studying/trying to do this Wubi migration for 3 days straight now.

I'm feeling dumb now!

I really want Ubuntu (the Wubi install is out of space and keeps popping up errors even though I've dumped all of the superfluous stuff) so I've been tempted to just install fresh and start over again... but I really would like to keep all the work I've done on there so I thought I'd give posting here a shot.

Presently I have Wubi in Windows 7... I already had four partitions on my C:/ drive from the factory so I deleted the 'HP Tools' partition. Then I created and formatted a new (primary) partition in the third slot on C:/.

(BTW, does this mean that my new partion is designated 'SD3' or 'SD[COLOR=Red]**A**[/COLOR]3'? In other words is the first drive; the C:/ drive designated 'SD' or does this system just start with SDA?)

Anyhow, some more basic instruction here would have been nice.

I still have not been able to run the automated script (AFAIK)... Apparently I need insructions that a chimp could decipher!

I personally would appreciate literal step-by step instruction on how to run this thing. I've been using Ubuntu exclusively for a while now and I've been able to do everything I put my mind to except for this, and it's driving me nuts!

After finally figuring out that I had to open a terminal to run an '.sh' script, here's what I came up with (I'll just post everything that was in the terminal at the time)...

A screenshot:

[IMG]http://christconquers.files.wordpress.com/2011/03/screenshot.png[/IMG]

So what does that mean? How is it that the partition I made is not a 'valid' one? Does it have to be set as 'Active' or something?

I will really, really appreciate any help that you (or anyone here for that matter) may be so generous as to offer...

EDIT: I also should have noted that I cannot seem to access the 'Help' or 'Notes' which I was supposed to be able to access by entering:

```
bash wubi-move-2.0.sh --help
bash wubi-move-2.0.sh --notes
```

Lastly, I just noticed that though I had fully formatted the new partition meant for Ubuntu... it now contains a folder called '$RECYCLE.BIN'.

Inside that folder is another folder called 'S-1-5-21-3880768036-1885516967-3323286761-1001' which itself contains a single file entitled 'desktop.ini'.

That file contains:

```
[.ShellClassInfo]
CLSID={645FF040-5081-101B-9F08-00AA002F954E}
LocalizedResourceName=@%SystemRoot%\system32\shell32.dll,-8964

```

What is all this?

Thanks,

---

### Post by bcbc on 2011-03-28
Wally,

Assuming the partition you created is /dev/sda3, you would enter:
sudo bash wubi-move.sh /dev/sda3

Ideally you would also create a swap partition. So where you created a primary partition, you'd replace that with an extended partition, and then create two logical partitions within that. It's not strictly necessary though - you can use a swap file instead.

I'll take a look if you give me the output of:
```
sudo fdisk -l   (lower case -L)
```
and
```
sudo blkid
```
and
```
df -h
```

EDIT: just noticed your edits. You downloaded the older wubi-move.sh script. That still works fine, but the instructions refer to the newer script wubi-move-2.0.sh. So it's better to download that script. Then those commands will work.

---

### Post by Wallace Duffy on 2011-03-29
Ah bcbc, 

Thank you for the quick reply!

When I first created the partition it was a 'Dynamic' drive and I changed it to 'Primary'... Is 'Dynamic' the same as 'Extended'? Should I change it back to 'Dynamic' then?

And are you saying then that Ubuntu requires **two** drives?

I appreciate your offer to take a look and I will gladly accept.

Here are the three respective outputs in the same order as your post presents them:

```


wally@ubuntu:~$ sudo fdisk -l 
[sudo] password for wally: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8ae1e4ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       34533   277178368    7  HPFS/NTFS
/dev/sda3           34533       37083    20480000    7  HPFS/NTFS
/dev/sda4           37083       38914    14704640    7  HPFS/NTFS

Disk /dev/sdb: 1499.6 GB, 1499598946304 bytes
255 heads, 63 sectors/track, 182315 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000389f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182316  1464451072    7  HPFS/NTFS
wally@ubuntu:~$ 


``````


wally@ubuntu:~$ sudo blkid
[sudo] password for wally: 
/dev/loop0: UUID="400d6f0f-e15b-46ba-ba96-1575941f0561" TYPE="ext4" 
/dev/sda1: LABEL="SYSTEM" UUID="E0EE6700EE66CDFA" TYPE="ntfs" 
/dev/sda2: UUID="E4B20950B209291E" TYPE="ntfs" 
/dev/sda3: LABEL="Ubuntu" UUID="F2D2E657D2E62019" TYPE="ntfs" 
/dev/sda4: LABEL="RECOVERY" UUID="E24A56994A566A75" TYPE="ntfs" 
/dev/sdb1: LABEL="My Book" UUID="486E622C6E62134C" TYPE="ntfs" 
wally@ubuntu:~$ 


``````


wally@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   15G  1.2G  93% /
none                  1.4G  296K  1.4G   1% /dev
none                  1.4G  432K  1.4G   1% /dev/shm
none                  1.4G  400K  1.4G   1% /var/run
none                  1.4G     0  1.4G   0% /var/lock
/dev/sda2             265G  103G  162G  39% /host
/dev/sdb1             1.4T  726G  671G  52% /media/My Book
/dev/sda3              20G   87M   20G   1% /media/Ubuntu
wally@ubuntu:~$ 


```

By the way... do you have any idea where that $RECYCLE.BIN folder on my new partition came from?

Again - I probably can't thank you enough... but I can try!

---

### Post by bcbc on 2011-03-29
> **Wallace Duffy said:**
> Ah bcbc, 

Thank you for the quick reply!

When I first created the partition it was a 'Dynamic' drive and I changed it to 'Primary'... Is 'Dynamic' the same as 'Extended'? Should I change it back to 'Dynamic' then?

And are you saying then that Ubuntu requires **two** drives?

I appreciate your offer to take a look and I will gladly accept.


Yes you want to avoid dynamic drives. They're a windows construct and the partitions aren't always in the MBR partition table in which case they are undetectable to Ubuntu. 
Extended is not the same as dynamic - the extended partition gives you the option to create additional logical partitions (to get around the limit of max 4 primary partitions).

I'd normally recommend you create two logical partitions, however you have a Wubi install using 15GB and you're migrating to a partition of about 19 or so GB so that doesn't leave a lot of room if you create a swap partition.

You do have 162GB free on your windows partition, so technically you could delete /dev/sda3, shrink /dev/sda2 (use windows to do it) and create a larger extended /dev/sda3 partition in that space.

I tried to avoid getting into partitioning advice in this thread ;) but that's probably the best long-term approach.

If you just want to stick with the single partition - go for it - but you might be looking for more space soon.

---

### Post by Zanderist on 2011-03-29
I've been looking and I don't think anyone asked this or at least in a way I could of related to.

How am I partitioning this? 

Do I set it up as in this guide,

[http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/](http://www.linuxbsdos.com/2011/01/28/dual-booting-windows-7-and-ubuntu-10-10/)

Where I create a partition for (I have 500gigs):

> Windows (480 gigs - 200 gigs)
20 gig recovery partition 
/boot ~ 500mb
/~ equal to wubi, 30 gigs
/home ~ the rest all here
swap space~ equal to ram 4 gigs

(4 partitions total)

Then migrate wubi to the '/' partition? With the root parition of course being greater than or equal to the size of the wubi partition.

Or do I make a single partition, and migrate it.

I'm going to be doing this from a liveUSB, from which I already tried the script which the terminal flashed on and off the screen rapidly. This wasn't the case when I had to use the bootscript a while back.

---

### Post by bcbc on 2011-03-29
Zanderist,

If you're using Windows vista/7, then I recommend using it's disk manager to shrink the windows partition and then create an extended partition in the space using Gparted. Make sure you don't let windows create dynamic partitions.

The script has to be run from the terminal (CTRL+ALT+t). I suppose it would be nice to popup a window and get input that way, but it's not there yet. So it's a command line tool. You can make it executable but it's not necessary if you run it according to the instructions in post #1.

Also, it only supports migration to a single target partition. I've considered supporting multiple targets, but the error checking and validation gets more intricate and probably the confusion factor in running it. If you'd like a separate /home you could always customize the manual migration instructions or move /home after migrating.

Personally I stopped using a separate /home. I just keep backups.

---

### Post by Wallace Duffy on 2011-03-29
Hi again bcbc,

I still haven't completed the migration... but I'm getting closer!

I had just used Windows to shrink SDA2 to make more room... It showed that I had over 180 GB of unused space so I thought shrinking it would give me lots of room but apparently Windows wants most of that space for itself because it only freed up approx 30 GB. I never realized that the Ubuntu/Wubi package was taking that much space either.

Now I'm using an aftermarket program (Perfect Disk) to rearrange things on SDA2 so I can dedicate more like 80 GBs to Ubuntu. Then all I have to do is create and format an 'Extended' drive containing two 'Virtual' drives and run your script... Right?

I think I'm set now (thanks solely to your help) but I just thought I'd make sure since you're so amicable. A lot of computer folks seem to hold on to and jealously guard their knowledge like it was their 'Precious'!

I apologize for taking this thread a little off topic but if I've run into these issues -chances are others have and will in the future so this may still be helpful and actually very relevant to the process of pulling off this migration.

Thanks again... Best wishes to you from the Island!

---

### Post by Zanderist on 2011-03-29
So I've gotten the script working, and I made that extended partition like you said.

I'm trying the root.disk from a liveCD option and now am being told that the target to the disk is not found.

I think I'll try instead booting into my wubi-ubuntu and doing the second option you had for the automated script

I'm now getting this, after giving up on the second option and opting for the first.
```

@ubuntu:~$ sudo bash wubi-move-2.0.sh /dev/sda4 

wubi-move-2.0.sh: Partition /dev/sda4 could not be mounted for validation.
wubi-move-2.0.sh: This is normal if the partition is unformatted or the file
wubi-move-2.0.sh: system is corrupted. It could also mean you have entered
wubi-move-2.0.sh: the wrong partition. The partition will have to be formatted
wubi-move-2.0.sh: in order to complete validation.
wubi-move-2.0.sh: PLEASE MAKE SURE YOU HAVE SELECTED THE CORRECT PARTITION.
wubi-move-2.0.sh: Please close all open files before continuing.
wubi-move-2.0.sh: About to format the target partition (/dev/sda4).
wubi-move-2.0.sh: Proceed with format (Y/N)
Y
wubi-move-2.0.sh: Formatting /dev/sda4 with ext4 file system
wubi-move-2.0.sh: Formatting /dev/sda4 failed or was canceled
wubi-move-2.0.sh: Migration request canceled

```

---

### Post by bcbc on 2011-03-29
> **Wallace Duffy said:**
> Hi again bcbc,

I still haven't completed the migration... but I'm getting closer!

I had just used Windows to shrink SDA2 to make more room... It showed that I had over 180 GB of unused space so I thought shrinking it would give me lots of room but apparently Windows wants most of that space for itself because it only freed up approx 30 GB. I never realized that the Ubuntu/Wubi package was taking that much space either.

Now I'm using an aftermarket program (Perfect Disk) to rearrange things on SDA2 so I can dedicate more like 80 GBs to Ubuntu. Then all I have to do is create and format an 'Extended' drive containing two 'Virtual' drives and run your script... Right?

I think I'm set now (thanks solely to your help) but I just thought I'd make sure since you're so amicable. A lot of computer folks seem to hold on to and jealously guard their knowledge like it was their 'Precious'!

I apologize for taking this thread a little off topic but if I've run into these issues -chances are others have and will in the future so this may still be helpful and actually very relevant to the process of pulling off this migration.

Thanks again... Best wishes to you from the Island!
Yes, create an extended partition with two logical partitions within it. Make the one for root ext4 (type '83 - linux') and the other '82 - swap'. The swap should be > size of RAM in order to support hibernation. Personally I'd go RAM + 1GB, but the overflow amount differs between releases and memory usage (and there's no clear guide I've found). 

Regarding sharing knowledge - that seems to be the Ubuntu way, and I'm more than comfortable with it as I learned that way as well. And you're right that others will likely encounter the same questions that you have.

---

### Post by bcbc on 2011-03-29
> **Zanderist said:**
> So I've gotten the script working, and I made that extended partition like you said.

I'm trying the root.disk from a liveCD option and now am being told that the target to the disk is not found.

I think I'll try instead booting into my wubi-ubuntu and doing the second option you had for the automated script

I'm now getting this, after giving up on the second option and opting for the first.
```

@ubuntu:~$ sudo bash wubi-move-2.0.sh /dev/sda4 

wubi-move-2.0.sh: Partition /dev/sda4 could not be mounted for validation.
wubi-move-2.0.sh: This is normal if the partition is unformatted or the file
wubi-move-2.0.sh: system is corrupted. It could also mean you have entered
wubi-move-2.0.sh: the wrong partition. The partition will have to be formatted
wubi-move-2.0.sh: in order to complete validation.
wubi-move-2.0.sh: PLEASE MAKE SURE YOU HAVE SELECTED THE CORRECT PARTITION.
wubi-move-2.0.sh: Please close all open files before continuing.
wubi-move-2.0.sh: About to format the target partition (/dev/sda4).
wubi-move-2.0.sh: Proceed with format (Y/N)
Y
wubi-move-2.0.sh: Formatting /dev/sda4 with ext4 file system
wubi-move-2.0.sh: Formatting /dev/sda4 failed or was canceled
wubi-move-2.0.sh: Migration request canceled

```

Are you sure that /dev/sda4 isn't your extended partition? That's the reason I added that warning in there (and that's one of the known reasons that the format will fail).

Please output the results of:
sudo fdisk -l  (lower case -L)
sudo blkid

Also indicate which partition you are migrating to.
Thanks

---

### Post by Zanderist on 2011-03-29
> **bcbc said:**
> Yes, create an extended partition with two logical partitions within it. Make the one for root ext4 (type '83 - linux') and the other '82 - swap'. The swap should be > size of RAM in order to support hibernation. Personally I'd go RAM + 1GB, but the overflow amount differs between releases and memory usage (and there's no clear guide I've found). 

I think this also applies to me.

---

### Post by Zanderist on 2011-03-29
> **bcbc said:**
> Are you sure that /dev/sda4 isn't your extended partition? That's the reason I added that warning in there (and that's one of the known reasons that the format will fail).

Please output the results of:
sudo fdisk -l  (lower case -L)
sudo blkid

Also indicate which partition you are migrating to.
Thanks
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85f81c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       31696   254389912    7  HPFS/NTFS
/dev/sda3           58050       60802    22102016    7  HPFS/NTFS
/dev/sda4           31696       58050   211687424    5  Extended
/dev/sda5           31696       32239     4358144   82  Linux swap / Solaris
/dev/sda6           32239       58050   207327232   83  Linux

Partition table entries are not in disk order

```
```

/dev/loop0: UUID="e93b84b6-e974-485d-93f0-a3fd1c5447eb" TYPE="ext4" 
/dev/sda1: LABEL="SYSTEM" UUID="18C23628C2360B10" TYPE="ntfs" 
/dev/sda2: UUID="A0DA36C3DA36960E" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="6C5A52095A51D106" TYPE="ntfs" 
/dev/sda5: LABEL="swap" UUID="b5d34696-9ebd-47ca-8341-fae710d20e45" TYPE="swap" 
/dev/sda6: UUID="80bdc25b-5e20-49e1-a223-654217a89ab9" TYPE="ext4" 

```

Is that loop0 in that last one wubi?

---

### Post by bcbc on 2011-03-29
> **Zanderist said:**
> ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85f81c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       31696   254389912    7  HPFS/NTFS
/dev/sda3           58050       60802    22102016    7  HPFS/NTFS
/dev/sda4           31696       58050   211687424    5  Extended
/dev/sda5           31696       32239     4358144   82  Linux swap / Solaris
/dev/sda6           32239       58050   207327232   83  Linux

Partition table entries are not in disk order

```
```

/dev/loop0: UUID="e93b84b6-e974-485d-93f0-a3fd1c5447eb" TYPE="ext4" 
/dev/sda1: LABEL="SYSTEM" UUID="18C23628C2360B10" TYPE="ntfs" 
/dev/sda2: UUID="A0DA36C3DA36960E" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="6C5A52095A51D106" TYPE="ntfs" 
/dev/sda5: LABEL="swap" UUID="b5d34696-9ebd-47ca-8341-fae710d20e45" TYPE="swap" 
/dev/sda6: UUID="80bdc25b-5e20-49e1-a223-654217a89ab9" TYPE="ext4" 

```

Is that loop0 in that last one wubi?
Yes /dev/loop0 is wubi.

Ok so since your target is /dev/sda6 and swap is /dev/sda5 you'd use:
```
sudo bash wubi-move-2.0.sh /dev/sda6 /dev/sda5
```

I assume your BIOS is ok reading beyond 137GB as it will need to do this to load the grub boot files.

---

### Post by Zanderist on 2011-03-29
Well it worked but windows 7 no longer boots, and it looks like a familiar foe.

0xc000000f  <--something like this, boot loader.


I've also figure out that the vista loader on my laptop is actually the recovery partition's loader.

What should I do to correct this?

I'm already thinking about doing what I had to do before for this, first link in signature.

---

### Post by bcbc on 2011-03-29
> **Zanderist said:**
> Well it worked but windows 7 no longer boots, and it looks like a familiar foe.

0xc000000f  <--something like this, boot loader.


I've also figure out that the vista loader on my laptop is actually the recovery partition's loader.

What should I do to correct this?

I'm already thinking about doing what I had to do before for this, first link in signature.

Grub doesn't differentiate well between vista/7 recovery and main partitions. You need to look at which one partition has the boot flag set and use that one. Then you can customize the name if you like using this guide [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Zanderist on 2011-03-29
> **bcbc said:**
> Grub doesn't differentiate well between vista/7 recovery and main partitions. You need to look at which one partition has the boot flag set and use that one. Then you can customize the name if you like using this guide [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
EDIT:
OUTSTANDING!

I downloaded the app, the 'grub2' customizer, and saw that there was two windows 7 loaders, only on different partitions. I believe that was what was screwing it up, I'm now posting this within windows 7.

I am now preparing a no man's land for media (music/pictures).

---

### Post by bcbc on 2011-03-29
> **Zanderist said:**
> EDIT:
OUTSTANDING!

I downloaded the app, the 'grub2' customizer, and saw that there was two windows 7 loaders, only on different partitions. I believe that was what was screwing it up, I'm now posting this within windows 7.

I am now preparing a no man's land for media (music/pictures).
Great. Glad you got it sorted out.

---

### Post by Zanderist on 2011-03-29
> **bcbc said:**
> Great. Glad you got it sorted out.
Yeah thanks, I now have the issue of only being allowed 4 primary partitions. That's for another thread though.

---

### Post by bcbc on 2011-03-29
> **Zanderist said:**
> Yeah thanks, I now have the issue of only being allowed 4 primary partitions. That's for another thread though.

Just split /dev/sda6 using Gparted (you'd have to boot the wubi install or a live CD to do it - as you can't do it while it's mounted). But there is plenty of space there. You can't add another primary partition, but you can add as many more logical partitions as you need.

---

### Post by Wallace Duffy on 2011-03-30
Yay!

Mission accomplished! I'm typing from SDA5 as we speak... Everything seems to have worked perfectly.

You have my most sincere gratitude bcbc...

You are the man!

[IMG]http://christconquers.files.wordpress.com/2011/03/beanface.jpg[/IMG]

BTW, that's not you in there is it?

[COLOR=Green]&#8224;[/COLOR][FONT=Tahoma, serif][COLOR=Green][SIZE=2][B]IC XC&#8224;
[/B][/SIZE][/COLOR][/FONT]  [COLOR=Green]&#8224;[/COLOR][FONT=Tahoma, serif][COLOR=Green][SIZE=2][B]NI KA&#8224;

[/B][/SIZE][/COLOR][/FONT]

---

### Post by bcbc on 2011-03-30
> **Wallace Duffy said:**
> Yay!

Mission accomplished! I'm typing from SDA5 as we speak... Everything seems to have worked perfectly.

You have my most sincere gratitude bcbc...

You are the man!


Great to hear!
> **Wallace Duffy said:**
> 
BTW, that's not you in there is it?


Nah - I have more hair... although it does resemble the SABDFL.

---

### Post by SimpleWater on 2011-04-13
bcbc i think you broke my ubuntu. it no longer boots up :( 

I did step 1
1a
2 with /dev/sda1 instead of 5 because i think the empty partition was with 1
3 (took a while)
Skipped 4 because i have no clue what /dev/sda6 is
5 i think it worked although terminal said something about "-i" being invalid or something like that, also skipped echo....with "/dev/sda6"
6
7

So after, i closed terminal, then did a reboot. Everything looks like usuall with windows xp menu, so i chose ubuntu and nothing. Only thing that showed was "Try (Hd0,0): EXT2" at top-left corner of the screen. And will not boot of course

Before it went like this. menu boots. I choose ubuntu. then second menu shows. second menu has some other ubuntu things and windows xp at the bottom. so i choose first ubuntu on the list.

I have no idea what i am doing :confused: Can you help?

(windows xp still works though)

---

### Post by bcbc on 2011-04-13
> **SimpleWater said:**
> bcbc i think you broke my ubuntu. it no longer boots up :( 

I did step 1
1a
2 with /dev/sda1 instead of 5 because i think the empty partition was with 1
3 (took a while)
Skipped 4 because i have no clue what /dev/sda6 is
5 i think it worked although terminal said something about "-i" being invalid or something like that, also skipped echo....with "/dev/sda6"
6
7

So after, i closed terminal, then did a reboot. Everything looks like usuall with windows xp menu, so i chose ubuntu and nothing. Only thing that showed was "Try (Hd0,0): EXT2" at top-left corner of the screen. And will not boot of course

Before it went like this. menu boots. I choose ubuntu. then second menu shows. second menu has some other ubuntu things and windows xp at the bottom. so i choose first ubuntu on the list.

I have no idea what i am doing :confused: Can you help?

(windows xp still works though)
No... it should be OK :)

Yours isn't a typical setup. There is a problem with wubildr.mbr (grub4dos) that I became aware of recently - it gets stuck on ext4 file systems. That's because the version of grub4dos Wubi uses is from 2007 - before ext4. 

Usually if you migrate you're migrating to a higher partition than your windows partition (so wubildr.mbr can find wubildr before encountering the ext4 partition) OR you're installing the grub2 bootloader. In your case, you didn't install the grub2 bootloader so wubi is trying to boot and getting hung up on /dev/sda1.

Fix... there are two options
1. Boot a live CD and install the grub2 bootloader
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Or (if you really don't want grub2 bootloader in place)
2. Format /dev/sda1 to ntfs (then you'll be able to boot into your wubi again). Then migrate again but this time format /dev/sda1 as ext3.

I'll update the known issues to address this for other people.

If you are not sure, post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

---

### Post by SimpleWater on 2011-04-13
> **bcbc said:**
> No... it should be OK :)

Yours isn't a typical setup. There is a problem with wubildr.mbr (grub4dos) that I became aware of recently - it gets stuck on ext4 file systems. That's because the version of grub4dos Wubi uses is from 2007 - before ext4. 

Usually if you migrate you're migrating to a higher partition than your windows partition (so wubildr.mbr can find wubildr before encountering the ext4 partition) OR you're installing the grub2 bootloader. In your case, you didn't install the grub2 bootloader so wubi is trying to boot and getting hung up on /dev/sda1.

Fix... there are two options
1. Boot a live CD and install the grub2 bootloader
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Or (if you really don't want grub2 bootloader in place)
2. Format /dev/sda1 to ntfs (then you'll be able to boot into your wubi again). Then migrate again but this time format /dev/sda1 as ext3.

I'll update the known issues to address this for other people.

If you are not sure, post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")

ok so option 2 looks simple. but just to be clear, it has been formatted to ntfs from the beginning and still currently is. Do you want me to reformat to its current state? then try to boot ubuntu and after format to ext3? then restart migrate?

sorry if i'm being slow. but bootininfoscript only works for linux i think

---

### Post by bcbc on 2011-04-13
> **SimpleWater said:**
> ok so option 2 looks simple. but just to be clear, it has been formatted to ntfs from the beginning and still currently is. Do you want me to reformat to its current state? then try to boot ubuntu and after format to ext3? then restart migrate?

sorry if i'm being slow. but bootininfoscript only works for linux i think

You said you migrated to /dev/sda1 i.e. you formatted it as ext4? I'm going based on what you told me. Also this tells me that /dev/sda1 is not formatted as NTFS (in grub4dos terminology (hd0,0) is /dev/sda1): > Try (Hd0,0): EXT2

If you intend to use Ubuntu you should get an Ubuntu CD/USB you can boot from. You would use this to boot in live CD/USB mode (i.e. Try without installing) and then run the bootinfoscript from the live environment. Follow the instructions here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by SimpleWater on 2011-04-14
> **bcbc said:**
> You said you migrated to /dev/sda1 i.e. you formatted it as ext4? I'm going based on what you told me. Also this tells me that /dev/sda1 is not formatted as NTFS (in grub4dos terminology (hd0,0) is /dev/sda1): 

If you intend to use Ubuntu you should get an Ubuntu CD/USB you can boot from. You would use this to boot in live CD/USB mode (i.e. Try without installing) and then run the bootinfoscript from the live environment. Follow the instructions here: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

well i formatted to NTFS no difference also tried ext4 and same black screen with message. 

i dont have a cd drive and booting from usb did not work i tried it unetbootin and pendrive and switched to hard disk priority in bios, any suggestions?

Edit: which is the reason i used wubi to install instead of normal because i could not get that usb method to work

but if you know how to get the usb trick to work then that would be great also

---

### Post by bcbc on 2011-04-14
> **SimpleWater said:**
> well i formatted to NTFS no difference also tried ext4 and same black screen with message. 

i dont have a cd drive and booting from usb did not work i tried it unetbootin and pendrive and switched to hard disk priority in bios, any suggestions?

Edit: which is the reason i used wubi to install instead of normal because i could not get that usb method to work

but if you know how to get the usb trick to work then that would be great also

Please boot windows, right click on My computer, Manage, Disk Management, and take a screenshot. Then output:
dir c:\
and then
dir x:\  (where x: is the ntfs drive representing /dev/sda1)

We'll try and figure this out. Note also that there is a partition type as well as a file system type. It's possible that when you formatted /dev/sda1 to ext4 that you left the partition type as ntfs, so windows might be confused. In that case, ensure you've fully formatted and can access it to make sure there is no more ext4 file system present.

PS when I created an Ubuntu USB I just followed the instructions on [www.ubuntu.com/desktop/get-ubuntu/download](www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by SimpleWater on 2011-04-14
[IMG]http://i1195.photobucket.com/albums/aa400/SimpleWater/diskmangement.jpg[/IMG]



Ok here it is. note the drive is acting funky probably because of the format switch i would think. since it displays as unknown

the first command worked but the second "dir x:\" did not

---

### Post by bcbc on 2011-04-14
> **SimpleWater said:**
> 

Ok here it is. note the drive is acting funky probably because of the format switch i would think. since it displays as unknown

the first command worked but the second "dir x:\" did not
Do "dir D:\" instead.

---

### Post by SimpleWater on 2011-04-14
> **bcbc said:**
> Do "dir D:\" instead.

"The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted." 

should i go back to NTFS?

---

### Post by bcbc on 2011-04-14
> **SimpleWater said:**
> "The volume does not contain a recognized file system.
Please make sure that all required file system drivers are loaded and that the volume is not corrupted." 

should i go back to NTFS?
Go back to the Disk Management, right click on D: and select Format. That should return it to NTFS and then allow your Wubi to boot again.

---

### Post by SimpleWater on 2011-04-14
> **bcbc said:**
> Go back to the Disk Management, right click on D: and select Format. That should return it to NTFS and then allow your Wubi to boot again.

no i think you misunderstood me. I meant the linux dedicated partition should i be switching that back to NTFS? the pc recognizes it as unknown with ext3. Don't know if that is a concern.

Strangely enough D drive is unformatted which i'm certain is what formatted before but cant recall the original format.

switch both or just D drive?

Edit: it seams i cannot access the D drive while it is unformatted

---

### Post by bcbc on 2011-04-14
> **SimpleWater said:**
> no i think you misunderstood me. I meant the linux dedicated partition should i be switching that back to NTFS? the pc recognizes it as unknown with ext3. Don't know if that is a concern.

Strangely enough D drive is unformatted which i'm certain is what formatted before but cant recall the original format.

switch both or just D drive?

You said you migrated to /dev/sda1 - that's what Windows sees as D:

---

### Post by SimpleWater on 2011-04-14
> **bcbc said:**
> You said you migrated to /dev/sda1 - that's what Windows sees as D:

are you sure? on ubuntu's disk utility the 30g partition said it was /dev/sda1

so have I been doing it wrong the whole time?:confused:

---

### Post by bcbc on 2011-04-14
I'm trying to figure out how to do this on XP. There is a "diskpart" program.

```
C:\>[COLOR="Blue"]diskpart[/COLOR]

Microsoft DiskPart version 5.1.3565

Copyright (C) 1999-2003 Microsoft Corporation.
On computer: INSPIRON

DISKPART> [COLOR="blue"]list disk[/COLOR]

  Disk ###  Status      Size     Free     Dyn  Gpt
  --------  ----------  -------  -------  ---  ---
  Disk 0    Online        73 GB  2636 MB

DISKPART> [COLOR="blue"]select disk 0[/COLOR]

Disk 0 is now the selected disk.

DISKPART> [COLOR="blue"]list partition[/COLOR]

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    OEM                 47 MB    32 KB
  Partition 2    Primary             39 GB    47 MB
  Partition 3    Primary             20 GB    39 GB
  Partition 4    Extended            14 GB    59 GB
  Partition 5    Logical             10 GB    59 GB
  Partition 6    Logical           2048 MB    71 GB

DISKPART>[COLOR="blue"]exit[/COLOR]
```

I've shown you how I listed my partitions (commands in blue). Do the same on yours and post back.

---

### Post by SimpleWater on 2011-04-14
> **bcbc said:**
> I'm trying to figure out how to do this on XP. There is a "diskpart" program.

I've shown you how I listed my partitions (commands in blue). Do the same on yours and post back.

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Joel>diskpart

Microsoft DiskPart version 5.1.3565

Copyright (C) 1999-2003 Microsoft Corporation.
On computer: MICASA

DISKPART> list disk

  Disk ###  Status      Size     Free     Dyn  Gpt
  --------  ----------  -------  -------  ---  ---
  Disk 0    Online        75 GB      0 B

DISKPART> select disk 0

Disk 0 is now the selected disk.

DISKPART> list partition

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary           5146 MB    32 KB
  Partition 2    Primary             39 GB  5154 MB
  Partition 3    Unknown             31 GB    44 GB

DISKPART>
```

c:\>diskpart did not happen to work but just simply "diskpart" did

---

### Post by bcbc on 2011-04-14
>   Partition 1    Primary           5146 MB    32 KB
That's /dev/sda1 and it's 5GB == D:

---

### Post by SimpleWater on 2011-04-14
> **bcbc said:**
> That's /dev/sda1 and it's 5GB == D:

well thats just unfortunate isn't? so i guess that means that D: with all its contents is gone.

If i want to try this again should i uninstall ubuntu and reinstall with wubi and try again and repeat the steps that i did on this guide with /dev/sda1

also do you know what format D: was in before. And if want to do this on the 31GB partition is that /dev/sda3 and NTFS format and 4k cluster size? or is there anything i'm missing

---

### Post by bcbc on 2011-04-14
> **SimpleWater said:**
> well thats just unfortunate isn't? so i guess that means that D: with all its contents is gone.

If i want to try this again should i uninstall ubuntu and reinstall with wubi and try again and repeat the steps that i did on this guide with /dev/sda1

also do you know what format D: was in before. And if want to do this on the 31GB partition is that /dev/sda3 and NTFS format and 4k cluster size? or is there anything i'm missing

It is unfortunate. You know there is a warning about using the manual migration - the script won't allow you to format a non-empty partition and also checks the size of the partition (5GB is a hard minimum and most Wubi installs will be bigger than that). 

You do not need to uninstall Wubi Ubuntu and reinstall - it will delete your existing Wubi install which will likely boot normally as long as you clear out that ext4 file system from /dev/sda1. If you don't reformat /dev/sda1 then reinstalling Wubi won't boot for the same reason your current one is not booting.

I have no idea what is in /dev/sda3 (the 31GB partition) or what /dev/sda1 looked like prior to the format. 

This migration howto is provided to enable Wubi users to migrate to a partition install if they wish, and the script provides a lot of protection (I've also spent a lot of time testing it and making sure it's safe). But the job of partitioning is left up to the user, and when you choose to do the manual migration - you assume those risks.

I tried to be clear on the first post:
> *[COLOR="Red"]Please don't use the manual migration unless you fully understand what you are doing. The automated migration has many additional safeguards and will protect you from errors.[/COLOR]*...
> 
2. Format new partition if not done so already - make sure it's empty, large enough and unmounted
[COLOR="red"]WARNING[/COLOR] -- the next command will wipe all existing data on [COLOR="red"]/dev/sda5[/COLOR]
Code:
mkfs.ext4 /dev/sda5

I have been considering removing the manual migration instructions. I think the risk is too high versus the benefit (and curious people can just review the script).

---

### Post by SimpleWater on 2011-04-14
> **bcbc said:**
> It is unfortunate. You know there is a warning about using the manual migration - the script won't allow you to format a non-empty partition and also checks the size of the partition (5GB is a hard minimum and most Wubi installs will be bigger than that). 

You do not need to uninstall Wubi Ubuntu and reinstall - it will delete your existing Wubi install which will likely boot normally as long as you clear out that ext4 file system from /dev/sda1. If you don't reformat /dev/sda1 then reinstalling Wubi won't boot for the same reason your current one is not booting.

I have no idea what is in /dev/sda3 (the 31GB partition) or what /dev/sda1 looked like prior to the format. 

This migration howto is provided to enable Wubi users to migrate to a partition install if they wish, and the script provides a lot of protection (I've also spent a lot of time testing it and making sure it's safe). But the job of partitioning is left up to the user, and when you choose to do the manual migration - you assume those risks.

I tried to be clear on the first post:
...


I have been considering removing the manual migration instructions. I think the risk is too high versus the benefit (and curious people can just review the script).

Well i now see why people call linux too hard. I know about the warning, believe me i spent much time reassuring myself about each individual code but i guess that doesn't help if you know nothing about computing

I am going to try and get wubi install back to normall and i might stick it if i'm not feeling confident about the migration (probably tomorow). Thanks for your help you stuck with me for long hours :) much appreciated. 

i am going and try to see if i can learn a little about the terminal

Edit: 31GB is the empty partition which is purposely made for this

---

### Post by bcbc on 2011-04-14
> **SimpleWater said:**
> Well i now see why people call linux too hard. I know about the warning, believe me i spent much time reassuring myself about each individual code but i guess that doesn't help if you know nothing about computing

I am going to try and get wubi install back to normall and i might stick it if i'm not feeling confident about the migration (probably tomorow). Thanks for your help you stuck with me for long hours :) much appreciated. 

i am going and try to see if i can learn a little about the terminal
I am pretty sure that if you format D: as ntfs, your wubi will boot again. 

If I were you I'd just stick with Wubi. Unfortunately many people knock Wubi, but the fact is it is a safe way to learn Linux. And if you get Wubi booting, run the bootinfoscript and maybe it will show more information about /dev/sda3.

Anyway - I am truly sorry about your problems - and if you do end up migrating in the future, feel free to post here beforehand and we can check everything is good before going ahead.

---

### Post by idodialog on 2011-04-14
Many thanks, easy, quick effective!. To have no issues whatsoever is a rare thing - many thanks.
Some suggestions:
you may wish to explain that this move occurs entirely within the Wubi install and that on rebooting both the Wubi install and the new install on a partition will co-exist, also you may like to post a link to a guide for partitoning, and a link to discover the names of the filesystem drives as newbies coming from windows find that rather arcane.
Many thanks.

---

### Post by bcbc on 2011-04-14
> **idodialog said:**
> Many thanks, easy, quick effective!. To have no issues whatsoever is a rare thing - many thanks.
Some suggestions:
you may wish to explain that this move occurs entirely within the Wubi install and that on rebooting both the Wubi install and the new install on a partition will co-exist, also you may like to post a link to a guide for partitoning, and a link to discover the names of the filesystem drives as newbies coming from windows find that rather arcane.
Many thanks.

You're welcome and thanks for the feedback. 

I'm not sure that I can get all that additional info you've suggested into this howto - I looked for a one-stop shop partitioning guide, but it seems like you have to review a couple to get all the pieces, and people differ on whether it's better to use GParted or Vista/7 disk manager (for example); and some are good but out of date. (I also don't want this to become a partitioning Howto.) But if you have some specific site recommendations, please let me know and I'll consider them for inclusion in post #1. 

I'm going to be looking at the script and howto in the next couple of weeks to make sure everything is good for the release of 11.04 Natty Narwhal and I'll try to make things clearer. Thanks

---

### Post by SimpleWater on 2011-04-15
> **bcbc said:**
> I am pretty sure that if you format D: as ntfs, your wubi will boot again. 

If I were you I'd just stick with Wubi. Unfortunately many people knock Wubi, but the fact is it is a safe way to learn Linux. And if you get Wubi booting, run the bootinfoscript and maybe it will show more information about /dev/sda3.

Anyway - I am truly sorry about your problems - and if you do end up migrating in the future, feel free to post here beforehand and we can check everything is good before going ahead.

Cheers, worked with the new format. For now i will stick to wubi but thanks again for all your help.

---

### Post by bcbc on 2011-04-16
> **SimpleWater said:**
> Cheers, worked with the new format. For now i will stick to wubi but thanks again for all your help.

Great! I'm glad you've got it resolved.

---

### Post by dmtaylor2011 on 2011-04-17
Ok, so, new Ubuntu user here. I've tried running the script in the terminal, but no luck. It seems that no matter what I do, I keep hitting "bash: wubi-move: No such file or directory"

Any ideas?

---

### Post by bcbc on 2011-04-18
> **dmtaylor2011 said:**
> Ok, so, new Ubuntu user here. I've tried running the script in the terminal, but no luck. It seems that no matter what I do, I keep hitting "bash: wubi-move: No such file or directory"

Any ideas?
If you downloaded the latest script it would be: wubi-move-2.0.sh and if you have the old one: wubi-move**.sh**

So download the script - I would suggest the latest (you'll need to extract it as described in the first post).
Usually it goes to the ~/Downloads directory, or you might have placed it on your ~/Desktop instead.

Then, go to the terminal, change to the appropriate directory and then you should find it:
```
cd Downloads
sudo bash wubi-move-2.0.sh --help
```

Note you can use the TAB key to autocomplete... e.g. sudo bash wubi[TAB] (as long as you're in the correct directory).

PS ~/ is shorthand for your home directory. e.g. if your username is xxx, then "cd ~/Downloads" is the same as "cd /home/xxx/Downloads"

---

### Post by dmtaylor2011 on 2011-04-18
Thank you! Worked like a charm. :D

---

### Post by bcbc on 2011-04-19
> **dmtaylor2011 said:**
> Thank you! Worked like a charm. :D

Good to hear :)

---

### Post by claytongulick on 2011-04-19
I just want to take a second to thank you for the very valuable and time saving script, it was a life saver. If you're ever near Dallas, Texas, send me a note, I'd be happy to buy you a beer.

---

### Post by bcbc on 2011-04-20
> **claytongulick said:**
> I just want to take a second to thank you for the very valuable and time saving script, it was a life saver. If you're ever near Dallas, Texas, send me a note, I'd be happy to buy you a beer.

Now we're talking... I knew the script would pay off eventually ;)

---

### Post by who_buntu on 2011-04-20
OK, so I want to do this.

XP Pro SP3 on a 120GB HD and a 17GB wubi installation, plus a NTFS swap file for Windows and a 2GB hibernate file (I've got a laptop with 2GB of memory). Right now, I'm able to boot the Windows Recovery Console but am afraid I'll lose this ability if I install any GRUB loader whatsoever.

Am I right?

Can I use my existing Windows swap file for Ubuntu?

Thanks!

---

### Post by bcbc on 2011-04-20
> **who_buntu said:**
> OK, so I want to do this.

XP Pro SP3 on a 120GB HD and a 17GB wubi installation, plus a NTFS swap file for Windows and a 2GB hibernate file (I've got a laptop with 2GB of memory). Right now, I'm able to boot the Windows Recovery Console but am afraid I'll lose this ability if I install any GRUB loader whatsoever.

Am I right?

Can I use my existing Windows swap file for Ubuntu?

Thanks!
Grub2 will offer any windows partition as well as windows recovery partition, as long as it finds the relevant boot files on it. If you have a wubi install, then you can see what it will look like: the grub os-prober works in the same way on Wubi as normal Ubuntu and that part of the grub menu will be the same. If you have some custom OEM bootloader i.e. not a standard windows bootloader, then installing grub2's bootloader will remove any additional functionality that came with that.

You cannot share the windows hibernate file as swap. Also, Ubuntu needs a swap partition to hibernate (there is an exception mentioned previously in this thread).

---

### Post by Factorial on 2011-04-30
Hi!

I tried running your script from a live usb pen, but it gave errors:

```
ubuntu@ubuntu:/media/5D18-F276/Migrate$ sudo bash wubi-move-2.0.sh --root-disk=/media/EC2E7CC72E7C8C78/ubuntu/disks/root.disk /dev/sda4 /dev/sda2

wubi-move-2.0.sh: The Grub2 bootloader will be installed to /dev/sda.
wubi-move-2.0.sh: This is required when a migration is performed
wubi-move-2.0.sh: from a named root.disk file.
wubi-move-2.0.sh: Continue and install Grub2 to /dev/sda? (Y/N)
y
wubi-move-2.0.sh: Please close all open files before continuing.
wubi-move-2.0.sh: About to format the target partition (/dev/sda4).
wubi-move-2.0.sh: Proceed with format (Y/N)
y
wubi-move-2.0.sh: Formatting /dev/sda4 with ext4 file system

wubi-move-2.0.sh: Copying files - please be patient - this takes some time
mkdir: cannot create directory `/tmp/wubitarget/host': File exists
wubi-move-2.0.sh: Creating swap...
wubi-move-2.0.sh: Command mkswap on /dev/sda2 failed
wubi-move-2.0.sh: Migration will continue without swap

wubi-move-2.0.sh: Starting chroot to the target install.
wubi-move-2.0.sh: An error occurred within chroot
wubi-move-2.0.sh: Error is: chroot: cannot run command `dpkg-divert': Exec format error
wubi-move-2.0.sh: Attempting to exit chroot normally...
wubi-move-2.0.sh: Exiting from chroot on target install...
wubi-move-2.0.sh: Cancelling migration... 
ubuntu@ubuntu:/media/5D18-F276/Migrate$ 

```

What could have went wrong?

Thanks,
Factorial

---

### Post by bcbc on 2011-04-30
> **Factorial said:**
> Hi!

I tried running your script from a live usb pen, but it gave errors:

What could have went wrong?

Thanks,
Factorial
There are a couple of things I noticed. The mkswap command failed. The /host directory on the target exists already - which is puzzling that can only happen if the mountpoint is not associated with the newly formatted partition (in which case I'd expect a separate mount error). Did you run this more than once, and also have errors the first time?

The root.disk migration also requires a working, fully contained Ubuntu install (on just the root.disk) - did you have any issues with this wubi install before or was everything working normally.

Please also state the Ubuntu release you are migrating and the release of the Ubuntu live environment you are running. Also whether the live environment is 64bit/32bit and whether the original wubi was 64bit/32bit. The architecture should match and I'm not checking this in the script - and this seems likely to be the cause of the chroot problem.
Thanks

---

### Post by Factorial on 2011-04-30
Thanks for your answer!

> Did you run this more than once

No, this was the first and only time.

> did you have any issues with this wubi install before or was everything working normally.

I had one major issue: The same as post #10 in this thread:
[http://ubuntuforums.org/showthread.php?t=1474253](http://ubuntuforums.org/showthread.php?t=1474253)
It has happened three times. (This is the main reason I was trying to migrate.) I solved it following the instructions in post #39.

> Please also state the Ubuntu release you are migrating and the release of the Ubuntu live environment you are running.

Both are 10.04 LTS. However, the architectures don't match. The live environment is 32bit, wubi is 64bit.

---

### Post by bcbc on 2011-04-30
> **Factorial said:**
> Thanks for your answer!

> Did you run this more than once

No, this was the first and only time.

> did you have any issues with this wubi install before or was everything working normally.

I had one major issue: The same as post #10 in this thread:
[http://ubuntuforums.org/showthread.php?t=1474253](http://ubuntuforums.org/showthread.php?t=1474253)
It has happened three times. (This is the main reason I was trying to migrate.) I solved it following the instructions in post #39.

> Please also state the Ubuntu release you are migrating and the release of the Ubuntu live environment you are running.

Both are 10.04 LTS. However, the architectures don't match. The live environment is 32bit, wubi is 64bit.

OK thanks for the feedback - I'm going to have to add some check on the architecture or else figure out how to do the chroot with mismatching architectures. The live cd migration was a new feature and I don't have a 64bit machine so just didn't take it into account. If you can rerun it with a 64 bit Ubuntu CD and let me know the result then I'll update the known issues for others that might run into this and add a check in the next release. 

I don't think the wubildr (rebooting 10.04) problem will make any difference here, so it's likely just the architecture issue. 
I am still confused though as to why the mkswap failed - that seems unrelated.

Thanks

---

### Post by Factorial on 2011-05-01
I downloaded a 64bit 10.04, and it worked!

mkswap still failed, though:
```

wubi-move-2.0.sh: Copying files - please be patient - this takes some time
mkdir: cannot create directory `/tmp/wubitarget/host': File exists
wubi-move-2.0.sh: Creating swap...
wubi-move-2.0.sh: Command mkswap on /dev/sda2 failed
wubi-move-2.0.sh: Migration will continue without swap

wubi-move-2.0.sh: Starting chroot to the target install.
wubi-move-2.0.sh: Removing lupin-support on target...
wubi-move-2.0.sh: Grub bootloader installed to /dev/sda
wubi-move-2.0.sh: Updating the target grub menu...
wubi-move-2.0.sh: Exiting from chroot on target install...

wubi-move-2.0.sh: Operation completed successfully.
ubuntu@ubuntu:/media/5D18-F276/Migrate$ 

```

I will attempt to manually set up the swap.

---

### Post by Factorial on 2011-05-01
Thanks for the assistance! Everything is working now!

---

### Post by bcbc on 2011-05-01
> **Factorial said:**
> Thanks for the assistance! Everything is working now!

Great to hear! And thanks for the feedback - I'll update the known issues list and deal with it in the next version of the script.

---

### Post by dogger on 2011-05-10
Hi, Im another new to ubuntu person trying to get rid of the wubi install.  I tried the migration yesterday but ran into an error. I ran the script and said yes to both questions. It ran for about two hours then the broken pipe message popped up. What could cause this? Any help would be greatly appreciated. 

[PHP]wubi-move-2.0.sh: Copying files - please be patient - this takes some time  
 rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)  
 rsync: write failed on "/tmp/wubitarget/vista/ubuntu/disks/root.disk": No space left on device (28)  
 rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]  
 rsync: connection unexpectedly closed (8343408 bytes received so far) [sender]  
 rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]  
 

 wubi-move-2.0.sh: Copying files failed - user canceled?  
 wubi-move-2.0.sh: Unmounting target...  
 wubi-move-2.0.sh: Migration request canceled  
 [/PHP]

---

### Post by bcbc on 2011-05-10
> **dogger said:**
> Hi, Im another new to ubuntu person trying to get rid of the wubi install.  I tried the migration yesterday but ran into an error. I ran the script and said yes to both questions. It ran for about two hours then the broken pipe message popped up. What could cause this? Any help would be greatly appreciated. 

[PHP]wubi-move-2.0.sh: Copying files - please be patient - this takes some time  
 rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)  
 rsync: write failed on "/tmp/wubitarget/vista/ubuntu/disks/root.disk": No space left on device (28)  
 rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]  
 rsync: connection unexpectedly closed (8343408 bytes received so far) [sender]  
 rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]  
 

 wubi-move-2.0.sh: Copying files failed - user canceled?  
 wubi-move-2.0.sh: Unmounting target...  
 wubi-move-2.0.sh: Migration request canceled  
 [/PHP]

It looks like you have your host ntfs partition mounted or linked under /vista - so that Wubi is trying to copy the whole partition and running out of space. 

I thought the rsync command was set to constrain itself to one filesystem - so I'll look into that as a bug. But this is obviously not happening, and since you have a custom mountpoint (/vista) the standard exclusions on /host and /media are being bypassed.

My recommendation for the meantime is to unmount /vista and try again. 
```
sudo umount /vista
```

PS you'll have to use gparted to clear out that target partition again (as the script won't allow you to migrate to one that isn't empty).

---

### Post by dogger on 2011-05-10
Thanks for the quick response. I un mounted vista after reformatting the partitions  then tried again and got this error:
[PHP]
wubi-move-2.0.sh: Copying files - please be patient - this takes some time
wubi-move-2.0.sh: Creating swap...

wubi-move-2.0.sh: Starting chroot to the target install.
wubi-move-2.0.sh: Removing lupin-support on target...
wubi-move-2.0.sh: An error occurred within chroot
wubi-move-2.0.sh: Error is: /bin/df: `/home/chris/.gvfs': No such file or directory
/bin/df: `/tmp/wubitarget': No such file or directory
/bin/df: `/home/chris/.gvfs': No such file or directory
/bin/df: `/tmp/wubitarget': No such file or directory
/bin/df: `/home/chris/.gvfs': No such file or directory
/bin/df: `/tmp/wubitarget': No such file or directory
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
E: Sub-process /usr/bin/dpkg returned an error code (1)
wubi-move-2.0.sh: Attempting to exit chroot normally...
wubi-move-2.0.sh: Exiting from chroot on target install...
wubi-move-2.0.sh: Cancelling migration... [/PHP]Any suggestions on how to fix this would be great.

---

### Post by bcbc on 2011-05-10
> **dogger said:**
> Thanks for the quick response. I un mounted vista after reformatting the partitions  then tried again and got this error:
Any suggestions on how to fix this would be great.
Can you give me the output of:
```
cat /proc/mounts
cat /etc/mtab
cat /etc/fstab

```

Also I'd recommend rebooting - even though the script has a chroot recovery process - to be safe it'd be better to reboot. But give me the output before you reboot.

---

### Post by dogger on 2011-05-10
[PHP]
chris@ubuntu:~$ cat /proc/mounts

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=1023864k,nr_inodes=255966,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/sda1 /host fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
/dev/loop0 / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
/dev/sda2 /media/HP_RECOVERY fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/chris/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0


chris@ubuntu:~$ cat /etc/mtab

/dev/loop0 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda1 /host fuseblk rw,nosuid,nodev,locale=en_US.utf8 0 0
/dev/sda2 /media/HP_RECOVERY fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/chris/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=chris 0 0


chris@ubuntu:~$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/dev/sda2    /media/HP_RECOVERY    ntfs-3g    defaults,locale=en_US.utf8    00
/dev/sda1    /vista    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0


[/PHP]Thanks for your patience, I seem to be in way over my head:confused:

---

### Post by bcbc on 2011-05-10
> **dogger said:**
> [PHP]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda1    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/dev/sda2    /media/HP_RECOVERY    ntfs-3g    defaults,locale=en_US.utf8    00
/dev/sda1    /vista    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0


[/PHP]Thanks for your patience, I seem to be in way over my head:confused:

That's not a problem. Unfortunately I am at work - so don't have the ability to do a detailed analysis, but I'd like to get some diagnostics so I can debug this later.

But what I do notice is that, apart from mounting your host as /vista, you also have a separate line in /etc/fstab to mount /host. This is already performed on your behalf so there's no need to include it. 

What I'd try is... edit /etc/fstab and add a # to the start of those lines. Reboot and try again. If that still fails then I'm afraid you'll have to wait until I can spend some time looking at this.

So /etc/fstab will look like this:
[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#/dev/sda1    /host    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/dev/sda2    /media/HP_RECOVERY    ntfs-3g    defaults,locale=en_US.utf8    00
#/dev/sda1    /vista    ntfs-3g    defaults,nosuid,nodev,locale=en_US.utf8    0    0
/host/ubuntu/disks/root.disk    /    ext4    loop,errors=remount-ro    0    1
/host/ubuntu/disks/swap.disk    none    swap    loop,sw    0    0

[/PHP]

(I might just comment out the HP recovery as well - I'm not sure why you need to automount this)

---

### Post by bcbc on 2011-05-10
dogger, 
how did you mount your /host (/dev/sda1) as /vista? I've tried to duplicate this using ntfs-config but it refuses to mount. (Also what release are you running?) I suspect whatever you had to do, has something to do with the problem... but it's hard to confirm if I can't reproduce the error.

---

### Post by aropop on 2011-05-13
Hi, i've quite succesfully moved my wubi to a my second harddisk on my laptop (/dev/sdb1) but my grub doesn't find the disk.
It only finds hd0/msdos' 
When i try to boot one of the migrated ubuntu's it sais doesn't find disk and first load kernel...
Please help ;)

---

### Post by bcbc on 2011-05-13
> **aropop said:**
> Hi, i've quite succesfully moved my wubi to a my second harddisk on my laptop (/dev/sdb1) but my grub doesn't find the disk.
It only finds hd0/msdos' 
When i try to boot one of the migrated ubuntu's it sais doesn't find disk and first load kernel...
Please help ;)

So, I'm going to assume that you ran the script, migrated to your second drive, and installed the bootloader (which means it's on /dev/sdb).
If you are still booting from /dev/sda then you won't see any difference. But if you select Ubuntu (wubi) then you should see the migrated install at the bottom of the grub menu.
In order to boot the new install directly you need to either select /dev/sdb as the first boot device, or install grub to /dev/sda from within the migrated install.

If I've not correctly interpreted the problem or you need help installing the grub bootloader, please explain in more details what you have done and what symptoms you have, and include the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results as well.

Thanks

---

### Post by aropop on 2011-05-13
> **bcbc said:**
> So, I'm going to assume that you ran the script, migrated to your second drive, and installed the bootloader (which means it's on /dev/sdb).
If you are still booting from /dev/sda then you won't see any difference. But if you select Ubuntu (wubi) then you should see the migrated install at the bottom of the grub menu.
In order to boot the new install directly you need to either select /dev/sdb as the first boot device, or install grub to /dev/sda from within the migrated install.

If I've not correctly interpreted the problem or you need help installing the grub bootloader, please explain in more details what you have done and what symptoms you have, and include the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results as well.

Thanks
So bootscript said 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   323,055,615   302,082,048   7 HPFS/NTFS
/dev/sda3         323,055,616   625,139,711   302,084,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       dc79e77b-0576-4ff6-9e12-06af4f5cb01e   ext4                                     
/dev/sda1        A688EFB988EF85E1                       ntfs       PQSERVICE                     
/dev/sda2        805AD09B5AD08F72                       ntfs       ACER                          
/dev/sda3        3A88ADB588AD7055                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7f98a24e-fa4f-429b-831b-96860a21100f   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1        /media/7f98a24e-fa4f-429b-831b-96860a21100f ext4       (rw,nosuid,nodev,uhelper=udisks)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-28-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-28-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-28-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-27-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-27-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a688efb988ef85e1
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro quiet splash
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux /boot/vmlinuz-2.6.35-28-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro single
	initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


   4.2GB: boot/grub/grub.cfg
   1.9GB: boot/initrd.img-2.6.35-22-generic
   4.1GB: boot/initrd.img-2.6.35-27-generic
   6.3GB: boot/initrd.img-2.6.35-28-generic
   5.0GB: boot/vmlinuz-2.6.35-22-generic
   5.0GB: boot/vmlinuz-2.6.35-27-generic
   6.1GB: boot/vmlinuz-2.6.35-28-generic
   6.3GB: initrd.img
   4.1GB: initrd.img.old
   6.1GB: vmlinuz
   5.0GB: vmlinuz.old

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
set locale_dir=($root)/boot/grub/locale
set lang=nl
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=7f98a24e-fa4f-429b-831b-96860a21100f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 7f98a24e-fa4f-429b-831b-96860a21100f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set a688efb988ef85e1
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 805ad09b5ad08f72
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sdb1 when migrated
UUID=7f98a24e-fa4f-429b-831b-96860a21100f    /    ext4    errors=remount-ro    0    1

=================== sdb1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
 229.9GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.35-22-generic
    .1GB: boot/initrd.img-2.6.35-27-generic
   1.6GB: boot/initrd.img-2.6.35-28-generic
  13.0GB: boot/vmlinuz-2.6.35-22-generic
  13.0GB: boot/vmlinuz-2.6.35-27-generic
  13.0GB: boot/vmlinuz-2.6.35-28-generic
   1.6GB: initrd.img
    .1GB: initrd.img.old
  13.0GB: vmlinuz
  13.0GB: vmlinuz.old
```
And for more detail. When i boot i first get to choose between Windows and ubuntu, then i get in grub menu. In this menu there are the wubi boots and then the migrated boots. If i try to run one of these migrated boots the grub said he couldn't find the drive where i've puted it on (or something simular gonna reboot for exact text).

EDIT: exact text is :"no such device :  DEVICE WHERE MY MIGRATION IS
h1,msdos1 cannot get C/H/S values
You need to load the kernel first"
then it let me return to grub..

---

### Post by bcbc on 2011-05-13
> **aropop said:**
> So bootscript said 

And for more detail. When i boot i first get to choose between Windows and ubuntu, then i get in grub menu. In this menu there are the wubi boots and then the migrated boots. If i try to run one of these migrated boots the grub said he couldn't find the drive where i've puted it on (or something simular gonna reboot for exact text).

It looks good to me... how is /dev/sdb connected?
Try this... boot your computer, select Ubuntu, when you see the grub menu hit 'c' to get to a grub prompt.
Enter lower case LS to make sure that the BIOS can see the second hard drive:
```
ls
```
Write down what you see. Should be (hd0) (hd0,1) ... (hd1) (hd1,1). Or it will be (hd0) (hd0,msdos1)... (hd1) (hd1, msdos1) (something like that)

Also try to load the migrated install's grub menu:
```
configfile (hd1,1)/boot/grub/grub.cfg
```

---

### Post by aropop on 2011-05-13
I Can only see hd0,msdos1 to 3 :s

---

### Post by bcbc on 2011-05-13
> **aropop said:**
> I Can only see hd0,msdos1 to 3 :s

Your BIOS cannot see the drive. So grub cannot boot from it. If you've attached it via USB check your BIOS settings and see whether you can get it to recognize it.

If you get this fixed - then also make sure your BIOS can see past 137GB. I noticed that your grub.cfg is sitting at 229GB - so that will likely be the next problem you face. If this is an issue, repartition /dev/sdb, make /dev/sdb1 <= 137GB.

---

### Post by aropop on 2011-05-13
Ok, apparently my bios doesn't detect my first hard disk (wich is in my laptop not usb) so i copied all my files to an external hard disk and am now formatting all partitions (except for the ones i need) and putting my linux a /dev/sda5 wich he hopefully does detect, thanks for your advice about bios really helped!

---

### Post by bcbc on 2011-05-13
> **aropop said:**
> Ok, apparently my bios doesn't detect my first hard disk (wich is in my laptop not usb) so i copied all my files to an external hard disk and am now formatting all partitions (except for the ones i need) and putting my linux a /dev/sda5 wich he hopefully does detect, thanks for your advice about bios really helped!
??? that seems strange. You're booting windows/wubi from your first hard drive? or the external?

Also, you shouldn't need to reformat everything to create a new partition. It's possible to split your partitions from within Windows Vista/7 using it's disk manager.

But backing up is definitely a good idea. Still do that.

---

### Post by Pi Robot on 2011-05-16
> **bcbc said:**
> It seems to be working for me... you should have been prompted:
```
wubi-move.sh: The grub2 bootloader will be installed to drive (/dev/sda)
wubi-move.sh: If you select no, you have to boot your new install
wubi-move.sh: from the wubi menu and install it later manually.
wubi-move.sh: Install the grub bootloader to /dev/sda? (Y/N)

```Then, unless, you enter 'n' or 'N' it proceeds to install it. 

Note, if you migrate your wubi to a partition on another drive, the script will only permit installing the bootloader on that drive, which may not necessarily be the drive you boot from.

The only exception to this is if you use the --no-bootloader option. But I'll run some more tests anyway to make sure.

EDIT:
After further testing I've discovered that the package lupin-support (required for Wubi installs) modifies the grub-install command, but this isn't consistent across releases. For 10.04 the command 'grub-install --root-directory=xxx /dev/sda' was not actually updating the MBR, whereas on a 9.10 install it works fine. So I've modified the script to run grub-install within the target install (using chroot) as the lupin-support is already removed and the results should be consistent across releases.

Thanks again for the feedback.

Further EDIT: 
In fact there is a bug in lupin-support in 10.04 Ubuntu that makes grub-install act differently depending on whether the wubi is installed on the same partition as windows or not. In my case, the --root-directory option was working, but when I tried the same command on a more typical install on the same partition as windows, it did not work. 

It's not relevant for the migration anymore as the script is doing grub-install in chroot, however, might impact other wubi users. Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417)

Thank you very much for providing this script.  I used your script to migrate a wubi 10.04LTS installation (itself installed under Windows 7) to a new partition on the same disk.  The new partition is /dev/sda5 under an extended partition and I am using /dev/sda6 for swap.  So the command I used to run the migration was:

sudo bash wubi-move-2.0.sh /dev/sda5 /dev/sda6
[FONT=monospace]
I answered "Y" to install the grub bootloader.  However, my machine still insists on *not* showing the new 10.04LTS install on /dev/sda5 as one of the boot options.  Instead, I have to first choose "Windows 7", then "Ubuntu", and finally, scroll all the way down to the bottom of the list of "Ubuntu 10.04LTS" menu items.  Then I get in fine.

After rebooting this way, I tried running 'sudo grub-install /dev/sda' followed by sudo update-grub' but it results in the same behavior.  Is there some way I can fix this?  My ultimate goal is to delete the Windows 7 partition entirely and use the extra space for Linux but at the moment I am forced to go through the Windows 7/wubi boot sequence.

Thanks!
patrick

[/FONT]

---

### Post by bcbc on 2011-05-16
> **Pi Robot said:**
> Thank you very much for providing this script.  I used your script to migrate a wubi 10.04LTS installation (itself installed under Windows 7) to a new partition on the same disk.  The new partition is /dev/sda5 under an extended partition and I am using /dev/sda6 for swap.  So the command I used to run the migration was:

sudo bash wubi-move-2.0.sh /dev/sda5 /dev/sda6
[FONT=monospace]
I answered "Y" to install the grub bootloader.  However, my machine still insists on *not* showing the new 10.04LTS install on /dev/sda5 as one of the boot options.  Instead, I have to first choose "Windows 7", then "Ubuntu", and finally, scroll all the way down to the bottom of the list of "Ubuntu 10.04LTS" menu items.  Then I get in fine.

After rebooting this way, I tried running 'sudo grub-install /dev/sda' followed by sudo update-grub' but it results in the same behavior.  Is there some way I can fix this?  My ultimate goal is to delete the Windows 7 partition entirely and use the extra space for Linux but at the moment I am forced to go through the Windows 7/wubi boot sequence.

Thanks!
patrick

[/FONT]
That's interesting. It seems that Grub is installed but perhaps there is an issue with the grub 10_linux script.

From the migrated install on /dev/sda5, please list the output of:
```
ls -l /etc/grub.d/
``` (that's lower case LS -L in the above command)

Also, hit # above and paste the /boot/grub/grub.cfg between the [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

Thanks

---

### Post by Pi Robot on 2011-05-16
> **bcbc said:**
> That's interesting. It seems that Grub is installed but perhaps there is an issue with the grub 10_linux script.

From the migrated install on /dev/sda5, please list the output of:
```
ls -l /etc/grub.d/
``` (that's lower case LS -L in the above command)

Also, hit # above and paste the /boot/grub/grub.cfg between the  tags.

Thanks

Thanks for the quick reply!  Here is the listing you asked for.  Is the problem the lack of execution bits on 10_lupin?

```
$ ls -l /etc/grub.d/
total 24
-rw-r--r-- 1 root root 4078 2010-03-23 02:14 10_lupin
-rwxr-xr-x 1 root root  918 2010-03-23 02:37 20_memtest86+
-rwxr-xr-x 1 root root 6605 2010-07-01 13:53 30_os-prober
-rwxr-xr-x 1 root root  214 2010-07-01 13:53 40_custom
-rw-r--r-- 1 root root  483 2010-07-01 13:53 README

```And just in case it helps, here are the contents of 10_lupin:

```
#! /bin/sh -e

# grub-mkconfig helper script for lupin. Some of this is based on 10_linux,
# but with irrelevant bits removed and the rest extended to cope with
# loopback mounts.
#
# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
# Copyright (C) 2009  Canonical Ltd.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib

if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
  OS=GNU/Linux
else
  OS="${GRUB_DISTRIBUTOR}"
fi

case ${GRUB_DEVICE} in
  /dev/loop/*|/dev/loop[0-9])
    loop_file=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
  ;;
esac

# Is the root filesystem loop-mounted from a file on another filesystem?
if [ "x${loop_file}" = x ] || [ ! -f "${loop_file}" ]; then
  exit 0
fi
dev_mountpoint="$(awk '"'${loop_file}'" ~ "^"$2 && $2 != "/" { print $1";"$2 }' 
/proc/mounts | tail -n1)"
host_device="${dev_mountpoint%;*}"
host_mountpoint="${dev_mountpoint#*;}"
if [ "x${host_device}" = x ]; then
  exit 0
fi
loop_file_relative="${loop_file#$host_mountpoint}"

# Device containing the host filesystem.
host_device_uuid="`${grub_probe} --device "${host_device}" --target=fs_uuid 2> /
dev/null`" || true

if [ "x${host_device_uuid}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue"
 ] \
    || ! test -e "/dev/disk/by-uuid/${host_device_uuid}" \
    || [ "`${grub_probe} -t abstraction --device ${host_device} | sed -e 's,.*\(
lvm\).*,\1,'`" = "lvm"  ] ; then
  LINUX_HOST_DEVICE=${host_device}
else
  LINUX_HOST_DEVICE=UUID=${host_device_uuid}
fi

# add crashkernel option if we have the required tools
if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
fi

lupin_entry ()
{
  cat << EOF
menuentry "$1" {
EOF
  save_default_entry | sed -e "s/^/\t/"
  prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/"

  cat << EOF
    linux ${rel_dirname}/${basename} root=${LINUX_HOST_DEVICE} loop=${loop_f
ile_relative} ro $2
    initrd ${rel_dirname}/${initrd}
EOF
  cat << EOF
}
EOF
}

list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* ; do
        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
      done`

while [ "x$list" != "x" ] ; do
  linux=`version_find_latest $list`
  echo "Found linux image: $linux" >&2
  basename=`basename $linux`
  dirname=`dirname $linux`
  rel_dirname=`make_system_path_relative_to_its_root $dirname`
  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
  alt_version=`echo $version | sed -e "s,\.old$,,g"`
  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"

  initrd=
  for i in "initrd.img-${version}" "initrd-${version}.img" \
       "initrd-${version}" "initrd.img-${alt_version}" \
       "initrd-${alt_version}.img" "initrd-${alt_version}"; do
    if test -e "${dirname}/${i}" ; then
      initrd="$i"
      break
    fi
  done
  if test -n "${initrd}" ; then
    echo "Found initrd image: ${dirname}/${initrd}" >&2
  else
    # None of this can work without an initrd, so don't even bother.
    list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
    continue
  fi

  lupin_entry "${OS}, Linux ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}
" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    lupin_entry "${OS}, Linux ${version} (recovery mode)" \
    "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

---

### Post by bcbc on 2011-05-16
> **Pi Robot said:**
> Thanks for the quick reply!  Here is the listing you asked for.  Is the problem the lack of execution bits on 10_lupin?

```
$ ls -l /etc/grub.d/
total 24
-rw-r--r-- 1 root root 4078 2010-03-23 02:14 10_lupin
-rwxr-xr-x 1 root root  918 2010-03-23 02:37 20_memtest86+
-rwxr-xr-x 1 root root 6605 2010-07-01 13:53 30_os-prober
-rwxr-xr-x 1 root root  214 2010-07-01 13:53 40_custom
-rw-r--r-- 1 root root  483 2010-07-01 13:53 README

```

No the problem is you're missing 10_linux 
I'm not sure how that got deleted - I assume it's not on your Wubi install either. 10_lupin is just for loopmounted installs (Wubi) so you don't need the +x on that (in fact the script removes it during the migration).

Let me think about the best way to get a new 10_linux  - reinstalling grub-pc would probably do it. Go into Synaptic (on your migrated install) and search for grub-pc, then click green box and select to reinstall.

You're also missing 00_header and 05_debian_theme ... this is pretty strange. Did you do anything that might have affected grub from your Wubi install?

Edit: Reinstalling grub-pc should take care of all the missing scripts. You might be able to achieve the same with "sudo dpkg-reconfigure grub-pc" (but I think I'd just reinstall).

---

### Post by Pi Robot on 2011-05-16
> **bcbc said:**
> No the problem is you're missing 10_linux 
I'm not sure how that got deleted - I assume it's not on your Wubi install either. 10_lupin is just for loopmounted installs (Wubi) so you don't need the +x on that (in fact the script removes it during the migration).

Let me think about the best way to get a new 10_linux  - reinstalling grub-pc would probably do it. Go into Synaptic (on your migrated install) and search for grub-pc, then click green box and select to reinstall.

Unfortunately, reinstalling grub-pc using Synaptic did not restore 10_linux.  I can get it and 00_header and 05_debian_theme from another 10.04LTS machine I have on the same network.  Do you think they would work, or are they customized for each machine on installation?

> **bcbc said:**
> You're also missing 00_header and 05_debian_theme ... this is pretty strange. Did you do anything that might have affected grub from your Wubi install?

Not that I know of.  But on at least two occasions in the past 6 months, a standard Ubuntu update broke my grub bootloader and force me to fix it manually from a LiveCD...

---

### Post by bcbc on 2011-05-16
> **Pi Robot said:**
> Unfortunately, reinstalling grub-pc using Synaptic did not restore 10_linux.  I can get it and 00_header and 05_debian_theme from another 10.04LTS machine I have on the same network.  Do you think they would work, or are they customized for each machine on installation?



Not that I know of.  But on at least two occasions in the past 6 months, a standard Ubuntu update broke my grub bootloader and force me to fix it manually from a LiveCD...

Yes, copy them. They'll be the same for the same grub version. 

Maybe the scripts are part of grub-common. I can check it out later tonight... not able to do any testing at the moment.
You could also purge and reinstall grub-pc and grub-common which will do it for sure, but personally I'd just go the easy route and copy them.

---

### Post by Pi Robot on 2011-05-16
> **bcbc said:**
> Yes, copy them. They'll be the same for the same grub version. 

Maybe the scripts are part of grub-common. I can check it out later tonight... not able to do any testing at the moment.
You could also purge and reinstall grub-pc and grub-common which will do it for sure, but personally I'd just go the easy route and copy them.

Bingo!  Copying over the missing files and running 'sudo update-grub' did the trick.  (I tried reinstalling grub-common first to no avail.)

Many, many thanks for all your help!  Finally I can look forward to using the rest of my disk for Linux.

--patrick

---

### Post by bcbc on 2011-05-16
> **Pi Robot said:**
> Bingo!  Copying over the missing files and running 'sudo update-grub' did the trick.  (I tried reinstalling grub-common first to no avail.)

Many, many thanks for all your help!  Finally I can look forward to using the rest of my disk for Linux.

--patrick

Great. You're very welcome!

---

### Post by ktaragorn on 2011-05-18
Hi,

I have recently moved my 11.04 wubi install to a drive of its own, and the guide gave me no issues at all, and to the best of my knowledge i have done it right. 
However now, when i boot into the 2.6.35 kernel, my Wifi isnt able to connect, and dmesg returns an apparmor denied message for /sbin/dhclient. I am at work right now so i cant quote it, can post the exact message later on if needed. This kernel works fine with the wubi install, and it works fine if i stop apparmor and unload the profiles, but doubt that is a good thing to do. So was wondering how i can fix it. 
The kernel itself is maverick while the OS is natty. There is some other post somewhr saying this combo causes some issue.. but the wubi side is fine for me, so doubt that is the issue.
The reason i am not using 2.6.38.8 that comes with natty is that both installs have a consistent issue with my wifi card that even tho it says connected, the network basically drops after a while.. My wifi card is TP Link 321G 

Thanks a lot for your patience
Karthik T

---

### Post by bcbc on 2011-05-18
> **ktaragorn said:**
> Hi,

I have recently moved my 11.04 wubi install to a drive of its own, and the guide gave me no issues at all, and to the best of my knowledge i have done it right. 
However now, when i boot into the 2.6.35 kernel, my Wifi isnt able to connect, and dmesg returns an apparmor denied message for /sbin/dhclient. I am at work right now so i cant quote it, can post the exact message later on if needed. This kernel works fine with the wubi install, and it works fine if i stop apparmor and unload the profiles, but doubt that is a good thing to do. So was wondering how i can fix it. 
The kernel itself is maverick while the OS is natty. There is some other post somewhr saying this combo causes some issue.. but the wubi side is fine for me, so doubt that is the issue.
The reason i am not using 2.6.38.8 that comes with natty is that both installs have a consistent issue with my wifi card that even tho it says connected, the network basically drops after a while.. My wifi card is TP Link 321G 

Thanks a lot for your patience
Karthik T
The script updates the initrd.img of the current kernel during the migration, but not for older kernels. Perhaps this is the cause of the problem. 

Why don't you try doing this manually and see if it fixes it?
```
sudo update-initramfs -u -k 2.6.35-xx-generic
```  (hit TAB after -k to see list of kernels)

---

### Post by ktaragorn on 2011-05-18
Thanks for the quick response, glad to hear it might be quite as simple as this.. will get back tonight hopefully thru the new install :)

---

### Post by bcbc on 2011-05-18
> **ktaragorn said:**
> Thanks for the quick response, glad to hear it might be quite as simple as this.. will get back tonight hopefully thru the new install :)

Well, no guarantees ;) but it's best to try the simple fix first.

Oh... hold on. Not that simple. There's a bug report for this problem: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/771544](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/771544)

So it's not related. I recommend clicking "This affects me" on that bug report and subscribe for feedback (you'll need a launchpad.net account for this).

PS if you plan on using the maverick kernel I'd recommend updating the initrd.img anyway.

---

### Post by ktaragorn on 2011-05-18
Yes i saw that, however since it only affects one install and not the other, thought it might not be related.. anyway will do the initrd update and check first..

---

### Post by bcbc on 2011-05-18
> **ktaragorn said:**
> Yes i saw that, however since it only affects one install and not the other, thought it might not be related.. anyway will do the initrd update and check first..
Right, that's a good point!

---

### Post by ktaragorn on 2011-05-18
as i had hoped.. reporting it works from the dedicated install :) tnx a lot!

---

### Post by bcbc on 2011-05-18
> **ktaragorn said:**
> as i had hoped.. reporting it works from the dedicated install :) tnx a lot!

That's great! 

It would be nice if the script could update all of these... without introducing more potential points of failure (maybe I could ignore any exceptions for older initrd.img's and just spit out a warning).
Thanks for the feedback.

---

### Post by errrn on 2011-05-18
hi!

I'm about to try this script to migrate my installation. Before I started, I noticed something:

I don't have a clue what the swap is. should I have another partition for it? (if so, how big should it be, in average)
My drive is 600GB big, and I had two partitions, one for the system and one for the files, both 300 GB. Istarted making room for the ubuntu partition and I now have a windows 7 partition (about 160GB) and a  files partition (about 300GB). 

I did this with the windows disk utility, and the partition with the remainung 140GB shows up in ubuntu as a /dev/sda5 inside a /dev/sda3, tagged as lba and as an extended file system. I didn't give it any format, because the script's help says it will.

question would be: should I try taking care of that myself, reformatting, and so on?
and if so, how??

thanks in advance!

---

### Post by bcbc on 2011-05-18
> **errrn said:**
> hi!

I'm about to try this script to migrate my installation. Before I started, I noticed something:

I don't have a clue what the swap is. should I have another partition for it? (if so, how big should it be, in average)
My drive is 600GB big, and I had two partitions, one for the system and one for the files, both 300 GB. Istarted making room for the ubuntu partition and I now have a windows 7 partition (about 160GB) and a  files partition (about 300GB). 

I did this with the windows disk utility, and the partition with the remainung 140GB shows up in ubuntu as a /dev/sda5 inside a /dev/sda3, tagged as lba and as an extended file system. I didn't give it any format, because the script's help says it will.

question would be: should I try taking care of that myself, reformatting, and so on?
and if so, how??

thanks in advance!
If you want to hibernate the swap must be > RAM. If you enter "free" from a terminal it will tell you how much memory you have. So if you have 4GB then you need a swap partition of 4+ GB. The plus is a bit of a mystery and seems to be dependent on usage, but I added +1GB to my computer with 1GB ram, and I'd assume this will go down the more RAM you have. Probably if you have 6GB ram you wouldn't require much more than 6GB swap.

Regarding the partition setup - I recommend you prepare these first e.g. in GParted. Although the script will migrate to an NTFS partition, replacing the file system as ext4, it doesn't change the partition type from "7 - NTFS" to "83 - Linux". This doesn't bother Ubuntu, but will probably confuse windows. I'm looking to enforce this in a future script release.

So you can create many logical partitions within that extended. If you've used all the space on /dev/sda5, then delete that and create two in it's place, one for root (/) as ext4, and one for swap as "82 - linux swap".

Any other questions, feel free to ask :)

PS with GParted you won't see the partition type e.g. 7, 83, 82. But choosing ext4 will set it to 83, and choosing linux-swap will set it to 82. These show up when running e.g. "sudo fdisk -l"

---

### Post by ktaragorn on 2011-05-18
> **bcbc said:**
> That's great! 

It would be nice if the script could update all of these... without introducing more potential points of failure (maybe I could ignore any exceptions for older initrd.img's and just spit out a warning).
Thanks for the feedback.
tnx again. 
And i used the "How to", rather than the script. This can i think atleast be mentioned there, and also left as a message to the user at the end of the script.

---

### Post by bcbc on 2011-05-19
> **ktaragorn said:**
> tnx again. 
And i used the "How to", rather than the script. This can i think atleast be mentioned there, and also left as a message to the user at the end of the script.

Oh okay... Done!

---

### Post by ryanh06 on 2011-05-19
Thanks buddy. The script worked like a charm. At first I was in shock at how large and confusing the instructions all seemed. When I re-read it a few times the bash script was clear as day. Maybe you should split the methods into different posts and reduce all the warnings and redundancies. I am not nitpicking here because you saved me tons of headaches and potentially lost data with what is ultimately a very simple and painless solution but I just think that all that text might be too much for n00bs :p

---

### Post by bcbc on 2011-05-19
> **ryanh06 said:**
> Thanks buddy. The script worked like a charm. At first I was in shock at how large and confusing the instructions all seemed. When I re-read it a few times the bash script was clear as day. Maybe you should split the methods into different posts and reduce all the warnings and redundancies. I am not nitpicking here because you saved me tons of headaches and potentially lost data with what is ultimately a very simple and painless solution but I just think that all that text might be too much for n00bs :p

I hear you... I'm not happy with it either. :P

But good to hear it's doing the job ;)

---

### Post by ryanh06 on 2011-05-20
> **bcbc said:**
> I hear you... I'm not happy with it either. :P

But good to hear it's doing the job ;)

lol cheers! Great job though, it feels great to be rocking the dual boot world again [mostly Ubuntu]For all the naysayers I think Natty will be remembered as the 1st Linux Distro that captured the casual audience [pitchfork wielding fanboys be gone!] It works, looks fantastic out of the box and literally just works! [at least on a modern PC/Laptop] I can't wait to see the improvements that ocelot will bring [the first word is such a mouthful that I am sticking to calling 11.10 Ocelot!]and of course the next big LTS. I think that by LTS 12.04 Ubuntu will really take off in the casual crowd. Anyways basically thanks BCBC and sorry about the long rant! :popcorn:

---

### Post by bcbc on 2011-05-21
> **ryanh06 said:**
> lol cheers! Great job though, it feels great to be rocking the dual boot world again [mostly Ubuntu]For all the naysayers I think Natty will be remembered as the 1st Linux Distro that captured the casual audience [pitchfork wielding fanboys be gone!] It works, looks fantastic out of the box and literally just works! [at least on a modern PC/Laptop] I can't wait to see the improvements that ocelot will bring [the first word is such a mouthful that I am sticking to calling 11.10 Ocelot!]and of course the next big LTS. I think that by LTS 12.04 Ubuntu will really take off in the casual crowd. Anyways basically thanks BCBC and sorry about the long rant! :popcorn:
lol if you wanted to rant you'll have to try harder... (not that I'm encouraging that sort of thing)
I agree... Natty is great (way beyond my expectations) and I'm looking forward to Oneiric and beyond.

---

### Post by penguinslide on 2011-05-23
Hi I was so happy to find this thread thinking my problems were going to be solved with some cut and paste, but it was too good to be true. Set up partitions, tried the script, didn't work, so tried manual install, hit a snag saying I had run out of space, ok maybe my partitions weren't big enough, so recloned hd from my backup, redid partitions with buckets of room, cut and paste through the steps and was hit with the same problem, Here's what the terminal says after step 3 is pasted after editing to suit my partition names:
rofs/usr/share/nano/sh.nanorc
rofs/usr/share/nano/tcl.nanorc
rofs/usr/share/nano/tex.nanorc
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/tmp/wubimove/rofs/usr/share/myspell/dicts/DicOOo.sxw": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]
rsync: connection unexpectedly closed (1451664 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
ubuntu@ubuntu:~$ chmod -x /tmp/wubimove/etc/grub.d/10_lupin
chmod: cannot access `/tmp/wubimove/etc/grub.d/10_lupin': No such file or directory
ubuntu@ubuntu:~$ 

I would post a screen shot, but can't save it to post off a live cd

Any suggestions how to avoid this glitch? Thanks in advance

---

### Post by penguinslide on 2011-05-23
> **penguinslide said:**
> Hi I was so happy to find this thread thinking my problems were going to be solved with some cut and paste, but it was too good to be true. Set up partitions, tried the script, didn't work, so tried manual install, hit a snag saying I had run out of space, ok maybe my partitions weren't big enough, so recloned hd from my backup, redid partitions with buckets of room, cut and paste through the steps and was hit with the same problem, Here's what the terminal says after step 3 is pasted after editing to suit my partition names:
rofs/usr/share/nano/sh.nanorc
rofs/usr/share/nano/tcl.nanorc
rofs/usr/share/nano/tex.nanorc
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/tmp/wubimove/rofs/usr/share/myspell/dicts/DicOOo.sxw": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]
rsync: connection unexpectedly closed (1451664 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
ubuntu@ubuntu:~$ chmod -x /tmp/wubimove/etc/grub.d/10_lupin
chmod: cannot access `/tmp/wubimove/etc/grub.d/10_lupin': No such file or directory
ubuntu@ubuntu:~$ 

I would post a screen shot, but can't save it to post off a live cd

Any suggestions how to avoid this glitch? Thanks in advance

Got gparted shot if it helps

[[IMG]http://img846.imageshack.us/img846/4259/screenshoteit.th.png[/IMG]]("http://img846.imageshack.us/i/screenshoteit.png/")

---

### Post by bcbc on 2011-05-23
> **penguinslide said:**
> Hi I was so happy to find this thread thinking my problems were going to be solved with some cut and paste, but it was too good to be true. Set up partitions, tried the script, didn't work, so tried manual install, hit a snag saying I had run out of space, ok maybe my partitions weren't big enough, so recloned hd from my backup, redid partitions with buckets of room, cut and paste through the steps and was hit with the same problem, Here's what the terminal says after step 3 is pasted after editing to suit my partition names:
rofs/usr/share/nano/sh.nanorc
rofs/usr/share/nano/tcl.nanorc
rofs/usr/share/nano/tex.nanorc
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: write failed on "/tmp/wubimove/rofs/usr/share/myspell/dicts/DicOOo.sxw": No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.7]
rsync: connection unexpectedly closed (1451664 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
ubuntu@ubuntu:~$ chmod -x /tmp/wubimove/etc/grub.d/10_lupin
chmod: cannot access `/tmp/wubimove/etc/grub.d/10_lupin': No such file or directory
ubuntu@ubuntu:~$ 

I would post a screen shot, but can't save it to post off a live cd

Any suggestions how to avoid this glitch? Thanks in advance
Did you say you were running the manual instructions from the live CD? That's not going to work. Those are supposed to be run after booting your wubi install. The only 'supported' way to migrate from a live cd is with the --root-disk= option from the script (the manual instructions would get way to complex if I had to cover every possibly scenario).

But if you really want to do it manually, the hint is to loopmount the root.disk and then modify the rsync command so that the copy source (and all the excludes) are prefixed by that mountpoint. If you look through this thread there is a link to someone else's thread where I listed the manual steps to do this.

---

### Post by bcbc on 2011-05-23
> **penguinslide said:**
> Got gparted shot if it helps



There's something strange with /dev/sda1. If it really is ext4 then wubi won't boot (the bootloader wubi uses hangs up on these). So you'll have to deal with that. Maybe run the bootinfoscript and post it back here if you need help.

---

### Post by penguinslide on 2011-05-23
> **bcbc said:**
> There's something strange with /dev/sda1. If it really is ext4 then wubi won't boot (the bootloader wubi uses hangs up on these). So you'll have to deal with that. Maybe run the bootinfoscript and post it back here if you need help.


Hi thanks for reply, sorry my mistake using the live cd, thought it would have to be done that was so it could be unmounted (still learning linux) will look for that link in this thread and get back to you

Yeah something weird with /dev/sda1 being ext4, didn't exist before, unless it is something to do with a failed migration, will find out how to run the bootinfoscript and get back to you. About to go to work.

---

### Post by bcbc on 2011-05-23
> **penguinslide said:**
> Hi thanks for reply, sorry my mistake using the live cd, thought it would have to be done that was so it could be unmounted (still learning linux) will look for that link in this thread and get back to you

Yeah something weird with /dev/sda1 being ext4, didn't exist before, unless it is something to do with a failed migration, will find out how to run the bootinfoscript and get back to you. About to go to work.

If /dev/sda1 is empty - and interfering with Wubi booting, just format it ntfs or if you want it for linux, ext3. (It's just ext4 that's a problem for the wubildr.mbr).

You can check it e.g.
```
sudo mount /dev/sda1 /mnt
nautilus /mnt
# or just use ls
ls -l /mnt
```

---

### Post by penguinslide on 2011-05-24
GREETINGS FROM UBUNTU /dev/sda3!!!  Thanks for you help and patience bcbc, you are a champion!!

Thought what the hell, got nothing to lose (wouldn't say that If I didn't have a clone!)

Gave the manual instructions one more go and it worked beautifully, 

Again thank you very much, saved me much pain and anguish!! 

Can now edit some video using ubuntu :)

---

### Post by bcbc on 2011-05-24
> **penguinslide said:**
> Thanks for helping me out, your code gave me:

*@ubuntu:~$ ls -l /mnt
total 0
*@ubuntu:~$ sudo mount /dev/sda1 /mnt

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Have no idea what to do with that info, will look for that link in this thread you mentioned

Probably it's not formatted. Try:
```
sudo blkid
sudo fdisk -l
```

---

### Post by penguinslide on 2011-05-24
> **bcbc said:**
> Probably it's not formatted. Try:
```
sudo blkid
sudo fdisk -l
```


ok that gave me this:

root@ubuntu:~# sudo blkid
/dev/sda1: UUID="160dd9c8-3a25-4490-b0fb-1726e123da7f" TYPE="ext4" 
/dev/sda4: UUID="18a5b014-a62e-4562-b261-3300938a1eab" TYPE="swap" 
/dev/loop0: UUID="37fec30f-6ef3-4f0e-9049-4652fe93998a" TYPE="ext4" 
/dev/sda2: LABEL="OS" UUID="E2C839DAC839AE23" TYPE="ntfs" 
/dev/sda3: UUID="65d29eb3-faf0-47b1-a341-2d37241a6ca8" TYPE="ext4" 
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2167    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2168       22525   163520512    7  HPFS/NTFS
/dev/sda3           27050       53820   215038057+  83  Linux
/dev/sda4           53821       60801    56074882+  82  Linux swap / Solaris
root@ubuntu:~# 

I don't get that at all, why with one command sda1 is identified as ext4 then the next command says it is fat32 (fat 32 was what I saw it as prior to last cloning)

 I'm suspecting I'm still on wubi, just moved some files into it and stated I was running out of space!

What can I put in terminal to find what partition you are running on?

Fixed it, changed default boot onto sda3 solved that problem, will try to boot windows and see what happens.

---

### Post by bcbc on 2011-05-24
It's a bit of a mess. Somehow you have an extended partition /dev/sda1 that encompasses /dev/sda2, yet /dev/sda1 contains an ext4 file system according to blkid, and /dev/sda2 should be numbered /dev/sda5 if it were a logical partition.

So I'm not sure what's going on there... but my advice is to take backups now if you haven't already.

---

### Post by srs5694 on 2011-05-24
> **penguinslide said:**
> ```
root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2167    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2168       22525   163520512    7  HPFS/NTFS
/dev/sda3           27050       53820   215038057+  83  Linux
/dev/sda4           53821       60801    56074882+  82  Linux swap / Solaris
```

[quote=bcbc]It's a bit of a mess. Somehow you have an extended partition /dev/sda1 that encompasses /dev/sda2, yet /dev/sda1 contains an ext4 file system according to blkid, and /dev/sda2 should be numbered /dev/sda5 if it were a logical partition.[/quote]

I believe you've misinterpreted the fdisk output, bcbc. /dev/sda1 is *not* an extended partition; it's marked as a type-0x1c (hidden FAT32) partition in the partition table, although blkid has identified it as containing an ext4 filesystem. (More on that shortly.) I suspect you got confused by the fact that penguinslide did not use code formatting, which caused the fdisk columnar output to be lost, so you misinterpreted /dev/sda1 as starting at cylinder 2167 and /dev/sda2 as starting at cylinder 2168. This would be consistent with /dev/sda1 being an extended partition that contains /dev/sda2; but in fact the output indicates that /dev/sda1 *ends* at 2167. I've added the appropriate [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to the fdisk output quoted above, but sometimes that goes wonky in quoted text, so I can't guarantee it'll be any better. (Edit: It looks good now.)

As to the type codes, Linux ignores them, so if the partition really *does* contain an ext4 filesystem, that shouldn't make much of a difference; however, it's possible that blkid is misidentifying the filesystem for one reason or another. Perhaps it's been damaged in some way. Perhaps penguinslide knows what the partition *should* be. Running fsck on the partition might fix any damage; or it might make it worse. If it contains any useful information, I advise doing a low-level backup of /dev/sda1, as in:

```

sudo dd if=/dev/sda1 of=/some/backup/file 

```Change /some/backup/file to a (non-existent; dd will create it) file on a partition with enough free space to hold the whole partition image (about 16 GiB).

You can then experiment with fsck and, if appropriate, change the type code for the partition using fdisk.

Of course, if the partition doesn't hold any useful data, you could just wipe it clean and set the partition type code to whatever's appropriate.

Beyond that, I can't comment, since I've never used WUBI, much less bcbc's script, so I don't know what the script does.

---

### Post by bcbc on 2011-05-24
Oops - thanks for the correction srs5694. I misread that completely.

PS I don't believe the script has been involved to this point.

---

### Post by bcbc on 2011-05-24
penguinslide:

I've just noticed your Edit to an earlier post that it all worked out! Great news! (Now I can stop worrying about /dev/sda1 ;) )

---

### Post by penguinslide on 2011-05-24
> **bcbc said:**
> It's a bit of a mess. Somehow you have an extended partition /dev/sda1 that encompasses /dev/sda2, yet /dev/sda1 contains an ext4 file system according to blkid, and /dev/sda2 should be numbered /dev/sda5 if it were a logical partition.

So I'm not sure what's going on there... but my advice is to take backups now if you haven't already.

Yeah I have a clone tucked safely away in case it goes pear shape, so I'm not going to mess with it anymore, all of them, win7, wubi, ubuntu on sda3 and hibernation on sda4 on are working without any problem.

Thanks bcbc for all your help!

---

### Post by bacaloubaca on 2011-06-01
usually don't post in forums unless I have something important to say but I wanted to thank everyone who was involved with preparing this script. Spent most of the day freeing up space on c:, & was kinda tired by the time I got around to this step & worried it'd be involved & painstaking, but it worked for me without a hitch (xp running on asus eee netbook, kubuntu 11.04 dual boot). Now for a celebratory beer :D

---

### Post by NotyethappywithNatty on 2011-06-02
Just wanted to add my thanks to you for creating this script. This is now my favourite piece of code ever written. Seriously.

Worked exactly as advertised, perfectly (Natty running within Windows 7 on an Asus K52J notebook, installed with Wubi 10.10).

No problems with GRUB, no issues at all. I now have a perfect, Windows free install, and I am incredibly grateful.

---

### Post by bcbc on 2011-06-02
> **bacaloubaca said:**
> usually don't post in forums unless I have something important to say but I wanted to thank everyone who was involved with preparing this script. Spent most of the day freeing up space on c:, & was kinda tired by the time I got around to this step & worried it'd be involved & painstaking, but it worked for me without a hitch (xp running on asus eee netbook, kubuntu 11.04 dual boot). Now for a celebratory beer :D
I can't speak for Agostino Russo - who created the original wubi-move-to-partition script - but for the current incarnation, you're welcome :)

> **NotyethappywithNatty said:**
> Just wanted to add my thanks to you for creating this script. This is now my favourite piece of code ever written. Seriously.

Worked exactly as advertised, perfectly (Natty running within Windows 7 on an Asus K52J notebook, installed with Wubi 10.10).

No problems with GRUB, no issues at all. I now have a perfect, Windows free install, and I am incredibly grateful.

Great to hear! :)

---

### Post by ssreddy555 on 2011-06-03
I have installed win 7 & thro WUBI, ubuntu 11.04. Now I want to migrate ubuntu to a partition. Can I follow the instructions given in this thread? Do they apply to the combination of windows7 & ubuntu 11.04 as well?

---

### Post by bcbc on 2011-06-03
> **ssreddy555 said:**
> I have installed win 7 & thro WUBI, ubuntu 11.04. Now I want to migrate ubuntu to a partition. Can I follow the instructions given in this thread? Do they apply to the combination of windows7 & ubuntu 11.04 as well?

Yes. This will migrates your Wubi install to the target partition you specify. (It runs from Ubuntu so it makes no difference which version of Windows you have). 

You need to create the partition(s) first - at least one for Ubuntu and an optional second partition for swap (if you want to be able to hibernate).

---

### Post by robimo on 2011-06-04
Hi, this is my first post on this forum :p

I've migrated the Ubuntu installation from wubi and all works fine.
Now, can I unnstall the ubuntu installation from windows ?

---

### Post by ssreddy555 on 2011-06-04
> **bcbc said:**
> Yes. This will migrates your Wubi install to the target partition you specify. (It runs from Ubuntu so it makes no difference which version of Windows you have). 

You need to create the partition(s) first - at least one for Ubuntu and an optional second partition for swap (if you want to be able to hibernate).

 I created sda 5 of about 45GB & a small sda 6 of about 1.5 GB for swap as detailed in this thread.
 
This is in addition to sda 1, 2 & 3, where Windows 7 is installed. 

When I tried to execute the command for "migration with swap file" in the Terminal, as detailed in this thread,It says sda 6 is not a swap partition. What does it mean? All the sda's are NTFS formatted.

---

### Post by bcbc on 2011-06-04
> **ssreddy555 said:**
> I created sda 5 of about 45GB & a small sda 6 of about 1.5 GB for swap as detailed in this thread.
 
This is in addition to sda 1, 2 & 3, where Windows 7 is installed. 

When I tried to execute the command for "migration with swap file" in the Terminal, as detailed in this thread,It says sda 6 is not a swap partition. What does it mean? All the sda's are NTFS formatted.
The script requires that the swap partition is already setup (this is a bit heavy-handed, it should just require that the partition type is '82 - Linux swap') 
The target partition should be type '83 - Linux' (although the current script will migrate to a target that is an ntfs partition and this doesn't cause any problems, ideally it should enforce that the type is '83' - I'll correct this in a future script release).

So you can modify the partitions e.g. using GParted. GParted is installed by default if you boot an Ubuntu CD in live CD mode (select "Try it" without installing). Since you already have the partitions setup you can also run it from Wubi if you install it first - e.g. via software centre. 

When you use GParted to set the target partition to ext4 and the swap partition to 'swap' it will automatically update the partition type. 

PS any partitioning carries a small risk. Please make sure your backups are current prior to doing this.

---

### Post by bcbc on 2011-06-04
> **robimo said:**
> Hi, this is my first post on this forum :p

I've migrated the Ubuntu installation from wubi and all works fine.
Now, can I unnstall the ubuntu installation from windows ?

Hi robimo, welcome to the forums!

If you installed the Grub2 bootloader when you migrated and are happy that everything is working as before, then - yes - you can uninstall Wubi from Windows.

You can tell whether you have the Grub2 bootloader if the first menu you see at bootup (after the BIOS splash) has Grub on the top.

If you are unsure - you can run and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by robimo on 2011-06-05
> **bcbc said:**
> Hi robimo, welcome to the forums!

If you installed the Grub2 bootloader when you migrated and are happy that everything is working as before, then - yes - you can uninstall Wubi from Windows.

You can tell whether you have the Grub2 bootloader if the first menu you see at bootup (after the BIOS splash) has Grub on the top.

If you are unsure - you can run and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

Thanks, i've uninstalled wubi and it's all ok :P

Now, my next goal is installing virtualbox on ubuntu and porting my xp installation under.

---

### Post by qzpac on 2011-06-06
[SIZE=2]OS: Ubuntu version 11.04 Final and Windows Server 2008 Standard
Motherboard : Gigabyte GA-H67M-D2-B3
BIOS Type/Date/Version: Award Modular v6.00PG
Processor : Intel Core i3-2100CPU - 3.10GHz
Chipset: Intel H67 chipset
Ram :  Kingston 4GB
HDD : 500Gb seagate sata

I have 2 OS: [/SIZE] [SIZE=2]
1. Ubuntu version 11.04 Final 
2. Windows Server 2008 Standard

Ubuntu 11.04 with wubi installed.

If i do migrate over a wubi installed to create ext4 & swap partitions[/SIZE][SIZE=2]  as a standalone ubuntu bootloader instead of a windows boot manager,  will all my data and desktop setting on ubuntu gone when migrating?

Can i just migrate without resizing my windows partition?[/SIZE]

---

### Post by bcbc on 2011-06-06
qzpac,
You have to create the partition(s) before migrating. You can migrate without resizing your windows partition only if you already have available partitions, or you migrate to another drive.

The migrated install will be the same as your current wubi install (the same data, installed programs and settings).

---

### Post by life in color on 2011-06-06
I'm considering moving Wubi to a new partition but I'm afraid I'm going to mess it up and make my computer inoperable, the only thing that looks sketchy to me is the /dev/sda5 portion. Here's a scenario: say I split my partition in two and I have 'partition 1' and 'partition 2' and I wanted to put Wubi on partition 2, would I simply replace '/dev/sda5' with 'partiton 2' in the sudo terminal code or is there more to it?

---

### Post by bcbc on 2011-06-06
> **life in color said:**
> I'm considering moving Wubi to a new partition but I'm afraid I'm going to mess it up and make my computer inoperable, the only thing that looks sketchy to me is the /dev/sda5 portion. Here's a scenario: say I split my partition in two and I have 'partition 1' and 'partition 2' and I wanted to put Wubi on partition 2, would I simply replace '/dev/sda5' with 'partiton 2' in the sudo terminal code or is there more to it?

That's pretty much it - you just change the target partition to the one you want to migrate to. 

I just picked /dev/sda5 as it's the first logical partition number - which is the most common migration scenario:
Usually it makes sense to create an extended partition, and then one or more logical partitions. This allows more flexibility as there is a hard max of 4 primary partition in a MBR partition table.

If you only have 1 primary this may not concern you now, but in the future you might want a separate partition for /home and maybe one for /boot (it's a little easier to manipulate logical partitions than deleting and replacing primary partitions).

PS please backup prior to partitioning as there is always a small risk of data loss.

---

### Post by life in color on 2011-06-06
ok I don't have anything important on the computer though so the only data I'm worried about would be anything necessary to download Ubuntu

---

### Post by life in color on 2011-06-07
I made a new partition labeled /dev/sda3 then went into terminal and input "sudo bash wubi-move-2.0.sh /dev/sda3" and got the error:
"bash: wubi-move-2.0.sh: No such file or directory"
yet I have 'wubi-move-2.0.sh' in my downloads folder.

---

### Post by bcbc on 2011-06-07
> **life in color said:**
> ok I don't have anything important on the computer though so the only data I'm worried about would be anything necessary to download Ubuntu

Okay... for wubi installs 9.10 to 11.04 there's nothing to download other than the migration script from post #1. Everything you need is already running under Wubi.

> **life in color said:**
> I made a new partition labeled /dev/sda3 then went into terminal and input "sudo bash wubi-move-2.0.sh /dev/sda3" and got the error:
"bash: wubi-move-2.0.sh: No such file or directory"
yet I have 'wubi-move-2.0.sh' in my downloads folder.

Go to terminal, change to the Downloads directory and make sure it is there before running:
```
cd Downloads
ls

```

---

### Post by life in color on 2011-06-07
Never mind I just moved wubi-move-2.0.sh to my home folder and now its working, thanks a trillion.

---

### Post by bcbc on 2011-06-07
> **life in color said:**
> Never mind I just moved wubi-move-2.0.sh to my home folder and now its working, thanks a trillion.

That works too ;)

You're welcome!

---

### Post by dinogoesmoo on 2011-06-14
I'm new to this as well. I really love Ubuntu and I wanna get rid of Windows but I'm honestly not sure what I'm doing D: I used Wubi to dual-boot Windows 7 Eternity and Ubuntu. I downloaded the file you said to but I'm not really sure what the difference is between "with swap" and "without swap" and whenever I type either one of them into the terminal, it says "no such file or directory exists" or something like that :( help?? :(

---

### Post by bcbc on 2011-06-14
> **dinogoesmoo said:**
> I'm new to this as well. I really love Ubuntu and I wanna get rid of Windows but I'm honestly not sure what I'm doing D: I used Wubi to dual-boot Windows 7 Eternity and Ubuntu. I downloaded the file you said to but I'm not really sure what the difference is between "with swap" and "without swap" and whenever I type either one of them into the terminal, it says "no such file or directory exists" or something like that :( help?? :(

Please go into gparted and take a screen shot showing the partition you want to migrate to. If you prefer you can run the command "sudo fdisk -l" (that's lower case -L) from the terminal and paste the response back here.

Also here is an intro to swap: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Hope that helps!

---

### Post by moshekarako on 2011-06-26
working perfectly on Lenovo X61 Tablet (Ubuntu 11.04)

Thanks.

---

### Post by Josep_Caselles on 2011-06-30
Hi everyone,

It's my first post, so I'm a noob here. I've been playing a little bit for a few days with ubuntu and wubi, and want to migrate to a partition. I've reduced de free space of one of the existing partitions that I have, in order to format this free space in two partitions, the one for the linux and the other for swap. 

My problem comes here: I use an Asus Eee Pc, and it already comes with 4 partitions, one for the windows 7 system files, one for my stuff, other with the extremly usefull utility to reinstall windows [remember that as being a netbook, my computer doesn't have CD, and I don't have the Windows install CD, all I have it's this partition] and another one that I have no idea for what is it, but I supose it's needed somewhat. 

I don't want to get rid of the windows 7; I could reformat the partition where I have my stuff, but I will need to have a dedicated partition anyway. The problem, then it's that I can't creat any other partition, since the maximum of primary partitions is 4. 

Then I realized that this tutorial migrates linux and swap into sda5 and sda6. If I'm not wrong that means logical partitions [from an extended partition] sorry if this make no sense, I've just started learning all this concepts and else, so I may be totally wrong. 

It is possible to migrate to an extended partition? How could I organize it [maybe change my stuff partition to an extended one?]

Thank you very much for the help; if this question is out of the threat, I would apreciate if you direct me to the right threat. And finally, excuse me for my possible mistakes with the English, I don't know if I expressed good my problem.

---

### Post by bcbc on 2011-06-30
> **moshekarako said:**
> working perfectly on Lenovo X61 Tablet (Ubuntu 11.04)

Thanks.

Thanks for the feedback!

---

### Post by bcbc on 2011-06-30
> **Josep_Caselles said:**
> Hi everyone,

It's my first post, so I'm a noob here. I've been playing a little bit for a few days with ubuntu and wubi, and want to migrate to a partition. I've reduced de free space of one of the existing partitions that I have, in order to format this free space in two partitions, the one for the linux and the other for swap. 

My problem comes here: I use an Asus Eee Pc, and it already comes with 4 partitions, one for the windows 7 system files, one for my stuff, other with the extremly usefull utility to reinstall windows [remember that as being a netbook, my computer doesn't have CD, and I don't have the Windows install CD, all I have it's this partition] and another one that I have no idea for what is it, but I supose it's needed somewhat. 

I don't want to get rid of the windows 7; I could reformat the partition where I have my stuff, but I will need to have a dedicated partition anyway. The problem, then it's that I can't creat any other partition, since the maximum of primary partitions is 4. 

Then I realized that this tutorial migrates linux and swap into sda5 and sda6. If I'm not wrong that means logical partitions [from an extended partition] sorry if this make no sense, I've just started learning all this concepts and else, so I may be totally wrong. 

It is possible to migrate to an extended partition? How could I organize it [maybe change my stuff partition to an extended one?]

Thank you very much for the help; if this question is out of the threat, I would apreciate if you direct me to the right threat. And finally, excuse me for my possible mistakes with the English, I don't know if I expressed good my problem.
Hi (and welcome to the forums). 

If you already have 4 primary partitions, you have to delete one of these in order to create an extended. Then within the extended you can create logical partitions. If the partition you delete doesn't have enough space you may have to also resize another primary partition prior to creating the extended.

1. Even with a netbook you can create a full windows restore image to a USB stick. I'm not sure about Asus, but e.g. on a toshiba netbook it contains a utility that allows you to create a USB that will factory restore the netbook. 
2. You can also create a Windows repair USB. The Windows utility will only create a repair CD, but if you look on the net there are instructions to create a repair USB. (I've done this on the netbook).
3. Backup all your data prior to partitioning (not just from the partition you plan to delete).
4. It's a good idea to have an Ubuntu USB as well. It's easy to migrate a Wubi install on a netbook, but if something goes wrong you need a way to repair it.

If you have any questions feel free to ask.

PS I don't really have a recommended partitioning guide to link to. There are many out there - you just have to find one that explains things clearly and works for you. 
What I try and do is partition as much as possible using windows tools (for Vista/7). e.g. delete, split, create an extended. For the actual linux partitions I use gparted. That's my personal decision.
For Windows XP you have little choice but to use GParted or another partitioning tool.

---

### Post by Josep_Caselles on 2011-07-01
oh, thank's a lot for answering that quick! 

ok, then I will try to delete my stuff partition and make it an extended one with logical partitions. But then, Will I be able to migrate mi wubi linux to those logical partitions [system files and swap]? Is there any problem with having an OS in a logical partition? and the bootloader,what happens with it?

thank you! I will try it anyway, I would tell you if something goes wrong! 

PS When you finally migrate the wubi, you get exactly the same as if you would install the ubuntu in the partition for the first time [I mean, the normal way, not wubi], or it still has some diferences that make it worse?

---

### Post by bcbc on 2011-07-01
> **Josep_Caselles said:**
> oh, thank's a lot for answering that quick! 

ok, then I will try to delete my stuff partition and make it an extended one with logical partitions. But then, Will I be able to migrate mi wubi linux to those logical partitions [system files and swap]? Is there any problem with having an OS in a logical partition? and the bootloader,what happens with it?

thank you! I will try it anyway, I would tell you if something goes wrong! 

PS When you finally migrate the wubi, you get exactly the same as if you would install the ubuntu in the partition for the first time [I mean, the normal way, not wubi], or it still has some diferences that make it worse?

You can boot linux from a logical partition. That's not an issue. The recommended method is to install the grub2 bootloader. This works well except in [some circumstances]("http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html") (when certain windows programs use parts of the boot track for hiding data).

Wubi Ubuntu is identical to a normal install (except for the part that allows you to run from a loop device). So the migrated install is the same as a fresh install (except you keep your data/programs/customizations). 

PS you don't actually migrate [swap]("https://help.ubuntu.com/community/SwapFaq"). You're just creating a new swap partition.

---

### Post by Josep_Caselles on 2011-07-01
uau, thank you a lot, now I have almost everything clear! Only one last thing: I've tried to run it, an after a few problems I almost manage to make it work, but at the last time it says my sda6 partition is not a swap partition. Should I format it as a swap partition? [I've found a very clear tutorial] 

thank you very much! my last question, really!

---

### Post by bcbc on 2011-07-01
> **Josep_Caselles said:**
> uau, thank you a lot, now I have almost everything clear! Only one last thing: I've tried to run it, an after a few problems I almost manage to make it work, but at the last time it says my sda6 partition is not a swap partition. Should I format it as a swap partition? [I've found a very clear tutorial] 

thank you very much! my last question, really!

Yes. The current script actually checks for a swap partition (it should just check the partition type - that will eventually be fixed when I get around to it). If you use Gparted to change it to a swap partition, that will do it. The target partition for the migration should also be type "83 - linux". If you set this as "ext4" in gparted it will do that for you as well.

Then when you run:
```
sudo fdisk -l 
```
it will look similar to the picture here: [http://4.bp.blogspot.com/-xjnIR-P8_II/TdclPvCpmJI/AAAAAAAACIE/MzYEAllHtZ8/s640/hmp4.png](http://4.bp.blogspot.com/-xjnIR-P8_II/TdclPvCpmJI/AAAAAAAACIE/MzYEAllHtZ8/s640/hmp4.png)

---

### Post by Josep_Caselles on 2011-07-02
Done! You really make this easy! It's fantastic to have people like you taking care of the noobs like me, it really make me think about getting completely rid of windows forever! this is what makes the diference.

thank's a lot! Now works fine!

---

### Post by jonnystatts on 2011-07-02
So, I am new to this whole process as well, and so might be a little pedantic about this as I want to understand what's going on. 

When I look in Ubuntu's disk utility I see I have a 31 GB root partition /dev/loop0, and then on the main hard disk I have a bunch of stuff: 1.6 GB /dev/sda1, 260 GB mounted at /host and called /dev/sda2, a 226 GB partition that is simply labelled as "free" whose device name is /dev/sda, and then 12 GB called /dev/sda4. 

Ok, so two questions given this. First, from where exactly is wubi running? That is, should I be making partitions in /dev/sda or /dev/sda2... or should I be messing around with the /dev/loop0? I'm sorry if this question simply doesn't make any sense. 

Second, I am under the impression that I need logical partitions to do this migration correctly, but when I partition this stuff up, I never seem to get a /dev/sda5, for example... so my question is does that matter? Can I just divide /dev/sda into, say, an 8 gb piece for swap and whatever's left for home and root and then just run this script simply giving it their names? 

Anyway, thanks for putting this info up... this forum is awesome!

---

### Post by bcbc on 2011-07-02
> **Josep_Caselles said:**
> Done! You really make this easy! It's fantastic to have people like you taking care of the noobs like me, it really make me think about getting completely rid of windows forever! this is what makes the diference.

thank's a lot! Now works fine!

Great! You're welcome :)

---

### Post by bcbc on 2011-07-02
> **jonnystatts said:**
> So, I am new to this whole process as well, and so might be a little pedantic about this as I want to understand what's going on. 

When I look in Ubuntu's disk utility I see I have a 31 GB root partition /dev/loop0, and then on the main hard disk I have a bunch of stuff: 1.6 GB /dev/sda1, 260 GB mounted at /host and called /dev/sda2, a 226 GB partition that is simply labelled as "free" whose device name is /dev/sda, and then 12 GB called /dev/sda4. 

Ok, so two questions given this. First, from where exactly is wubi running? That is, should I be making partitions in /dev/sda or /dev/sda2... or should I be messing around with the /dev/loop0? I'm sorry if this question simply doesn't make any sense. 

Second, I am under the impression that I need logical partitions to do this migration correctly, but when I partition this stuff up, I never seem to get a /dev/sda5, for example... so my question is does that matter? Can I just divide /dev/sda into, say, an 8 gb piece for swap and whatever's left for home and root and then just run this script simply giving it their names? 

Anyway, thanks for putting this info up... this forum is awesome!
1. /dev/loop0 is a virtual partition - don't make any changes to it. 
2. The script doesn't require logical partitions to migrate to. But in your specific case you have used 3 primary partitions so if you want to create more than one (you get max 4 primary partitions), you need to first create an extended partition in that free space and then the logicals.

You can use GParted. It's available on the Ubuntu CD (live environment) or from Wubi you can install it: from software centre enter *gparted* in the search box and select "Gnome partition editor" or from command line:
```
sudo apt-get install gparted
```

GParted will show that "free space" as unallocated. You can create an extended partition in that space (/dev/sda3). Then you can create logical partitions within that.

Unfortunately the script does not permit you to migrate your /home to a separate partition. This feature might be available in the future, but you could do this manually after the migration. 

If you have any other questions - fire away. I'm going to be out most of the day... but I'll answer when I can.

---

### Post by bcbc on 2011-07-06
The Wubi migration Howto avoids discussing how to partition - which would take another entire howto. I've also avoided recommending a particular guide - many are either too old or too technical. However here is a guide that is recent (written for 10.10) and seems to be very well written: [http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

It shows how to manually partition from a live CD using GParted - and also to install to those partitions. You can skip the installation part if you're migrating since the Wubi migration script takes care of that.

---

### Post by ProffesorT on 2011-07-08
So I was trying to use this to migrate to the full version in my Acer netbook. This is when I discovered I only have--
/dev/sda1
/dev/sda2
/dev/sda3

So I tried doing what the guy on page 2 did, but it didn't work either. It would show errors along the lines of having to dismount partitions and partitions being not empty, and that it was not a swap partition.

Any advice?
I'm a newbie to bash.
>:U

---

### Post by bcbc on 2011-07-08
> **ProffesorT said:**
> So I was trying to use this to migrate to the full version in my Acer netbook. This is when I discovered I only have--
/dev/sda1
/dev/sda2
/dev/sda3

So I tried doing what the guy on page 2 did, but it didn't work either. It would show errors along the lines of having to dismount partitions and partitions being not empty, and that it was not a swap partition.

Any advice?
I'm a newbie to bash.
>:U
You need to prepare partitions for the migration. The script will not allow you to migrate to a mounted partition and it will not allow migration to a non-empty partition. If you want the migration script to setup a swap partition, it requires that the partition is already set up as swap.

What you ideally will have for the migration are two partitions, one ext4 partition for / (root) and one swap partition for swap. You can prepare these using GParted. Please refer to [this]("http://ubuntuforums.org/showpost.php?p=11021363&postcount=418") on how to partition manually.

---

### Post by glisstech on 2011-07-09
I just wanted to say thank you for a great utility. Migrated my WUBI install to a 750GB hard drive with no issue whatsoever and everything works perfectly.

I have been a Windows Sys Admin for several years, and am greatly enjoying the level of support I am receiving from the Linux community as a whole. Its a far cry better than what I am used to.

Keep up the GREAT WORK!!!

---

### Post by bcbc on 2011-07-10
> **glisstech said:**
> I just wanted to say thank you for a great utility. Migrated my WUBI install to a 750GB hard drive with no issue whatsoever and everything works perfectly.

I have been a Windows Sys Admin for several years, and am greatly enjoying the level of support I am receiving from the Linux community as a whole. Its a far cry better than what I am used to.

Keep up the GREAT WORK!!!
You're welcome - thanks for the feedback!

---

### Post by vivakh on 2011-07-18
Hi there.

Thank you for this amazing script. I've used this several times to migrate wubi installs. 

I have a question though. Will this method work to migrate linux mint 11 that's installed via mint4win? LM 11 is based upon ubuntu and the mint4win is based on wubi. Will it be able to migrate?

---

### Post by bcbc on 2011-07-18
> **vivakh said:**
> Hi there.

Thank you for this amazing script. I've used this several times to migrate wubi installs. 

I have a question though. Will this method work to migrate linux mint 11 that's installed via mint4win? LM 11 is based upon ubuntu and the mint4win is based on wubi. Will it be able to migrate?
I've never used Mint4win, so I can't make any guarantees. But I'd expect that if Mint is comparable to the current Ubuntu setup (in terms of the versions of grub/lupin/etc), it should be compatible with the migration script. 

You should be able to try it without risk to mint4win with the --no-bootloader option. If that works fine then running it normally will probably work as well.

PS Thanks for the feedback - let us know how it goes.

---

### Post by vivakh on 2011-07-18
Will try it out and post my outcome. Thanks much :)

---

### Post by vivakh on 2011-07-20
Doesn't work guys. When i enter, "sudo bash wubi-move-2.0.sh /dev/sdb2", it returns the message "invalid wubi format or incorrect root.disk"

:(
Are there any other ways to do this?

---

### Post by bcbc on 2011-07-20
> **vivakh said:**
> Doesn't work guys. When i enter, "sudo bash wubi-move-2.0.sh /dev/sdb2", it returns the message "invalid wubi format or incorrect root.disk"

:(
Are there any other ways to do this?

Ah okay. I was a little strict about validating the wubi install :( and since I don't use Mint.... I didn't consider it, but obviously it's not going to be in the \ubuntu directory)

```
    # Irregular root.disk - don't allow (at this time) since it's possible
    # to migrate using the --root-disk= option anyway.
    if [ "$loop_file" != "/host/ubuntu/disks/root.disk" ]; then
        return 2 # migrate not permitted
    fi
```

What is the content of your /etc/fstab file?

PS or you could edit the script - just put '#' before each of those lines:

```
    # Irregular root.disk - don't allow (at this time) since it's possible
    # to migrate using the --root-disk= option anyway.
    [COLOR="DarkRed"]#[/COLOR]if [ "$loop_file" != "/host/ubuntu/disks/root.disk" ]; then
    [COLOR="DarkRed"]#[/COLOR]    return 2 # migrate not permitted
    [COLOR="DarkRed"]#[/COLOR]fi
```

---

### Post by miciurin on 2011-07-28
I am writing from a fresh transfer of kubuntu into its own 500GB partition, so it is obviously working. Thank you for sharing this excellent script.:)

---

### Post by bcbc on 2011-07-28
> **miciurin said:**
> I am writing from a fresh transfer of kubuntu into its own 500GB partition, so it is obviously working. Thank you for sharing this excellent script.:)

You're welcome :)

---

### Post by errrn on 2011-07-30
I finally did it, and it went FLAWLESSLY. usually that never happens to me, but anyway. I didn't use any swap partition. 

great work, and many thanks!

btw, it's now safe for me to uninstall/delete the ubuntu installation I did in windows beofre, or is it? what I actually want is not to have any OS selection menu after I choose windows in the ubuntu grub.

thanks again!

---

### Post by bcbc on 2011-07-30
> **errrn said:**
> I finally did it, and it went FLAWLESSLY. usually that never happens to me, but anyway. I didn't use any swap partition. 

great work, and many thanks!

btw, it's now safe for me to uninstall/delete the ubuntu installation I did in windows beofre, or is it? what I actually want is not to have any OS selection menu after I choose windows in the ubuntu grub.

thanks again!

You're welcome :)

Yes it's safe to uninstall the Wubi install since grub2 is now in charge of booting (the first menu you see is grub). The second menu is the Windows boot manager which will be hidden once you uninstall Wubi. To do this go to the control panel, Add/remove programs, and double click on "Ubuntu".

---

### Post by intel design on 2011-08-04
I have read your post migrate wubi install to partition! 

Here is my problem. the original wubi install is located on my HD:

telesismedia@ubuntu:/host/ubuntu$ ls
disks  install  Ubuntu.ico  uninstall-wubi.exe  winboot

It is mounted at /media/SYSTEM/  In Ubuntu it is  /dev/sda1

The original root.disk is now an 18GB file type EXT4. In Ubuntu it is /dev/loop0. 

In Windows 1 recently shrunk the original partition & created a new partition calling the volume "VHD_WUBI" However The main issues are as follows /dev/sda1

has shrunk but /media/SYSTEM/ IS STILL MOUNTED AND IS /dev/sda1. The windows boot manager is on /dev/sda3 in volume "VHD_WUBI"

When I run the "fdisk -l command I see that the 18GB root.disk  is partly located at /dev/sda3 I gave it a volume name of VHD_WUBI it was
created in Ubuntu using the GPart partition editor tool but it remains unmounted. 

gedit fstab gives me this info:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /host    fuseblk    defaults,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096    0    0
/dev/sda1    /media/SYSTEM    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sda3       /media/VHD_WUBI ntfs-3g defaults,user,locale=en_US.utf8 0       0



WHILE TRYING TO BOOT INTO UBUNTU FROM THE WINDOWS BOOT MANAGER 
THE UBUNTU SCREEN MESSAGE READS AS FOLLOWS: 
"AN ERROR HAS OCCURRED WHILE MOUNTING 
/HOST/UBUNTO/DISK/SWAP.DISK" 
 
 
"PRESS S TO SKIP MOUNTING OR M FOR MANUAL RECOVER"

I press "S" and am able to use Ubuntu normally without the migratation of wubi install to partition! I nned advice on how
to proceed!

---

### Post by bcbc on 2011-08-04
*intel design*,
You need to run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").I don't fully understand what you have done and this may help. Your /etc/fstab isn't right for Wubi and I'm not sure what you mean by your root.disk is partly located on /dev/sda3.

I think the bootinfoscript will be the easiest way to proceed.

---

### Post by altheablue on 2011-08-05
Thank you so much for this! Worked beautifully (touches wood). I'm now one small partition away from being Windows-free. ;)

---

### Post by intel design on 2011-08-05
I will take a look at  the bootinfoscript you mention!

---

### Post by bcbc on 2011-08-05
> **altheablue said:**
> Thank you so much for this! Worked beautifully (touches wood). I'm now one small partition away from being Windows-free. ;)
You're welcome :)

---

### Post by intel design on 2011-08-06
This note is for altheablue! Since you have had apparent success, what is the process like running "the boot_info_script"! I am reluctant to run the script fearing that it will alter my wubi master boot record! I admit I have a confidence deficit! bcbc post intrigued me but I know for a fact that  [http://ubuntuforums.org/showthread.php?t=1519354------HOWTO:](http://ubuntuforums.org/showthread.php?t=1519354------HOWTO:) migrate wubi install to partition caused my terminal to freeze up after inputing the command: 
sudo bash wubi-move-2.0.sh [COLOR=red]/dev/sda5[/COLOR]

---

### Post by altheablue on 2011-08-06
> **intel design said:**
> This note is for altheablue! Since you have had apparent success, what is the process like running "the boot_info_script"! I am reluctant to run the script fearing that it will alter my wubi master boot record! I admit I have a confidence deficit! bcbc post intrigued me but I know for a fact that  [http://ubuntuforums.org/showthread.php?t=1519354------HOWTO:](http://ubuntuforums.org/showthread.php?t=1519354------HOWTO:) migrate wubi install to partition caused my terminal to freeze up after inputing the command: 
sudo bash wubi-move-2.0.sh [COLOR=red]/dev/sda5[/COLOR]

Don't worry, the bootinfo script won't alter anything. It just tells you (and the experts ;)) how your system and partitions are configured. Fear not! :cheers:

---

### Post by bcbc on 2011-08-07
intel design,

If you look through the forums you'll see that the bootinfoscript is requested and run by many people on a daily basis. If there were a bug, then we'd know about it. So, as *altheablue* said, it's safe to run.

Regarding the script, you say the terminal froze when you attempted to migrate. Do you have any more info than that? The script goes through a number of phases:
1 Validation
a. attempts to mount the target/checks the swap if any
b. makes sure it's big enough (compared to the used space on the wubi)
c. makes sure the target is empty
This is a simplified list e.g. it also checks whether you're migrating a wubi install or a normal install; and whether it has grub-legacy.

2. User input 
All the questions that need answers are asked. No changes have been made up to this point. If the user decides not to format the target partition, the script ends.

3. The migration begins - this doesn't modify the Windows install or the Wubi install. It does replace the windows bootloader if you request it (recommended).
a. format target partition and swap
b. copy all files (this takes a long time depending on the size of the wubi install)
c. modify the target to make it a standalone ubuntu install
d. setup grub

4. Make the new install bootable from wubi
a. updates the wubi grub menu to detect the new install.

So, this is a bit of a long post. But it would help to know at which point the terminal froze - if it was during the long file copy stage then it may not have frozen at all. If it didn't get past the 'format confirmation' then no changes would have been made. It also helps to know what action you took at that point e.g. turning off a computer running a wubi install is a bad idea (instead use Alt+SysRq R-E-I-S-U-B).

In your original post you mentioned that you had shrunk /dev/sda1 but "/media/system is still mounted". This will automount because it's in /etc/fstab. You also have an entry for /host which is non-standard Wubi (the /host is automatically mounted prior to /etc/fstab being processed). And finally there are other entries in /etc/fstab that I'd expect, but are missing, like a mountpoint for / and swap.

You also mention that when you run "*fdisk -l command I see that the 18GB root.disk is partly located at /dev/sda3*". The fdisk -l output doesn't show any data files (which is what the root.disk is).

Anyway, if you can provide this information (and anything else you can think of that may help), I'd be more than happy to take a look to try to understand what has happened and how to get your computer working again.

---

### Post by minipot on 2011-08-08
I tryed manual partitioning (autamatic didn't work) and it said coudld not start dev/sda5 ---no such file or directory. what do I do?

---

### Post by minipot on 2011-08-08
I tryed autamatic this time and it only gave me the option off /dev/sda1. what should I do?
and it wont let me select. It goes straight back to minipot@ubuntu:~/Downloads$

---

### Post by bcbc on 2011-08-08
> **minipot said:**
> I tryed autamatic this time and it only gave me the option off /dev/sda1. what should I do?
and it wont let me select. It goes straight back to minipot@ubuntu:~/Downloads$

Hi minipot, This *Howto* covers the migration of a Wubi install. It's not geared to assisting users on partitioning. The script requires that the partitions are already setup.

When you refer to automatic partitioning, I'm not sure what that means - outside of the context of the Ubuntu installer. If you're using the partitioning guide that I did provide a link for, those instructions need to be run from a live CD unless you are using Vista/7 (because Vista/7 can shrink a partition that is in use, whereas GParted cannot).

You haven't provided a lot of info - so to be honest - I'm not really certain what exactly you are doing. Please consider screenshots and copy and pasting the terminal output so I can see what you are doing and what the error is.

Thanks

---

### Post by minipot on 2011-08-09
Ive found the problem I didnt partition my disk already sorry:rolleyes:
Okfollowing the instructions here [http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html") (the one u suggested) how would I do this in wubi?
I'm on windows 7 and the guide baffles me slightly by atamatic I mean the 2 options u gave automatic migration or manual (remember the first post)
ok CAN U ACTUALLY INCLUDE SOMETHING FOR NOOBS i ve been reding ur [http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html") link again and again and looking for how to partition a system nothing makes sense whats this /dev/sda thing about how do I actually create a partition my system to move wubi too.

---

### Post by minipot on 2011-08-09
sorry for yelling at you in txt way Ive found a tut dont worry

---

### Post by bcbc on 2011-08-09
> **minipot said:**
> sorry for yelling at you in txt way Ive found a tut dont worry

You referred to the automatic or manual migration. Please don't use the manual migration. It's there more for 'documentation' and for the curious who enjoy that sort of thing. For normal users, the script contains a lot of checks that prevent user error.

PS partitioning is generally safe, but there is always a small risk. Please backup before hand.

---

### Post by victoriatao on 2011-08-10
HELLO!
My problem is 
 
'target_partition (/dev/sda5) must be a valid partition'

I am a newer, I really don't know why my partition is unvalid.. Anyway..is it possible for me to migrate? I just use the default partition on Win7

Thank you very much!

---

### Post by bcbc on 2011-08-10
> **victoriatao said:**
> HELLO!
My problem is 
 
'target_partition (/dev/sda5) must be a valid partition'

I am a newer, I really don't know why my partition is unvalid.. Anyway..is it possible for me to migrate? I just use the default partition on Win7

Thank you very much!

The script will migrate a wubi install to a partition, but that partition must be already present i.e. you need to create them beforehand. There is a link on the first post that describes how to partition manually ([here]("http://members.iinet.net.au/~herman546/p22.html")). 

If you think you've already created the partitions, please post the output of:
```
sudo fdisk -l
```
That's a lower case -L. 

Thanks

---

### Post by mahin on 2011-08-13
I have migrated to a new partition using your script without any difficulties...thanks alot.
Is it possible to uninstall the wubi which i installed in the C: before migrating to the new partition.  
Thank you.

---

### Post by bcbc on 2011-08-13
> **mahin said:**
> I have migrated to a new partition using your script without any difficulties...thanks alot.
Is it possible to uninstall the wubi which i installed in the C: before migrating to the new partition.  
Thank you.
Yes, once you've booted the migrated install and confirmed everything is working, you can uninstall the Wubi - boot windows and go to Control Panel, Add/remove programs, Ubuntu.

The migrated install is not dependent in any way on the wubi install (unless you chose not to install the grub bootloader and are booting it from the wubi grub menu - in which case you'd need to install the grub bootloader first).

---

### Post by Gikoskos on 2011-08-20
Can i use this guide to migrate in a new hard drive?
I mean is it safe?:confused:

---

### Post by bcbc on 2011-08-20
> **Gikoskos said:**
> Can i use this guide to migrate in a new hard drive?
I mean is it safe?:confused:
Yes, you can migrate to a new drive. Note that the script will only install the grub2 bootloader on the drive you migrate to. e.g. if you migrate to /dev/sdb1 it will only allow the bootloader to be installed on /dev/sdb. So it won't make changes to the way you currently boot (or your current drive) - you can adjust that yourself later on, once you are happy with the migration.

Immediately following the migration, you will be able to boot the migrated install either by modifying the drive boot order or using the Wubi grub menu.

Hope that helps

---

### Post by Gikoskos on 2011-08-20
> **bcbc said:**
> Yes, you can migrate to a new drive. Note that the script will only install the grub2 bootloader on the drive you migrate to. e.g. if you migrate to /dev/sdb1 it will only allow the bootloader to be installed on /dev/sdb. So it won't make changes to the way you currently boot (or your current drive) - you can adjust that yourself later on, once you are happy with the migration.

Immediately following the migration, you will be able to boot the migrated install either by modifying the drive boot order or using the Wubi grub menu.

Hope that helps
Thanks for the reply!
Great guide btw:D

---

### Post by bcbc on 2011-08-20
> **Gikoskos said:**
> Thanks for the reply!
Great guide btw:D

No prob. Thanks ;)

---

### Post by kroq-gar78 on 2011-08-20
Thanks dude! Great script! Worked flawlessly AFAIK.
In fact, I think it worked better than flawlessly - my boot time has been cut in half from ~90 seconds to ~45 seconds (I'm SOOOOOOO sticking with ext(4) from now on vs. NTFS)

Awesome work!

Sincerely,
kroq-gar78

---

### Post by bcbc on 2011-08-20
> **kroq-gar78 said:**
> Thanks dude! Great script! Worked flawlessly AFAIK.
In fact, I think it worked better than flawlessly - my boot time has been cut in half from ~90 seconds to ~45 seconds (I'm SOOOOOOO sticking with ext(4) from now on vs. NTFS)

Awesome work!

Sincerely,
kroq-gar78

Great! You're welcome :)

That's a pretty dramatic increase in boot time!

---

### Post by kroq-gar78 on 2011-08-20
Yep, and for the better! Ubuntu is the best......

---

### Post by bcbc on 2011-08-20
oops I meant 'decrease' ;)

---

### Post by sdphuse on 2011-08-30
solution to resize the ubuntu partition install within windows

1 BOOT FROM LIVE CD
2 BACKUP ROOT DISK
  go to console 

3 sudo mkdir -p /media/win 

4 sudo mount /dev/sda5 /media/win

5 check the size of the root.disk
    du -h --apparent-size /media/win/ubuntu/disks/root.disk
6 fsck -f  /media/win/ubuntu/disks/root.disk

7 resize2fs /media/win/ubuntu/disks/root.disk 25G
    e.g. 25G specifies the size you want to resize
8 sudo reboot

9   remove the cd from cdrom drive first
10 go to normal ubuntu boot

11 open the console 
12 df -kh 
sandip@ubuntu:~$ df -kh
Filesystem            Size  Used Avail Use% Mounted on
[COLOR=Blue]**/dev/loop0             25G  5.9G   18G  26% /**[/COLOR]
none                  491M  232K  491M   1% /dev
none                  497M  580K  496M   1% /dev/shm
none                  497M   96K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
/dev/sda5             108G   21G   87G  20% /host
/dev/loop1            9.2G  150M  8.6G   2% /vdisk

---

### Post by bcbc on 2011-08-30
sdphuse,

I think your post probably belongs in the [HOWTO: Resize the WUBI virtual disk]("http://ubuntuforums.org/showthread.php?t=1625371") thread (from where those instructions originated - see post #2).

This thread is concerned with migrating a Wubi install to a partition.

---

### Post by glindste on 2011-09-07
Thanks alot! Your script worked perfectly! It feels so much cleaner to have a separate ubuntu install independent of windows. And the boot time has also improved. :D
Great work!

---

### Post by bcbc on 2011-09-07
> **glindste said:**
> Thanks alot! Your script worked perfectly! It feels so much cleaner to have a separate ubuntu install independent of windows. And the boot time has also improved. :D
Great work!
Great. You're welcome :)

---

### Post by s_dv on 2011-09-09
hello bcbc

thank u for such a great work
i just migrated my ubuntu
first i used disk utility to create a ext4 partition and a swap partition and then i migrated.
it went smooth except for one thing
here is the code

                                 abc123@ubuntu:~$ cd Downloads/  
 abc123@ubuntu:~/Downloads$ ls  
 wubi-move-2.0.sh  wubi-move-2.0.sh.tar.gz  
 abc123@ubuntu:~/Downloads$ sudo fdisk -l  
 [sudo] password for abc123:  
 

 Disk /dev/sda: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Sector size (logical/physical): 512 bytes / 512 bytes  
 I/O size (minimum/optimal): 512 bytes / 512 bytes  
 Disk identifier: 0x2abe2abd  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *           1        3187    25599546    7  HPFS/NTFS  
 /dev/sda2            3188       19456   130680742+   f  W95 Ext'd (LBA)  
 /dev/sda5            3188        4158     7799526    7  HPFS/NTFS  
 /dev/sda6            4159        5433    10241406    7  HPFS/NTFS  
 /dev/sda7            5434        6708    10241406    7  HPFS/NTFS  
 /dev/sda8            6709        7983    10241406    7  HPFS/NTFS  
 /dev/sda9            7984        9258    10241406    7  HPFS/NTFS  
 /dev/sda10           9259       10533    10241406    7  HPFS/NTFS  
 /dev/sda11          10534       11808    10241406    7  HPFS/NTFS  
 /dev/sda12          11809       13083    10241406    7  HPFS/NTFS  
 /dev/sda13          13084       14358    10241406    7  HPFS/NTFS  
 /dev/sda14          14359       15633    10241406    7  HPFS/NTFS  
 /dev/sda15          15634       16908    10241406    7  HPFS/NTFS  
 /dev/sda16          16909       18183    10241406    7  HPFS/NTFS  
 /dev/sda17          18184       19456    10225341    7  HPFS/NTFS  
 abc123@ubuntu:~/Downloads$ sudo bash wubi-move-2.0.sh /dev/sda12 /dev/sda13  
 

 

 wubi-move-2.0.sh: Would you like the grub2 bootloader to be installed  
 wubi-move-2.0.sh: to drive /dev/sda? If you choose not to, you will  
 wubi-move-2.0.sh: still be able to boot your migrated install from  
 wubi-move-2.0.sh: your current install. 
 wubi-move-2.0.sh: Install grub bootloader to /dev/sda? (Y/N)  
 y  
 wubi-move-2.0.sh: Please close all open files before continuing.  
 wubi-move-2.0.sh: About to format the target partition (/dev/sda12).  
 wubi-move-2.0.sh: Proceed with format (Y/N)  
 y  
 wubi-move-2.0.sh: Formatting /dev/sda12 with ext4 file system  
 

 wubi-move-2.0.sh: Copying files - please be patient - this takes some time  
 wubi-move-2.0.sh: Creating swap...  
 

 wubi-move-2.0.sh: Starting chroot to the target install.  
 wubi-move-2.0.sh: Removing lupin-support on target... 



                                  wubi-move-2.0.sh: Grub bootloader installed to /dev/sda  
 wubi-move-2.0.sh: Updating the target grub menu...  
 wubi-move-2.0.sh: Exiting from chroot on target install...  
 

 wubi-move-2.0.sh: Updating current grub menu to add new install...  
 Generating grub.cfg ...  
 _cat: /boot/grub/video.lst: No such file or directory _ 
 Found linux image: /boot/vmlinuz-2.6.38-8-generic  
 Found initrd image: /boot/initrd.img-2.6.38-8-generic  
 Found Windows NT/2000/XP (loader) on /dev/sda1  
 Found Ubuntu 11.04 (11.04) on /dev/sda12  
 done  
 

 wubi-move-2.0.sh: Operation completed successfully.  
 abc123@ubuntu:~/Downloads$ 



it says [U]cat: /boot/grub/video.lst: No such file or directory 
[/U]is it an important file. i am completely new to ubuntu.

i am able to login and run internet.


please help

---

### Post by bcbc on 2011-09-09
> 
 wubi-move-2.0.sh: Updating current grub menu to add new install...  
[COLOR="Red"] Generating grub.cfg ...  
 _cat: /boot/grub/video.lst: No such file or directory _ 
 Found linux image: /boot/vmlinuz-2.6.38-8-generic  
 Found initrd image: /boot/initrd.img-2.6.38-8-generic  
 Found Windows NT/2000/XP (loader) on /dev/sda1  
 Found Ubuntu 11.04 (11.04) on /dev/sda12  
 done  
[/COLOR] 

 wubi-move-2.0.sh: Operation completed successfully.  
 abc123@ubuntu:~/Downloads$ 

s_dv,

You do not need to worry about that error. The output (in red above) is actually coming from the command "sudo update-grub" and it's a 'normal' output on current Wubi installs. If you boot your Wubi install (not your migrated one) and run that from a terminal, you'll see the same message.

Why do you get it? Traditionally Wubi has had a near empty /boot/grub directory (the grub.cfg plus a couple others). But in a normal install you get all the grub modules and some other config files. And one of these is the video.lst which is referred to in the grub scripts. Anyway... long story short, it tries to inject the contents of video.lst into the grub.cfg and doesn't find it.

So nothing to worry about. Enjoy! ;)

---

### Post by s_dv on 2011-09-10
thank you 
well i am a novice at ubuntu. still trying to find my feet here
once again thank you for your help.

---

### Post by stoneworrior on 2011-09-10
Fixed it myself thanks

---

### Post by qzpac on 2011-09-12
OS: Ubuntu version 11.04 Final and Windows Server 2008 Standard
Motherboard : Gigabyte GA-H67M-D2-B3
BIOS Type/Date/Version: Award Modular v6.00PG
Processor : Intel Core i3-2100CPU - 3.10GHz
Chipset: Intel H67 chipset
Ram :  Kingston 4GB
HDD : 500Gb seagate sata

I have 2 OS:
1. Ubuntu version 11.04 Final 
2. Windows Server 2008 Standard Trial

Ubuntu 11.04 with wubi installed.

Once my windows server expired, can i still use my wubi installed OS to access all windows data on my harddisk without migrating?

---

### Post by bcbc on 2011-09-12
qzpac,

it's in your best interests to migrate to a partition or install direct rather than relying on Wubi after your windows license has expired. While it may work (it's unlikely the windows boot manager will be locked out), you could still have issues if e.g. you need to run chkdsk.

---

### Post by TubbyT on 2011-09-18
Hi there, first of all, the migration went off without a hitch for me, great stuff. Here's my question though.

I see it's safe to uninstall wubi from Windows now, and that's well and good, but what led me to this in the first place is that after running ubuntu this way for a bit, I've come to not use Windows at all. I want to eliminate Windows altogether. My question is: is it safe to format the partition that Windows 7 is installed on and just add the free space to this partition, or do I need to format the entire hard drive and start fresh with ubuntu 11.04?

---

### Post by bcbc on 2011-09-18
> **TubbyT said:**
> Hi there, first of all, the migration went off without a hitch for me, great stuff. Here's my question though.

I see it's safe to uninstall wubi from Windows now, and that's well and good, but what led me to this in the first place is that after running ubuntu this way for a bit, I've come to not use Windows at all. I want to eliminate Windows altogether. My question is: is it safe to format the partition that Windows 7 is installed on and just add the free space to this partition, or do I need to format the entire hard drive and start fresh with ubuntu 11.04?

It's safe to format the windows partition (assuming you installed the grub bootloader, which is the default).

You can use that partition as a separate /home or even migrate your install over to it (the wubi migration script also moves normal ubuntu installs). 

Trying to remove the partition and resizing from a live CD/USB will probably take a long time (gparted can resize to the right quicker). Also take care when deleting/creating partitions as grub uses the partition number and/or the partition uuid to load it's modules and the grub.cfg (boot menu). So modifying partitions can interfere with this. At the least keep a bootable Ubuntu CD/USB handy.

---

### Post by TubbyT on 2011-09-18
Yeah I have the grub loader installed. By the way, I saw way earlier in the thread someone mentioning it didn't install. I got the same error message that it didn't install even though I chose to install it, however, when I rebooted, it was there and loaded fine.

As for migrating to that partition after I delete Windows, I'd already split my hard drive 50/50 so that wouldn't give me any more room than I have now. So you're saying for safety's sake I shouldn't try adding the free space I create by deleting Windows to this partition until I make a USB boot? (I have no CD drive.) Sorry for the repeated questions, I've only been using ubuntu for about a week and I've never messed with partitions or anything before this.

EDIT: Could I format the Windows partition and use it for extra storage without resizing the current partition? Like would I be able to simply save new files to that partition while running ubuntu from this partition? 

Thanks for your help.

---

### Post by Hakunka-Matata on 2011-09-18
> **TubbyT said:**
> Yeah I have the grub loader installed. By the way, I saw way earlier in the thread someone mentioning it didn't install. I got the same error message that it didn't install even though I chose to install it, however, when I rebooted, it was there and loaded fine.

As for migrating to that partition after I delete Windows, I'd already split my hard drive 50/50 so that wouldn't give me any more room than I have now. [COLOR=Red]So you're saying for safety's sake I shouldn't try adding the free space I create by deleting Windows to this partition until I make a USB boot? (I have no CD drive.)[/COLOR] Sorry for the repeated questions, I've only been using ubuntu for about a week and I've never messed with partitions or anything before this.

EDIT: Could I format the Windows partition and use it for extra storage without resizing the current partition? Like would I be able to simply save new files to that partition while running ubuntu from this partition? 

Thanks for your help.
[COLOR=Red]Since you have Grub installed to the MBR, you're safe.[/COLOR]
as bcbc stated: "It's safe to format the windows partition (assuming you installed the grub bootloader, which is the default).If the bootloader had not been installed, at that stage your computer would be unbootable, Windows bootloader in MBR pointing to a deleted partition.  @ that point, if you didn't have a liveCD/USB, you could take a break until you got one, then boot and fix the MBR, "install Grub".

---

### Post by Hakunka-Matata on 2011-09-18
> **Hakunka-Matata said:**
> [COLOR=Red]Since you have Grub installed to the MBR, you're safe.[/COLOR]
as bcbc stated: "It's safe to format the windows partition (assuming you installed the grub bootloader, which is the default)."[COLOR="SeaGreen"]**If the bootloader had not been installed, at that stage your computer would be unbootable, Windows bootloader in MBR pointing to a deleted partition**[/COLOR].  @ that point, if you didn't have a liveCD/USB, you could take a break until you got one, then boot and fix the MBR, "install Grub".
[COLOR="SeaGreen"]**ummmhh, is that statement completely accurate?**[/COLOR]

---

### Post by TubbyT on 2011-09-18
I have the grub loader installed I believe.

Before I did this migration, I'd get the Windows boot menu where I'd choose to boot Windows 7 or ubuntu. If I chose ubuntu, it'd give me the purple screen then give me an option of 4 versions of linux to boot or the Windows 7 boot loader. Since doing the migration (and I chose to install grub loader) it automatically gives me the purple screen with the four linux choices when I boot up. 

Am I understanding correctly that this means I have the grub loader installed?

Sorry for the noob questions, I'm just nervous about doing this until I'm 100% sure I've got this right.

---

### Post by bcbc on 2011-09-18
> **TubbyT said:**
> I have the grub loader installed I believe.

Before I did this migration, I'd get the Windows boot menu where I'd choose to boot Windows 7 or ubuntu. If I chose ubuntu, it'd give me the purple screen then give me an option of 4 versions of linux to boot or the Windows 7 boot loader. Since doing the migration (and I chose to install grub loader) it automatically gives me the purple screen with the four linux choices when I boot up. 

Am I understanding correctly that this means I have the grub loader installed?

Sorry for the noob questions, I'm just nervous about doing this until I'm 100% sure I've got this right.

Yes you have the grub bootloader installed. If you are unsure run  the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and it will confirm that.

Partitioning is generally easy and safe. But there is always a small risk. That's why you should always back up beforehand and also have a rescue medium (like an Ubuntu USB). Since you don't have a bootable Ubuntu USB yet, my advice is to wait. If you've only had Ubuntu for a couple of weeks, why rush it?

---

### Post by AnotherPenguin on 2011-09-22
Can you use another device as storage after migrating Wubi? I would like to know because i want to use a memory card as storage but received a suggestion to install Ubuntu onto a Partition.

---

### Post by bcbc on 2011-09-22
> **AnotherPenguin said:**
> Can you use another device as storage after migrating Wubi? I would like to know because i want to use a memory card as storage but received a suggestion to install Ubuntu onto a Partition.

I'm not sure that I understand. Are you asking whether you can migrate to a memory card? Whether it's a hard disk or a card you still need a partition. The only issue is whether BIOS can see the device since grub relies on BIOS functions to load the grub modules and grub.cfg and if it can't see the partition you'll get a grub rescue prompt (no way to boot from that if the ubuntu partition is not visible). If you want to experiment, boot with the card in the computer, go to your wubi grub menu, hit 'c' to get to a grub command prompt and see whether you can see the device ("ls", and then "ls (hdx,y)/" replacing x,y with the appropriate values).

Or try to migrate but **don't** install the grub bootloader and then confirm that you can boot the migrated install from the wubi grub menu, before installing the grub bootloader. 

I personally don't recommend migrating to a card, but if you must do it then take precautions and have a rescue disk handy.

---

### Post by AnotherPenguin on 2011-09-22
No I mean migrate Wubi to a hard drive but not use the hard drive to keep all your data or documents, and instead keep your data on a Memory Card, by default without having to move your data from the hard drive to the card.

---

### Post by bcbc on 2011-09-22
> **AnotherPenguin said:**
> No I mean migrate Wubi to a hard drive but not use the hard drive to keep all your data or documents, and instead keep your data on a Memory Card, by default without having to move your data from the hard drive to the card.
ah ok, I get it. The migration script moves the Wubi install to a single partition. If you need to divert some of this data to the card first, you have to do it manually. If you wanted to have a separate /home or /usr or /boot that has to be done manually as well. Maybe one day the script will evolve to support this, but not in the foreseeable future.

---

### Post by AnotherPenguin on 2011-09-23
So there is no script that allows me to save my data on a Card by default? Well that's a bummer. Regardless I'm probaly going to migrate Wubi anyways.

---

### Post by bcbc on 2011-09-23
> **AnotherPenguin said:**
> So there is no script that allows me to save my data on a Card by default? Well that's a bummer. Regardless I'm probaly going to migrate Wubi anyways.

You don't need a script. You can create a symbolic link from e.g. your "Documents" directory to somewhere on your card. Or just save data on it directly. 
If want to actually mount /home on it you'll need to have it in your /etc/fstab but this has to be done manually following the migration.

I'm not the best reference for this - create a new post or look for oldfred's many posts on the subject e.g. [http://ubuntuforums.org/showthread.php?t=1610975](http://ubuntuforums.org/showthread.php?t=1610975)

---

### Post by geekhush on 2011-09-27
hi, bcbc.... this is very helpful tutorial... i used it a while ago to migrate and everything went just fine...but since i am rally a newbie to linux...i messed up with that installation and had to remove everything and install windows then again ubuntu via wubi...but now the problem is i am not able to do the migration with th above method...every time i try an error pops up..saying something like error in home/user/.morzila something....could u shed some light onto this..please.....u c after i reinstalled ubuntu i ve literally fallen in love with it :D....
thanks
  hush

---

### Post by bcbc on 2011-09-27
> **geekhush said:**
> hi, bcbc.... this is very helpful tutorial... i used it a while ago to migrate and everything went just fine...but since i am rally a newbie to linux...i messed up with that installation and had to remove everything and install windows then again ubuntu via wubi...but now the problem is i am not able to do the migration with th above method...every time i try an error pops up..saying something like error in home/user/.morzila something....could u shed some light onto this..please.....u c after i reinstalled ubuntu i ve literally fallen in love with it :D....
thanks
  hush
I'm curious as to why you needed to use Wubi a second time? If it was a new install you could just setup a normal dual boot.

In terms of the error you are getting, it's not something I've run across before. There are some folders that are explicitly excluded because they fail the rsync copy (e.g. **.gvfs** folders) but I've never seen a case involving the .mozilla settings. It might be related to a plugin I suppose. If you could please post the exact error text then I'll investigate it further and see if it warrants a workaround. 

There's a new version of the script being released soon because of changes in Oneiric 11.10, so if you get that exception text to me soon I'll try and incorporate a fix in that.

Thanks for the feedback.

---

### Post by geekhush on 2011-09-28
hi, bcbc thanks a lot for ua time...ok first of all let me help help u with ua curosity, ok i installed ubuntu via wibi (coz i recently burnet off my dvd drive :P) for the first time and i liked it very much, then this problem, bug actually which was touchering half of the world, the blank screen problem occurred to me too..and at that time i did not know about ya awesome megathread..i posted the problem on the forums but i couldnt quite get a fix...so i though if i migrate to a native install my problem might be solved, so i decided to experiment it...but alas t didnot work..then i had to format everything..including windws and did a new installation...then i installed ubuntu all over again :) and fyi i found the migration tutorial of urs through google :)
now  the problem ;) ok when i tried, actually a dozen times to do the migration this problem pops up.Heres the full error message
wubi-move-2.0.sh: Copying files - please be patient - this takes some time
rsync: read errors mapping "/home/hush/.mozilla/firefox/dtbf3hfr.default/urlclassifier3.sqlite": Input/output error (5)
rsync: read errors mapping "/home/hush/.mozilla/firefox/dtbf3hfr.default/urlclassifier3.sqlite": Input/output error (5)
ERROR: home/hush/.mozilla/firefox/dtbf3hfr.default/urlclassifier3.sqlite failed verification -- update discarded.
hope this time i get a nice fix and it proves to be a solid blow on the face of the loser,the bug ;) thanks anyways :) :)

---

### Post by bcbc on 2011-09-28
geekhush,

It appears that there is some firefox sqlite corruption. Refer to the [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567") which, from post #3 to #7 talk about mysql corruption. 

In post #1 there is this link which might help: [http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles](http://www.webgapps.org/tutorials/firefox/troubleshooting/fixing-corrupted-profiles)

If you are unsure, post in that thread and then *lovinglinux* might be able to shed more light on this issue.

---

### Post by geekhush on 2011-09-29
hi, bcbc..thanks a lot...the problem i fixed.. i just used a command to delete the morzila profile..and created a new one ond it worked just fine...and i just migrated to a native partition :) 
regards
hush

---

### Post by bcbc on 2011-09-29
> **geekhush said:**
> hi, bcbc..thanks a lot...the problem i fixed.. i just used a command to delete the morzila profile..and created a new one ond it worked just fine...and i just migrated to a native partition :) 
regards
hush
Great! That's good to hear!

---

### Post by PayPaul on 2011-10-03
> **bcbc said:**
> Initial ram disk: [http://en.wikipedia.org/wiki/Initrd](http://en.wikipedia.org/wiki/Initrd)

I don't know how it would be corrupted... but it does happen. There's no problem with the space side of things. I suppose there might be fragmentation of the root.disk itself from Windows. 

In general, wubi is good to try out Ubuntu, but once you're tried it out and want to keep it, it's better to install it direct. I think I mentioned already in another thread you posted in, but you can [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi or backup/reinstall manually.

When I migrate the Wubi as per the instructions on that thread do I use this code as my Ubuntu Wubi install may be on sda5? I've downloaded the file 

sudo bash wubi-move-2.0.sh [COLOR=red]/dev/sda5[/COLOR]
What is the [COLOR=DeepSkyBlue][COLOR=RoyalBlue]other[/COLOR] [/COLOR]indication mean on your screenshots in that page?

bcbc@ubuntu:~/downloads$ ls
[COLOR=RoyalBlue]other[/COLOR] wubi-move-2.0.sh wubi-move-2.0.sh.gz

I suspect you are extracting the file with the above command. I could be wrong. Please tell me if I am and what the above string means. It would seem that second line might be generated by the Terminal after you entered the first line.

I see in your set of screenshots you also use the command 

[COLOR=Red]sudo fdisk -1(?)[/COLOR]. I'm not sure if that character is a 1 or an L.

I also saw this command on your screenshot. 

[COLOR=Red]sudo bash wubi-move-2.0.sh/dev/sda5 [COLOR=SeaGreen]dev/sda6[/COLOR][/COLOR]

Why is the wubi-move program name placed next to one of the partitions and then another partition, sda6 comes after it.?

If I have a partition on the main drive ready for the Ubuntu migration how do I know which one it is and what kind of syntax do I use to make sure the migration from Wubi goes to that partition?

I do hate sounding a little nit picky or like a serious noob but I'm not even certain if I'm correct that sda5 means a partition or drive indication. The rest seems pretty straightforward with the prompts. 

Oh, yes. One more thing I must look up. The term "Swap".

Thank you in advance for your patience and help here.

---

### Post by bcbc on 2011-10-03
PayPaul, it's probably best to post on the Howto itself (Rubi1200, if you like you can move it and my response). 

In answer to your questions:
1. **other** - that just happens to be a directory on my machine that I used to clean up my Downloads directory so it looked better on the screenshot - that simply shows the archive and the extracted script.
2. **-l** - it's a lowercase -L
3. **/dev/sda5** - this is an example partition. You need to change it to one that you have created for the express purpose of migrating to - it's not the one holding the wubi install - it's an empty partition of type 83 (create as an ext4 partition)
4. there is a space between wubi-move-2.0.sh and /dev/sda5

Take your time - there's no rush to migrate. Please review the Howto thread and the links e.g. the one that shows how to manually partition. Please don't hesitate to ask if you have any questions: it's best to make sure you understand before migrating. 
Thanks

---

### Post by ViewtifulM on 2011-10-05
Hi bcbc,

First of all, thanks for the howto. I must say, though, that I have a problem at the very beginning, when I try to make the partitions. If I run Gparted from my wubi installation, I can see the space used and unused by the windows partition. However, when I run ubuntu from a USB stick and start Gparted, I only see the total space of the Windows partition, but not the used space nor the remaining one, and there is an error icon beside this partition. I have the option of rezising, but it won't change when I try to settle a new value. What could be the problem? If you think this needs a new thread, just tell me and I will open a new one.

Thanks in advance.

P.S.: I forgot to say this is for Ubuntu 10.04.

---

### Post by bcbc on 2011-10-05
> **raza123 said:**
> I think its a very useful tutorial and very helpful for us.
Great! :)

> **ViewtifulM said:**
> Hi bcbc,

First of all, thanks for the howto. I must say, though, that I have a problem at the very beginning, when I try to make the partitions. If I run Gparted from my wubi installation, I can see the space used and unused by the windows partition. However, when I run ubuntu from a USB stick and start Gparted, I only see the total space of the Windows partition, but not the used space nor the remaining one, and there is an error icon besides this partition. I have the option of rezising, but it won't change when I try to settle a new value. What could be the problem? If you think this needs a new thread, just tell me and I will open a new one.

Thanks in advance.

P.S.: I forgot to say this is for Ubuntu 10.04.
When you click on that error icon does it give you any information as to what it thinks is the problem? You might want to run chkdsk from windows to ensure that the partition is clean before trying again to resize it from the live USB.

If it's windows vista/7 you can resize it from within Windows (just make sure it doesn't switch you to dynamic drives on win7).

PS before running chkdsk, back up important data on your wubi install. This link shows how to run chkdsk from within windows [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html) (just refer to the section titled 'Running chksdk' as the rest of that post is to do with missing root.disk files)

---

### Post by ViewtifulM on 2011-10-06
> When you click on that error icon does it give you any information as to  what it thinks is the problem? You might want to run chkdsk from  windows to ensure that the partition is clean before trying again to  resize it from the live USB.I attach two screenshots now, hope this makes it more clear. In the first one, which is taken when I run GParted from the liveUSB, you can see the errors. However, when I run GParted from my wubi installation, you can see everything's OK. I just don't get it...

Edit: chkdsk seems to have worked, thank you! I will let you know if the migration has gone alright when it's done.
Edit 2: Everything went fine and seem to work correctly. Thank you!

---

### Post by bcbc on 2011-10-06
> **ViewtifulM said:**
> Edit 2: Everything went fine and seem to work correctly. Thank you!

Great! Sweet desktop.

---

### Post by claudiuzme on 2011-10-07
Great job with this script.
It worked like a charm to move Ubuntu from windows to a new partition. 
Thanks to you, now I can enjoy Ubuntu at it's best. :popcorn:

---

### Post by bcbc on 2011-10-08
> **claudiuzme said:**
> Great job with this script.
It worked like a charm to move Ubuntu from windows to a new partition. 
Thanks to you, now I can enjoy Ubuntu at it's best. :popcorn:

Thanks :) Enjoy!

---

### Post by saurabh pandey on 2011-10-08
good tutorial but how to directly installed.

---

### Post by bcbc on 2011-10-08
> **saurabh pandey said:**
> good tutorial but how to directly installed.

The migration script (not the manual instructions) also works on a direct install.

---

### Post by ashhab2010 on 2011-10-09
```

$ sudo bash wubi-move-2.0.sh /dev/sda7 /dev/sda8


wubi-move-2.0.sh: Would you like the grub2 bootloader to be installed
wubi-move-2.0.sh: to drive /dev/sda? If you choose not to, you will
wubi-move-2.0.sh: still be able to boot your migrated install from
wubi-move-2.0.sh: your current install.
wubi-move-2.0.sh: Install grub bootloader to /dev/sda? (Y/N)
y
wubi-move-2.0.sh: Please close all open files before continuing.
wubi-move-2.0.sh: About to format the target partition (/dev/sda7).
wubi-move-2.0.sh: Proceed with format (Y/N)
y
wubi-move-2.0.sh: Formatting /dev/sda7 with ext4 file system

wubi-move-2.0.sh: Copying files - please be patient - this takes some time
file has vanished: "/dev/.bootchart/proc/10/exe"
file has vanished: "/dev/.bootchart/proc/10/task/10/exe"
file has vanished: "/dev/.bootchart/proc/11/exe"
file has vanished: "/dev/.bootchart/proc/11/task/11/exe"
file has vanished: "/dev/.bootchart/proc/12/exe"
file has vanished: "/dev/.bootchart/proc/12/task/12/exe"
file has vanished: "/dev/.bootchart/proc/13/exe"
file has vanished: "/dev/.bootchart/proc/13/task/13/exe"
file has vanished: "/dev/.bootchart/proc/14/exe"
file has vanished: "/dev/.bootchart/proc/14/task/14/exe"
file has vanished: "/dev/.bootchart/proc/15/exe"
file has vanished: "/dev/.bootchart/proc/15/task/15/exe"
file has vanished: "/dev/.bootchart/proc/17/exe"
file has vanished: "/dev/.bootchart/proc/17/task/17/exe"
file has vanished: "/dev/.bootchart/proc/18/exe"
file has vanished: "/dev/.bootchart/proc/18/task/18/exe"
file has vanished: "/dev/.bootchart/proc/19/exe"
file has vanished: "/dev/.bootchart/proc/19/task/19/exe"
file has vanished: "/dev/.bootchart/proc/195/exe"
file has vanished: "/dev/.bootchart/proc/195/task/195/exe"
file has vanished: "/dev/.bootchart/proc/197/exe"
file has vanished: "/dev/.bootchart/proc/197/task/197/exe"
file has vanished: "/dev/.bootchart/proc/2/exe"
file has vanished: "/dev/.bootchart/proc/2/task/2/exe"
file has vanished: "/dev/.bootchart/proc/20/exe"
file has vanished: "/dev/.bootchart/proc/20/task/20/exe"
file has vanished: "/dev/.bootchart/proc/202/exe"
file has vanished: "/dev/.bootchart/proc/202/task/202/exe"
file has vanished: "/dev/.bootchart/proc/207/exe"
file has vanished: "/dev/.bootchart/proc/207/task/207/exe"
file has vanished: "/dev/.bootchart/proc/21/exe"
file has vanished: "/dev/.bootchart/proc/21/task/21/exe"
file has vanished: "/dev/.bootchart/proc/22/exe"
file has vanished: "/dev/.bootchart/proc/22/task/22/exe"
file has vanished: "/dev/.bootchart/proc/221/exe"
file has vanished: "/dev/.bootchart/proc/221/task/221/exe"
file has vanished: "/dev/.bootchart/proc/23/exe"
file has vanished: "/dev/.bootchart/proc/23/task/23/exe"
file has vanished: "/dev/.bootchart/proc/239/exe"
file has vanished: "/dev/.bootchart/proc/239/task/239/exe"
file has vanished: "/dev/.bootchart/proc/24/exe"
file has vanished: "/dev/.bootchart/proc/24/task/24/exe"
file has vanished: "/dev/.bootchart/proc/25/exe"
file has vanished: "/dev/.bootchart/proc/25/task/25/exe"
file has vanished: "/dev/.bootchart/proc/2562/exe"
file has vanished: "/dev/.bootchart/proc/2562/task/2562/exe"
file has vanished: "/dev/.bootchart/proc/2563/exe"
file has vanished: "/dev/.bootchart/proc/2563/task/2563/exe"
file has vanished: "/dev/.bootchart/proc/2564/exe"
file has vanished: "/dev/.bootchart/proc/2564/task/2564/exe"
file has vanished: "/dev/.bootchart/proc/26/exe"
file has vanished: "/dev/.bootchart/proc/26/task/26/exe"
file has vanished: "/dev/.bootchart/proc/27/exe"
file has vanished: "/dev/.bootchart/proc/27/task/27/exe"
file has vanished: "/dev/.bootchart/proc/277/exe"
file has vanished: "/dev/.bootchart/proc/2565/fdinfo/3"
file has vanished: "/dev/.bootchart/proc/277/task/277/exe"
file has vanished: "/dev/.bootchart/proc/279/exe"
file has vanished: "/dev/.bootchart/proc/2565/task/2565/fdinfo/3"
file has vanished: "/dev/.bootchart/proc/279/task/279/exe"
file has vanished: "/dev/.bootchart/proc/28/exe"
file has vanished: "/dev/.bootchart/proc/28/task/28/exe"
file has vanished: "/dev/.bootchart/proc/280/exe"
file has vanished: "/dev/.bootchart/proc/280/task/280/exe"
file has vanished: "/dev/.bootchart/proc/281/exe"
file has vanished: "/dev/.bootchart/proc/281/task/281/exe"
file has vanished: "/dev/.bootchart/proc/29/exe"
file has vanished: "/dev/.bootchart/proc/29/task/29/exe"
file has vanished: "/dev/.bootchart/proc/3/exe"
file has vanished: "/dev/.bootchart/proc/3/task/3/exe"
file has vanished: "/dev/.bootchart/proc/30/exe"
file has vanished: "/dev/.bootchart/proc/30/task/30/exe"
file has vanished: "/dev/.bootchart/proc/304/exe"
file has vanished: "/dev/.bootchart/proc/304/task/304/exe"
file has vanished: "/dev/.bootchart/proc/305/exe"
file has vanished: "/dev/.bootchart/proc/305/task/305/exe"
file has vanished: "/dev/.bootchart/proc/306/exe"
file has vanished: "/dev/.bootchart/proc/306/task/306/exe"
file has vanished: "/dev/.bootchart/proc/307/exe"
file has vanished: "/dev/.bootchart/proc/307/task/307/exe"
file has vanished: "/dev/.bootchart/proc/308/exe"
file has vanished: "/dev/.bootchart/proc/308/task/308/exe"
file has vanished: "/dev/.bootchart/proc/309/exe"
file has vanished: "/dev/.bootchart/proc/309/task/309/exe"
file has vanished: "/dev/.bootchart/proc/31/exe"
file has vanished: "/dev/.bootchart/proc/31/task/31/exe"
file has vanished: "/dev/.bootchart/proc/310/exe"
file has vanished: "/dev/.bootchart/proc/310/task/310/exe"
file has vanished: "/dev/.bootchart/proc/311/exe"
file has vanished: "/dev/.bootchart/proc/311/task/311/exe"
file has vanished: "/dev/.bootchart/proc/312/exe"
file has vanished: "/dev/.bootchart/proc/312/task/312/exe"
file has vanished: "/dev/.bootchart/proc/313/exe"
file has vanished: "/dev/.bootchart/proc/313/task/313/exe"
file has vanished: "/dev/.bootchart/proc/314/exe"
file has vanished: "/dev/.bootchart/proc/314/task/314/exe"
file has vanished: "/dev/.bootchart/proc/315/exe"
file has vanished: "/dev/.bootchart/proc/315/task/315/exe"
file has vanished: "/dev/.bootchart/proc/316/exe"
file has vanished: "/dev/.bootchart/proc/316/task/316/exe"
file has vanished: "/dev/.bootchart/proc/317/exe"
file has vanished: "/dev/.bootchart/proc/317/task/317/exe"
file has vanished: "/dev/.bootchart/proc/318/exe"
file has vanished: "/dev/.bootchart/proc/318/task/318/exe"
file has vanished: "/dev/.bootchart/proc/319/exe"
file has vanished: "/dev/.bootchart/proc/319/task/319/exe"
file has vanished: "/dev/.bootchart/proc/32/exe"
file has vanished: "/dev/.bootchart/proc/32/task/32/exe"
file has vanished: "/dev/.bootchart/proc/320/exe"
file has vanished: "/dev/.bootchart/proc/320/task/320/exe"
file has vanished: "/dev/.bootchart/proc/321/exe"
file has vanished: "/dev/.bootchart/proc/321/task/321/exe"
file has vanished: "/dev/.bootchart/proc/33/exe"
file has vanished: "/dev/.bootchart/proc/33/task/33/exe"
file has vanished: "/dev/.bootchart/proc/34/exe"
file has vanished: "/dev/.bootchart/proc/34/task/34/exe"
file has vanished: "/dev/.bootchart/proc/35/exe"
file has vanished: "/dev/.bootchart/proc/35/task/35/exe"
file has vanished: "/dev/.bootchart/proc/36/exe"
file has vanished: "/dev/.bootchart/proc/36/task/36/exe"
file has vanished: "/dev/.bootchart/proc/37/exe"
file has vanished: "/dev/.bootchart/proc/37/task/37/exe"
file has vanished: "/dev/.bootchart/proc/38/exe"
file has vanished: "/dev/.bootchart/proc/38/task/38/exe"
file has vanished: "/dev/.bootchart/proc/39/exe"
file has vanished: "/dev/.bootchart/proc/39/task/39/exe"
file has vanished: "/dev/.bootchart/proc/4/exe"
file has vanished: "/dev/.bootchart/proc/4/task/4/exe"
file has vanished: "/dev/.bootchart/proc/44/exe"
file has vanished: "/dev/.bootchart/proc/44/task/44/exe"
file has vanished: "/dev/.bootchart/proc/45/exe"
file has vanished: "/dev/.bootchart/proc/45/task/45/exe"
file has vanished: "/dev/.bootchart/proc/46/exe"
file has vanished: "/dev/.bootchart/proc/46/task/46/exe"
file has vanished: "/dev/.bootchart/proc/47/exe"
file has vanished: "/dev/.bootchart/proc/47/task/47/exe"
file has vanished: "/dev/.bootchart/proc/48/exe"
file has vanished: "/dev/.bootchart/proc/48/task/48/exe"
file has vanished: "/dev/.bootchart/proc/49/exe"
file has vanished: "/dev/.bootchart/proc/49/task/49/exe"
file has vanished: "/dev/.bootchart/proc/5/exe"
file has vanished: "/dev/.bootchart/proc/5/task/5/exe"
file has vanished: "/dev/.bootchart/proc/50/exe"
file has vanished: "/dev/.bootchart/proc/50/task/50/exe"
file has vanished: "/dev/.bootchart/proc/51/exe"
file has vanished: "/dev/.bootchart/proc/51/task/51/exe"
file has vanished: "/dev/.bootchart/proc/52/exe"
file has vanished: "/dev/.bootchart/proc/52/task/52/exe"
file has vanished: "/dev/.bootchart/proc/584/exe"
file has vanished: "/dev/.bootchart/proc/584/task/584/exe"
file has vanished: "/dev/.bootchart/proc/6/exe"
file has vanished: "/dev/.bootchart/proc/6/task/6/exe"
file has vanished: "/dev/.bootchart/proc/608/exe"
file has vanished: "/dev/.bootchart/proc/608/task/608/exe"
file has vanished: "/dev/.bootchart/proc/609/exe"
file has vanished: "/dev/.bootchart/proc/609/task/609/exe"
file has vanished: "/dev/.bootchart/proc/610/exe"
file has vanished: "/dev/.bootchart/proc/610/task/610/exe"
file has vanished: "/dev/.bootchart/proc/611/exe"
file has vanished: "/dev/.bootchart/proc/611/task/611/exe"
file has vanished: "/dev/.bootchart/proc/612/exe"
file has vanished: "/dev/.bootchart/proc/612/task/612/exe"
file has vanished: "/dev/.bootchart/proc/613/exe"
file has vanished: "/dev/.bootchart/proc/613/task/613/exe"
file has vanished: "/dev/.bootchart/proc/614/exe"
file has vanished: "/dev/.bootchart/proc/614/task/614/exe"
file has vanished: "/dev/.bootchart/proc/625/exe"
file has vanished: "/dev/.bootchart/proc/625/task/625/exe"
file has vanished: "/dev/.bootchart/proc/626/exe"
file has vanished: "/dev/.bootchart/proc/626/task/626/exe"
file has vanished: "/dev/.bootchart/proc/627/exe"
file has vanished: "/dev/.bootchart/proc/627/task/627/exe"
file has vanished: "/dev/.bootchart/proc/668/exe"
file has vanished: "/dev/.bootchart/proc/668/task/668/exe"
file has vanished: "/dev/.bootchart/proc/7/exe"
file has vanished: "/dev/.bootchart/proc/7/task/7/exe"
file has vanished: "/dev/.bootchart/proc/746/exe"
file has vanished: "/dev/.bootchart/proc/746/task/746/exe"
file has vanished: "/dev/.bootchart/proc/747/exe"
file has vanished: "/dev/.bootchart/proc/747/task/747/exe"
file has vanished: "/dev/.bootchart/proc/8/exe"
file has vanished: "/dev/.bootchart/proc/8/task/8/exe"
file has vanished: "/dev/.bootchart/proc/9/exe"
file has vanished: "/dev/.bootchart/proc/9/task/9/exe"
rsync: send_files failed to open "/dev/.bootchart/proc/sys/net/ipv4/route/flush": Permission denied (13)
rsync: send_files failed to open "/dev/.bootchart/proc/sys/net/ipv6/route/flush": Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

wubi-move-2.0.sh: Copying files failed - user canceled?
wubi-move-2.0.sh: Unmounting target...
wubi-move-2.0.sh: Migration request canceled


```

im getting this thing ...
plz help

---

### Post by bcbc on 2011-10-09
ashhab2010,

try uninstalling *bootchart* and rebooting before rerunning the script, or else edit the script and add a manual exclusion for /dev/.bootchart:
```
rsync -a [COLOR="Red"]--exclude="$root"dev/.bootchart[/COLOR] --exclude="$root"host --exclude="$root"mnt/* --exclude="$root"home/*/.gvfs --exclude="$root"media/*/* --exclude="$root"tmp/* --exclude="$root"proc/* --exclude="$root"sys/* $root $target # let errors show
```

---

### Post by geekhush on 2011-10-11
hi again, bcbc..... i needed some help from ya..its like last time when i was using ubuntu on wubi i had this problem with the grub...and it would take a lot of rebooting to successfully boot into ubuntu...and then i found ya awesome guide with the fix and i applied it...then the problem was fixed...then i migrated to a native install and then the problem appears again..please if u could suggest me something it would be really nice of of yu..coz like i ll ve to reboot for like 10 times and then and only "SUCCESS".....
any help really appreciated
thanks! :)

---

### Post by bcbc on 2011-10-11
> **geekhush said:**
> hi again, bcbc..... i needed some help from ya..its like last time when i was using ubuntu on wubi i had this problem with the grub...and it would take a lot of rebooting to successfully boot into ubuntu...and then i found ya awesome guide with the fix and i applied it...then the problem was fixed...then i migrated to a native install and then the problem appears again..please if u could suggest me something it would be really nice of of yu..coz like i ll ve to reboot for like 10 times and then and only "SUCCESS".....
any help really appreciated
thanks! :)
At first blush it sounds like you might have some hardware incompatibility... but looking over your old posts, you have a bootinfoscript [result]("http://ubuntuforums.org/showthread.php?t=1838985") that indicates you have dynamic drives on /dev/sdb. These don't play well with Linux, but I assume if you migrated to /dev/sda you should be okay (however I don't recommend mounting /dev/sdb*Y* partitions from linux as you could potentially run lose data).

Why don't you create a new thread (since this doesn't seem like a migration issue), post your complete computer specs, plus a new bootinfoscript result, and then post back here with a link to it and I'll see if anything stands out?
Thanks

---

### Post by Atomic-Fanboy on 2011-10-13
This is awesome. I've been trying to migrate to a dedicated partition for ages.

---

### Post by geekhush on 2011-10-13
Hi, BCBC i did as u said and heres the link [http://ubuntuforums.org/showthread.php?p=11339805#post11339805](http://ubuntuforums.org/showthread.php?p=11339805#post11339805)

---

### Post by ashhab2010 on 2011-10-17
> **bcbc said:**
> ashhab2010,

try uninstalling *bootchart* and rebooting before rerunning the script, or else edit the script and add a manual exclusion for /dev/.bootchart:
```
rsync -a [COLOR="Red"]--exclude="$root"dev/.bootchart[/COLOR] --exclude="$root"host --exclude="$root"mnt/* --exclude="$root"home/*/.gvfs --exclude="$root"media/*/* --exclude="$root"tmp/* --exclude="$root"proc/* --exclude="$root"sys/* $root $target # let errors show
```

thanks it workd fine

---

### Post by bcbc on 2011-10-17
> **ashhab2010 said:**
> thanks it workd fine

Great! I'm looking into adding the ability to manually supply 'exclude directories' in the next script version. Wasn't able to squeeze it in for the 2.1 release that was required for Oneiric... but maybe Pangolin.

---

### Post by smeraji on 2011-10-21
Thanks a lot for you script

However, after running migrate wubi, I lost my old boot options. I used to have windows (7) and wubi boot options. I added a partition to move wubi to but now when I restart my computer, It directly goes to wubi. So basically I don't have the option to either boot windows or the new ubuntu which I moved from wubi!!!!??? any ideas??!!

BTW, the migrate wubi script finished without any problem

I have to mention that my windows was on sda2 and I created sda4 for the ubuntu

---

### Post by bcbc on 2011-10-21
> **smeraji said:**
> Thanks a lot for you script

However, after running migrate wubi, I lost my old boot options. I used to have windows (7) and wubi boot options. I added a partition to move wubi to but now when I restart my computer, It directly goes to wubi. So basically I don't have the option to either boot windows or the new ubuntu which I moved from wubi!!!!??? any ideas??!!

BTW, the migrate wubi script finished without any problem

I have to mention that my windows was on sda2 and I created sda4 for the ubuntu

Hi, please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and I'll see what's up. Thanks

Edit: I'm going offline for a bit. Please try this as well - drop to a terminal (Ctrl+Alt+T) and run:
```
sudo update-grub
```
Technically, it's not possible to boot directly into a wubi install - at least not without creating a custom boot partition and this is obviously not the case. So I suspect you are actually booting your migrated install, not the wubi one. If it turns out that updating grub fixes it, please still post the bootinfoscript result or at least the ubuntu release and windows version you have as well. Thanks.

---

### Post by smeraji on 2011-10-21
Thanks a lot, Actually I ran update-grub last night and everything is fine now:)

Great script:)

> **bcbc said:**
> Hi, please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and I'll see what's up. Thanks

Edit: I'm going offline for a bit. Please try this as well - drop to a terminal (Ctrl+Alt+T) and run:
```
sudo update-grub
```Technically, it's not possible to boot directly into a wubi install - at least not without creating a custom boot partition and this is obviously not the case. So I suspect you are actually booting your migrated install, not the wubi one. If it turns out that updating grub fixes it, please still post the bootinfoscript result or at least the ubuntu release and windows version you have as well. Thanks.

---

### Post by orphean on 2011-10-22
Couldn't have been easier.  Thanks so much for writing and maintaining this script. Loved the fact it supported Oneiric.

---

### Post by bcbc on 2011-10-22
> **orphean said:**
> Couldn't have been easier.  Thanks so much for writing and maintaining this script. Loved the fact it supported Oneiric.
Cool. You're welcome :)

---

### Post by javacookies on 2011-10-27
Good day bcbc, since everything is working well now,Thanks for all your help on my thread ;) I decided to migrate my wubi to a dedicated partition. I'll just ask if this script can migrate my wubi to an external hdd. My external is just an enclosure with the extra hdd of my laptop. Another Ubuntu is installed on dedicated partitions there. One for the root and one as swap space and i'm planning to replace that with my wubi install. If it's possible, do i need to erase that ubuntu first or the script can just replace with the wubi? Thanks :)

---

### Post by bcbc on 2011-10-27
> **javacookies said:**
> Good day bcbc, since everything is working well now,Thanks for all your help on my thread ;) I decided to migrate my wubi to a dedicated partition. I'll just ask if this script can migrate my wubi to an external hdd. My external is just an enclosure with the extra hdd of my laptop. Another Ubuntu is installed on dedicated partitions there. One for the root and one as swap space and i'm planning to replace that with my wubi install. If it's possible, do i need to erase that ubuntu first or the script can just replace with the wubi? Thanks :)

Hi javacookies, 
Yes the script will migrate to an external hard drive. It will not migrate to a non-empty partition (as a safety measure) so you will have to format it or clear it prior to migrating. It also will only install the bootloader to the drive you install to (in your case the external) which is usually what you would want anyway.

So, yes, it's definitely supported :)

---

### Post by javacookies on 2011-10-27
Wow that's really nice! So first thing I should do is format the root partition and swap partition....but to what? ext4,NTFS or any kind? Anyway I'll definitely try your script. Thank you very much :)

---

### Post by javacookies on 2011-10-27
an error occurred :( I can't quite understand it.


An error occurred within chroot
wubi-move-2.1.sh: Error is: /usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
wubi-move-2.1.sh: Attempting to exit chroot normally...
wubi-move-2.1.sh: Exiting from chroot on target install...
wubi-move-2.1.sh: Cancelling migration... 

is it related with blacklisting? coz i blacklisted my wireless lan.

EDIT: oops I misread it...it's blocklist not blacklist LOL. I've read somewhere that it's because my partition starts with sector 1. I don't reall understand that but what could sole this?

EDIT: one more thing I reformatted my whole external hdd. Erased XP partition and ubuntu. adn now copying files was successful so everytime i try to boot from it, it just loops restarting. :(

---

### Post by dehnhardt on 2011-10-27
Worked great for me but the check for the SWAP partition should be case insensitive. 

... |grep -i  "Linux swap" (I had 'Linux Swap' with fdisk -l) 

Holger

---

### Post by javacookies on 2011-10-27
I got it done! I made the first partition not start with 1 in the partition table. But my grub menu is blank though ubuntu boots after few seconds....Thanks for this very useful script :D

---

### Post by bcbc on 2011-10-27
> **javacookies said:**
> an error occurred :( I can't quite understand it.


An error occurred within chroot
wubi-move-2.1.sh: Error is: /usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
wubi-move-2.1.sh: Attempting to exit chroot normally...
wubi-move-2.1.sh: Exiting from chroot on target install...
wubi-move-2.1.sh: Cancelling migration... 

is it related with blacklisting? coz i blacklisted my wireless lan.

EDIT: oops I misread it...it's blocklist not blacklist LOL. I've read somewhere that it's because my partition starts with sector 1. I don't reall understand that but what could sole this?

EDIT: one more thing I reformatted my whole external hdd. Erased XP partition and ubuntu. adn now copying files was successful so everytime i try to boot from it, it just loops restarting. :(

The first problem is that the installation of the grub2 bootloader failed because there wasn't enough space to embed the core.img. See [here]("http://www.gnu.org/software/grub/manual/grub.html#BIOS-installation"):
> The GRUB development team generally recommends embedding GRUB before the first partition, unless you have special requirements. You must ensure that the first partition starts at least 31 KiB (63 sectors) from the start of the disk; on modern disks, it is often a performance advantage to align partitions on larger boundaries anyway, so the first partition might start 1 MiB from the start of the disk.

I don't understand the second problem - about the loop and restarting. What I'd suggest is to repartition your external and ensure that the first partition is 63 sectors from the start of the disk.

PS in reply to your other question, yes formatting the ext4 partition is required. The swap doesn't need to be reinitialized.

---

### Post by bcbc on 2011-10-27
> **javacookies said:**
> I got it done! I made the first partition not start with 1 in the partition table. But my grub menu is blank though ubuntu boots after few seconds....Thanks for this very useful script :D

Great :) that's the right fix.

Regarding the blank grub menu - not sure about that. Grub won't show a menu if it only detects Ubuntu, so check whether it has entries for your internal drive. If not run: sudo update-grub

Sometimes if there is a graphics issue - grub won't show either. In that case setting: 
GRUB_GFXMODE=text
inside /etc/default/grub and rerunning 'sudo update-grub' will fix it.

---

### Post by bcbc on 2011-10-27
> **dehnhardt said:**
> Worked great for me but the check for the SWAP partition should be case insensitive. 

... |grep -i  "Linux swap" (I had 'Linux Swap' with fdisk -l) 

Holger

Thanks for the feedback. I'll put a fix in. :)

---

### Post by bcbc on 2011-10-27
> **dehnhardt said:**
> Worked great for me but the check for the SWAP partition should be case insensitive. 

... |grep -i  "Linux swap" (I had 'Linux Swap' with fdisk -l) 

Holger
This has been [fixed]("https://github.com/bcbc/Wubi-move/commit/f4ead364cef0ac3689ec9cb692c7dcab88d90f67") - I've just uploaded a revised 2.1 script (attachment on post #1).  
Thanks.

---

### Post by javacookies on 2011-10-28
Thanks for the fix bcbc :)
I'm having another problem..stupid me :D My swap space is sda1 and my root partition is sda2. Evrytime I boot, it always try to mount sda1 and of course it results to an error. How can I stop that?

---

### Post by bcbc on 2011-10-28
> **javacookies said:**
> Thanks for the fix bcbc :)
I'm having another problem..stupid me :D My swap space is sda1 and my root partition is sda2. Evrytime I boot, it always try to mount sda1 and of course it results to an error. How can I stop that?

```
sudo bash wubi-move-2.1.sh /dev/sda2 /dev/sda1
```
The root and swap partition parameters are positional so the first is always assumed to be root.

Let me know if you have any other issues :)

---

### Post by CHAUDHRY07 on 2011-10-29
hey bcbc,
i am new to ubuntu.i just have 40GB harddrive (not joke).which is shared by 2 windows xp and 11.10 using wubi....i want to make ubuntu partition and free space i have on harddrive excluding the space under wubi is 2GB....help me out what should i do,do i have to empty space  then partition wubi there or the space where wubi is stored can be made partition.

---

### Post by javacookies on 2011-10-29
what I mean is I already migrated it and it's booting fine except that it always tries to mount sda1 which is the swap space so I always have to press S to skip mounting.

---

### Post by bcbc on 2011-10-29
> **javacookies said:**
> what I mean is I already migrated it and it's booting fine except that it always tries to mount sda1 which is the swap space so I always have to press S to skip mounting.

Oh okay, got it. You probably have an entry in /etc/fstab that mounts /dev/sda1 from before the migration. Check and remove this if that is the case.

---

### Post by bcbc on 2011-10-29
> **CHAUDHRY07 said:**
> hey bcbc,
i am new to ubuntu.i just have 40GB harddrive (not joke).which is shared by 2 windows xp and 11.10 using wubi....i want to make ubuntu partition and free space i have on harddrive excluding the space under wubi is 2GB....help me out what should i do,do i have to empty space  then partition wubi there or the space where wubi is stored can be made partition.

That's a tough one. Basically you're going to have to make space or migrate to an external drive. I can't really help you with the decision on how to make space. 

There is another option. The script can be run from a live CD/USB and migrate from the root.disk file - what this means is that it's possible to move the virtual disks from \ubuntu\disks to e.g. a USB drive, then uninstall wubi, create partitions in the space, and then boot a live CD/USB and migrate the root.disk to those new partitions. 
It sounds like this might be your only option if all you have is 2GB space and you can't remove one of your XP installs. This option might be a bit more difficult if you're new to Ubuntu.
If you have questions about this, feel free to ask.

---

### Post by aciddesir on 2011-11-02
Couldn't get past step 1, the Terminal refuses to acknowledge the wubi-move-2.1.sh file despite the fact that I have it and can open it.

I think this is a record for failing at simple instructions.

---

### Post by bcbc on 2011-11-02
> **aciddesir said:**
> Couldn't get past step 1, the Terminal refuses to acknowledge the wubi-move-2.1.sh file despite the fact that I have it and can open it.

I think this is a record for failing at simple instructions.

Generally you'd download it into your Downloads directory:
```
cd ~/Downloads
bash wubi-move-2.1.sh --help
```

You can also use the [TAB] key to autocomplete file names. This really helps as it's easy to make a typo or get the case wrong. So type: ```
bash wubi[TAB]
``` and it should automatically complete. If it doesn't you're likely in the wrong directory.

Let me know if you run into any difficulty.

---

### Post by Rythmtech on 2011-11-04
[FONT=Arial][SIZE=2]Hi,[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I'm very new to Linux/Ubuntu, but giving it a go and have struck a snag...[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]After going through the migrate process as described with no problems, upon booting, I get the usual Windows boot selector, I select Ubuntu, then Grub pops up and I select the new "Ubuntu on dev/sdb5" entry as per below... but then it just hangs on a purple screen.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I started with Paragon Partition manager under WinXP to shrink my existing C: drive to allow space for a new extended partition, but then rebooted into the Ubuntu Wubi install to use GParted to actually create the partitions. (sdb5 & sdb6)
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]GParted identified my drive as sdb and my (so I thought) second drive as sda, so I modified the "wubi-move" command line to suit and as stated all seemed to go through with out problems.... except for not booting into the newly moved install. The original wubi install still works fine.
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT][SIZE=2] [/SIZE]
[FONT=Arial][SIZE=2] [/SIZE][/FONT][FONT=Arial][SIZE=2]Can anyone identify any obvious problems???[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]I[/SIZE][/FONT][FONT=Arial][SIZE=2]'m suspecting the "insmod ext2" line, but only because I created an ext4 sdb5 partition OR maybe the "[/SIZE][/FONT][FONT=Arial][SIZE=2]set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63" entry as this identifier looks a lot larger than the previous ones. Can I just directly modify this line?
[/SIZE][/FONT]


[FONT=Arial][SIZE=2]The below is (obviously) just an extract from the grub config of the entry that hangs... if the whole file is required, I can post it if needed.
[/SIZE][/FONT][FONT=Arial][SIZE=2] [/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Grub2 Entry:[/SIZE][/FONT]
 

 [FONT=Courier New][SIZE=1]menuentry "Ubuntu, with Linux 2.6.38-12-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os { [/SIZE][/FONT]
 [FONT=Courier New][SIZE=1]	insmod part_msdos [/SIZE][/FONT]
 [FONT=Courier New][SIZE=1]	insmod ext2 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=1]	set root='(/dev/sdb,msdos5)' [/SIZE][/FONT]
 [FONT=Courier New][SIZE=1]	search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=1]	linux /boot/vmlinuz-2.6.38-12-generic root=/dev/sdb5 ro quiet splash vt.handoff=7 [/SIZE][/FONT]
 [FONT=Courier New][SIZE=1]	initrd /boot/initrd.img-2.6.38-12-generic[/SIZE][/FONT]


[FONT=Arial][SIZE=2]Any help is much appreciated.. TIA.
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Courier New][SIZE=1][FONT=Arial][SIZE=2]Peter.[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by bcbc on 2011-11-04
> **Rythmtech said:**
> Any help is much appreciated.. TIA.

Please post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") between [CODE[SIZE="1"] [/SIZE]][/CODE] tags 

Thanks

---

### Post by Rythmtech on 2011-11-04
Wow! That was quick! :P
Thanks.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400087375360 bytes
16 heads, 63 sectors/track, 775218 cylinders, total 781420655 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   781,419,743   781,419,681   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   266,245,244   266,245,182   7 NTFS / exFAT / HPFS
/dev/sdb2         266,246,144   321,671,167    55,425,024   5 Extended
/dev/sdb5         266,248,192   317,577,215    51,329,024  83 Linux
/dev/sdb6         317,579,264   321,671,167     4,091,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       863ad177-206f-446c-afda-e47d67426c7f   ext4       
/dev/sda1        0A8CB7218CB705EB                       ntfs       DATA
/dev/sdb1        78DC33EADC33A0F4                       ntfs       ACER
/dev/sdb5        73b03530-ccf9-4f7e-b597-6081771c777a   ext4       
/dev/sdb6        77831b94-dacf-4026-90ff-832f89dd0616   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

======================== sdb1/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-12-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-12-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux /boot/vmlinuz-2.6.38-12-generic root=/dev/sdb5 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux /boot/vmlinuz-2.6.38-12-generic root=/dev/sdb5 ro single
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdb5 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdb5 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sdb1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sdb1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  12.242542267 = 13.145329664   boot/grub/grub.cfg                             1
   1.410411835 = 1.514418176    boot/initrd.img-2.6.38-12-generic              1
   1.004127502 = 1.078173696    boot/initrd.img-2.6.38-8-generic               2
   0.988590240 = 1.061490688    boot/vmlinuz-2.6.38-12-generic                 1
   6.799411774 = 7.300812800    boot/vmlinuz-2.6.38-8-generic                  1
   1.410411835 = 1.514418176    initrd.img                                     1
   1.004127502 = 1.078173696    initrd.img.old                                 2
   0.988590240 = 1.061490688    vmlinuz                                        1
   6.799411774 = 7.300812800    vmlinuz.old                                    1

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux    /boot/vmlinuz-2.6.38-12-generic root=/dev/sdb5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=/dev/sdb5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sdb5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sdb5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root a8d11602-6074-43fc-92c8-3d8de4ce6b63
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sdb5 when migrated
UUID=73b03530-ccf9-4f7e-b597-6081771c777a    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sdb6 when migrated
UUID=77831b94-dacf-4026-90ff-832f89dd0616    none    swap    sw    0    0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 139.322296143 = 149.596176384  boot/grub/grub.cfg                             1
 128.660156250 = 138.147790848  boot/initrd.img-2.6.38-12-generic              2
 127.117408752 = 136.491278336  boot/initrd.img-2.6.38-8-generic               1
 141.092124939 = 151.496515584  boot/vmlinuz-2.6.38-12-generic                 1
 141.096336365 = 151.501037568  boot/vmlinuz-2.6.38-8-generic                  1
 128.660156250 = 138.147790848  initrd.img                                     2
 127.117408752 = 136.491278336  initrd.img.old                                 1
 141.092124939 = 151.496515584  vmlinuz                                        1
 141.096336365 = 151.501037568  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  a3 e8 8d 57 00 00 80 01  |...........W....|
000001c0  01 00 07 fe ff fe 3f 00  00 00 3e 94 de 0f 00 fe  |......?...>.....|
000001d0  ff ff 05 fe ff ff 00 98  de 0f 00 b8 4d 03 00 00  |............M...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  ae e5 3b bf 0e b2 6c a5  7d db 62 a1 8a 5d 73 d1  |..;...l.}.b..]s.|
00000010  7f 2d a2 a1 9a 95 a4 29  71 99 66 e5 ec fa ec 96  |.-.....)q.f.....|
00000020  72 c4 d5 de da ce d0 2f  36 d8 97 cb 37 6e 6d af  |r....../6...7nm.|
00000030  36 a2 c9 b9 2f 3f e0 53  fa 95 cd 1d 54 cf ca b3  |6.../?.S....T...|
00000040  de ca b4 96 e8 c1 27 fd  f7 f8 ae 24 fb 28 e3 29  |......'....$.(.)|
00000050  77 cf 9f 2e fa ae ca 3d  2e 5e 4d 8d e7 61 51 fb  |w......=.^M..aQ.|
00000060  36 7f 66 c0 ea 8a c1 0f  26 bc d9 4a 9c 76 45 7f  |6.f.....&..J.vE.|
00000070  f6 ee 97 c5 e0 33 71 71  d4 e7 f1 78 34 b2 fb f2  |.....3qq...x4...|
00000080  55 56 25 83 81 0a 92 07  a6 18 6a 4b a2 cb d3 db  |UV%.......jK....|
00000090  91 3d b7 6f 7d d5 c7 7d  e8 6b 9e 3d 4c 14 ee eb  |.=.o}..}.k.=L...|
000000a0  0f 57 be 3f 7b a8 28 7d  7b de e6 29 ea 50 0a 7b  |.W.?{.(}{..).P.{|
000000b0  db da c6 42 3d d8 ab ca  7f 83 a9 19 a1 59 17 af  |...B=........Y..|
000000c0  57 98 ab 6f 29 7c e5 60  79 2d 93 2a 7f ca 81 ef  |W..o)|.`y-.*....|
000000d0  58 23 74 de 81 45 dd dc  29 a2 81 b3 e2 77 c7 8c  |X#t..E..)....w..|
000000e0  ed a1 63 99 d8 8d 19 b6  2f 01 38 98 47 d8 8e 73  |..c...../.8.G..s|
000000f0  13 65 bd 2a 7a 79 73 95  0c 31 5d 7a 82 4e af 3e  |.e.*zys..1]z.N.>|
00000100  68 95 fb ab ec f2 aa de  cb 9f 03 31 b5 b2 b0 ae  |h..........1....|
00000110  63 14 83 db de fa 2a 05  4f b4 0f 5a 9e 36 3e 18  |c.....*.O..Z.6>.|
00000120  23 f7 63 73 25 66 76 22  7f b3 00 d7 17 55 66 aa  |#.cs%fv".....Uf.|
00000130  ff 16 d9 7c 95 57 23 75  d2 59 72 60 f3 e0 a6 57  |...|.W#u.Yr`...W|
00000140  fd 9f c6 4b be ca 6f 72  9c 63 62 e5 f1 d7 74 3e  |...K..or.cb...t>|
00000150  cb 9c b2 55 5b df 59 b1  10 29 aa d7 c3 07 11 aa  |...U[.Y..)......|
00000160  d3 e1 7e 70 bf 22 df 93  55 7d 2b 31 9d 8a f1 30  |..~p."..U}+1...0|
00000170  05 dc d6 91 68 e7 38 93  e8 9f 2c 83 55 7b ef f0  |....h.8...,.U{..|
00000180  7f 36 f3 a0 a5 4a 05 f0  94 43 d2 ee 93 e9 75 80  |.6...J...C....u.|
00000190  75 57 f7 da dc 29 9c cb  a4 f3 57 19 04 c2 e3 78  |uW...)....W....x|
000001a0  bd ce d3 eb ef 7b 9d f7  2a c8 8f 3e 3a ce 3d 5c  |.....{..*..>:.=\|
000001b0  c9 38 c2 b3 ee 73 56 f1  b4 e1 f7 ab 3e 6b 00 fe  |.8...sV.....>k..|
000001c0  ff ff 83 fe ff ff 00 08  00 00 00 38 0f 03 00 fe  |...........8....|
000001d0  ff ff 05 fe ff ff 00 40  0f 03 00 78 3e 00 00 00  |.......@...x>...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by bcbc on 2011-11-04
> **Rythmtech said:**
> Wow! That was quick! :P
Thanks.

You were quick too - didn't expect such a fast response.

So... there are two things. First, as per the known issues on the first post, this could be an issue with the BIOS loading the boot files:
> Other known issues:
1. Many older BIOSes cannot address more than 137GB from the start of the disk. If you try migrating to a partition that falls outside of this, then Grub2 will fail to load it's boot files. Even if only a part of the partition falls outside this range there is a possibility of grub failure in the future. Therefore, either confirm your BIOS is unaffected prior to partitioning, or ensure your target partition falls within this limit.

The second thing that's strange is that the UUID on the migrated grub.cfg doesn't match the actual UUID. This wouldn't actually cause problems though as it uses /dev/sdb5 to boot. I'll look into whether I can work around this - and maybe there's a bug in grub that's not bypassing UUID cache.

So that's why I suspect it's the 137GB limit.
```
=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 139.322296143 = 149.596176384  boot/grub/grub.cfg                             1
 128.660156250 = 138.147790848  boot/initrd.img-2.6.38-12-generic              2
 127.117408752 = 136.491278336  boot/initrd.img-2.6.38-8-generic               1
 [COLOR="Red"]141.092124939 = 151.496515584  boot/vmlinuz-2.6.38-12-generic                 1[/COLOR]
 141.096336365 = 151.501037568  boot/vmlinuz-2.6.38-8-generic                  1
```

You can confirm this theory:
Hit 'c' when you get the Wubi grub menu.
Then enter:
```
configfile (hd1,msdos5)/boot/grub/grub.cfg
```
This will attempt to load the migrated grub menu - but as this is over the 137GB limit as well, it should fail. If it works, then that's not the issue.

---

### Post by Rythmtech on 2011-11-04
Sorry bcbc, I was not as quick this time... had to go out for a couple of hours. :-)

Ok ... not sure about the bios compatibility, but it is the original 160GB HD that came with the computer and has the latest bios available (AMI R01-B1 vers 2.3.3  Feb'07). Unfortunately Acer don't seem to supply any documentation on the bios... that I could find anyway.

I tried your quick test and you were right, it did fail. It just came back with a "grub>" prompt.

Also FYI (not sure if it matters...)

[LIST]
[*]sda is on a PATA connection & sdb is a SATA connection.... and also
[*]was there a requirement to set any flags (boot?) on the sdb2 or sdb5 partition?
[/LIST]
Thanks again bcbc your help is appreciated.:)
Peter

---

### Post by bcbc on 2011-11-05
> **Rythmtech said:**
> Sorry bcbc, I was not as quick this time... had to go out for a couple of hours. :-)

Ok ... not sure about the bios compatibility, but it is the original 160GB HD that came with the computer and has the latest bios available (AMI R01-B1 vers 2.3.3  Feb'07). Unfortunately Acer don't seem to supply any documentation on the bios... that I could find anyway.

I tried your quick test and you were right, it did fail. It just came back with a "grub>" prompt.

Also FYI (not sure if it matters...)

[LIST]
[*]sda is on a PATA connection & sdb is a SATA connection.... and also
[*]was there a requirement to set any flags (boot?) on the sdb2 or sdb5 partition?
[/LIST]
Thanks again bcbc your help is appreciated.:)
Peter
You don't need to set any boot flags.

I don't know a whole lot about the BIOS limitation but think it's likely. Unfortunately your extended partition is at the 136GB mark - if you could create it at 110GB you're likely going to be okay.

---

### Post by Rythmtech on 2011-11-05
Hmmm...
> 
if you could create it at 110GB you're likely going to be okay. 	

Unfortunately that's a problem, it doesn't leave me a lot of space for the WinXP partition and I sooo didn't want to go stuffing around with re-arranging the stuff that's on that.

Is there an actual requirement to have grub? Could the boot be done directly from the Windows boot loader?

---

### Post by bcbc on 2011-11-05
> **Rythmtech said:**
> Hmmm...

Unfortunately that's a problem, it doesn't leave me a lot of space for the WinXP partition and I sooo didn't want to go stuffing around with re-arranging the stuff that's on that.

Is there an actual requirement to have grub? Could the boot be done directly from the Windows boot loader?
No - from what I understand windows' bootmgr (and all boot managers) use bios functions so you have the same restrictions.

If you don't mind doing a little bit of work you can create a separate boot partition - it doesn't have to be too big - maybe 200MB-500MB and make sure it's under the 137GB mark. That should work.
Here's something I found: [https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

Caution: it says you should set the boot flag on the boot partition - do not do this - or windows won't boot. The windows boot loader is simple and requires the boot flag to identify which partition to transfer control to. Ubuntu does not need it.

Also you can skip the part about installing grub2 - just run 'sudo update-grub' from the wubi install and it will pick it up. That way you can figure out if everything is working before deciding which bootloader to use permanently.

---

### Post by Rythmtech on 2011-11-05
Thanks for your efforts so far bcbc,

> 
If you don't mind doing a little bit of work you can create a separate  boot partition - it doesn't have to be too big - maybe 200MB-500MB and  make sure it's under the 137GB mark. That should work.
Here's something I found: [https://help.ubuntu.com/community/Cr...onAfterInstall]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall")


There's a fair bit for me to digest there... i'll keep reading and see how I go.

Cheers.

---

### Post by bcbc on 2011-11-05
> **Rythmtech said:**
> Thanks for your efforts so far bcbc,



There's a fair bit for me to digest there... i'll keep reading and see how I go.

Cheers.
You might want to hold off a bit. I've tried this and the wubi grub menu is not picking up the separate boot partition. So I need to understand how grub determines that there is a separate boot partition. (I'm trying to do it without installing the grub-bootloader - just booting from the wubi menu as you indicated you are doing).

---

### Post by bcbc on 2011-11-05
> **Rythmtech said:**
> Thanks for your efforts so far bcbc,



There's a fair bit for me to digest there... i'll keep reading and see how I go.

Cheers.

Yeah this is a bit of a pain. I got mine to work following those instructions, but I also  had to chroot into the migrated install to run 'update-grub' before the Wubi install would pick up the separate boot partition.

The instructions are not exactly straightforward so I'm hesitant just to dump them down here. This would ideally be handled within the migration script itself in the future.

If you want them I can write up what I did. Later today.

---

### Post by Rythmtech on 2011-11-05
> 
If you want them I can write up what I did. Later today.


Yeah that'd be great. Cheers.

---

### Post by bcbc on 2011-11-06
> **Rythmtech said:**
> Yeah that'd be great. Cheers.

I put together a new version of the script that supports separate target partitions e.g. for /boot. I've run this a couple of times and it works with a caveat. You can download it here: github.com/bcbc/Wubi-move/zipball/Multi-partition-alpha **(edit: link has been removed; obsolete version)**

Usage:
If your boot partition is /dev/sdb5, your main "/" partition is /dev/sdb6 and your swap is /dev/sdb7, then you would run:
```
sudo bash wubi-move.sh /dev/sdb6 /dev/sdb7 --boot=/dev/sdb5 --no-bootloader
```

That specifies that everything will be migrated to /dev/sdb6 except the /boot directory which is migrated to /dev/sdb5. And /dev/sdb7 is the swap partition. The --no-bootloader prevents replacing the windows bootloader.

Caveats:
1. I don't check the size on the boot partition. Make sure it's big enough (but even 200MB should be plenty as long as you don't plan on keeping lots of different kernels). Check your current usage with this command:
```
du -sh /boot
```
(the size of mine is only 23MB)
2. I don't yet check whether the boot partition is empty, only that it's type 83 - Linux. It will be formatted provided all other checks pass (no change to existing safeguards in the script)
3. Since you're not installing the grub2 bootloader, you need to boot it from the Wubi menu. For some reason, Wubi won't pick it up until after it's been booted the first time - and I haven't figured out why yet. To boot the first time, from the Wubi grub menu, hit 'c' to get to the grub prompt.
Load the migrated install's grub menu manually (assuming /boot is on /dev/sdb5):
```
configfile (hd1,5)/grub/grub.cfg
```

Boot the first entry. Run 'sudo update-grub'. Reboot into Wubi, run 'sudo update-grub'. From then on, you can boot from the Wubi menu, and later install the grub bootloader for a permanent solution.

Note: even if the Wubi menu has an entry for the migrated install the first time - don't boot it. In my tests, it was incomplete. Or at least inspect it first (hit 'e' to view, ESC to return) and make sure it looks complete and references the boot partition, not the target.

As I said earlier, I've run this a couple of times. But obviously it's not been tested as much as a normal release, plus of course you have to boot manually the first time. So you do use it at your own risk. But I have run it on my own new win7 computer (which is also using the windows bootloader to boot since I try to use Wubi as much as possible for testing etc.) which means I believe it's safe.

PS or if you want to wait a few days I'll probably have figured out how to get it in the wubi menu the first time.

---

### Post by Rythmtech on 2011-11-07
> 
PS or if you want to wait a few days I'll probably have figured out how to get it in the wubi menu the first time. 
Sounds like a good plan for a lazy bloke like me!  :D 

I'll have to delete my broken install and re-do the partitioning anyway and i've also got a few other things keeping me busy at the mo' too.

---

### Post by bcbc on 2011-11-08
> **Rythmtech said:**
> Sounds like a good plan for a lazy bloke like me!  :D 

I'll have to delete my broken install and re-do the partitioning anyway and i've also got a few other things keeping me busy at the mo' too.

Cool. I'm debugging os-prober. Bit of a pain, but I've found some interesting stuff along the way.

---

### Post by itayh1 on 2011-11-08
hellow everyone.
i'm new here so please forgive me if i made some mistakes...
i have a question for you,
i installed ubuntu via wubi on a separate partition.
i used win7 disk management tool to shrink my C volume and
used the new space in wubi installation.
how can i migrate wubi into "real" dual boot system in this case?
can i use this guide for that?

thank you very much!

---

### Post by bcbc on 2011-11-08
> **itayh1 said:**
> hellow everyone.
i'm new here so please forgive me if i made some mistakes...
i have a question for you,
i installed ubuntu via wubi on a separate partition.
i used win7 disk management tool to shrink my C volume and
used the new space in wubi installation.
how can i migrate wubi into "real" dual boot system in this case?
can i use this guide for that?

thank you very much!

The nice thing about Wubi is that you don't need to partition - so it's good to try out Ubuntu. For most users they'd install on an existing partition (e.g C: ) and then when the time comes to migrate, you shrink C: and migrate to the new partition.

In your case, you partitioned, and then placed the wubi install on the new partition. So it makes things a little more complicated.

In general, it's best to create an extended partition when you free up space, so you have more flexibility (e.g. to create multiple partitions - it's recommended to have a minimum of two for linux, and if you don't create an extended you can run out of primary partitions (max 4 )). If you created a primary partition (and you are at the max) you will probably have to delete it before migrating. If you created an extended and are able to create more logical partitions, then you should do this and migrate to them.

If you cannot create more logical partitions for the migration, then I can think of the following scenarios:
1. Migrate to an external drive and then prepare your internal hard drives partitions and move the install back. (Note the wubi-move script also moves normal Ubuntu installs - so you can have bootable backups and move your install around after migrating)
2. A root.disk migration: you can copy the wubi virtual disks back to C:, boot from an Ubuntu live CD, create the partitions you need and then migrate using the "--root-disk=" option.
3. You could move the wubi install to the C: partition, get it booting and then create the partitions and migrate.

Option 1 is probably the simplest.
Option 2 isn't too complicated.
Option 3 is actually fairly complex even though it sounds easy.

So... it's possible - the choice is up to you.

---

### Post by itayh1 on 2011-11-08
thank you very much for your quick help!!
i think i will try your first option :)

---

### Post by bcbc on 2011-11-08
> **itayh1 said:**
> thank you very much for your quick help!!
i think i will try your first option :)
Okay... few things to note:

With an external drive migration the grub2 bootloader is installed to the external, not the internal, drive MBR. To boot the migrated install, hit your bios boot options key and select to boot from the usb device. When you move it back to the internal you can install the grub2 bootloader at that time.

Also, see [this post]("http://ubuntuforums.org/showpost.php?p=11399673&postcount=516") for an issue that could happen if there is not enough room on the external drive's boot track for the grub bootloader.

---

### Post by bcbc on 2011-11-11
> **Rythmtech said:**
> Sounds like a good plan for a lazy bloke like me!  :D 

I'll have to delete my broken install and re-do the partitioning anyway and i've also got a few other things keeping me busy at the mo' too.

I just wanted to stop by and let you know I haven't forgotten about this. My week was busier than I predicted so no final answer. However, I did spend some time debugging the os-prober and grub scripts. And I found this strange thing... I migrate, run update-grub and it fails to identify the boot partition. I open /etc/grub.d/30_os-prober and save it (no other modification). Then I run update-grub and it picks it up perfectly. Obviously this makes no sense, so I need to go back and test again when I have time and figure out exactly what is going on. I found this out while I was adding debug statements into 30_os-prober and then removed them. And found it was suddenly 'magically' working.

So basically what I am saying is that the migration seems to be fine, and it's something obscure to do with grub. But clearly that's not good enough to leave it there, so I'll have to figure out what's up and get the script to bypass this.

---

### Post by Rythmtech on 2011-11-12
Hi bcbc,
Yeah I've had a busy week too, but I did try out your suggestion and found some strange things happening...
Once I booted past the WinXP boot loader and got to Wubi's grub screen, I pressed "c" as suggested and entered "configfile (hd1,3)/grub/grub.cfg" (sdb3 is my new boot partition starting at sector 63) but I just got an empty screen with the grub> prompt. After much mucking around checking & re-checking I used the grub [TAB] auto fill feature and found that it is seeing my sdb drive as HD0 instead of Hd1! (what the?). Anyway, I then tried "configfile (hd0,3)/grub/grub.cfg", but I just get a blank screen and no prompt.... It's got me stumped...

I've attached a new bootinfoscript file, if that may help.

Also just to reiterate my physical drive configuration is...

PATA (IDE) Drive - 400GB "DATA" (Holds data only, no O/S's) (Shows as HD1 but sda)

    sda1 (Data only)

SATA Drive - 160GB "ACER" (Shows as HD0 but sdb)

    sdb3 (250MB boot partition.
    sdb1 (130GB WinXP)
    sdb2 (Extended partition)
        sdb5 (Ubuntu)
        sdb6 (swap)

 ```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System: 
    Boot files:       

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr
                       /ubuntu/winboot/wubildr /wubildr.mbr
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System: 
    Boot files:        /grub/grub.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400087375360 bytes
16 heads, 63 sectors/track, 775218 cylinders, total 781420655 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   781,419,743   781,419,681   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *        514,080   265,747,229   265,233,150   7 NTFS / exFAT / HPFS
/dev/sdb2         265,747,230   321,671,167    55,923,938   f W95 Extended (LBA)
/dev/sdb5         265,747,293   317,476,529    51,729,237  83 Linux
/dev/sdb6         317,476,593   321,669,494     4,192,902  82 Linux swap / Solaris
/dev/sdb3                  63       514,079       514,017  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       863ad177-206f-446c-afda-e47d67426c7f   ext4      
/dev/sda1        0A8CB7218CB705EB                       ntfs       DATA
/dev/sdb1        78DC33EADC33A0F4                       ntfs       ACER
/dev/sdb3        dcd82c7a-52ff-4b50-b002-f699fb0a1485   ext4      
/dev/sdb5        1573bc8f-b569-40c0-8b46-e6b2e21563bc   ext4      
/dev/sdb6        911818b6-2a9a-4751-adb1-8bf753cf9a71   swap      

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)
/dev/sr0         /media/HERE              udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

======================== sdb1/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-12-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-12-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 9e990505-c39a-42ab-835f-9cc00a6b85e1
    linux /boot/vmlinuz-2.6.38-12-generic root=/dev/sdb5
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 9e990505-c39a-42ab-835f-9cc00a6b85e1
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sdb5
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sdb1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sdb1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  14.417354584 = 15.480516608   boot/grub/grub.cfg                             1
   1.410411835 = 1.514418176    boot/initrd.img-2.6.38-12-generic              1
   1.004127502 = 1.078173696    boot/initrd.img-2.6.38-8-generic               2
   0.988590240 = 1.061490688    boot/vmlinuz-2.6.38-12-generic                 1
   6.799411774 = 7.300812800    boot/vmlinuz-2.6.38-8-generic                  1
   1.410411835 = 1.514418176    initrd.img                                     1
   1.004127502 = 1.078173696    initrd.img.old                                 2
   0.988590240 = 1.061490688    vmlinuz                                        1
   6.799411774 = 7.300812800    vmlinuz.old                                    1

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sdb5 when migrated
UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sdb6 when migrated
UUID=911818b6-2a9a-4751-adb1-8bf753cf9a71    none    swap    sw    0    0
# /boot was on /dev/sdb3 when migrated
UUID=dcd82c7a-52ff-4b50-b002-f699fb0a1485    /boot    ext4    errors=remount-ro    0    2
--------------------------------------------------------------------------------

============================= sdb3/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 9e990505-c39a-42ab-835f-9cc00a6b85e1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-12-generic root=/dev/sdb5 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /vmlinuz-2.6.38-12-generic root=/dev/sdb5 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-8-generic root=/dev/sdb5 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=/dev/sdb5 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.133336544 = 0.143169024    grub/grub.cfg                                  1
   0.076708317 = 0.082364928    initrd.img-2.6.38-12-generic                   2
   0.047124386 = 0.050599424    initrd.img-2.6.38-8-generic                    2
   0.053071499 = 0.056985088    vmlinuz-2.6.38-12-generic                      1
   0.059175968 = 0.063539712    vmlinuz-2.6.38-8-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  a3 e8 8d 57 00 00 80 00  |...........W....|
000001c0  01 20 07 fe ff fe 20 d8  07 00 fe 22 cf 0f 00 fe  |. .... ...."....|
000001d0  ff fe 0f fe ff ff 1e fb  d6 0f e2 54 55 03 00 01  |...........TU...|
000001e0  01 00 83 fe 3f 1f 3f 00  00 00 e1 d7 07 00 00 00  |....?.?.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Don't know if any of this helps, but it's all a bit over my head! ](*,)

---

### Post by bcbc on 2011-11-12
Rythmtech,
Yeah there're a couple of things I noticed. The UUID on /dev/sdb5 is 1573bc8f-b569-40c0-8b46-e6b2e21563bc but the grub.cfg on /dev/sdb3 refers to it here as 9e990505-c39a-42ab-835f-9cc00a6b85e1:
```
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 9e990505-c39a-42ab-835f-9cc00a6b85e1
if loadfont /usr/share/grub/unicode.pf2 ; then
```

Normally grub can handle the confusion between /dev/sda and /dev/sdb using the uuids, but in your grub.cfg it also uses **root=/dev/sdb5** instead of **root=UUID=xxx-xxx**
Not sure why as your wubi entries use the uuid notation.

So... try this - manual boot from grub command prompt:
```
    insmod part_msdos
    insmod ext2
    set root=(hd0,3)
    linux    /vmlinuz-2.6.38-12-generic root=/dev/sda5 ro   quiet splash
    initrd    /initrd.img-2.6.38-12-generic

```
I switched to hd0 based on your experience, but you can try hd1 & /dev/sdb5 if that doesn't work. TAB will autocomplete /vmlinuz- and /initrd (and that will also confirm whether you got the correct partition).

Try that and run "sudo update-grub" on both installs. Hopefully that'll be it.

---

### Post by Rythmtech on 2011-11-12
Woohoo! Thanks bcbc!

Just had to change /dev/sda5 to sdb5 and it booted straight up. All is working fine.

To get rid of the wubi install, do I just need to uninstall it from the windows side? That won't uninstall the grub will it? (Only a small bit of worry here, given all the other issues it's thrown at me!)

Many thanks for your help bcbc, again it is very much appreciated.

:D:D:D:D:D:D:D:D

---

### Post by bcbc on 2011-11-12
> **Rythmtech said:**
> Woohoo! Thanks bcbc!

Just had to change /dev/sda5 to sdb5 and it booted straight up. All is working fine.

To get rid of the wubi install, do I just need to uninstall it from the windows side? That won't uninstall the grub will it? (Only a small bit of worry here, given all the other issues it's thrown at me!)

Many thanks for your help bcbc, again it is very much appreciated.

:D:D:D:D:D:D:D:D

Cool!

Before uninstalling Wubi, did you install the grub bootloader yet? Because you're booting it from Wubi's grub menu - and that will be gone when you uninstall Wubi.

Maybe rerun that bootinfoscript first. I am a little puzzled because - according to your last bootinfoscript - your windows bootloader is in /dev/sda, but windows is on /dev/sdb. And from what you are saying in the grub prompt you are using hd0 but /dev/sdb5. 

Normally, you would install the grub bootloader to the same drive e.g. from the migrated Ubuntu (not Wubi) run:
```
sudo grub-install /dev/sdb
```
and then you'll see the migrated install as the first entry when you boot up.

---

### Post by Rythmtech on 2011-11-13
No haven't installed grub from the new install yet.

> 
I am a little puzzled because - according to your last bootinfoscript -  your windows bootloader is in /dev/sda, but windows is on /dev/sdb. And  from what you are saying in the grub prompt you are using hd0 but  /dev/sdb5. 
A little puzzled is an understatement from this end! :-)

Anyway, here's the new output from bootinfoscript (not wubi). Cheers!
```

[FONT=monospace]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sdb1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 400.1 GB, 400087375360 bytes
16 heads, 63 sectors/track, 775218 cylinders, total 781420655 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   781,419,743   781,419,681   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *        514,080   265,747,229   265,233,150   7 NTFS / exFAT / HPFS
/dev/sdb2         265,747,230   321,671,167    55,923,938   f W95 Extended (LBA)
/dev/sdb5         265,747,293   317,476,529    51,729,237  83 Linux
/dev/sdb6         317,476,593   321,669,494     4,192,902  82 Linux swap / Solaris
/dev/sdb3                  63       514,079       514,017  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       863ad177-206f-446c-afda-e47d67426c7f   ext4       
/dev/sda1        0A8CB7218CB705EB                       ntfs       DATA
/dev/sdb1        78DC33EADC33A0F4                       ntfs       ACER
/dev/sdb3        dcd82c7a-52ff-4b50-b002-f699fb0a1485   ext4       
/dev/sdb5        1573bc8f-b569-40c0-8b46-e6b2e21563bc   ext4       
/dev/sdb6        911818b6-2a9a-4751-adb1-8bf753cf9a71   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb3        /boot                    ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/HERE              udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

======================== sdb1/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-12-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-12-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro quiet splash vt.handoff=7
    initrd /initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single
    initrd /initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro quiet splash vt.handoff=7
    initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single
    initrd /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sdb1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sdb1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  16.584201813 = 17.807151104   boot/grub/grub.cfg                             1
   1.410411835 = 1.514418176    boot/initrd.img-2.6.38-12-generic              1
   1.004127502 = 1.078173696    boot/initrd.img-2.6.38-8-generic               2
   0.988590240 = 1.061490688    boot/vmlinuz-2.6.38-12-generic                 1
   6.799411774 = 7.300812800    boot/vmlinuz-2.6.38-8-generic                  1
   1.410411835 = 1.514418176    initrd.img                                     1
   1.004127502 = 1.078173696    initrd.img.old                                 2
   0.988590240 = 1.061490688    vmlinuz                                        1
   6.799411774 = 7.300812800    vmlinuz.old                                    1

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 1573bc8f-b569-40c0-8b46-e6b2e21563bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sdb5 when migrated
UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sdb6 when migrated
UUID=911818b6-2a9a-4751-adb1-8bf753cf9a71    none    swap    sw    0    0
# /boot was on /dev/sdb3 when migrated
UUID=dcd82c7a-52ff-4b50-b002-f699fb0a1485    /boot    ext4    errors=remount-ro    0    2
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 126.851491451 = 136.205751808  boot/grub/grub.cfg                             1
 126.794862270 = 136.144946688  boot/initrd.img-2.6.38-12-generic              2
 126.765278339 = 136.113181184  boot/initrd.img-2.6.38-8-generic               2
 126.771225452 = 136.119566848  boot/vmlinuz-2.6.38-12-generic                 1
 126.777329922 = 136.126121472  boot/vmlinuz-2.6.38-8-generic                  1
 126.794862270 = 136.144946688  initrd.img                                     2
 126.765278339 = 136.113181184  initrd.img.old                                 2
 126.771225452 = 136.119566848  vmlinuz                                        1
 126.777329922 = 136.126121472  vmlinuz.old                                    1

============================= sdb3/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 1573bc8f-b569-40c0-8b46-e6b2e21563bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.133337498 = 0.143170048    grub/grub.cfg                                  1
   0.076708317 = 0.082364928    initrd.img-2.6.38-12-generic                   2
   0.047124386 = 0.050599424    initrd.img-2.6.38-8-generic                    2
   0.053071499 = 0.056985088    vmlinuz-2.6.38-12-generic                      1
   0.059175968 = 0.063539712    vmlinuz-2.6.38-8-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  a3 e8 8d 57 00 00 80 00  |...........W....|
000001c0  01 20 07 fe ff fe 20 d8  07 00 fe 22 cf 0f 00 fe  |. .... ...."....|
000001d0  ff fe 0f fe ff ff 1e fb  d6 0f e2 54 55 03 00 01  |...........TU...|
000001e0  01 00 83 fe 3f 1f 3f 00  00 00 e1 d7 07 00 00 00  |....?.?.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
[/FONT]
```

---

### Post by Rythmtech on 2011-11-13
Also...
Just to prove the installation of a boot loader on the WinXP (sdb) drive, I disconnected the DATA drive and the computer booted into the Windows bootloader the same as it always did. I also ran a new boot_info_script for comparison if that helps...


```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        514,080   265,747,229   265,233,150   7 NTFS / exFAT / HPFS
/dev/sda2         265,747,230   321,671,167    55,923,938   f W95 Extended (LBA)
/dev/sda5         265,747,293   317,476,529    51,729,237  83 Linux
/dev/sda6         317,476,593   321,669,494     4,192,902  82 Linux swap / Solaris
/dev/sda3                  63       514,079       514,017  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        78DC33EADC33A0F4                       ntfs       ACER
/dev/sda3        dcd82c7a-52ff-4b50-b002-f699fb0a1485   ext4       
/dev/sda5        1573bc8f-b569-40c0-8b46-e6b2e21563bc   ext4       
/dev/sda6        911818b6-2a9a-4751-adb1-8bf753cf9a71   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /boot                    ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/HERE              udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

======================== sda1/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-12-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-12-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78DC33EADC33A0F4 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro quiet splash vt.handoff=7
    initrd /initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single
    initrd /initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro quiet splash vt.handoff=7
    initrd /initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single
    initrd /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda1/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda1/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  16.584201813 = 17.807151104   boot/grub/grub.cfg                             1
   1.410411835 = 1.514418176    boot/initrd.img-2.6.38-12-generic              1
   1.004127502 = 1.078173696    boot/initrd.img-2.6.38-8-generic               2
   0.988590240 = 1.061490688    boot/vmlinuz-2.6.38-12-generic                 1
   6.799411774 = 7.300812800    boot/vmlinuz-2.6.38-8-generic                  1
   1.410411835 = 1.514418176    initrd.img                                     1
   1.004127502 = 1.078173696    initrd.img.old                                 2
   0.988590240 = 1.061490688    vmlinuz                                        1
   6.799411774 = 7.300812800    vmlinuz.old                                    1

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 1573bc8f-b569-40c0-8b46-e6b2e21563bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sdb5 when migrated
UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sdb6 when migrated
UUID=911818b6-2a9a-4751-adb1-8bf753cf9a71    none    swap    sw    0    0
# /boot was on /dev/sdb3 when migrated
UUID=dcd82c7a-52ff-4b50-b002-f699fb0a1485    /boot    ext4    errors=remount-ro    0    2
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 126.851491451 = 136.205751808  boot/grub/grub.cfg                             1
 126.794862270 = 136.144946688  boot/initrd.img-2.6.38-12-generic              2
 126.765278339 = 136.113181184  boot/initrd.img-2.6.38-8-generic               2
 126.771225452 = 136.119566848  boot/vmlinuz-2.6.38-12-generic                 1
 126.777329922 = 136.126121472  boot/vmlinuz-2.6.38-8-generic                  1
 126.794862270 = 136.144946688  initrd.img                                     2
 126.765278339 = 136.113181184  initrd.img.old                                 2
 126.771225452 = 136.119566848  vmlinuz                                        1
 126.777329922 = 136.126121472  vmlinuz.old                                    1

============================= sda3/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 1573bc8f-b569-40c0-8b46-e6b2e21563bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /vmlinuz-2.6.38-12-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1573bc8f-b569-40c0-8b46-e6b2e21563bc ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos3)'
    search --no-floppy --fs-uuid --set=root dcd82c7a-52ff-4b50-b002-f699fb0a1485
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 78DC33EADC33A0F4
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.133337498 = 0.143170048    grub/grub.cfg                                  1
   0.076708317 = 0.082364928    initrd.img-2.6.38-12-generic                   2
   0.047124386 = 0.050599424    initrd.img-2.6.38-8-generic                    2
   0.053071499 = 0.056985088    vmlinuz-2.6.38-12-generic                      1
   0.059175968 = 0.063539712    vmlinuz-2.6.38-8-generic                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  a3 e8 8d 57 00 00 80 00  |...........W....|
000001c0  01 20 07 fe ff fe 20 d8  07 00 fe 22 cf 0f 00 fe  |. .... ...."....|
000001d0  ff fe 0f fe ff ff 1e fb  d6 0f e2 54 55 03 00 01  |...........TU...|
000001e0  01 00 83 fe 3f 1f 3f 00  00 00 e1 d7 07 00 00 00  |....?.?.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by bcbc on 2011-11-13
Rythmtech,
It looks like you have a custom bootloader on /dev/sdb. Usually that'd be an OEM bootloader (i.e. dell, compaq, hp) that has some built-in code e.g. to support special function keys - maybe to kick off a restore.

So - it probably doesn't matter to overwrite, but if you're concerned you should back it up. And then install grub to /dev/sdb

I'm glad you've got this sorted. And the rest of the bootinfoscript looks good.

---

### Post by Rythmtech on 2011-11-14
Again, thanks very much for your help bcbc. 

I've managed to remove wubi totally now, and every thing is running nicely.

Cheers!
:D:D:D:D:D:D:D:D

---

### Post by bcbc on 2011-11-15
> **Rythmtech said:**
> Again, thanks very much for your help bcbc. 

I've managed to remove wubi totally now, and every thing is running nicely.

Cheers!
:D:D:D:D:D:D:D

Great! You're very welcome. :D I've been planning to support multi-partition migrations and you gave me the incentive. (Still got to sort out that little technical issue, but that can wait for another day.)

---

### Post by bcbc on 2011-11-15
PS I think I have the grub update problem resolved now. To be more precise, it is working in limited testing on the development release (pun intended). Anyway - I removed the link to the Multi-partition-alpha script as it is out of date - anyone interested in following development can review the *experimental* branch on [github]("https://github.com/bcbc/Wubi-move/tree/experimental").

---

### Post by javacookies on 2011-11-20
does this work on non-wubi installation? I mean Ubuntu installation on dedicated partition? Thanks :)

---

### Post by bcbc on 2011-11-20
> **javacookies said:**
> does this work on non-wubi installation? I mean Ubuntu installation on dedicated partition? Thanks :)

Yes - it works. I use it to move around my partition installs and to keep bootable backups.

---

### Post by javacookies on 2011-11-20
really? nice. great script! Yesterday I used Gparted to copy my partition to m external then booted from livecd to install grub2. With this script, next time I backup all I need to do is run this script. Thank you very much :D

---

### Post by bcbc on 2011-11-21
> **javacookies said:**
> really? nice. great script! Yesterday I used Gparted to copy my partition to m external then booted from livecd to install grub2. With this script, next time I backup all I need to do is run this script. Thank you very much :D

Cool! Glad you're finding a use for it.

I've been toying with the idea of adding a 'synch' option to the script. This would make use of rsync's built in ability to synchronize a previously migrated install. 

I don't think there is a lot of demand for something like this since for most the script is a one-way ticket out of Wubi, but it's something I find useful so might make it's way into a future release. That would definitely help if you're using it for bootable backups.

---

### Post by PayPaul on 2011-11-23
I was looking at the notes for the 2.0 script and would like a bit of clarification. If migrates to a partition with the grub boot-loader, reboots, what do I see? Will I see the current list of two OS's like I do now with my Wubi install? Isn't it preferable to use the GRUB boot-loader than not. Would not installing it with this script prohibit dual boots? 

I also have another question about the sd partitions. I'm not certain as to which sd my current Wubi install is on. I've looked in Gparted and it does seem that my main drive, which should contain both Win7 and the Wubi installation has been given the sde designation. That flies in the face of the norm I think. I want to migrate my Wubi install to what is referred to in Gparted as sde5. There is no sde6. SDE5 is indicated as the logical partition. Will this script, the 2.0 version recognize which partition Wubi is on and allow me to choose the sd partition I want to migrate to? The label of that partition is seen in Gparted but, a big BUT, I can't view the files on it. My only option here is to reboot back into Win7 and move any files in the sde5 partition to other locations. That would be a nuisance as I'd like to perform this entire operation, including housekeeping, within Ubuntu. I've tried to mount that partition but it is indicated in Gparted as "busy". Any help with this would be appreciated.

I had originally planned on reformatting everything but it seems like Win7 is behaving itself again so I've settled on this option instead. I only need Windows for Photoshop. 

Slightly off topic: Funny thing about Windows...when I play video files in Ubuntu they play perfectly with no codecs issues. When I finally got to restart Win7 all the videos sounded weird. Side question: Does Ubuntu know or load the proper codecs from the get-go? That would seem to be the case as Videos and sound files played perfectly out of the box.

---

### Post by bcbc on 2011-11-23
PayPaul,
Use the 2.1 version of the script. This is the only one that supports 11.10, but also it's got some enhanced editing and messages.

Note that the script will not migrate to a partition that is not empty. Also, it should be of type '83 - Linux'. So, first move any data you want off /dev/sde5 (from Windows if that's the only place you can access it). Then boot into Wubi, make sure it's unmounted (sudo umount /dev/sde5) and then use GParted to replace it with a suitable partition (and you could also add swap at the same time).

To determine what partition wubi is on, enter "df" from a terminal. That will show a partition mounted as /host. 

e.g. mine is on /dev/sda3
```
~$ df 
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/loop0       7689788  6535152    764012  90% /
udev             1913284        4   1913280   1% /dev
tmpfs             768840      984    767856   1% /run
none                5120        0      5120   0% /run/lock
none             1922096      212   1921884   1% /run/shm
[COLOR="Red"]/dev/sda3[/COLOR]      309081136 99957580 209123556  33% [COLOR="red"]/host[/COLOR]

```

Side note - Ubuntu doesn't play videos by default unless you install ubuntu-restricted-extras and then there's an additional step for videos. If you install a normal Ubuntu nowadays there's an option to include this at install time, but I believe you still have to do this manually for Wubi installs.

I missed the part about Grub:
It is recommended that you install the Grub2 bootloader when you migrate. You will then see a grub menu at startup with the migrated install first, and at the bottom your Windows install. When you boot Windows, it will show you the Windows boot manager (as you see today) where you can boot Windows or Wubi. Once you have removed Wubi, Windows will boot directly from the first grub menu.
If you do not install the grub2 bootloader then you will have to boot the migrated install from the Wubi menu. It will be shown at the bottom of the Wubi's grub menu. In this case, before removing the Wubi install you should either install the grub bootloader or make some other provision for booting.

---

### Post by lesliek on 2011-11-25
A recent problem with a disappearing root.disk has made me panic and think that I'd better migrate my Wubi install to a partition.

However, my knowledge of these things is pretty rudimentary and 
I have some preliminary questions.

I'm going to have to carve at least one new partition out of an existing one. I created a live CD of the latest version of GParted for the purpose.

However, how big a new partition should I be creating? (I seem to remember something about 17GB when I was installing Wubi, so I'm assuming it can't be smaller than that.)

Also, is it a good idea for me to create a swap partition? (I know I have a file called swap.disk in Wubi.) If so, how big should it be?

Leslie

---

### Post by bcbc on 2011-11-25
LeslieK,

Your partition doesn't have to be the same size as the wubi install - only as big as the space you have used. Running "df -h" will give you an idea of the minimum partition size.
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
**/dev/loop0**       10G  **6.2G**  3.3G  66% /

```

Having said that, it makes sense to plan for the future so you don't have to resize your partitions later. Also consider whether you'll be sharing data between Ubuntu and Linux because then it's probably better to use a separate NTFS partition.

In terms of the swap partition, it's required to hibernate - so if that's something you're likely to use, you'll need one that's bigger than the size of your RAM. You might also need it for overflow if you do memory intensive tasks or you have a small amount of RAM. 
If you don't want to hibernate, have plenty of memory, then it's not required (and you can always add a swap file later).

Let me know if you have any other questions.

---

### Post by lesliek on 2011-11-25
Thanks so much for your reply, bcbc.

You said, "... consider whether you'll be sharing data between Ubuntu and Linux because then it's probably better to use a separate NTFS partition."

I took it that "Linux" was intended to be "Windows", but, in any event, I'm not sure what you meant by suggesting that I use "a separate NTFS partition". Did you mean that I should create a new partition devoted solely to shared files, in addition to either one or two Linux partitions?

Incidentally, I recovered from the missing root.disk file problem that I mentioned in my first post by using a blog post of yours. I was very grateful to find it.

Leslie

---

### Post by bcbc on 2011-11-25
> **lesliek said:**
> Thanks so much for your reply, bcbc.

You said, "... consider whether you'll be sharing data between Ubuntu and Linux because then it's probably better to use a separate NTFS partition."

I took it that "Linux" was intended to be "Windows", but, in any event, I'm not sure what you meant by suggesting that I use "a separate NTFS partition". Did you mean that I should create a new partition devoted solely to shared files, in addition to either one or two Linux partitions?

Incidentally, I recovered from the missing root.disk file problem that I mentioned in my first post by using a blog post of yours. I was very grateful to find it.

Leslie
Yes, I meant Windows :)

I try to keep my data on a separate partition (makes it easier to access and backup), but it's not required. I just threw that out there in terms of deciding whether to have a 17GB Ubuntu partition or a 50GB one. If you keep multimedia separate, then 17GB is probably adequate. (You can also keep mounting your current windows partition).

Anyway - didn't mean to complicate things. ;)

---

### Post by lesliek on 2011-11-25
Well, I've been reading about GParted ever since my first post and have a question that you may be willing to answer, since this is all in aid of preparing to use your migration script.

When I look at my sole hard disk, I see that there are already four partitions on it, created by Windows. (The computer came that way.) One of them is the only one that could practically be shrunk.

If I shrink that partition, will I then be able to create new partitions in the freed space or does will this business about primary, extended and logical partitions prevent me from doing so?

Thanks again for all your help,

Leslie

---

### Post by bcbc on 2011-11-25
lesliek,
Reference -  [wikipedia]("http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types"): 
> The total data storage space of a PC hard disk can be divided into at most four primary partitions, or alternatively three primary partitions and an extended partition.

You would need to delete one of the primary partitions and replace it with an extended. Then you can create multiple logical partitions in that extended. You may also have to resize one or more primary partitions (as the one you delete will likely be small).

Alternatively, you could migrate to another hard drive (e.g. an external).

Apparently you can also convert a primary to a logical (i.e. replace primary with an extended and a logical). See [here]("http://www.partitionwizard.com/help/set-partition-as-logical.html") (I can't vouch for this, just been googling. I wouldn't do this on your main windows OS. You might still need to resize other primary partitions to give the extended enough space)

Note before partitioning, make sure you have your data backed up. There is always a small risk associated with partitioning. I recommend creating restore DVDs for your windows OS as well if your computer didn't come with these. And also a windows repair CD.

---

### Post by lesliek on 2011-11-26
In case anyone who has an HP Windows 7 computer that came with four partitions pre-installed, all of them "primary" partitions, is reading this thread, I thought I'd add the following, in case you find it helpful.

I found material on the HP Web site that deals with the RECOVERY partition, one of the four pre-installed primary ones. HP says that it doesn't recommend removing that partition (which isn't the same as recommending that it not be removed!). Then, it gives instructions as to how to remove it, which didn't work on my computer anyway. However, booted up in Windows 7, I created the required recovery DVDs (six of them!) using the Recovery Manager and was then able to use the Recovery Manager to delete itself and the entire RECOVERY partition.

The freed-up space was automatically added to the C: partition.

I then shrank the C: partition using Windows Disk Management. After the space from the deleted RECOVERY partition had been added, the C: partition was about 600GB. Windows Disk Management allowed me to shrink it to about 300GB, leaving 300GB unallocated, so that's what I did. (I used Windows Disk Management because I thought that would decrease the risk of breaking the Windows installation, which I want to keep, just in case I need it for something sometime.)

Then I switched to the GParted live CD and used it to create a new extended partition occupying all of the unallocated space I'd just created, which partition replaced the former RECOVERY primary partition. Now, I'll use GParted to create new logical partitions in my new 300GB extended partition. I'll use those new logical partitions as the home for my WUBI-installed Ubuntu that I now intend to migrate.

Leslie

---

### Post by lesliek on 2011-11-26
I appear to have a new problem after using the migration script.

I can boot up either in Ubuntu 10.04 (default) or in Windows 7 and all seems normal.

However, if, in Ubuntu, I go to Computer > File System > Properties, I'm told "some contents unreadable".

I ran GParted from a live CD, unmounted the relevant partition (/dev/sda5) and checked it. No errors were reported.

What could be the explanation for the "some contents unreadable" message and is there a way to fix the problem?

Leslie

---

### Post by bcbc on 2011-11-26
lesliek,
Try running nautilus as root: Alt-F2, gksu nautilus. See if you still get that message.

---

### Post by lesliek on 2011-11-26
Well, I did that, but couldn't find a way to get up an icon for the file system, so as to duplicate what I'd been able to do when I ran nautilus as an ordinary user.

Instead, I got a message saying, "Could not display 'computer:'. Nautilus cannot handle 'computer' locations."

Did the message I got at first not mean what it said? Did it really mean, "some contents unreadable BY YOU, an ordinary user"? If so, that'd be a relief to me, since otherwise everything seems to have gone so well!

Thanks again for all your help: the blog post about the disappearing root.disk, the migration script and your answers to my babyish questions.

Leslie

---

### Post by bcbc on 2011-11-26
> **lesliek said:**
> Well, I did that, but couldn't find a way to get up an icon for the file system, so as to duplicate what I'd been able to do when I ran nautilus as an ordinary user.

Instead, I got a message saying, "Could not display 'computer:'. Nautilus cannot handle 'computer' locations."

Did the message I got at first not mean what it said? Did it really mean, "some contents unreadable BY YOU, an ordinary user"? If so, that'd be a relief to me, since otherwise everything seems to have gone so well!

Thanks again for all your help: the blog post about the disappearing root.disk, the migration script and your answers to my babyish questions.

Leslie
Okay I see what you mean by that error: when you click _G_o, Computer. I just clicked on the file system on the left bar and then _F_ile, Properties.

I hadn't noticed the "some contents unreadable" message before, but I was able to reproduce it and then running as root it didn't appear. Also searching on the error message, it seems to be a consensus that this is a permissions issue. 

So I think it's okay. If you have any other questions, don't hold back. Any and all feedback is welcome ;)

---

### Post by pakopako on 2011-12-08
Not sure if I'm in the right state to ask this (just spend four days almost non-stop trying to unscrew myself after borking a harddrive repartitioning), but I think something went wrong with my migration.

I started with a WUBU install on my HDD, but after a little [stumbling](http://ubuntuforums.org/search.php?searchid=84472487), managed to move it to a USB flash-drive.

Now to do that, I still left a copy of root.disk on SDA (again, stumbling), but bcbc's script copied the right one (the one on the USB). Unfortunately I don't know how it created grub.cfg and I don't know what file I'm editing.

The command-line I used to migrate ```
sudo bash wubi-move-2.1.sh [COLOR=red]/dev/sda3[/COLOR] [COLOR=Blue]/dev/sda4[/COLOR]
```

I'm given GRUB2 upon boot, which is a nice turn of events, but the Ubuntu choice is a bit weird.
```
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
**insmod ext2**
set root='(/dev/sda,msdos3)'
search ..
linux /boot/vmlinuz...
initrd /boot/initrd.img...
```
This gives me a [white-screen of death](http://imageshack.us/photo/my-images/822/p1040916o.jpg/).
Now, if I edit it and remove ```
recordfail
set gfxpayload=$linux_gfx_mode
```, I get a few UDEVD error messages and killing, but I get to my Ubuntu login screen. I tried **"sudo update-grub"**, but the loader doesn't seem to change.

I thought it was affecting my Windows loader (I haven't removed WUBI from Windows yet because having it "installed" meant my USB drive WUBI would work, but that GRUB loader is unchanged.

What did my update-grub update then? And why does it say "insmod ext2" when the partition Ubuntu is resting on is not ext2?

---

### Post by bcbc on 2011-12-08
pakopako,

Check /etc/default/grub for a line like this:
```
#GRUB_GFXMODE=640x480
```

Copy that line, remove the # from the front and set it to:
```
GRUB_GFXMODE=text
```

By the way, to edit the file:
```
gksu gedit /etc/default/grub
#or
sudo nano /etc/default/grub
```

Then run "sudo update-grub" again. If that works okay you might want to experiment with different values other than 'text'. See here for more info: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

PS that "insmod ext2" is okay. It's probably just a legacy naming issue, but it's used for any *ext* file system.

Also, what graphics card do you have? Do you have any custom drivers installed?

---

### Post by pakopako on 2011-12-09
> **bcbc said:**
> Then run "sudo update-grub" again. If that works okay you might want to experiment with different values other than 'text'. See here for more info: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
...
Also, what graphics card do you have? Do you have any custom drivers installed?
Thanks bcbc. I'm no longer getting that white screen after selecting Ubuntu, it just turns off. It turns back on again when I'm at the Ubuntu login screen.

I am curious why that worked. I rebooted and edited the entry and found the starting two lines to be the same. And when I hit CTRL-X to see it run, the UDEVD errors no longer showed up. Granted, a quarter-line of ANSI text showed up in the upper left, but then the screen did the shut off and on bit before the login screen.

What is supposed to happen after selecting Ubuntu from GRUB?

I'm running 11.04 on an M200 laptop; according to [lspci and lshw]("https://help.ubuntu.com/community/BinaryDriverHowto"), my built-in video is a NV34M [nVidia Go5200 32M/64M]. Pretty sure I don't have custom drivers, just the standard nVidia ones from the Ubuntu Software Center.

---

### Post by bcbc on 2011-12-09
> **pakopako said:**
> Thanks bcbc. I'm no longer getting that white screen after selecting Ubuntu, it just turns off. It turns back on again when I'm at the Ubuntu login screen.

I am curious why that worked. I rebooted and edited the entry and found the starting two lines to be the same. And when I hit CTRL-X to see it run, the UDEVD errors no longer showed up. Granted, a quarter-line of ANSI text showed up in the upper left, but then the screen did the shut off and on bit before the login screen.

What is supposed to happen after selecting Ubuntu from GRUB?

I'm running 11.04 on an M200 laptop; according to [lspci and lshw]("https://help.ubuntu.com/community/BinaryDriverHowto"), my built-in video is a NV34M [nVidia Go5200 32M/64M]. Pretty sure I don't have custom drivers, just the standard nVidia ones from the Ubuntu Software Center.
The lines don't change, but the value of $linux_gfx_mode does. And it forces grub into text mode.

There's some tweaking required for nvidia and unfortunately I don't know a lot about this as I've never owned an nvidia card. I suggest you keep your current setup or play with some different graphic resolutions, and maybe start a new thread to find out how to get around this problem.

Good luck!

---

### Post by pakopako on 2011-12-10
> **bcbc said:**
> The lines don't change, but the value of $linux_gfx_mode does. And it forces grub into text mode.

There's some tweaking required for nvidia and unfortunately I don't know a lot about this as I've never owned an nvidia card. I suggest you keep your current setup or play with some different graphic resolutions, and maybe start a new thread to find out how to get around this problem.

Good luck!
Thanks bcbc, I think I'll keep what I have for now since it's letting me boot into Ubuntu with little problems. I still see udevd errors and killed processes, but no signs that my installation is hindered. In fact, [other users here have similar errors](http://ubuntuforums.org/showthread.php?t=1690959) and a workaround is found. (Although, again, I don't understand exactly why the workaround works or what was wrong in the first place.)

Thanks again, and Happy Holidays!

---

### Post by Tallowman on 2011-12-17
Just used your script to migrate my Wubi 11.10 to a new partition on my laptop. Outstanding - amazed at how simple this has been. 

Just started with Linux and Ubuntu as I start a new job in Jan with a web company that use Ubuntu. So far loving the support, the ease of use, the community, etc etc  I could go on. 

Thanks again for the effort you have put into this!

One question, what are the new memtest options I have in the grub now?

Cheers,
Tallowman :P

---

### Post by bcbc on 2011-12-17
> **Tallowman said:**
> Just used your script to migrate my Wubi 11.10 to a new partition on my laptop. Outstanding - amazed at how simple this has been. 

Just started with Linux and Ubuntu as I start a new job in Jan with a web company that use Ubuntu. So far loving the support, the ease of use, the community, etc etc  I could go on. 

Thanks again for the effort you have put into this!

One question, what are the new memtest options I have in the grub now?

Cheers,
Tallowman :P
[Memtest]("http://packages.ubuntu.com/lucid/memtest86+") tests your RAM for errors. It runs a long time... from what I've read (since I've never bothered to test my own RAM). My feeling is that it's a low percentage thing so it's not worth it unless you have intermittent, unexplained problems - or you've added/removed memory chips yourself.

You can hide it from grub if you want... or just ignore it. :)

---

### Post by linux_noobq2m on 2012-01-03
I misunderstood Wubi. I thought it was a program that would *install* ubuntu on a new partition, not just a virtual image, but the real thing. So, before installing ubuntu through wubi, I made a new partition, and installed wubi on that partition. Now I want to migrate wubi to the new partition which has wubi installed, and thus, is not empty. Can I use the method here to do this safely? And, after migrating, can I still uninstall wubi(ubuntu) from program files through windows, and have ubuntu working properly?

I am a beginner, so please try to answer in simple way...

Thanks :D

---

### Post by bcbc on 2012-01-03
> **linux_noobq2m said:**
> I misunderstood Wubi. I thought it was a program that would *install* ubuntu on a new partition, not just a virtual image, but the real thing. So, before installing ubuntu through wubi, I made a new partition, and installed wubi on that partition. Now I want to migrate wubi to the new partition which has wubi installed, and thus, is not empty. Can I use the method here to do this safely? And, after migrating, can I still uninstall wubi(ubuntu) from program files through windows, and have ubuntu working properly?

I am a beginner, so please try to answer in simple way...

Thanks :D

It's possible but it's more complex than the default migration (which runs right from the current Wubi install). You'll need to migrate using a live CD/USB i.e. boot from an Ubuntu CD/USB, select "Try Ubuntu" and then download the script and use the ***--root-disk=*** option.

Since you'll be overwriting (and formatting) the partition that contains your current Wubi install, you won't be able to keep it as well as test the migrated install. You'll need to uninstall Wubi prior to migrating. So you must make sure you copy the virtual disk (root.disk) before uninstalling. Note: in some cases there may be other virtual disks - to be safe, copy the entire ***\ubuntu\disks*** directory to a safe place either your C: drive, or an external drive. Call it e.g. C:\wubidisks\ or something different than \ubuntu because Wubi (when it boots) looks specifically for this named folder.

So... here are some example steps (assuming your C: partition is /dev/sda2 and your target partition is /dev/sda5):
1. Copy \ubuntu\disks\ to C:\wubidisks (make sure all the .disk files are copied)
2. Uninstall Wubi
3. Boot from a live CD
4. Format your target partition to 'ext4' using GParted. Prepare a swap partition if required
5. Mount the C: partition (e.g. if it's /dev/sda2)
```
sudo mount /dev/sda2 /mnt
```
5. Download the script and run:
```
sudo bash wubi-move-2.1.sh --root-disk=/mnt/wubidisks/root.disk /dev/sda5
```

So... not entirely simple, but probably a lot less work than reinstalling from scratch.

I didn't mention backups, but whenever you partition you should make sure you have up to date backups, and also you should make sure important data on the root.disk is backed up always.

I made up some partitions for the examples above - if you need instructions for specific partitions, let me know. Also, the root.disk migration is not for grub-legacy (this only applies to those people who installed Wubi prior to release 9.10 and upgraded).

---

### Post by linux_noobq2m on 2012-01-03
First off, thanks for your reply! Really appreciate the help.

> **bcbc said:**
> You'll need to migrate using a live CD/USB i.e. boot from an Ubuntu CD/USB, select "Try Ubuntu" and then download the script and use the ***--root-disk=*** option.

I didnt understand. Download what script?

> **bcbc said:**
> Since you'll be overwriting (and formatting) the partition that contains your current Wubi install, you won't be able to keep it as well as test the migrated install. You'll need to uninstall Wubi prior to migrating. So you must make sure you copy the virtual disk (root.disk) before uninstalling. Note: in some cases there may be other virtual disks - to be safe, copy the entire ***\ubuntu\disks*** directory to a safe place either your C: drive, or an external drive. Call it e.g. C:\wubidisks\ or something different than \ubuntu because Wubi (when it boots) looks specifically for this named folder.

So, if I uninstall wubi, would I still be able to boot to windows? I know this might be a silly question. Since wubi installs with its bootloader, and when I uninstall wubi, the bootloader will also get uninstalled; so, is there a chance that there is no bootloader after uninstalling wubi?

> **bcbc said:**
> So... here are some example steps (assuming your C: partition is /dev/sda2 and your target partition is /dev/sda5):
1. Copy \ubuntu\disks\ to C:\wubidisks (make sure all the .disk files are copied)
2. Uninstall Wubi
3. Boot from a live CD
4. Format your target partition to 'ext4' using GParted. Prepare a swap partition if required
5. Mount the C: partition (e.g. if it's /dev/sda2)
```
sudo mount /dev/sda2 /mnt
```

I know this does not need to be asked, but I'm just curious; why do I need to mount C drive?

> **bcbc said:**
> 5. Download the script and run:
```
sudo bash wubi-move-2.1.sh --root-disk=/mnt/wubidisks/root.disk /dev/sda5
```

So... not entirely simple, but probably a lot less work than reinstalling from scratch.

I didn't mention backups, but whenever you partition you should make sure you have up to date backups, and also you should make sure important data on the root.disk is backed up always.

I made up some partitions for the examples above - if you need instructions for specific partitions, let me know. Also, the root.disk migration is not for grub-legacy (this only applies to those people who installed Wubi prior to release 9.10 and upgraded).

The partition on which I want to install ubuntu is /sda2. And, I am planning to make another partition /sda3 for swap memory. For that, would I need to mount the swap partition using GParted before making it the swap partition?

Ok, so here are the steps I am going to do. Please correct if required:

1.Copy the /ubuntu/disks folder to C:\wubidisks\
2.Uninstall wubi
3.Download ubuntu and boot from USB(because I am using netbook, and it does not have CD drive) by following the instructions [[COLOR="BLUE"]here[/COLOR]]("http://www.ubuntu.com/download/ubuntu/download").
4. Format **/sda2** to 'ext4' using GParted. Prepare a swap partition /sda3. **(Should I do the second part in windows itself? Using disk management?)**
5. Mount the **/sda1 (C:\, where windows is installed, right?)** partition
```
sudo mount /dev/sda1 /mnt
```
6. Download the (what?) script and run:
```
sudo bash wubi-move-2.1.sh --root-disk=/mnt/wubidisks/root.disk /dev/sda2 [COLOR="RED"]/dev/sda3 (for swap partition)[/COLOR]
```
7.Shut Down and remove USB.
8.Start the computer, and hopefully it wil have dual boot with windows and ubuntu,:D !

Thanks again!

Please reply "yes" if all steps are right. :D

---

### Post by bcbc on 2012-01-03
The script is the migration script attached to [post #1]("http://ubuntuforums.org/showpost.php?p=9520119&postcount=1") of this thread.

Wubi doesn't replace the windows bootloader. It boots via the windows boot manager using a combination of grub4dos and grub2. So when you uninstall Wubi, it will not affect Windows booting.
When you migrate it will replace the windows bootloader with Grub2.

You can create space for the swap partition using the Windows disk management console, but you cannot create the swap partition itself. Use GParted from the live USB to do this.

Finally you need to mount the /dev/sda1 partition so that the script can access the root.disk (it's not mounted automatically from a live CD/USB)
--------
So, all the steps you have are correct. I'd probably run the live USB first to make sure it's working properly beforehand.

Oh and one more thing, the live USB architecture (32bit vs 64bit) must match the Wubi install. So check which you have first (the output of this will report whether it's 32-bit or 64-bit):
```
file /bin/bash
```

---

### Post by linux_noobq2m on 2012-01-06
Sorry for the late question (was busy for past days, and it took really long to download ubuntu i386 iso file, coz I have slow net connection). Anyways, I have finished downloading the i386.iso for ubuntu. I just have three questions:

1.I have a 1GB USB drive, and not a single 2GB one. Can I use the 1GB USB? Or is it preferred to use 2GB one? If yes, then why?

2.Since I am going to boot from USB, should I choose the "Try ubuntu" option after bootng into ubuntu? And then download the script?

3.There are different versions of ubuntu. WOuld you advise installing xubuntu instead of normal ubuntu? I have a HP Mini 2133. It has Intel Atom 1200 MHzprocesor, 2GB of RAM and 30GB of hard disk(for ubuntu). So, since I have lot of RAM, would installing xubuntu make any difference? The only problem I am facing with ubuntu is that I cannot play flash videos smoothly right now using wubi, so I dont know if this problem is due to me using wubi or GNOME using lot of resources. 

Thanks!

---

### Post by bcbc on 2012-01-06
> **linux_noobq2m said:**
> Sorry for the late question (was busy for past days, and it took really long to download ubuntu i386 iso file, coz I have slow net connection). Anyways, I have finished downloading the i386.iso for ubuntu. I just have three questions:

1.I have a 1GB USB drive, and not a single 2GB one. Can I use the 1GB USB? Or is it preferred to use 2GB one? If yes, then why?

2.Since I am going to boot from USB, should I choose the "Try ubuntu" option after bootng into ubuntu? And then download the script?

3.There are different versions of ubuntu. WOuld you advise installing xubuntu instead of normal ubuntu? I have a HP Mini 2133. It has Intel Atom 1200 MHzprocesor, 2GB of RAM and 30GB of hard disk(for ubuntu). So, since I have lot of RAM, would installing xubuntu make any difference? The only problem I am facing with ubuntu is that I cannot play flash videos smoothly right now using wubi, so I dont know if this problem is due to me using wubi or GNOME using lot of resources. 

Thanks!
I don't know why the [ubuntu website]("http://www.ubuntu.com/download/ubuntu/download") states you need at least 2GB of free space on the USB. Since the ISO is only 700MB I'd assume 1GB is sufficient, but really I am not in a position to comment on this as all my USB sticks are 2GB or more.

The migration converts your current Wubi install to a normal dual boot. It doesn't install any new version of Ubuntu, so you can't switch to Xubuntu or Lubuntu while migrating. You can convert Ubuntu using techniques such as this: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu) (I haven't tried this myself).

Since your questions aren't related to the migration, and you'll get a lot more responses from others in the community, I suggest you create a new thread with those questions if you want more info.

---

### Post by Xtreamer on 2012-01-07
txs man It worked like a charm. And now i can use ubuntu and xp from different partitions! TXS

---

### Post by bcbc on 2012-01-07
> **Xtreamer said:**
> txs man It worked like a charm. And now i can use ubuntu and xp from different partitions! TXS

You're welcome! Thanks for the feedback.

---

### Post by clueless77 on 2012-01-08
Does the (move.sh) also need to be downloaded to perform migration?


Or is that just an older file? Sorry if I answered my own question.

---

### Post by bcbc on 2012-01-08
> **clueless77 said:**
> Does the (move.sh) also need to be downloaded to perform migration?


Or is that just an older file? Sorry if I answered my own question.

Yeah that's just a bit of history. I haven't removed any scripts, but all you need is the latest (2.1).

---

### Post by clueless77 on 2012-01-09
> **bcbc said:**
> Yeah that's just a bit of history. I haven't removed any scripts, but all you need is the latest (2.1).

One other question, hopefully you see this soon, how should i designate the partition of my hard drive? Meaning should I make it another drive or something else? Also how and when do I make a Ubuntu /home partition and how to get settings there or will they automatically go after migration?

---

### Post by bcbc on 2012-01-09
> **clueless77 said:**
> One other question, hopefully you see this soon, how should i designate the partition of my hard drive? Meaning should I make it another drive or something else? Also how and when do I make a Ubuntu /home partition and how to get settings there or will they automatically go after migration?
You have to supply the target partition to the script. So if you're migrating to /dev/sda5 you'd run:
```
sudo bash wubi-move-2.1.sh /dev/sda5
```

The script will ensure that it's a valid partition.

The 2.1 release only supports migration to a single target partition. I do have a new version that supports migration to separate partitions, but it's not something in great demand so I'm not planning to release it any time soon. However, if you want it you can get it here: [https://github.com/bcbc/Wubi-move/zipball/proposed](https://github.com/bcbc/Wubi-move/zipball/proposed)
If you choose to use it, you could migrate e.g. to /dev/sda5 (root) and /dev/sda6 (/home) as follows:
```
###Note that the script is called **wubi-move.sh** in that zip
sudo bash wubi-move.sh --home=/dev/sda6 /dev/sda5
```

If you don't use the 'proposed' script and want to manually create a separate /home partition after the fact, then you'd follow the standard guides out there to copy /home to the partition, update /etc/fstab.

---

### Post by clueless77 on 2012-01-09
Well I am going to create one primary partition and a small swap partition, so there will only be 3 partitions, sda3 and ada4 if my thinking is correct, but should i create one smaller partition in front to create a /home partition inside Ubuntu thus making the migration sda4 and sad5. Also I am creating partitions inside Windows, so how should i name the partitions, its where I a little fuzzy?

Sorry about all the questions, as you can tell i am learning.

---

### Post by bcbc on 2012-01-09
> **clueless77 said:**
> Well I am going to create one primary partition and a small swap partition, so there will only be 3 partitions, sda3 and ada4 if my thinking is correct, but should i create one smaller partition in front to create a /home partition inside Ubuntu thus making the migration sda4 and sad5. Also I am creating partitions inside Windows, so how should i name the partitions, its where I a little fuzzy?

Sorry about all the questions, as you can tell i am learning.

You shouldn't create the partitions in Windows - you can make space for them in Windows, but you should create them in Ubuntu because Windows cannot create ext4 or swap partitions.

You don't have to name the partitions (that's the label). I'm referring to the partition device as Ubuntu refers to it, so the first hard drive is designated /dev/sda and the primary partitions will be numbered 1 2 3 4. Logical partitions are numbered 5 6 7 8 etc. So the first logical partition is /dev/sda5

You can only have 4 primary partitions (max) but if one of these is an extended partition you can create many logical partitions. So, I recommend created a single extended partition with as much space as you want to assign to Ubuntu, and then creating as many logical partitions as you need.
If you are planning to create a separate partition for /home you should do this upfront.

---

### Post by clueless77 on 2012-01-09
Thank you for all your help, I decided to just start from scratch and do a true duel boot, I did the resize last night and wasn't enough still, for what i am trying to do. So I am sure we will cross paths again, again thanks for the help.

---

### Post by bcbc on 2012-01-09
> **clueless77 said:**
> Thank you for all your help, I decided to just start from scratch and do a true duel boot, I did the resize last night and wasn't enough still, for what i am trying to do. So I am sure we will cross paths again, again thanks for the help.

You're welcome! Enjoy!

---

### Post by bariamtak on 2012-01-10
I install with WUBI inside windows 7 on a separate drive.
I have a problem here. when i type the commands i got this. I don't knw whether i have a swap or not.
how do I proceed next? Do i just proceed as it says in the picture? its urgent.



[SIZE=2][COLOR=black]wubi-move-2.0.sh.tar.gz
bariamtak@ubuntu:~/Downloads$ sudo fdisk -l
[sudo] password for bariamtak: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1707a8a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1845247      921600    b  W95 FAT32
/dev/sda2         1845248   206647295   102401024    7  HPFS/NTFS/exFAT
/dev/sda3       206647296   311525375    52439040    7  HPFS/NTFS/exFAT
/dev/sda4       311525376   976771071   332622848    f  W95 Ext'd (LBA)
/dev/sda5       311527424   416395263    52433920    7  HPFS/NTFS/exFAT
/dev/sda6       416397312   584179711    83891200    7  HPFS/NTFS/exFAT
/dev/sda7       584181760   751964159    83891200    7  HPFS/NTFS/exFAT
/dev/sda8       751966208   856834047    52433920    7  HPFS/NTFS/exFAT
/dev/sda9       856836096   976771071    59967488    7  HPFS/NTFS/exFAT
bariamtak@ubuntu:~/Downloads$ 
[/COLOR][/SIZE]

---

### Post by bcbc on 2012-01-10
bariamtak,

You should create a [swap]("https://help.ubuntu.com/community/SwapFaq") partition if you want it. Wubi uses a swap file, but if you migrate without a swap partition, your migrated install wont't have any swap.

You also don't have any ext4 partitions to migrate to. While the older versions of the migration can migrate to a partition marked as ntfs (type 7) - and it works fine, because it still replaces the file system with ext4 - it's better to replace the ntfs partition with a new ext4 partition as it will avoid confusion later.

So use the newest version of the script 2.1, and it won't let you proceed unless your target is a valid, empty linux partition (type 83) and if you want a swap it has to be type 82.

---

### Post by VVAW on 2012-01-10
bcbc
I am in need of Help I have a install that I can't boot into this has been a ongoing on/off issue. I am at the point were I would like to have my root.disk installed onto another HD and no more dual boot wubi..


Can I run a live cd and attach another hardrive and do this.
Please help I am not the greatest in linux. I have been using ubuntu for studies and need my work back

---

### Post by bcbc on 2012-01-10
> **VVAW said:**
> bcbc
I am in need of Help I have a install that I can't boot into this has been a ongoing on/off issue. I am at the point were I would like to have my root.disk installed onto another HD and no more dual boot wubi..


Can I run a live cd and attach another hardrive and do this.
Please help I am not the greatest in linux. I have been using ubuntu for studies and need my work back

Yes you can migrate from a root.disk. The instructions shown here are for someone who wants to replace windows, but they're good for migrating a root.disk from a live CD to any partition: [http://askubuntu.com/a/93963/14916](http://askubuntu.com/a/93963/14916)

However, if you're having problems booting or root.disk corruption (which I noticed from your other thread) then you could have issues depending on what the problem is.

---

### Post by VVAW on 2012-01-10
yes I am issues booting up. I tried everything but keeping getting a blinking cursor in the top left hand corner. I don't want to loose all that work. So I am desperate. I keep doing chkdsk /r and trying what ever I can to boot up

---

### Post by bcbc on 2012-01-10
> **VVAW said:**
> yes I am issues booting up. I tried everything but keeping getting a blinking cursor in the top left hand corner. I don't want to loose all that work. So I am desperate. I keep doing chkdsk /r and trying what ever I can to boot up

Please run the bootinfoscript and post the results. See if you can [mount the root.disk]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") and if not, fsck it.

Try editing the grub menu entry (hit E) remove 'quiet splash' and see where it halts.

These are just a few ideas. Sometimes corruption occurs on the internal ext4 filesystem with Wubi, and sometimes on ntfs. If it's internal, then running chkdsk won't help.

---

### Post by VVAW on 2012-01-10
Sorry for the delay. Here is the results. I am not sure how to do the other tasks..


 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   609,008,084   609,008,022   7 NTFS / exFAT / HPFS
/dev/sda2         609,008,085   625,137,344    16,129,260   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       12420771-eb61-4a1c-9af3-27ebe1460869   ext4       
/dev/sda1        0CB68709B686F30E                       ntfs       HP
/dev/sda2        2C88743C8874071C                       ntfs       Recovery

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde

---

### Post by bcbc on 2012-01-10
> **VVAW said:**
> Sorry for the delay. Here is the results. I am not sure how to do the other tasks..


...

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error


You need to fsck the root.disk:
```
sudo mount /dev/sda1 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk

```

---

### Post by VVAW on 2012-01-10
how do I do run those commands with live cd or boot up 
and somehow issues those commands

those for your help

---

### Post by bcbc on 2012-01-10
> **VVAW said:**
> how do I do run those commands with live cd or boot up 
and somehow issues those commands

those for your help

Boot from the Ubuntu CD, select "Try Ubuntu". When you see the desktop, drop to a terminal Ctrl+Alt+T and run those commands I gave you.
The first mounts the ntfs partition /dev/sda1
The second runs fsck on the root.disk file residing on /dev/sda1 - to fix the internal ext4 file system within the file.

You can run also add the options -vy to fsck (v=verbose, y=fix without prompting) i.e. sudo fsck -vy /mnt/ubuntu/disks/root.disk

---

### Post by VVAW on 2012-01-10
Thank you thank you thank you boot up 

Now I need to figure out how to put this on a differnt hard drive and be done with wubi install

I am going to follow these instructions
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by bariamtak on 2012-01-10
thank you bcbc for the help.
I just proceed without a swap. I don't really know what swap is actually.Now i have more problems. I still have the wubi installation in one separate drive so now i have two disk from the first wubi install (in saparate drive) and one from migration. How do I uninstalled my wubi ? I tried to uninstall from the control panel in windows but i got an error that say that the target is not found or something like that ( I don't remember ).
In the beginning i install ubuntu from wubi and i happen to format the drive on which ubuntu was. So i install again and i got two ubuntu in the boot menu entries. I install easyBCD in windows to delete one entry ( as suggested by someone in google ). It work but now i uninstall easyBCD and tried to uninstall wubi but i got the error as describe before.How do I rmove my wubi ? shall i just format the drive ?
 Another problem is i got the normal boot menu and when i choose windows it shows me another boot menu to choose from. One is windows 7 and one is ubuntu which i guess the one through wubi.How do i fix this.
thanks.

---

### Post by bcbc on 2012-01-11
> **bariamtak said:**
> thank you bcbc for the help.
I just proceed without a swap. I don't really know what swap is actually.Now i have more problems. I still have the wubi installation in one separate drive so now i have two disk from the first wubi install (in saparate drive) and one from migration. How do I uninstalled my wubi ? I tried to uninstall from the control panel in windows but i got an error that say that the target is not found or something like that ( I don't remember ).
In the beginning i install ubuntu from wubi and i happen to format the drive on which ubuntu was. So i install again and i got two ubuntu in the boot menu entries. I install easyBCD in windows to delete one entry ( as suggested by someone in google ). It work but now i uninstall easyBCD and tried to uninstall wubi but i got the error as describe before.How do I rmove my wubi ? shall i just format the drive ?
 Another problem is i got the normal boot menu and when i choose windows it shows me another boot menu to choose from. One is windows 7 and one is ubuntu which i guess the one through wubi.How do i fix this.
thanks.
You can use either easybcd or bcdedit (Microsofts built in command line tool) to remove the Wubi Ubuntu entry from the Windows boot manager. For bcdedit, go to an _administrator_ command prompt and enter: bcdedit
This will output the windows boot manager entries. Note the {GUID} for Ubuntu and delete it with:
```
bcdedit /delete {GUID}
```

Please also review how to [manually remove Wubi]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F") which may be necessary if the automatic uninstall doesn't work.

---

### Post by VVAW on 2012-01-11
bcbc
EDIT

From my current Harddrive can I just remove windows and have Ubuntu the only OS.

Or how can I install root.disk onto a new harddrive without windows or dualboot of any kind

Everytime I reboot my pc I have boot back into a live cd and mount the drive that boot up.

I am done with windows on this Harddrive 

Please let me know thank you

---

### Post by bcbc on 2012-01-11
Yes you can migrate from a root.disk. See here: [http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration](http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration)

You can also migrate to another hard drive (e.g. an external drive) from the Wubi install, which is a lot simpler.
1. boot Wubi
2. plug in external drive, create partition(s) e.g. /dev/sdb1 for root and /dev/sdb5 for swap
3. migrate
```
sudo bash wubi-move-2.1.sh /dev/sdb1 /dev/sdb5
```
The script will only install the Grub2 bootloader on the target drive i.e. /dev/sdb in this case. So /dev/sda is left untouched.

Note that this script moves normal installs around as well. (So you can migrate to an external, and then migrate from there somewhere else, while at each step being able to confirm the migrated install works correctly before removing the source).

---

### Post by coldjeanz on 2012-01-15
I'm interested in trying this now but I just want to make sure these steps would work

I found this video and creating the partition looks really easy from the way he did it:

[http://www.youtube.com/watch?v=6mePKIcafq4](http://www.youtube.com/watch?v=6mePKIcafq4)

If I follow the steps in that video to create the partition, do I just boot back into Wubi and then use the automated migration scripts? How will it know which newly made drive to install Ubuntu on to? And how do I know whether to use either:

"To migrate to /dev/sda5 without swap"

or 

"To migrate to /dev/sda5 with swap on /dev/sda6"

Thank you :)

---

### Post by bcbc on 2012-01-16
> **coldjeanz said:**
> I'm interested in trying this now but I just want to make sure these steps would work

I found this video and creating the partition looks really easy from the way he did it:

[http://www.youtube.com/watch?v=6mePKIcafq4](http://www.youtube.com/watch?v=6mePKIcafq4)

If I follow the steps in that video to create the partition, do I just boot back into Wubi and then use the automated migration scripts? How will it know which newly made drive to install Ubuntu on to? And how do I know whether to use either:

"To migrate to /dev/sda5 without swap"

or 

"To migrate to /dev/sda5 with swap on /dev/sda6"

Thank you :)
That tutorial shows how to shrink a partition using vista/win7. But it creates a single primary partition in the space and formats it as ntfs. What you want to do is shrink the partition and leave it as free space.
Then you can boot an Ubuntu CD/USB - select "Try Ubuntu" - and run GParted and create an extended partition in that space and then 2 logical partitions. One for Ubuntu (format it as ext4) and one for a swap partition (that is > than the size of your RAM; so you can hibernate).

By default these two logical partitions will be /dev/sda5 and /dev/sda6 so you can migrate using that command shown on post #1.

There is a partitioning guide I linked to in post #1 as well that is pretty good, so check that out.

You should just make sure you don't have 4 primary partitions already (some computers come with this, and you can't create the extended partition in this case). Also, there's always a small risk with partitioning so make sure you backup first and create a windows repair cd and restore disks if you don't have them already.

---

### Post by thinkfreedom on 2012-02-15
i migrated all the files from the above mentioned wubi-move script...now is it safe to remove wubi installed files in windows partition?

---

### Post by bcbc on 2012-02-16
> **thinkfreedom said:**
> i migrated all the files from the above mentioned wubi-move script...now is it safe to remove wubi installed files in windows partition?

If you did the 'default' migration, you installed the Grub bootloader, and the first menu you see when booting is the Grub Menu, with your migrated Ubuntu as the first option. If that's what you've done, then yes it's safe to remove the Wubi install.

If you're still booting through Windows - the Windows Boot Manager is the first menu you see with Windows (1st) and Ubuntu (2nd) then no, you will have to boot the migrated install and install grub before you remove Wubi.

If you'd like to double check, then please post the result of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and I'll take a look.

---

### Post by trailblazerz11 on 2012-02-16
Hello I am trying to follow the guide you linked to create the partition but run into some issues creating a partition.  
Since my computer includes a recovery drive, there was already an extended partition (sda3) which contains said recovery drive (sd4) 
I also have an sd5 which I guess is my wubi? 

Since I already have extended, Using Gparts I try to expand extended with the unallocated but it errors, saying I can't move it to the left and expand..(I actually took screenshots but didn't know how to use gparts so I didn't actually save em. I can repeat and upload screenies tomorrow if it helps)

Thanks in advance.

---

### Post by bcbc on 2012-02-16
> **trailblazerz11 said:**
> Hello I am trying to follow the guide you linked to create the partition but run into some issues creating a partition.  
Since my computer includes a recovery drive, there was already an extended partition (sda3) which contains said recovery drive (sd4) 
I also have an sd5 which I guess is my wubi? 

Since I already have extended, Using Gparts I try to expand extended with the unallocated but it errors, saying I can't move it to the left and expand..(I actually took screenshots but didn't know how to use gparts so I didn't actually save em. I can repeat and upload screenies tomorrow if it helps)

Thanks in advance.

Please post the output of:
```
sudo fdisk -l
```
Thanks

---

### Post by trailblazerz11 on 2012-02-16
> **bcbc said:**
> Please post the output of:
```
sudo fdisk -l
```Thanks

Here it is:

```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6292c561

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   428365823   214079488    7  HPFS/NTFS/exFAT
/dev/sda3       530766848   594199551    31716352    f  W95 Ext'd (LBA)
/dev/sda4       594199552   625142447    15471448   12  Compaq diagnostics
/dev/sda5       530768896   594199551    31715328    7  HPFS/NTFS/exFAT

```

---

### Post by bcbc on 2012-02-16
trailblazerz11,

/dev/sda3, your extended contains /dev/sda5 (38GB)
/dev/sda4 is separate (physically follows /dev/sda3)

38GB seems like a reasonable size for Ubuntu. You don't even need that much space, because since you are dual booting you probably want to keep your data separate so it's easily accessible to Windows (on an NTFS partition). But if you're using that 38GB partition now, you'll have to either shrink it or delete it in order to create 2 new partitions (one ext4 and one for swap) for the migration.

You could also increase the size of /dev/sda3 by reducing that of /dev/sda2, your main Windows partition (262GB), and then expanding /dev/sda3 to absorb that unallocated space you made. Then you can create new logical partitions for the migration without affecting /dev/sda5.

Note if you're using gparted from your Wubi install it won't let you move the /host partition in any way - so you'll need an Ubuntu CD/USB to do this. 

Please can you confirm where your Wubi is installed:
```
df -h
```
That will indicate the space used as well as the /host partition.

---

### Post by trailblazerz11 on 2012-02-16
I'm away from computer right now. I'll post the additional info in an hour.

The only reason I am trying to expand is because Ubuntu keeps spamming me I have 800 mob left..: ( 
Windows shows my Ubuntu folder has 30gb. I have plenty of space on windows so I unalocated 100gb to create partition to migrate wubi to
I am using gparted from USB can't expand sd3 is my.problem
 
Thanks for quick responses!!!

---

### Post by bcbc on 2012-02-16
> **trailblazerz11 said:**
> I'm away from computer right now. I'll post the additional info in an hour.

The only reason I am trying to expand is because Ubuntu keeps spamming me I have 800 mob left..: ( 
Windows shows my Ubuntu folder has 30gb. I have plenty of space on windows so I unalocated 100gb to create partition to migrate wubi to
Okay I missed the unallocated space... my fdisk reading skills need some work obviously. So I'm getting 110GB for /dev/sda2 and 16GB for /dev/sda5 now (sound right?)

So, if you shrunk /dev/sda2 then you need to expand /dev/sda3 to the left to absorb that space, and then you can create the new logical partitions for the migration within that. 

I'll wait for the df output though before continuing.

There are alternatives to migration, e.g. moving data from the wubi install to the /host, or increasing the virtual disk size. However, migrating to a dual boot is in my opinion the best option if you are going to be using Ubuntu long term. And since you've already shrunk /dev/sda2 this makes sense to continue.

---

### Post by trailblazerz11 on 2012-02-16
I gave you the wrong output earlier.  That output was with 48GB unallocated, I further shrunk my Windows 50GB for the total of 100GB i mentioned.  But otherwise you were correct.  150GB sd2, ~15GB sda5 and 100GB unallocated.  

Here is the updated fdisk 
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6292c561

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   327686143   163739648    7  HPFS/NTFS/exFAT
/dev/sda3       530766848   594199551    31716352    f  W95 Ext'd (LBA)
/dev/sda4       594199552   625142447    15471448   12  Compaq diagnostics
/dev/sda5       530768896   594199551    31715328    7  HPFS/NTFS/exFAT

```And df
```
 Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             29G   27G  811M  98% /
udev                  1.9G  4.0K  1.9G   1% /dev
tmpfs                 766M  904K  765M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.9G  128K  1.9G   1% /run/shm
/dev/sda2             157G  110G   47G  71% /host

```

---

### Post by bcbc on 2012-02-16
Okay, so your /host is /dev/sda2. You can run gparted, expand /dev/sda3 to the left to take up that unallocated space. Then create your target ext4 partition for Ubuntu and a swap partition (greater than the size of your RAM for hibernation). If you are going to be sharing data with Windows you might not want to use up all the available space on a single ext4 partition. You will obviously need a minimum of 30GB to migrate, so practically I'dsay 40GB minimum. However, you could probably shuffle some data before migrating if you want to reduce that.

---

### Post by trailblazerz11 on 2012-02-16
That's exactly what i thought to do, expand the extension, create ext4 96GB, and a swap 4GB (i wont share files) 

But I get an error every time I try to move and expand  the extension sda3. 

Heres the pictures, I cant upload here because too big. Sorry for the hassle :(

Current state:
[http://dl.dropbox.com/u/33930055/Pics/IMG_20120216_125030.jpg](http://dl.dropbox.com/u/33930055/Pics/IMG_20120216_125030.jpg)
Expanding extension:
[http://dl.dropbox.com/u/33930055/Pics/IMG_20120216_125054.jpg](http://dl.dropbox.com/u/33930055/Pics/IMG_20120216_125054.jpg)
Error message pops and heres the info:
[http://dl.dropbox.com/u/33930055/Pics/IMG_20120216_125133.jpg](http://dl.dropbox.com/u/33930055/Pics/IMG_20120216_125133.jpg)

---

### Post by bcbc on 2012-02-16
There's a issue with /dev/sda2 (that warning icon). If you click on that what does it say? How did you shrink it (from Windows?) or gparted. Have you booted windows since resizing it if it was from gparted?

---

### Post by trailblazerz11 on 2012-02-16
> **bcbc said:**
> There's a issue with /dev/sda2 (that warning icon). If you click on that what does it say? How did you shrink it (from Windows?) or gparted. Have you booted windows since resizing it if it was from gparted?

I'll boot into gparted and check on the warning icon. 
I shrunk from windows using a partition manager program that was already on my computer/ 
Yes, i have booted several times into windows.  

Booting gparted now, that warning is probably the issue..

---

### Post by trailblazerz11 on 2012-02-16
heres the warning log.
[http://dl.dropbox.com/u/33930055/IMG_20120216_132234.jpg](http://dl.dropbox.com/u/33930055/IMG_20120216_132234.jpg)
[http://dl.dropbox.com/u/33930055/error.jpg](http://dl.dropbox.com/u/33930055/error.jpg)

should i do what it says and go on windows chkdsk /f ?

---

### Post by bcbc on 2012-02-16
I would. 

The software you used to resize the partition shouldn't leave it in an inconsistent state. Just note that running chkdsk /f might mean that Windows 'recovers' files to hidden folders \found.000 \found.001 etc. and possibly will remove what it considers as unrecoverable data. You might consider backing up important data. (That may be overcautious, but I tend to err on the side of caution. Odds are if chkdsk would remove a file due to corruption then you couldn't copy it either).

---

### Post by trailblazerz11 on 2012-02-16
I ran it to auto to auto fix errors, but didnt "scan for and recover bad sectors"
It did get rid of the warning in Gparted but still the same result when i try to expand extension

EDIT: Did some googling could this be the issue
"From your description I would say that, when you booted the live CD, it used the swap on partition 6 and thus the extended partition was in use, not allowing GParted to do the grow operation."
im using usb buti assume its similar?

---

### Post by trailblazerz11 on 2012-02-16
Think I solved from 
[http://ubuntuforums.org/showthread.php?t=1669558&page=2](http://ubuntuforums.org/showthread.php?t=1669558&page=2)
Had to turn off constraint and leave space in between.  

I made ext4 and swap. Seem to have unmounted hard drive after, gave my a scare. But windows loading now after disk check. I'll see if the partitions were applied.

EDIT:  Ugh The partitions were created however fails to convert to ext4..
'attempt to read block from filesystem resulted in short read while creating root dir'
I can create the swap but when I try ext4, after about 2 minutes I can literally hear my hard drive stop and gparted errors out with my hard drive unmounted. Have to reboot.  I just checked hard drive smart data, passed...

---

### Post by bcbc on 2012-02-16
You're not having it easy, that's for sure :confused:

Normally I try and use Windows to shrink itself (Vista/7 can do it with built-in Disk Management tool). But a good partitioning tool should work as well. I'm not going to be able to look at this tonight, but I'll try and do some investigation tomorrow if you haven't sorted it out by then.

---

### Post by The Infinity on 2012-02-18
I just migrated my Ubuntu using this instruction. I think it worked, but there was no new boot loader installed (although I used that option).I just have the old one from Windows.

How can I add there my new migrated Ubuntu?
I prefer to still use the normal Windows boot loader. I had that configuration on an other computer some time before (using openSUSE). There I was able to create a file called Suse.lin which I could add to my Windows boot loader.

Here some information about my hard drives and partitions:
I have two hard drives. On the first one there is Windows 7 installed and there's another partition on it for my files. On the second hard drive there is the partition where is Wubi-Ubuntu installed and there's another partition where is the migrated Ubuntu installed.

---

### Post by bcbc on 2012-02-18
> **The Infinity said:**
> I just migrated my Ubuntu using this instruction. I think it worked, but there was no new boot loader installed (although I used that option).I just have the old one from Windows.

How can I add there my new migrated Ubuntu?
I prefer to still use the normal Windows boot loader. I had that configuration on an other computer some time before (using openSUSE). There I was able to create a file called Suse.lin which I could add to my Windows boot loader.

Here some information about my hard drives and partitions:
I have two hard drives. On the first one there is Windows 7 installed and there's another partition on it for my files. On the second hard drive there is the partition where is Wubi-Ubuntu installed and there's another partition where is the migrated Ubuntu installed.
The migration script will only install the grub2 bootloader on the target drive - most likely it did, but since you're probably booting from your primary Windows drive, you don't see the difference.

You could see if you can change the drive boot order on the fly - i.e. tell BIOS which drive to boot from. That would be a way to decide whether to boot Ubuntu or Windows. Or you could permanently set BIOS to boot from the Ubuntu drive - this way you leave the Windows drive untouched, but can still boot from Grub on the second drive.

Or you can look at something like easyBCD. I've never used it but that'll let you boot Ubuntu from the windows boot manager.

---

### Post by bcbc on 2012-02-18
> **trailblazerz11 said:**
> Think I solved from 
[http://ubuntuforums.org/showthread.php?t=1669558&page=2](http://ubuntuforums.org/showthread.php?t=1669558&page=2)
Had to turn off constraint and leave space in between.  

I made ext4 and swap. Seem to have unmounted hard drive after, gave my a scare. But windows loading now after disk check. I'll see if the partitions were applied.

EDIT:  Ugh The partitions were created however fails to convert to ext4..
'attempt to read block from filesystem resulted in short read while creating root dir'
I can create the swap but when I try ext4, after about 2 minutes I can literally hear my hard drive stop and gparted errors out with my hard drive unmounted. Have to reboot.  I just checked hard drive smart data, passed...

I can't find much on this - some people think it's a failing hard drive issue but strange that you can create an NTFS file system in some cases, but not ext2/3/4. You could try leaving a bit of room between the start of the partition (1MB). 
If it isn't a hardware issue, then maybe there's something funny in the partition table. Maybe do another copy and paste of:
```
sudo fdisk -l
sudo parted -l
```

I probably won't be able to offer much more on this - maybe a post in the [hardware section of the forum]("http://ubuntuforums.org/forumdisplay.php?f=332") will get some better help.

---

### Post by The Infinity on 2012-02-18
Thanks for you quick answer.
Now I know why there's no difference - I have two drives with two boot loaders.
But to change the order always in the BIOS is not a good solution. Maybe I can configure my BIOS to show me an selection. Or I just use GRUB like you suggested.

EDIT: I tested it now and things are exactly like you posted. I configured my BIOS to show me an selection and it works fine. My old Wubi-Ubuntu is uninstalled now :-).

---

### Post by bcbc on 2012-02-19
> **The Infinity said:**
> Thanks for you quick answer.
Now I know why there's no difference - I have two drives with two boot loaders.
But to change the order always in the BIOS is not a good solution. Maybe I can configure my BIOS to show me an selection. Or I just use GRUB like you suggested.

EDIT: I tested it now and things are exactly like you posted. I configured my BIOS to show me an selection and it works fine. My old Wubi-Ubuntu is uninstalled now :-).

Great to hear! Thanks for the feedback.

---

### Post by The Infinity on 2012-02-19
It just seemed to work perfectly.

As I wanted to put the computer (using Windows 7) into standby mode I noticed that it doesn't work anymore.
The reason: Windows 7 needs a special file with the name "BCD" to do this (this file also contains the settings of the windows boot loader). It is stored at the 100 MB partition which Windows 7 creates automatically. The problem is that Windows 7 always searches in the first partition of the first drive for that file.
But I changed the order of the hard drives in the BIOS to use the GRUB boot loader, so windows searched in the first partition of the wrong hard drive for that file. The solution: I just copied the file "BCD" from to the first partition of the hard drive which I use for Ubuntu.

I just posted this because I think it is might helpful for other people here who have the same problem.

---

### Post by bcbc on 2012-02-19
> **The Infinity said:**
> It just seemed to work perfectly.

As I wanted to put the computer (using Windows 7) into standby mode I noticed that it doesn't work anymore.
The reason: Windows 7 needs a special file with the name "BCD" to do this (this file also contains the settings of the windows boot loader). It is stored at the 100 MB partition which Windows 7 creates automatically. The problem is that Windows 7 always searches in the first partition of the first drive for that file.
But I changed the order of the hard drives in the BIOS to use the GRUB boot loader, so windows searched in the first partition of the wrong hard drive for that file. The solution: I just copied the file "BCD" from to the first partition of the hard drive which I use for Ubuntu.

I just posted this because I think it is might helpful for other people here who have the same problem.

That's a strange problem I haven't heard about before. Thanks for the heads up.

---

### Post by tmiskiew on 2012-03-02
I have laptop with WindowsXP. I've installed wubi on an external hard drive I'm connecting to via USB. When I'm booting the laptop I'm offered the choice between WinXP and ubuntu. ubuntu works just fine, but I ran out of space.

I tried to run your script, but it fails with:

sudo bash wubi-move.sh /dev/sda5
wubi-move.sh: target_partition (/dev/sda5) must be a valid partition.

Here's what fdisk -l says:

fdisk -l

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1669c708

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   186233039    93116488+   7  HPFS/NTFS/exFAT
/dev/sda2       186233040   195365519     4566240   12  Compaq diagnostics

Disk /dev/sdb: 128.0 GB, 128035675648 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069679 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7cbeea4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   152729954    76364946    7  HPFS/NTFS/exFAT
/dev/sdb2       152729955   250051724    48660885    f  W95 Ext'd (LBA)
/dev/sdb5       152730018   244545535    45907759   83  Linux
/dev/sdb6       244547584   250050559     2751488   82  Linux swap / Solaris
root@ubuntu:/home/tmiskiew/Downloads/bcbc-Wubi-move-4ee6759# fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1669c708

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   186233039    93116488+   7  HPFS/NTFS/exFAT
/dev/sda2       186233040   195365519     4566240   12  Compaq diagnostics

Disk /dev/sdb: 128.0 GB, 128035675648 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069679 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7cbeea4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   152729954    76364946    7  HPFS/NTFS/exFAT
/dev/sdb2       152729955   250051724    48660885    f  W95 Ext'd (LBA)
/dev/sdb5       152730018   244545535    45907759   83  Linux
/dev/sdb6       244547584   250050559     2751488   82  Linux swap / Solaris

```
What am I missing?

Thanks
Thomas

---

### Post by bcbc on 2012-03-02
> **tmiskiew said:**
> I have laptop with WindowsXP. I've installed wubi on an external hard drive I'm connecting to via USB. When I'm booting the laptop I'm offered the choice between WinXP and ubuntu. ubuntu works just fine, but I ran out of space.

I tried to run your script, but it fails with:

sudo bash wubi-move.sh /dev/sda5
wubi-move.sh: target_partition (/dev/sda5) must be a valid partition.

Here's what fdisk -l says:

fdisk -l

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1669c708

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   186233039    93116488+   7  HPFS/NTFS/exFAT
/dev/sda2       186233040   195365519     4566240   12  Compaq diagnostics

Disk /dev/sdb: 128.0 GB, 128035675648 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069679 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7cbeea4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   152729954    76364946    7  HPFS/NTFS/exFAT
/dev/sdb2       152729955   250051724    48660885    f  W95 Ext'd (LBA)
/dev/sdb5       152730018   244545535    45907759   83  Linux
/dev/sdb6       244547584   250050559     2751488   82  Linux swap / Solaris
root@ubuntu:/home/tmiskiew/Downloads/bcbc-Wubi-move-4ee6759# fdisk -l


```
What am I missing?

Thanks
Thomas

You don't have an /dev/sda5. Try /dev/sdb5 instead and I assume you'll want to use the swap on /dev/sdb6 as well.
i.e.
```
sudo bash wubi-move.sh /dev/sdb5 /dev/sdb6
```

PS what version are you running? If you download from here it's supposed to be wubi-move-2.1.sh. You can also download from Git (wubi-move.sh) if you want the latest code but it doesn't seem like you are using any of the unreleased features.

---

### Post by Ceriyx on 2012-03-05
Hi bcbc,
I've followed this for a while but I'm still not sure what I need to do to get started. This is my output from fdisk:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2167    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2168       17368   122096640    7  HPFS/NTFS
/dev/sda3           17368       60802   348881920    f  W95 Ext'd (LBA)
/dev/sda5           17368       60802   348880896    7  HPFS/NTFS

```and this is my output from df:
```

ilesystem            Size Used Avail Use% Mounted on
/dev/loop0             29G   17G   11G  62% /
none                  1.5G  288K  1.5G   1% /dev
none                  1.5G  272K  1.5G   1% /dev/shm
none                  1.5G   96K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda5             333G   31G  303G  10% /host

```My intention is to run:
```

sudo bash wubi-move-2.1.sh /dev/sda5

```Is this correct, or do I need to create a new partition to accept the migration? Alternatively, can I migrate to /sda3?
Thanks in anticipation,
Ceriyx

---

### Post by bcbc on 2012-03-05
Hi Ceriyx,

You will need to create a partition to migrate. If you want to hibernate you'll also need to create a swap partition. You can't migrate directly to /dev/sda5 because that is currently your Ubuntu /host, and you can't migrate to /dev/sda3 because that is an extended partition (that contains /dev/sda5).

But the good news is that you have lots of unused space on /dev/sda5 so you can shrink that and then create 2 new logical partitions: /dev/sda6 as Ext4 and /dev/sda7 as linux-swap. Then migrate to those.

1. Shrink /dev/sda5. If you're running Windows Vista/7 you can do this from Windows' Disk Management console; otherwise you'll need to do it from a live CD or use some other partitioning software. (You can't do this while running the Wubi install as it locks the host: /dev/sda5.)
2. Then use GParted to add the 2 new partitions. You can do this from the Wubi install or a live CD. The swap partition should be a little larger than the size of your RAM e.g. I have a 4.5 GB swap for 4GB RAM.
3. Then you can migrate as follows:
```
sudo bash wubi-move-2.1.sh /dev/sda6 /dev/sda7
```

Things to watch for... 
a. Shrinking the partition might change /dev/sda5's UUID depending on whatever software you use. Grub uses that to boot. Hopefully this doesn't happen, but it's not a big deal if it does: you can just edit the grub menu entry (press 'E' with the first entry selected) and looking at the line starting "linux /boot/vmlinuz.." you would change
```
root=UUID=xxxxx
```
to
```
root=/dev/sda5
```
Then Ctrl+X to boot.

b. GParted is not installed by default in Ubuntu (it is on the Ubuntu live CD). You can install it via Software Centre, Synaptic or command line:
```
sudo apt-get install gparted
```

If you have any other questions, feel free to ask.

---

### Post by Ceriyx on 2012-03-05
Hi bcbc,
Thanks very much for this, I'd been puzzled about this aspect for a while but you have cleared it up nicely. I have have GParted installed and EasyBCD on Windows7 so I will try the Windows tools first (because its the host system), reduce /sda5 to about 40 Gb, and create an ext4 partition and a swap partition with the remaining space. I'd like to absorb /sda3 and /sda5 into /sda2 if that's possible - what do you think?
Best regards,
Ceriyx

---

### Post by bcbc on 2012-03-05
If I understand you correctly you want to split off 290GB for Ubuntu, migrate, and then merge the remaining 40GB on /dev/sda5 back to your main windows partition?

You could do that.

If you intend to share data between windows and ubuntu you might also consider leaving /dev/sda5 as a shared NTFS partition between both OSes instead, because 290GB for Ubuntu is a lot and it's not easily accessible from Windows (I believe there are ext2/3/4 drivers you can use to access linux partitions from Windows, but I think most people probably just use NTFS for this). 
Of course if you don't intend to share data, then you don't need to be concerned about that.

If you decide to merge back /dev/sda5 to /dev/sda2 you'll need to delete it, resize /dev/sda3, and then merge the free space. You don't want to remove /dev/sda3 as it will be the extended partition housing your new logical partitions for Ubuntu - and while you could convert those to primary partitions it's far less flexible (you can only have 4 primary partitions, but you can have more logical partitions than you'll ever need within an extended).

---

### Post by Ceriyx on 2012-03-06
Hi bcbc,
First, the migration went fine, I used Windows disk manager to shrink /sda5 to 40 Gb, Microsoft buries it, I had to use the Help centre to access a link, then find 'Shrink' command in Actions menu; restart and boot to Ubuntu, Grub command already pointed to /dev/sda5; ran GParted, create new partitions in unallocated space, go to Edit menu, 'Apply' to create as /sda6 and /sda7; restart and boot to Ubuntu to check for functionality; run migration script, took about 30 mins to copy files, rebuilds Grub menu with all installed kernels; restart and boot to Ubuntu, everything works fine, so great result.
fdisk -l now shows:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2167    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        2168       17368   122096640    7  HPFS/NTFS
/dev/sda3           17368       60802   348881920    f  W95 Ext'd (LBA)
/dev/sda5           17368       22467    40960000    7  HPFS/NTFS
/dev/sda6           22468       60202   303106356   83  Linux
/dev/sda7           60203       60801     4811436   82  Linux swap / Solaris

```
Your point about keeping /sda5 is well taken; I've got no shortage of space so I'll keep things as they are for the time being and see what use I can make of it.
Thanks again, very much, for your advice and help,
Ceriyx

---

### Post by bcbc on 2012-03-06
Ceriyx,

Awesome job! Enjoy. And great feedback.

PS You can get to Disk Management by hitting the Windows key, typing "Disk man..." and then selecting "Create and format hard disk partitions" from above. (It is a bit buried)

---

### Post by Stonecold1995 on 2012-03-08
Sorry, but I'm very new to Linux, so it's kind of hard for me to follow along.  Anyways, when I try to use the install script, I get this:
```
alex@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda5 /dev/sda6
wubi-move-2.1.sh: target_partition (/dev/sda5) must be a valid partition.
```
I assume that means that I need to make those partitions, because Disk Utility says I only have up to /dev/sda4.  So how do I make the two new partitions (/dev/sda5/ and /dev/sda6/) without loosing or overwriting any data already present on my hard drive from my Windows install?  Is there a simple program that can do it for me?

I'm running Kubuntu 11.10, btw.

---

### Post by bcbc on 2012-03-08
> **Stonecold1995 said:**
> Sorry, but I'm very new to Linux, so it's kind of hard for me to follow along.  Anyways, when I try to use the install script, I get this:
```
alex@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda5 /dev/sda6
wubi-move-2.1.sh: target_partition (/dev/sda5) must be a valid partition.
```
I assume that means that I need to make those partitions, because Disk Utility says I only have up to /dev/sda4.  So how do I make the two new partitions (/dev/sda5/ and /dev/sda6/) without loosing or overwriting any data already present on my hard drive from my Windows install?  Is there a simple program that can do it for me?

I'm running Kubuntu 11.10, btw.
Yes, you do need to create the partitions. Please post the output of:
```
sudo fdisk -l
```
(That's a lower case -L). This should give a good idea of your starting point.
Thanks

---

### Post by Stonecold1995 on 2012-03-08
> **bcbc said:**
> Yes, you do need to create the partitions. Please post the output of:
```
sudo fdisk -l
```
(That's a lower case -L). This should give a good idea of your starting point.
Thanks

```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1a3f0dfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1434804223   717197312    7  HPFS/NTFS/exFAT
/dev/sda3      1434804224  1464936447    15066112    7  HPFS/NTFS/exFAT
/dev/sda4      1464936448  1465147119      105336    c  W95 FAT32 (LBA)

Disk /dev/sdb: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192    15523839     7757824    b  W95 FAT32
```

---

### Post by bcbc on 2012-03-09
> **Stonecold1995 said:**
> ```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1a3f0dfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1434804223   717197312    7  HPFS/NTFS/exFAT
/dev/sda3      1434804224  1464936447    15066112    7  HPFS/NTFS/exFAT
/dev/sda4      1464936448  1465147119      105336    c  W95 FAT32 (LBA)

...
```

Okay so it's not so simple. Some computers come with 4 primary partitions already setup (e.g. some HP computers). And that's the max number you can have. In order to create more partitions, you'd have to delete one of those primary partitions, and then create an extended partition in its place. An extended partition is also a primary partition, but you can create many logical partitions within an extended partition.

So I'm really bad at reading fdisk output ;) but it looks like you have a boot partition 200MB, a main windows partition 734GB, a 15GB restore partition, and a 100MB tools partition. Even if you deleted one of those (only /dev/sda3 and /dev/sda4 are candidates) you'd still need to take some space from /dev/sda2 i.e. shrink it. There's a [nice post]("http://ubuntuforums.org/showpost.php?p=11490815&postcount=570") by lesliek earlier in this thread about how to do this for an HP computer.

If you don't have the stomach for that you could migrate to an external drive.

Hope that helps!

---

### Post by Stonecold1995 on 2012-03-09
> **bcbc said:**
> Okay so it's not so simple. Some computers come with 4 primary partitions already setup (e.g. some HP computers). And that's the max number you can have. In order to create more partitions, you'd have to delete one of those primary partitions, and then create an extended partition in its place. An extended partition is also a primary partition, but you can create many logical partitions within an extended partition.

So I'm really bad at reading fdisk output ;) but it looks like you have a boot partition 200MB, a main windows partition 734GB, a 15GB restore partition, and a 100MB tools partition. Even if you deleted one of those (only /dev/sda3 and /dev/sda4 are candidates) you'd still need to take some space from /dev/sda2 i.e. shrink it. There's a [nice post]("http://ubuntuforums.org/showpost.php?p=11490815&postcount=570") by lesliek earlier in this thread about how to do this for an HP computer.

If you don't have the stomach for that you could migrate to an external drive.

Hope that helps!

So basically, if I don't want to delete any of my partitions, I'll just have to keep my Wubi install?  That won't be *too* bad, will it?  I know it's slightly slower and more susceptible to corruption from a hard-reboot, but other than that it's fine, right?

---

### Post by bcbc on 2012-03-09
> **Stonecold1995 said:**
> So basically, if I don't want to delete any of my partitions, I'll just have to keep my Wubi install?  That won't be *too* bad, will it?  I know it's slightly slower and more susceptible to corruption from a hard-reboot, but other than that it's fine, right?

[Alt + SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot") is your friend. Use it if your mouse/keyboard stop working (Ubuntu freezes).

I recommend keeping important data backed up regularly (but you should do that anyway). I've been running a Wubi install daily to see how unstable it is, but it's worked flawlessly for me... just a couple of freezes (but then i am running the dev release so I'd expect that anyway). But even though my experience has been fine, I can't fully explain why some users do get corruption (not all of them report hard resets), so I'd advise taking reasonable precautions. e.g. data backups and even periodic root.disk backups.

---

### Post by alex2035 on 2012-03-12
Can I install to HD leaving the Wubi Grub where Ubuntu stays last after Windows? --no--bootloader does this?
Will a HD install run better in a 64 bit 11.10?

thank you

---

### Post by bcbc on 2012-03-12
> **alex2035 said:**
> Can I install to HD leaving the Wubi Grub where Ubuntu stays last after Windows? --no--bootloader does this?
Will a HD install run better in a 64 bit 11.10?

thank you

Yes, the *--no-bootloader* option will let you migrate without installing the bootloader and use the 'Wubi grub' to boot. But note that you'll have to keep wubi installed and able to run in order to do this. In addition, if you install a new kernel on your partition install, the Wubi grub will not be updated to show this until you boot the wubi install and run: sudo update-grub

Note: it's possible to add a custom boot entry in wubi's grub menu that will always boot the latest kernel from your partition install

There are alternate ways to keep the windows boot manager in charge e.g. with Windows vista/7 you can use easyBCD (I haven't tried this myself).

I don't understand your last question. If you are asking: "Will Ubuntu 11.10 run faster from a partition than using a wubi install?" then my answer is "yes for some tasks" (but from my personal experience for most things you won't see a huge difference if any). But since you mentioned 64bits maybe I didn't quite understand the question.

---

### Post by alex2035 on 2012-03-12
> **bcbc said:**
> Yes, the *--no-bootloader* option will let you migrate without installing the bootloader and use the 'Wubi grub' to boot. But note that you'll have to keep wubi installed and able to run in order to do this. In addition, if you install a new kernel on your partition install, the Wubi grub will not be updated to show this until you boot the wubi install and run: sudo update-grub

If I have to keep Wubi install it doesnt look a proper way to do this, I would end up  with a 11.10 updated (filewise, etc) and a Wubi 11.10 getting outdated

Note: it's possible to add a custom boot entry in wubi's grub menu that will always boot the latest kernel from your partition install


There are alternate ways to keep the windows boot manager in charge e.g. with Windows vista/7 you can use easyBCD (I haven't tried this myself).


I don't understand your last question. If you are asking: "Will Ubuntu 11.10 run faster from a partition than using a wubi install?" then my answer is "yes for some tasks" (but from my personal experience for most things you won't see a huge difference if any). But since you mentioned 64bits maybe I didn't quite understand the question.

this answered my questions, perhaps it is not worth it, I have everything working great, I only wondered if Photo processing might get faster (raw development, big pictures)

thanks for your help

---

### Post by bcbc on 2012-03-12
> **alex2035 said:**
> this answered my questions, perhaps it is not worth it, I have everything working great, I only wondered if Photo processing might get faster (raw development, big pictures)

thanks for your help
You can see where wubi is slower: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1)

There are other benefits to a partition install - the virtual disk is higher risk than a partition install, because if the root.disk file is corrupted you can lose everything on the virtual disk. As long as you backup data regularly this is less of a concern.

---

### Post by alex2035 on 2012-03-12
Yes, I always had my Ubuntu on HD, but I am bothered over the difficulty to edit Grub2 to make Windows the default boot (for the other 2 people using it), as Wubi does. I have edited Grub and LILO for years now but Grub2 is inescrutable to me, I am not programmer, I could never do this and there is no tweak to easily access it that I know.

---

### Post by bcbc on 2012-03-12
> **alex2035 said:**
> Yes, I always had my Ubuntu on HD, but I am bothered over the difficulty to edit Grub2 to make Windows the default boot (for the other 2 people using it), as Wubi does. I have edited Grub and LILO for years now but Grub2 is inescrutable to me, I am not programmer, I could never do this and there is no tweak to easily access it that I know.

I think this is what you're after: [HOWTO: Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183")

---

### Post by alex2035 on 2012-03-16
I finally used your method and moved Wubi install of 11.10 to an ext4 partition on the same partition as Wubi install. I used the --no-bootloader option just in case.
Now I dont know how to proceed, should I install Grub in the HD install? then update-grub? then deinstall Wubi from Win? or deinstall Wubi first, could I boot 11.10 HD then? I dont think so. you see, I am a bit confused here. thanks for your help.

By the way, HD install is little faster on boot as Wubi, but not a difference launching or using programs. Worth it? not sure, except for security reasons.

---

### Post by bcbc on 2012-03-16
> **alex2035 said:**
> I finally used your method and moved Wubi install of 11.10 to an ext4 partition on the same partition as Wubi install. I used the --no-bootloader option just in case.
Now I dont know how to proceed, should I install Grub in the HD install? then update-grub? then deinstall Wubi from Win? or deinstall Wubi first, could I boot 11.10 HD then? I dont think so. you see, I am a bit confused here. thanks for your help.

By the way, HD install is little faster on boot as Wubi, but not a difference launching or using programs. Worth it? not sure, except for security reasons.
First boot your migrated install. Then to install GRUB 2 to the sdX drive's MBR (sda, sdb, etc.)
```
sudo grub-install /dev/sdX
```
For most people that would be:
```
sudo grub-install /dev/sda
```
This will replace the windows bootloader and the next time you boot, you'll see the grub menu first and have to select windows at the bottom of the list.

I think it's worth it to migrate from a reliability/stability point of view. Speed, security? maybe but it depends on how you use the OS and possibly your computer specs.

---

### Post by alex2035 on 2012-03-22
Finally did as you suggested, then managed to change Grub with grub-customizer, made Win as default and even put some nice boot splash. Thanks a lot.

---

### Post by bcbc on 2012-03-22
> **alex2035 said:**
> Finally did as you suggested, then managed to change Grub with grub-customizer, made Win as default and even put some nice boot splash. Thanks a lot.

Great! You're welcome. :)

---

### Post by aphrxia on 2012-03-24
hi bcbc, 
This is the first time for me here and I just want to say thank you for your awesome job. Got no problems migrating on my Acer Aspire 4750z. Feel much more smoother when running Ubuntu now. Hopefully the battery and power management issue will get fixed soon.

But again, thanks for this cool stuff. And I'm sorry for my crappy English, I'm from Indonesia.. ):P

---

### Post by bcbc on 2012-03-24
> **aphrxia said:**
> hi bcbc, 
This is the first time for me here and I just want to say thank you for your awesome job. Got no problems migrating on my Acer Aspire 4750z. Feel much more smoother when running Ubuntu now. Hopefully the battery and power management issue will get fixed soon.

But again, thanks for this cool stuff. And I'm sorry for my crappy English, I'm from Indonesia.. ):P
You're welcome :)

PS your English is great
PPS The battery life in 12.04 should be much better (that's my experience anyway)

---

### Post by aphrxia on 2012-03-25
> **bcbc said:**
> You're welcome :)

PS your English is great
PPS The battery life in 12.04 should be much better (that's my experience anyway)

Well then can't wait to give 12.04 a test! :p

---

### Post by ofca on 2012-03-27
Sorry if this has already been asked and answered but I haven't found it. I am moving ubuntu to separate partition. Since I'm noobish, [I asked how to do it on linux SE]("http://unix.stackexchange.com/questions/35061/partitioning-ubuntu-and-windows-7-once-and-for-all/35064#comment47598_35064"). Guy there answered and referenced this thread to consult when deleting wubi install. 

So I came here and followed the steps. **But when I execute bash wubi-move to sda2 it says I cannot move it there because partition is not empty.**

Am I doing something wrong? Why does the partition need to be empty?

---

### Post by bcbc on 2012-03-27
> **ofca said:**
> Sorry if this has already been asked and answered but I haven't found it. I am moving ubuntu to separate partition. Since I'm noobish, [I asked how to do it on linux SE]("http://unix.stackexchange.com/questions/35061/partitioning-ubuntu-and-windows-7-once-and-for-all/35064#comment47598_35064"). Guy there answered and referenced this thread to consult when deleting wubi install. 

So I came here and followed the steps. **But when I execute bash wubi-move to sda2 it says I cannot move it there because partition is not empty.**

Am I doing something wrong? Why does the partition need to be empty?
The partition needs to be empty because the migration script formats it. The script makes sure it's empty to prevent accidental data loss if the user has made a mistake e.g. chosen the wrong partition.

Make sure you're using the lastest version of the script - it is required for the latest version of Ubuntu. That script would also have complained about the fact that /dev/sda2 is an NTFS partition. Make it ext4 instead.
If you want to hibernate, also create a swap partition that is the size of your RAM + 500MB, let's assume /dev/sda3.

Then you'd boot your Wubi install (which is on /dev/sda1) and migrate using:
```
sudo bash wubi-move-2.1.sh /dev/sda2 /dev/sda3
```

This will migrate the wubi to /dev/sda2, setup your swap on /dev/sda3, and replace the windows bootloader on /dev/sda with Grub2.

Let me know if you have any questions or the information on that [link]("http://unix.stackexchange.com/q/35061") isn't valid anymore (I used that to determine the details of the above).

EDIT: just saw you commented on that thread that you uninstalled Wubi. So scratch the above. Once you uninstall, the root.disk is deleted and migration is no longer possible. Hopefully the manual method you used worked out okay.

---

### Post by jpav on 2012-03-29
Ok, I tried the move. Started to go well, and came back to the computer and saw this:

```

amy@ubuntu:~/Downloads$ sudo bash wubi-move-2.1.sh /dev/sda5 /dev/sda6


wubi-move-2.1.sh: Would you like the grub2 bootloader to be installed
wubi-move-2.1.sh: to drive /dev/sda? If you choose not to, you will
wubi-move-2.1.sh: still be able to boot your migrated install from
wubi-move-2.1.sh: your current install.
wubi-move-2.1.sh: Install grub bootloader to /dev/sda? (Y/N)
y
wubi-move-2.1.sh: Please close all open files before continuing.
wubi-move-2.1.sh: About to format the target partition (/dev/sda5).
wubi-move-2.1.sh: Proceed with format (Y/N)
y
wubi-move-2.1.sh: Formatting /dev/sda5 with ext4 file system

wubi-move-2.1.sh: Copying files - please be patient - this takes some time
file has vanished: "/home/amy/.local/share/gvfs-metadata/uuid-94626600-ec2d-4154-a9ce-9f1b0d594187-8d6a8153.log"
rsync warning: some files vanished before they could be transferred (code 24) at main.c(1070) [sender=3.0.8]

wubi-move-2.1.sh: Copying files failed - user canceled?
wubi-move-2.1.sh: Unmounting target...
wubi-move-2.1.sh: Migration request canceled
amy@ubuntu:~/Downloads$ 

```On the restart, the move was not completed, I still get the 'wubi boot selector' and my new install does not appear in the list. In a quick look at my file system, compared to the working wubi version, there are some folders empy, sys for example, and some that do not contain the same number of files as the working system, so I am assuming this stopped for some reason.
Is there a fix for me?

Thanks,
Josh

---

### Post by bcbc on 2012-03-29
> **jpav said:**
> Ok, I tried the move. Started to go well, and came back to the computer and saw this:
...
On the restart, the move was not completed, I still get the 'wubi boot selector' and my new install does not appear in the list. In a quick look at my file system, compared to the working wubi version, there are some folders empy, sys for example, and some that do not contain the same number of files as the working system, so I am assuming this stopped for some reason.
Is there a fix for me?

Thanks,
Josh

Rsync issued return code 24 when copying the files. This means that some files 'vanished' during the copy. Either because you or a background process was working during the migration.

This return code isn't really a problem; it basically means that rsync identified some files to copy and when it got to one of them it was no longer there. Most of the time they seem to be cache files.
However, the script is a little too strict - it looks for a return code of 0, or it fails. 

If the failure was due to something you were doing while the script was running, then the easiest plan is to rerun the script. In order to do this you'll have to empty the partition first (either delete all the files or format it using gparted). This is because the script requires that the partition is empty to prevent accidental data loss if a user selects the incorrect partition.

If you think it's some background process that caused it, rerunning may be an exercise in frustration. In that case, you'd do better to wait a few weeks before retrying: I've got to release a new version of the script for Ubuntu 12.04 that comes out in 28 days. And this new version will add a *--resume* option to pick up from a migration that failed with copying errors, without having to recopy all the files; it will also ignore return code 24.

---

### Post by jpav on 2012-03-29
Should have been nothing running, but appears something was open I guess. I cleared the partition, and tried again and it worked fine. Good to hear the version for 12.04 will allow it to continue. There is a chance someone may have hit the trackpad, and on this laptop, it could have sent a click to open something since it is sensative.

Thanks for the help. Everything seems to be running almost exactly as the wubi version. Had a couple of links set up to access the user data under windows in the 'my documents' area that had to be recreated of course, but other than that, I see no issues.

Josh

---

### Post by bcbc on 2012-03-29
> **jpav said:**
> Should have been nothing running, but appears something was open I guess. I cleared the partition, and tried again and it worked fine. Good to hear the version for 12.04 will allow it to continue. There is a chance someone may have hit the trackpad, and on this laptop, it could have sent a click to open something since it is sensative.

Thanks for the help. Everything seems to be running almost exactly as the wubi version. Had a couple of links set up to access the user data under windows in the 'my documents' area that had to be recreated of course, but other than that, I see no issues.

Josh

Great! Glad to hear it worked out.

---

### Post by Wojo71 on 2012-04-07
*If you don't want to install the grub bootloader, use the --no-bootloader option. You can boot from the Wubi install's grub menu temporarily and manually install the grub bootloader later.*

I'm running the wubi install on an Alienware m14x. To boot it took a bit of tweeking of the grub bootloader to make Ubuntu work with the Nvidia graphics card. With a migration to a partition do you recommend installing the grub bootloader or not?

Thanks for any assistance.

---

### Post by bcbc on 2012-04-07
> **Wojo71 said:**
> *If you don't want to install the grub bootloader, use the --no-bootloader option. You can boot from the Wubi install's grub menu temporarily and manually install the grub bootloader later.*

I'm running the wubi install on an Alienware m14x. To boot it took a bit of tweeking of the grub bootloader to make Ubuntu work with the Nvidia graphics card. With a migration to a partition do you recommend installing the grub bootloader or not?

Thanks for any assistance.

Yes I recommend installing it. The tweaking you are talking about is carried forward automatically as it sits in the generated grub.cfg within the Ubuntu install. 

The *--no-bootloader* option just prevents grub replacing the Windows bootloader in the drive master boot record (MBR). This area is very small, so the bootloader itself doesn't have much logic in it, just the capabilities of loading the core image, additional grub modules and the grub.cfg. 

Let me know if you have any other questions!

---

### Post by bcbc on 2012-04-08
For those interested, I've included the steps required to manually migrate. These instructions used to be in [post #1]("http://ubuntuforums.org/showthread.php?t=1519354"), but made it less readable, so I've moved them here. Also, I don't recommend manual migration, unless you are doing it for educational purposes ;)

**_Manual migration_**

These are only suitable for Wubi installs from release 9.10 and later (Grub2 only). The instructions should be run from the booted Wubi install (not a liveCD).
*[COLOR=Red]Please don't use the manual migration unless you fully understand what you are doing. The automated migration has many additional safeguards and will protect you from errors.[/COLOR]*

This example assumes the new install will be on [COLOR=Red]/dev/sda5[/COLOR] and that there will be a swap on [COLOR=Blue]/dev/sda6[/COLOR]. If there is no swap, just ignore lines containing [COLOR=Blue]/dev/sda6[/COLOR]. If there is a swap partition it must be of type 'swap'. Change the device names as appropriate.

Most of these commands are best cut-and-pasted to avoid typos. If you need to change the device names, I recommend doing it in a text editor before pasting to terminal. Otherwise, if you paste a linefeed by accident the command will run before you have a chance to change it.


1. Do this all as root
```
sudo -i
```1.a. Ensure you do not have grub-legacy. If the output of the following shows version 0.97 then please do not continue. These instructions only work with grub versions 1.96 and greater. You can use the attached script *wubi-move-2.2.sh* instead.
```
grub-install --version
```2. Format new partition if not done so already - make sure it's empty, large enough and unmounted
[COLOR=Red]WARNING[/COLOR] -- the next command will wipe all existing data on [COLOR=Red]/dev/sda5[/COLOR]
```
mkfs.ext4 [COLOR=Red]/dev/sda5[/COLOR]
```3. Mount new partition and copy files. 
```
mkdir /tmp/wubimove
mount [COLOR=Red]/dev/sda5[/COLOR] /tmp/wubimove
rsync -av --exclude=/host --exclude=/mnt/* --exclude=/home/*/.gvfs --exclude=/home/*/.cache/gvfs --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/* --exclude=/sys/* --exclude=/var/lib/lightdm/.gvfs / /tmp/wubimove
chmod -x /tmp/wubimove/etc/grub.d/10_lupin
```4. Setup swap partition and enable hibernation (swap must be at least as big as RAM to hibernate)
```
mkswap [COLOR=Blue]/dev/sda6[/COLOR]
echo "RESUME=UUID=$(blkid -o value -s UUID [COLOR=blue]/dev/sda6[/COLOR])" > /tmp/wubimove/etc/initramfs-tools/conf.d/resume
```5. Edit fstab (blank out wubi mounts with sed and add new partitions)
```
sed -i 's:/.*[\.]disk .*::' /tmp/wubimove/etc/fstab    
echo "UUID=$(blkid -o value -s UUID [COLOR=Red]/dev/sda5[/COLOR])    /    ext4    errors=remount-ro    0    1" >> /tmp/wubimove/etc/fstab
echo "UUID=$(blkid -o value -s UUID [COLOR=blue]/dev/sda6[/COLOR])    none    swap    sw    0    0" >> /tmp/wubimove/etc/fstab

```6. Remove lupin support and update grub (all in chroot). Note that this step installs the grub bootloader to /dev/sda and will replace your windows bootloader (the line 'grub-install  /dev/sda') -- see note below
```
mkdir /tmp/wubimove/host
for i in dev proc sys dev/pts host; do mount --bind /$i /tmp/wubimove/$i; done
chroot /tmp/wubimove
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
apt-get -y remove lupin-support
update-grub
[I]grub-install **/dev/sda**
echo SET grub-pc/install_devices **/dev/sda** | debconf-communicate[/I]
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in host dev/pts dev proc sys; do umount /tmp/wubimove/$i; done
rmdir /tmp/wubimove/host
umount [COLOR=red]/dev/sda5[/COLOR]
```7. Update wubi grub menu to pick up new install and exit sudo
```
update-grub
exit
```You're done. When you reboot, you should see a grub menu instead of the windows boot menu. Select the first entry. If you didn't run 'grub-install' you can boot from the wubi menu, select your new install from the bottom after the Windows entry.

NOTE on installing the grub bootloader: you can try out the new installation by booting it from the wubi grub menu first - if you want to make sure everything is working before replacing the windows bootloader. To do this, bypass the line 'grub-install /dev/sda' and the following line (in step 6.). You can then install the grub2 bootloader manually later after booting into the new install.
I also recommend updating the grub menu after booting into the target partition ```
sudo update-grub
```Other comments:
1. Mounted partitions under /host and /media are excluded from the rsync copy automatically. Partitions mounted under other mountpoints are not and will be copied unless manually unmounted first (when running manual migration).
2. Only the current kernel's initrd.img is updated on the migrated install; if you require others you can update them with "sudo update-initramfs -u -k <kernel version>".

---

### Post by Wojo71 on 2012-04-09
Thanks bcbc! Did the migration this morning and everything went without a hitch. I'm very new to Linux however confidence is growing. I appreciate your advice. Great thread! Cheers! Mark

---

### Post by bcbc on 2012-04-09
> **Wojo71 said:**
> Thanks bcbc! Did the migration this morning and everything went without a hitch. I'm very new to Linux however confidence is growing. I appreciate your advice. Great thread! Cheers! Mark

Great! Enjoy!

---

### Post by mustafaakin on 2012-04-23
Works in Ubuntu 11.10 64-bit WUBI installation very well!

---

### Post by bcbc on 2012-04-25
> **mustafaakin said:**
> Works in Ubuntu 11.10 64-bit WUBI installation very well!

Great! Thanks for the feedback!

---

### Post by VVAW on 2012-06-23
I need some help

My hp6930p latop died so i bought the same model and hardware.

My wubi install was backed up and on orignal drive.

So I installed wubi ubuntu 11.40 they copied the files over to new hard drive but it wont boot up..IS there a trick to get this to work like mount the new drive.....Please help me

---

### Post by VVAW on 2012-06-23
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   312,578,047   312,371,200   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       b0961dff-4944-4940-8ea4-2bcde83d93e6   ext4       
/dev/sda1        FA845EBC845E7AD9                       ntfs       System Reserved
/dev/sda2        84C06827C06821A2                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root A4AAC4A2AAC471FA
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-13-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A4AAC4A2AAC471FA
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-13-generic root=UUID=A4AAC4A2AAC471FA loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, Linux 2.6.38-13-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A4AAC4A2AAC471FA
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-13-generic root=UUID=A4AAC4A2AAC471FA loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A4AAC4A2AAC471FA
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A4AAC4A2AAC471FA loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A4AAC4A2AAC471FA
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=A4AAC4A2AAC471FA loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A4AAC4A2AAC471FA
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

   4.205650330 = 4.515782656    boot/grub/grub.cfg                             1
   1.801311493 = 1.934143488    boot/initrd.img-2.6.38-13-generic              1
   1.004428864 = 1.078497280    boot/initrd.img-2.6.38-8-generic               2
   1.379234314 = 1.480941568    boot/vmlinuz-2.6.38-13-generic                 1
  12.132816315 = 13.027512320   boot/vmlinuz-2.6.38-8-generic                  1
   1.801311493 = 1.934143488    initrd.img                                     1
   1.004428864 = 1.078497280    initrd.img.old                                 2
   1.379234314 = 1.480941568    vmlinuz                                        1
  12.132816315 = 13.027512320   vmlinuz.old                                    1

---

### Post by bcbc on 2012-06-23
VVAW,
Yes, you need to edit the grub menu before it boots. It's pointing at the old partition (/dev/sda1), but now it's on the new one (/dev/sda2).

When you select "Ubuntu" you'll see the grub menu. Hit 'E' to edit the first entry, and change it from:
```
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root A4AAC4A2AAC471FA
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.38-13-generic root=UUID=A4AAC4A2AAC471FA loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-13-generic
```
To:
```
insmod part_msdos
insmod ntfs
set root='(/dev/sda,**[COLOR="blue"]msdos2[/COLOR]**)'
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.38-13-generic **[COLOR="Blue"]root=/dev/sda2[/COLOR]** loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.38-13-generic
```
Then Ctrl+X to boot. After booting update the grub menu:
```
sudo update-grub
```

Note I also deleted the line 'search --no-floppy' (not critical, but it will probably pop an error msg if you leave it in).

---

### Post by VVAW on 2012-06-24
Thank you very much it worked..

I have one question if I were to upgrade my laptop to say i7 8 gig. Could I move the root file and boot my wubi install .

Just do the same steps above

thanks again

---

### Post by bcbc on 2012-06-24
> **VVAW said:**
> Thank you very much it worked..

I have one question if I were to upgrade my laptop to say i7 8 gig. Could I move the root file and boot my wubi install .

Just do the same steps above

thanks again
You can move wubi installs between computers. only issue is if you have a custom graphics driver, or try to run a 64-bit install on a 32-bit architecture. This thread is about migrating from wubi... and that's what I'd recommend. Wubi works great but there are too many corrupt root.disks out there for my liking and for that reason I'd recommend the dual boot route.

---

### Post by lisati on 2012-06-26
Thread closed by request of OP. Please see [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012400](http://ubuntuforums.org/showthread.php?t=2012400)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

