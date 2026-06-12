---
title: "Kernel upgrade - server keeps booting from old kernel"
date: 2022-01-11
forum: Server Platforms
---

### Post by kinser06 on 2022-01-11
[FONT=century gothic]I'm running 20.04.3 LTS, current kernel is 4.15.0-135.

I've tried to upgrade the kernel several times and every time after reboot its loading back up on the old kernel with no errors.

If i run [/FONT]
[COLOR=#ff0000]sudo grub-mkconfig | grep -E [/COLOR][COLOR=#ff0000]'submenu |menuentry '[/COLOR]

[FONT=century gothic]it outputs[/FONT] 

```
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50-curtin-settings.cfg'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.6.10-050610-generic
Found initrd image: /boot/initrd.img-5.6.10-050610-generic
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-85498d88-6d8b-11eb-bfff-b083feda1f05' {
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-85498d88-6d8b-11eb-bfff-b083feda1f05' {
        menuentry 'Ubuntu, with Linux 5.6.10-050610-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.6.10-050610-generic-advanced-85498d88-6d8b-11eb-bfff-b083feda1f05' {
        menuentry 'Ubuntu, with Linux 5.6.10-050610-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.6.10-050610-generic-recovery-85498d88-6d8b-11eb-bfff-b083feda1f05' {
Found linux image: /boot/vmlinuz-5.4.0-92-generic
Found initrd image: /boot/initrd.img-5.4.0-92-generic
        menuentry 'Ubuntu, with Linux 5.4.0-92-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-92-generic-advanced-85498d88-6d8b-11eb-bfff-b083feda1f05' {
        menuentry 'Ubuntu, with Linux 5.4.0-92-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-92-generic-recovery-85498d88-6d8b-11eb-bfff-b083feda1f05' {
done

```

[FONT=century gothic]I can see the 2 different kernels that I've tried over the last week, I'm kind of surprised that i can't see my current 4.15.0 kernel.[/FONT]

[FONT=century gothic]I've reviewed and followed several guides to perform this upgrade. Everything goes as planned with no errors it just always reboots to the old kernel.
I'm open to any ideas or suggestions at this point.

Thanks in advance,
[/FONT]

---

### Post by TheFu on 2022-01-11
I thought 20.04 default kernel was 5.4.x and the HWE is 5.11.x?

Why is there a 5.6.x*.

I've never used grub-mkconfig.
Usually when a kernel fails to be setup, it is due to lacking free storage in /boot/.  That can cause all sorts of off outcomes. Check that first.  Then look in apt/dpkg for partially installed kernels - I expect there are failures.

Just some shots in the dark. Probably not it, but who knows?

---

### Post by MAFoElffen on 2022-01-12
@ThaFu: I'm wondering that also... 

Because me testing my system-info support script tonight:
```

These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':
For HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.11.0.46.51
Without HWE Package: linux-image-generic-hwe-20.04, Kernel Version: 5.4.0.26.32

```
What he should do is
```

sudo ls /boot/initrd.img-*
sudo /usr/src/linux-*

```
Historically, way back when, Ubuntu used to keep all kernels, forever until the user purged the older kernels. From time to time, especially with old version of LVM, which had it's own Boot Partition, this became a problem when that partition filled up and no longer had space left to add whatever the newest kernel updated to.

Then they started automatically purging old kernels, if there was an update, so that you had the current, and one older to fall back to if there was a problem... Using just that logic... If you install a newer kernel, it is logically the newest kernel and will default as the default boot. The next newest kernel would be the fall back... and your older kernels would be purged... 

I think what you are going to find is that somehow you have that newer kernels installed (5.6.x), your next newer kernel was 5.4.... So "logically, it is doing what it should, because you didn't pin your old kernels. All those kernels are "new" and a lot newer than 4.13.x, which I am sorry to point out, is a mistake on your part. (Read below)

On you thinking you should be on Linux Kernel 4.13???). That kernel was released 4th Quarter 2017. It hit Ubuntu Mainline on September 3, 2018 (about the time of 17.10). The Kernel for Ubuntu 18.04 LTS was 4.15. You are on Ubuntu LTS 20.04 LTS...  Which right now the current kernel in non-HWE is 5.4.x...

---

### Post by ameinild on 2022-01-12
Can you please list your /etc/apt/sources.list or anything inside /etc/apt/sources.list.d ?

Your kernel versions seem pretty messed up, and a possible explanation is you added non-default repositories. 

As others have stated, the default kernel for 20.04 is 5.4 (non-HWE) or 5.11 (HWE). Anything else is completely at your own risk and largely unsupported.

Help us help you, by letting us understand what's going on here. ;-)

---

### Post by TheFu on 2022-01-12
The way that I've seen 4.15 kernels left on a system was if it was an upgrade, not a fresh install.  Then all the automatic cleanup methods will never remove the 4.15 line of kernels automatically. They need to be removed manually - along with the dependent modules, headers, etc for that line of kernels.
Yes, it is a pain, but I often keep the old OS line of kernels around for a few weeks after an OS migration (I'm an LTS --> LTS type). Then I start with 
```
sudo apt-get --purge remove  linux-image-4.15*
``` as the first step.

---

### Post by LHammonds on 2022-01-12
> **TheFu said:**
> The way that I've seen 4.15 kernels left on a system was if it was an upgrade, not a fresh install.  Then all the automatic cleanup methods will never remove the 4.15 line of kernels automatically. They need to be removed manually - along with the dependent modules, headers, etc for that line of kernels.
Yes, it is a pain, but I often keep the old OS line of kernels around for a few weeks after an OS migration (I'm an LTS --> LTS type). Then I start with 
```
sudo apt-get --purge remove  linux-image-4.15*
``` as the first step.
But ONLY if the currently loaded kernel is not the 4.15 branch.  Never purge an active kernel (not sure if it would let you though).

One can check which kernel is loaded with the following command:

```
uname -r
```

Here is an example of my up-to-date server:

```

$ lsb_release -d
Description:    Ubuntu 20.04.3 LTS
$ uname -r
5.4.0-94-generic
```

My guess in regards to the original post is that the system never auto-purged old kernels and has been failing to update for a long time due to space issues in "/boot" or "/var" but the 5.6 kernel and how it is active is NOT normal for an LTS server so something had to be manually selected to get it that way.

My suggestion is to build another 20.04.3 server with the correct kernel, then setup your applications and configurations to work like your original server and then copy over the data to make it the new server.  My line of thinking here is that if the kernel is non-standard and causing issues, maybe other areas of the system also suffer from configuration issues...so rather than bandaid-fix this one problem, it might be best to avoid others by making a standard server with a known-good configuration.

LHammonds

---

### Post by deadflowr on 2022-01-12
Hmm, weird this user has a similar issue: [https://ubuntuforums.org/showthread.php?t=2470683]("https://ubuntuforums.org/showthread.php?t=2470683")
I'd probably start by exploring those config files listed in the output, both the /etc/default/grub file and the /etc/grub.d/init-select.cfg and /etc/grub.d/50-curtin-settings.cfg files.
And see if they have anything worth noting.

---

### Post by LHammonds on 2022-01-12
> **deadflowr said:**
> Hmm, weird this user has a similar issue: [https://ubuntuforums.org/showthread.php?t=2470683](https://ubuntuforums.org/showthread.php?t=2470683)
I'd probably start by exploring those config files listed in the output, both the /etc/default/grub file and the /etc/grub.d/init-select.cfg and /etc/grub.d/50-curtin-settings.cfg files.
And see if they have anything worth noting.
Not quite.  The going from 18.04 to 20.04 will yield similar kernels.  The crux of the oddity here is how/when the OP got onto 5.6.

LHammonds

---

### Post by deadflowr on 2022-01-12
> **LHammonds said:**
> Not quite.  The going from 18.04 to 20.04 will yield similar kernels.  The crux of the oddity here is how/when the OP got onto 5.6.

LHammonds

Agree not quite the same but similar enough in what is happening to both.

---

### Post by kinser06 on 2022-01-12
So i was originally on 18.04 and did the upgrade to 20.04 a while back. I didn't realize i was on such a old kernel until i tried to activate livepatch. I have purged  all of the other 5.6.x & 5.4.x kernels out of the system. So i only had 4.15.x left.

I enabled the HWE stack and see it added 5.11.x onto the system. It still boots to 4.15 and i dont see 5.11 in my grub menu at boot.

If i run sudo ls /boot/initrd.img-*

I get 
```
root@dellserver:/# sudo ls /boot/initrd.img-*
/boot/initrd.img-4.15.0-135-generic     /boot/initrd.img-5.11.0-46-generic
/boot/initrd.img-5.11.0-051100-generic  /boot/initrd.img-5.4.0-050400-generic
/boot/initrd.img-5.11.0-44-generic      /boot/initrd.img-5.4.0-050400-lowlatency

```

uname -r

```
root@dellserver:/etc/apt/sources.list.d# uname -r
4.15.0-135-generic
```

 /etc/apt/sources.list has the following inside
```
root@dellserver:/# nano /etc/apt/sources.list
  GNU nano 4.8                                   /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu focal main restricted
# deb-src http://archive.ubuntu.com/ubuntu bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu focal-updates main restricted
# deb-src http://archive.ubuntu.com/ubuntu bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu focal universe
# deb-src http://archive.ubuntu.com/ubuntu bionic universe
deb http://archive.ubuntu.com/ubuntu focal-updates universe
# deb-src http://archive.ubuntu.com/ubuntu bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu focal multiverse
# deb-src http://archive.ubuntu.com/ubuntu bionic multiverse
deb http://archive.ubuntu.com/ubuntu focal-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://archive.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://archive.ubuntu.com/ubuntu bionic-security main restricted
deb http://archive.ubuntu.com/ubuntu focal-security universe
# deb-src http://archive.ubuntu.com/ubuntu bionic-security universe
deb http://archive.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://archive.ubuntu.com/ubuntu bionic-security multiverse
deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu focal stable


```


ls etc/apt/sources.list.d shows

root@dellserver:/# ls etc/apt/sources.list.d
cappelikan-ubuntu-ppa-focal.list  ubuntu-esm-infra.list  ubuntu-esm-infra.list.save

---

### Post by kinser06 on 2022-01-12
Also /boot and /var aren't full.

```
root@dellserver:/# du -hs /boot/
404M    /boot/

root@dellserver:/# du -hs /var/
33G     /var/

```

---

### Post by TheFu on 2022-01-12
**df -Th** would show how full any file system is. **du** not so much.
Also 4.15 kernels are left over from earlier releases. Not part of 20.04, so it might cause driver issues - especially for proprietary GPU drivers. If not now, later.

18.04 LTS running HWE uses the 5.4 kernel. 20.04 started with 5.4 kernels, I believe.

---

### Post by kinser06 on 2022-01-12
df -th shows

```
root@dellserver:/# df -Th
Filesystem                        Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      2.7T  430G  2.2T  17% /
/dev/sda1                         vfat      511M  6.1M  505M   2% /boot/efi

edited*

```

---

### Post by TheFu on 2022-01-12
```
Filesystem                        Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      2.7T  430G  2.2T  17% /
/dev/sda1                         vfat      511M  6.1M  505M   2% /boot/efi
```

Those are the only REAL storage devices.
/var isn't a separate area. Neither is /boot, so only / matters.
The EFI partition looks fine too.

For this issue, I don't see any storage issue, though the way that LVM is setup is less than ideal - 1 huge LV - meh. That would be a different thread if you are interested in creating a more flexible and resilient LV setup to help have better backups and more security. Using different mount options for different parts of the file system will support better security than the defaults.

---

### Post by ajgreeny on 2022-01-12
It would be useful i think to see exactly which Linux versions are installed currently that the filesystem is aware of and is therefore potentially capable of removing.

So show us the output of command ```
dpkg -l linux* | grep ii
``` and we can then attempt to help you remove the various Linux packages that are completely superfluous to your system and leave you with just the normal 2 versions.

---

### Post by kinser06 on 2022-01-12
results of dpkg -l linux* | grep ii 


```
root@dellserver:/home/kinser06# dpkg -l linux* | grep ii
ii  linux-base                                   4.5ubuntu3.7               all          Linux image base package
ii  linux-firmware                               1.187.24                   all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                      5.11.0.46.51~20.04.23      amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.11.0-051100                  5.11.0-051100.202102142330 all          Header files related to Linux kernel version 5.11.0
ii  linux-headers-5.11.0-051100-generic          5.11.0-051100.202102142330 amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.11.0-44-generic              5.11.0-44.48~20.04.2       amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.11.0-46-generic              5.11.0-46.51~20.04.1       amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-050400                   5.4.0-050400.201911242031  all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-050400-generic           5.4.0-050400.201911242031  amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-050400-lowlatency        5.4.0-050400.201911242031  amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04              5.11.0.46.51~20.04.23      amd64        Generic Linux kernel headers
ii  linux-hwe-5.11-headers-5.11.0-44             5.11.0-44.48~20.04.2       all          Header files related to Linux kernel version 5.11.0
ii  linux-hwe-5.11-headers-5.11.0-46             5.11.0-46.51~20.04.1       all          Header files related to Linux kernel version 5.11.0
ii  linux-image-4.15.0-135-generic               4.15.0-135.139             amd64        Signed kernel image generic
ii  linux-image-5.11.0-44-generic                5.11.0-44.48~20.04.2       amd64        Signed kernel image generic
ii  linux-image-5.11.0-46-generic                5.11.0-46.51~20.04.1       amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                5.11.0.46.51~20.04.23      amd64        Generic Linux kernel image
ii  linux-image-unsigned-5.11.0-051100-generic   5.11.0-051100.202102142330 amd64        Linux kernel image for version 5.11.0 on 64 bit x86 SMP
ii  linux-image-unsigned-5.4.0-050400-generic    5.4.0-050400.201911242031  amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-unsigned-5.4.0-050400-lowlatency 5.4.0-050400.201911242031  amd64        Linux kernel image for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-135-generic             4.15.0-135.139             amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-051100-generic          5.11.0-051100.202102142330 amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-44-generic              5.11.0-44.48~20.04.2       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-46-generic              5.11.0-46.51~20.04.1       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-050400-generic           5.4.0-050400.201911242031  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-050400-lowlatency        5.4.0-050400.201911242031  amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-135-generic       4.15.0-135.139             amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-44-generic        5.11.0-44.48~20.04.2       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-46-generic        5.11.0-46.51~20.04.1       amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP

```

---

### Post by ajgreeny on 2022-01-13
Very odd!

There is no mention in that list of any 5.6 series kernels and even the 5.4 series is reported as strangely numbered.
I think we may need to be sure which kernel you're currently running then try using dpkg to remove the unnecessary versions such as that 5.6 series and the old 4 series.

Also, just to be certain, what happens if you boot to the latest, most up to date kernel from your grub menu then run **sudo apt autoremove**?

---

### Post by kinser06 on 2022-01-13
I think you missed post 10. I'm still running on  the 4.15 kernel. I had purged all of the other kernels then enabled the  HWE stack which i believe added all of those 5.11.x kernels. If i reboot  right now and go into grub it only shows me the 4.15 option to boot  from.

---

### Post by TheFu on 2022-01-13
If you run 
**sudo update-grub**
does that fix the menu?  I don't use UEFI, so I don't know if grub is involved or not.

---

### Post by kinser06 on 2022-01-13
Sudo upgrade-grub doesn’t seem to update my grub menu at boot.

---

### Post by ajgreeny on 2022-01-13
But the dpkg output you show in post #shows that you do still have some 5.4 series kernels installed, though they are not the default versions.
Is there some good reason for installing those unusual kernels?
[b]linux-image-unsigned-5.11.0-051100-generic
linux-image-unsigned-5.4.0-050400-lowlatency[/b]
as well as many dependencies, or at least suggested packages needed for those linux-image packages.

Have you ever run the ```
sudo apt aiutoremove
``` command I mentioned above which may remove those now unneeded packages, and with luck might also remove some of the old kernels that you don't want or need.

Give that a try and see if you can then get grub to show the later 5.11 kernels and boot to the latest by default.
If that still doesn't work then I am even more baffled,but I am sure we can remove any kernels and their dependencies using dpkg if necessary, though why it should be required to do it that way is at present beyond my understanding.

---

### Post by kinser06 on 2022-01-13
sudo apt autoremove did'nt remove anything.

I went in and removed each individually.

I am left with the following when I issues,
dpkg -l linux* | grep ii

```
dpkg -l linux* | grep ii
ii  linux-base                              4.5ubuntu3.7          all          Linux image base package
ii  linux-firmware                          1.187.24              all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-20.04                 5.11.0.46.51~20.04.23 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.11.0-46-generic         5.11.0-46.51~20.04.1  amd64        Linux kernel headers for version 5.11.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04         5.11.0.46.51~20.04.23 amd64        Generic Linux kernel headers
ii  linux-hwe-5.11-headers-5.11.0-46        5.11.0-46.51~20.04.1  all          Header files related to Linux kernel version 5.11.0
ii  linux-image-4.15.0-135-generic          4.15.0-135.139        amd64        Signed kernel image generic
ii  linux-image-5.11.0-46-generic           5.11.0-46.51~20.04.1  amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04           5.11.0.46.51~20.04.23 amd64        Generic Linux kernel image
ii  linux-modules-4.15.0-135-generic        4.15.0-135.139        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-5.11.0-46-generic         5.11.0-46.51~20.04.1  amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-135-generic  4.15.0-135.139        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.11.0-46-generic   5.11.0-46.51~20.04.1  amd64        Linux kernel extra modules for version 5.11.0 on 64 bit x86 SMP

```

I issued update-grub just to be sure and did a reboot.
Upon reboot in the grub menu i have 2 kernel boot options...
4.15.0-135-generic and 4.15.0-29-generic VERY WEIRD!

---

### Post by TheFu on 2022-01-13
Just to state the non-obvious, the basic grub menu doesn't really change, it is only when we enter into the "Advance" menu item that we get to see the kernels.  Yes?

---

### Post by kinser06 on 2022-01-13
Correct, iirc my options were ubuntu or advance boot, in advance boot is where i see both of the 4.x kernel listings.

---

### Post by MAFoElffen on 2022-01-13
> **MAFoElffen said:**
> What he should do is
```

sudo ls /boot/initrd.img-*
sudo /usr/src/linux-*

```


And did you do this to see what is actually there?

---

### Post by kinser06 on 2022-01-13
sudo ls /boot/initrd.img-* shows

```
root@dellserver:/home/kinser06# sudo ls /boot/initrd.img-*
/boot/initrd.img-4.15.0-135-generic  /boot/initrd.img-5.11.0-46-generic

```


sudo ls /usr/src/linux-* shows

```
root@dellserver:/home/kinser06# ls /usr/src/linux-*
/usr/src/linux-headers-5.11.0-46-generic:
arch   crypto         fs       ipc      kernel    mm              samples   sound   usr
block  Documentation  include  Kbuild   lib       Module.symvers  scripts   tools   virt
certs  drivers        init     Kconfig  Makefile  net             security  ubuntu

/usr/src/linux-hwe-5.11-headers-5.11.0-46:
arch   certs   Documentation  fs       init  Kbuild   kernel  Makefile  net      scripts   sound  ubuntu  virt
block  crypto  drivers        include  ipc   Kconfig  lib     mm        samples  security  tools  usr
```

---

### Post by ajgreeny on 2022-01-14
So which kernel does the computer boot to now, the old 4 series or the 5.11?

---

### Post by MAFoElffen on 2022-01-14
There is something missing here, and someone along the line hinted on it when they asked the question if this was the only OS installed on this machine... Becuase if there was another OS installed that also uses Grub, and if that other OS was the primary boot manager, then update-grub from this OS would update it's dynamic grub.cfg file, bt it would not be the one that the efi boot file would be pointing to... Those sets of circumstances would recreate this error and what is happening so far. for this user.

Does that make sense? I don't see any inkling of that anywhere from what he has said so far, but... Like I said, something is missing in this, that doesn't make sense so far.

To investigate that then the user should do 
```

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq
lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
df -hT -x tmpfs -x devtmpfs | grep -v '/snap/'

```
If that is not what is going on here, then there is something wrong with grub itself, that is not working as it should by all historical and logical means. Grub has an expected and consistent pattern which it follows... which this machine is not. This is more random acts of ??? It says it updates grub, but doesn't pick up any changes? It doesn't follow the expected pattern to use the newest kernel first as primary? Yes, random acts of indifference, which is not functional.

Which then I would recommend purging and reinstalling grub to see if that correct this.

---

### Post by kinser06 on 2022-01-14
> **ajgreeny said:**
> So which kernel does the computer boot to now, the old 4 series or the 5.11?

It's booting to the old 4.x kernel. I don't see the 5.x in my grub options on reboot

---

### Post by kinser06 on 2022-01-14
> **MAFoElffen said:**
> There is something missing here, and someone along the line hinted on it when they asked the question if this was the only OS installed on this machine... Becuase if there was another OS installed that also uses Grub, and if that other OS was the primary boot manager, then update-grub from this OS would update it's dynamic grub.cfg file, bt it would not be the one that the efi boot file would be pointing to... Those sets of circumstances would recreate this error and what is happening so far. for this user.

Does that make sense? I don't see any inkling of that anywhere from what he has said so far, but... Like I said, something is missing in this, that doesn't make sense so far.

To investigate that then the user should do 
```

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq
lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
df -hT -x tmpfs -x devtmpfs | grep -v '/snap/'

```
If that is not what is going on here, then there is something wrong with grub itself, that is not working as it should by all historical and logical means. Grub has an expected and consistent pattern which it follows... which this machine is not. This is more random acts of ??? It says it updates grub, but doesn't pick up any changes? It doesn't follow the expected pattern to use the newest kernel first as primary? Yes, random acts of indifference, which is not functional.

Which then I would recommend purging and reinstalling grub to see if that correct this.


I do agree it seems to be from my 18.04 upgrade to 20.04.

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

```
root@dellserver:/home/kinser06# sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

Disk /dev/sda: 2.75 TiB, 3000034656256 bytes, 5859442688 sectors
Disk model: PERC H710
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D3523FEF-E1E0-4687-85C0-274723452572

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624    3147775    2097152    1G Linux filesystem
/dev/sda3  3147776 5859440639 5856292864  2.7T Linux filesystem

Disk /dev/sdb: 3.65 TiB, 4000225165312 bytes, 7812939776 sectors
Disk model: PERC H710
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 903C995E-7CE1-3646-81F6-5231B83D54B9

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 7812939742 7812937695  3.7T Linux filesystem

Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 2.74 TiB, 2998419849216 bytes, 5856288768 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'

```
root@dellserver:/home/kinser06# lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
NAME                       SIZE FSTYPE      LABEL MOUNTPOINT        MODEL
sda                        2.7T                                     PERC_H710
&#9500;&#9472;sda1                     512M vfat              /boot/efi
&#9500;&#9472;sda2                       1G ext4
&#9492;&#9472;sda3                     2.7T LVM2_member
  &#9492;&#9472;ubuntu--vg-ubuntu--lv  2.7T ext4              /
sdb                        3.7T                                     PERC_H710
&#9492;&#9472;sdb1                     3.7T ext4
root@dellserver:/home/kinser06# lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL | grep -v '/snap/'
NAME                       SIZE FSTYPE      LABEL MOUNTPOINT        MODEL
sda                        2.7T                                     PERC_H710
&#9500;&#9472;sda1                     512M vfat              /boot/efi
&#9500;&#9472;sda2                       1G ext4
&#9492;&#9472;sda3                     2.7T LVM2_member
  &#9492;&#9472;ubuntu--vg-ubuntu--lv  2.7T ext4              /
sdb                        3.7T                                     PERC_H710
&#9492;&#9472;sdb1                     3.7T ext4

```

df -hT -x tmpfs -x devtmpfs | grep -v '/snap/'

```
root@dellserver:/home/kinser06# df -hT -x tmpfs -x devtmpfs | grep -v '/snap/'
Filesystem                        Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      2.7T  429G  2.2T  17% /
/dev/sda1                         vfat      511M  6.1M  505M   2% /boot/efi
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/8811fbc77164543cf0d520925f0f8c807932d7b139d3859b4fc824d2e463c0ef/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/74d506a6f3356aa3d78f76a063721990c1d0a4d822ef36742e67e3f5a36a8498/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/2b0443ec50efe7650a9137ca8ac50aa6dc2a3252c2da11e01938a1dc8c8e9b9c/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/3ce6775489bef5d5c04b1985efbffb5deb84f2ae0d9d55f2e987c36a372df6ea/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/2801a4a08478cab6604e06ceab0bd7f41e3aebcac9ba7a106b7d5cbb88c96bb4/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/fb8721b37a08471b66140b9470c49fd1cd36180b2d65f4fa043512d0ff13fad4/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/1e78bc50df0e0410cc7374d0f53ed1475ced300b638e38dda568eb61834b8534/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/09f063aa3988b71d3dc33a2bcff74d48a87a542ab0baf4f19ac6aa4828378b2a/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/97a80eab23fd2894eedc557225e9e9f22a0ea4d0dfff58a59d4ed4748ee5fc2a/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/ac71dc29e9e51df10c40a878c0bf33ce8213cd0dc195655b7d53a0a951972797/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/a86b0c3401df1247d1a927322352043d5b017670a98790fcae42ecbfb66afc8c/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/4706c31b24f1cf0ed1dcf5ae53e1a870270ffec0e3a970efd6a628b82a5a393e/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/4366886efac35e28dd009df091943548466d2ee75957a667ef4970e9bb773a4e/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/0520aa2287eae2adc8ee9078e1d9abf571be647be652045b1b4f6bed0325b9b9/merged
overlay                           overlay   2.7T  429G  2.2T  17% /var/lib/docker/overlay2/64958982611ec7c67d628da89ece96533311653961b6a91678eaf280564beb61/merged

```

---

### Post by ajgreeny on 2022-01-14
Unfortunately I can not help at all with LVM installs as I have never used it and do not understand it at all.

However, as mentioned above by MAFoElffen it could be possible that you have more than one grub on your computer but I can see no mention of that in your various output posts shown here.

I think it might be worth using the **Boot-Repair** in my signature below. Follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and all the boot system currently in use.
It can certainly do no harm as long as you do not just run the Default repair, and it may just help figure out why grub is not doing what it should.

---

### Post by TheFu on 2022-01-14
I use LVM and have upgraded a 16.04 --> 18.04 install. I don't remember anything funny related to storage, though I did have some issues with my perlbrew management of perl versions getting in the way of the upgrade. Lots of things were broke due to that - 100% my fault for putting a very new perl in my PATH before the system perl version and having lots of very new CPAN modules to go along with that perl version rather than using the Canonical Repo versions of those perl modules.

I have had multiple disks with identical UUIDs and that definitely causes some odd behaviors until I finally figured out what was happening.  Thought I was going mad for a few weeks, since about 50% of the time a different OS would be booted and programs I'd just installed and was using weren't there.  Crazy, right?  Once I figured out that UUID-based mounts were the issue and were being found randomly, I immediately forced UUID changes for any partitions/LVs that had a duplicate. After that, all those issues stopped.  The same sort of thing can happen if VGs and LVs are named the same, so be certain that isn't possible when LVM is used.  There are lots of different techniques that people use for this.  vg00, vg01, vg02 ... come to mind.

Also, I've found this df alias NOT to show junk we don't want to see:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```
Not sure if that would remove all the docker crap or not. I've only played with docker.

---

### Post by MAFoElffen on 2022-01-14
@TheFu

If you look at the commands both of us posted, they are exactly the same commands, with mine actually filtering out more (trying to exclude Snaps), so yours would actually not filter out those as you thought...

If it might be a problem of duplicate UUID's like TheFu brought up, then additionally:
```

lsblk -o NAME,HOTPLUG,PARTUUID,UUID | grep -v 'loop'

```

---

### Post by TheFu on 2022-01-14
> **MAFoElffen said:**
> @TheFu

If you look at the commands both of us posted, they are exactly the same commands, with mine actually filtering out more (trying to exclude Snaps), so yours would actually not filter out those as you thought...

If it might be a problem of duplicate UUID's like TheFu brought up, then additionally:
```

lsblk -o NAME,HOTPLUG,PARTUUID,UUID | grep -v 'loop'

```

Mine also excludes squashfs ... which includes snaps and some other things ... perhaps docker?

---

### Post by kinser06 on 2022-01-14
> **ajgreeny said:**
> Unfortunately I can not help at all with LVM installs as I have never used it and do not understand it at all.

However, as mentioned above by MAFoElffen it could be possible that you have more than one grub on your computer but I can see no mention of that in your various output posts shown here.

I think it might be worth using the **Boot-Repair** in my signature below. Follow the instructions there to run the Boot-Info-Script.     
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and all the boot system currently in use.
It can certainly do no harm as long as you do not just run the Default repair, and it may just help figure out why grub is not doing what it should.

Thanks for this, i will work on it tomorrow and post the output.

---

### Post by kinser06 on 2022-01-14
> **MAFoElffen said:**
> @TheFu

If you look at the commands both of us posted, they are exactly the same commands, with mine actually filtering out more (trying to exclude Snaps), so yours would actually not filter out those as you thought...

If it might be a problem of duplicate UUID's like TheFu brought up, then additionally:
```

lsblk -o NAME,HOTPLUG,PARTUUID,UUID | grep -v 'loop'

```

lsblk -o NAME,HOTPLUG,PARTUUID,UUID | grep -v 'loop' showes

```
root@dellserver:/home/kinser06# lsblk -o NAME,HOTPLUG,PARTUUID,UUID | grep -v 'loop'
NAME                      HOTPLUG PARTUUID                             UUID
sda                             0
&#9500;&#9472;sda1                          0 e54dd991-32b8-4b9c-8e6c-76dd9addf18b 1A4D-ED70
&#9500;&#9472;sda2                          0 4f8d2be0-d57f-4e07-b5a3-be0b23cc06f3 85498d87-6d8b-11eb-bfff-b083feda1f05
&#9492;&#9472;sda3                          0 2e5574d4-3470-4c5c-b2fa-1d84cc161547 U4k6HX-WVr0-Y2KI-MzsK-IMug-vPw1-n8tjOB
  &#9492;&#9472;ubuntu--vg-ubuntu--lv       0                                      85498d88-6d8b-11eb-bfff-b083feda1f05
sdb                             0
&#9492;&#9472;sdb1                          0 207bcd68-a916-be49-8bc8-0e5a88e4d58c c8ab2a4b-79ab-4b9b-865d-f2e97eed6309

```

---

### Post by MAFoElffen on 2022-01-15
I don't see any duplicates. So no conflicts there... Go to 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Do Option #2 on Yann's PPA.That is the most current scripts. Yann asked me and some others to help him test this, so I know it's up to date and in active development right now. The ISO will be update soon, once we are through... run the boot-info report and paste it to a pasebin. Do not apply anything until we can read that report and interpret it.

---

### Post by kinser06 on 2022-01-15
> **MAFoElffen said:**
> I don't see any duplicates. So no conflicts there... Go to 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


Do Option #2 on Yann's PPA.That is the most current scripts. Yann asked me and some others to help him test this, so I know it's up to date and in active development right now. The ISO will be update soon, once we are through... run the boot-info report and paste it to a pasebin. Do not apply anything until we can read that report and interpret it.


[https://paste.ubuntu.com/p/WGnQQYC88M/](https://paste.ubuntu.com/p/WGnQQYC88M/)

If you'd prefer the contents be uploaded let me know. I didn't want to fill a entire page with its output. sdc1 is the live-boot flash drive.

---

### Post by ajgreeny on 2022-01-15
I am not knowledgable enough to know what is going on here as the LVM info is pretty meaningless to me.

However, I note that you have both a grub.cfg and a menu.list file on the system both of which are loaded by grub according to the report.

I have not seen a menu.list file in Ubuntu for a very long time as it was used by legacy grub, ie grub 1 long ago overtaken by grub 2.
I will leave this to others to help further but I wonder if this is at least partly behind your problem.

---

### Post by kinser06 on 2022-01-15
Doesn't it seems odd its loading grub from sda2 but once booted sda2 isn't mounted?

---

### Post by MAFoElffen on 2022-01-15
Uploaded report would be preferred...

---

### Post by MAFoElffen on 2022-01-15
> **ajgreeny said:**
> I am not knowledgable enough to know what is going on here as the LVM info is pretty meaningless to me.

However, I note that you have both a grub.cfg and a menu.list file on the system both of which are loaded by grub according to the report.

[COLOR=#ff0000]I have not seen a menu.list file in Ubuntu for a very long time as it was used by legacy grub, ie grub 1 long ago overtaken by grub 2.[/COLOR]
I will leave this to others to help further but I wonder if this is at least partly behind your problem.
True that... Ubuntu first adopted Grub2 with 9.10. 10.04 LTS was the first LTS version to use it.

I'm feeling a bit old right now. LOL.

---

### Post by kinser06 on 2022-01-15
Pastebin from boot-repair


```
boot-repair-4ppa161                                              [20220115_1639]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg

sda3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 29990 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi 
                       /efi/BOOT/mmx64.efi


================================ 1 OS detected =================================

OS#1:   Ubuntu 20.04.3 LTS on mapper/ubuntu--vg-ubuntu--lv

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: G200eR2 from   Matrox Electronics Systems Ltd.
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.

efibootmgr -v
BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0003,0000,0001,0002
Boot0000  EFI Network 1    PcieRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x0)/MAC(b083feda1f05,0)/IPv4(0.0.0.00.0.0.0,0,0)
Boot0001  EFI Network 2    PcieRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x1)/MAC(b083feda1f06,0)/IPv4(0.0.0.00.0.0.0,0,0)
Boot0002* EFI Fixed Disk Boot Device 1    PcieRoot(0x0)/Pci(0x1,0x0)/Pci(0x0,0x0)/Ctrl(0x0)/SCSI(0,0)/HD(1,GPT,e54dd991-32b8-4b9c-8e6c-76dd9addf18b,0x800,0x100000)
Boot0003* ubuntu    HD(1,GPT,e54dd991-32b8-4b9c-8e6c-76dd9addf18b,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0004* Cruzer Fit          PcieRoot(0x0)/Pci(0x1d,0x0)/USB(0,0)/USB(7,0)

2895d47544fd587b26c7e29be1295c27   sda1/BOOT/fbx64.efi
5083a037078124a640e8dd1682fbbddb   sda1/ubuntu/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/ubuntu/mmx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/ubuntu/shimx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/BOOT/BOOTX64.efi


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

mapper/ubuntu--vg-ubuntu--lv    : is-os,    64, apt-get,    signed grub1 grub-efi ,    grub2,    grub-install,    grubenv-ng,    update-grub,    not-far
sda1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ng,    noupdategrub,    not-far
sdb1    : no-os,    32, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

mapper/ubuntu--vg-ubuntu--lv    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

mapper/ubuntu--vg-ubuntu--lv    : not-sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sda2    : is-sepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sda
sdb1    : maybesepboot,    no-boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    std-grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 2.75 TiB, 3000034656256 bytes, 5859442688 sectors
Disk identifier: D3523FEF-E1E0-4687-85C0-274723452572
        Start        End    Sectors  Size Type
sda1     2048    1050623    1048576  512M EFI System
sda2  1050624    3147775    2097152    1G Linux filesystem
sda3  3147776 5859440639 5856292864  2.7T Linux filesystem
Disk sdb: 3.65 TiB, 4000225165312 bytes, 7812939776 sectors
Disk identifier: 903C995E-7CE1-3646-81F6-5231B83D54B9
      Start        End    Sectors  Size Type
sdb1   2048 7812939742 7812937695  3.7T Linux filesystem
Disk mapper/ubuntu--vg-ubuntu--lv: 2.74 TiB, 2998419849216 bytes, 5856288768 sectors
Disk sdc: 29.12 GiB, 31260704768 bytes, 61056064 sectors
Disk identifier: 0x60ac0bab
      Boot Start      End  Sectors  Size Id Type
sdc1  *     2048 61054975 61052928 29.1G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:3000GB:scsi:512:512:gpt:DELL PERC H710:;
1:1049kB:538MB:537MB:fat32::boot, esp;
2:538MB:1612MB:1074MB:ext4::;
3:1612MB:3000GB:2998GB:::;
sdb:4000GB:scsi:512:512:gpt:DELL PERC H710:;
1:1049kB:4000GB:4000GB:ext4::;
sdc:31.3GB:scsi:512:512:msdos:SanDisk Cruzer Fit:;
1:1049kB:31.3GB:31.3GB:fat32::boot, lba;
mapper/ubuntu--vg-ubuntu--lv:2998GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:2998GB:2998GB:ext4::;

Free space (filtered): _________________________________________________________

sda:2861056MiB:scsi:512:512:gpt:DELL PERC H710:;
1:0.02MiB:1.00MiB:0.98MiB:free;
1:2861055MiB:2861056MiB:0.98MiB:free;
sdb:3814912MiB:scsi:512:512:gpt:DELL PERC H710:;
1:0.02MiB:1.00MiB:0.98MiB:free;
sdc:29813MiB:scsi:512:512:msdos:SanDisk Cruzer Fit:;
1:0.03MiB:1.00MiB:0.97MiB:free;
1:29812MiB:29813MiB:0.53MiB:free;

blkid (filtered): ______________________________________________________________

NAME                      FSTYPE      UUID                                   PARTUUID                             LABEL    PARTLABEL
sda                                                                                                                        
&#9500;&#9472;sda1                    vfat        1A4D-ED70                              e54dd991-32b8-4b9c-8e6c-76dd9addf18b          
&#9500;&#9472;sda2                    ext4        85498d87-6d8b-11eb-bfff-b083feda1f05   4f8d2be0-d57f-4e07-b5a3-be0b23cc06f3          
&#9492;&#9472;sda3                    LVM2_member U4k6HX-WVr0-Y2KI-MzsK-IMug-vPw1-n8tjOB 2e5574d4-3470-4c5c-b2fa-1d84cc161547          
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        85498d88-6d8b-11eb-bfff-b083feda1f05                                                 
sdb                                                                                                                        
&#9492;&#9472;sdb1                    ext4        c8ab2a4b-79ab-4b9b-865d-f2e97eed6309   207bcd68-a916-be49-8bc8-0e5a88e4d58c          
sdc                                                                                                                        
&#9492;&#9472;sdc1                    vfat        1121-233C                              60ac0bab-01                          UUI      

df (filtered): _________________________________________________________________

                              Avail Use% Mounted on
mapper/ubuntu--vg-ubuntu--lv   2.2T  16% /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv
sda1                         504.9M   1% /mnt/boot-sav/sda1
sda2                         769.8M  14% /mnt/boot-sav/sda2
sdb1                             3T  10% /mnt/boot-sav/sdb1
sdc1                          25.1G  14% /cdrom

Mount options: __________________________________________________________________

mapper/ubuntu--vg-ubuntu--lv rw,relatime
sda1                         rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
sda2                         rw,relatime
sdb1                         rw,relatime
sdc1                         rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
ubuntu--vg-ubuntu--lv

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 85498d87-6d8b-11eb-bfff-b083feda1f05 root hd0,gpt2 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

======================== sda2/grub/menu.lst (filtered) =========================

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
# on ec2, with no console access, there is no reason for a timeout.  set to 0.
timeout        0
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
# kopt=root=/dev/hda1 ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0)
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
# defoptions=console=hvc0
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
title        Ubuntu 18.04.1 LTS, kernel 4.15.0-135-generic
root        (hd0)
kernel        /vmlinuz-4.15.0-135-generic root=/dev/hda1 ro console=hvc0
initrd        /initrd.img-4.15.0-135-generic
title        Ubuntu 18.04.1 LTS, kernel 4.15.0-135-generic (recovery mode)
root        (hd0)
kernel        /vmlinuz-4.15.0-135-generic root=/dev/hda1 ro single
initrd        /initrd.img-4.15.0-135-generic
title        Ubuntu 18.04.1 LTS, kernel 4.15.0-29-generic
root        (hd0)
kernel        /vmlinuz-4.15.0-29-generic root=/dev/hda1 ro console=hvc0
initrd        /initrd.img-4.15.0-29-generic
title        Ubuntu 18.04.1 LTS, kernel 4.15.0-29-generic (recovery mode)
root        (hd0)
kernel        /vmlinuz-4.15.0-29-generic root=/dev/hda1 ro single
initrd        /initrd.img-4.15.0-29-generic
### END DEBIAN AUTOMAGIC KERNELS LIST

======================== sda2/grub/grub.cfg (filtered) =========================

Ubuntu   85498d88-6d8b-11eb-bfff-b083feda1f05
Ubuntu, with Linux 4.15.0-135-generic   85498d88-6d8b-11eb-bfff-b083feda1f05
Ubuntu, with Linux 4.15.0-29-generic   85498d88-6d8b-11eb-bfff-b083feda1f05
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

==================== sda2: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
   0.717777252 = 0.770707456    grub/menu.lst                                  1
   0.700202942 = 0.751837184    grub/grub.cfg                                  2
   0.711914062 = 0.764411904    vmlinuz-4.15.0-135-generic                     1
   0.692256927 = 0.743305216    vmlinuz-4.15.0-29-generic                      1
   0.801448822 = 0.860549120    initrd.img-4.15.0-135-generic                  2
   0.684112549 = 0.734560256    initrd.img-4.15.0-29-generic                   1

====================== sdc1/boot/grub/grub.cfg (filtered) ======================

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

==================== sdc1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


================================= User choice ==================================

Is there RAID on this computer? yes
[dmraid] packages may interfere with MDraid. Do you want to remove them? no

================================ LVM activation ================================

modprobe dm-mod  
vgscan --mknodes
  Found volume group "ubuntu-vg" using metadata type lvm2
vgchange -ay
  1 logical volume(s) in volume group "ubuntu-vg" now active
lvscan
  ACTIVE            '/dev/ubuntu-vg/ubuntu-lv' [<2.73 TiB] inherit
blkid -g

Unusual RAID (no raid in blkid).

=================== blkid (filtered) before raid activation: ===================

/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="85498d88-6d8b-11eb-bfff-b083feda1f05" TYPE="ext4"
/dev/sda1: UUID="1A4D-ED70" TYPE="vfat" PARTUUID="e54dd991-32b8-4b9c-8e6c-76dd9addf18b"
/dev/sda2: UUID="85498d87-6d8b-11eb-bfff-b083feda1f05" TYPE="ext4" PARTUUID="4f8d2be0-d57f-4e07-b5a3-be0b23cc06f3"
/dev/sdb1: UUID="c8ab2a4b-79ab-4b9b-865d-f2e97eed6309" TYPE="ext4" PARTUUID="207bcd68-a916-be49-8bc8-0e5a88e4d58c"
/dev/sdc1: LABEL="UUI" UUID="1121-233C" TYPE="vfat" PARTUUID="60ac0bab-01"
/dev/loop0: LABEL="writable" UUID="103df602-3275-cd40-968f-46bb264091ad" TYPE="ext2"
/dev/sda3: UUID="U4k6HX-WVr0-Y2KI-MzsK-IMug-vPw1-n8tjOB" TYPE="LVM2_member" PARTUUID="2e5574d4-3470-4c5c-b2fa-1d84cc161547"


==================================== dmraid ====================================

dmraid -si -c
no raid disks
No DMRAID disk.
User chose to keep dmraid. It may interfere with mdadm.


==================================== mdadm =====================================
mdadm --assemble --scan

mdadm --detail --scan

Warning: no active raid (DMRAID nor MD_ARRAY).


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to unsign-grub) and reinstall the grub-efi of
mapper/ubuntu--vg-ubuntu--lv,
using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file    

Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.3 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
```

---

### Post by TheFu on 2022-01-15
Things that jump out at me, but I don't know what to do with:
```
Is there RAID on this computer? yes
[dmraid] packages may interfere with MDraid. Do you want to remove them? no
```
again, this could be fine, but seems odd to me.  Best not to use FakeRAID ... er ... ever.

I've not used EFI much - only have it on 1 laptop there. 

[U]Everything below here is examples from an EFI and a non-EFI system. Both have LVM.
[/U]
On my laptop wiht EFI booting, here's the df -h with all the junk removed:
```
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root       25G   18G  5.9G  75% / 
/dev/sda2                        721M  176M  509M  26% /boot 
/dev/sda1                        511M  4.5M  507M   1% /boot/efi
/dev/mapper/ubuntu--vg-stuff      99G   65G   30G  69% /stuff
/dev/mapper/ubuntu--vg-home--lv   74G   23G   48G  33% /home 
```
Sorry it doesn't say the file system types.  All are ext4, except /dev/sda1 which is fat32.
Also, my backup data doesn't have pvs, vgs, or lvs information. That's something I need to fix globally.
There is a 4.1GB swap LV that doesn't show up in the DF.

The laptop is off, so I'm using backup data to get the table above.

**Without EFI booting**, all my systems using LVM have a separate /boot partition and look something like this:
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   21G  9.2G  70% /
/dev/sdb1                         ext2  720M  166M  518M  25% /boot
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  132G   33G  81% /var/lib/libvirt
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd

```
Only the first 2 are mandatory. 
It has a swap LV too, 4.25GB. My desktop systems get 4.1G swap (usually as an LV) and sometimes my math is a little off. ;)

Here's the parted -lm for hadar:
```
BYT;
/dev/sdb:512GB:scsi:512:512:msdos:ATA Micron_1100_MTFD:;
1:1049kB:768MB:767MB:ext2::boot;
2:769MB:512GB:511GB:::;
5:769MB:512GB:511GB:::lvm;
```
That can be fed into a parted command to recreate the exact partitioning.  I really need to convert that to GPT. We all have systems that aren't ideal. :(

My backups need to get a little more consistent with the system data captured nightly to be included in each backup. Having these different views into the storage over time (versions backups) consistently is a good thing, since we never know when a partition table or that sector of the storage will become corrupted.

---

### Post by kinser06 on 2022-01-15
So it seems sda2 wasn't mounting to /boot on its own. I issues the mount command and was able to update the kernel to 5.4.

I then had to remove all the 5.11.x kernel's then re-enable the hwe. I am now booted on the newest HWE kernel.

i found that UUID commented out in the /etc/fstab file. I can't believe this system was running and stable as out of date this was...

Thank you everyone that commented and helped along the way. Your commands to interrogate the file system were fantastic and a great learning experience.

---

### Post by MAFoElffen on 2022-01-16
I would like to address a few things first...

This machine does have RAID on it.

If I had asked the User to run the ubuntForums 'system-info' script, we would have caught this earlier...

From the user's output in Post #10:
> **kinser06 said:**
> 
... (editted)
I get 
```
[COLOR=#ff0000]root@dellserver[/COLOR]:/# sudo ls /boot/initrd.img-*
/boot/initrd.img-4.15.0-135-generic     /boot/initrd.img-5.11.0-46-generic
/boot/initrd.img-5.11.0-051100-generic  /boot/initrd.img-5.4.0-050400-generic
/boot/initrd.img-5.11.0-44-generic      /boot/initrd.img-5.4.0-050400-lowlatency

```
--- (edited)

From the 'boot-info' script he just ran which he posted in Post #43 (snippets):
```

## Edited
parted -lm (filtered): _________________________________________________________

sda:3000GB:scsi:512:512:gpt:[COLOR=#ff0000]DELL PERC H710[/COLOR]:;
1:1049kB:538MB:537MB:fat32::boot, esp;
2:538MB:1612MB:1074MB:ext4::;
3:1612MB:3000GB:2998GB:::;
sdb:4000GB:scsi:512:512:gpt:[COLOR=#ff0000]DELL PERC H710[/COLOR]:;
1:1049kB:4000GB:4000GB:ext4::;
sdc:31.3GB:scsi:512:512:msdos:SanDisk Cruzer Fit:;
1:1049kB:31.3GB:31.3GB:fat32::boot, lba;
mapper/ubuntu--vg-ubuntu--lv:2998GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:2998GB:2998GB:ext4::;
## Edited
==================================== dmraid ====================================

dmraid -si -c
no raid disks
No DMRAID disk.
User chose to keep dmraid. It may interfere with mdadm.


==================================== mdadm =====================================
mdadm --assemble --scan

mdadm --detail --scan

Warning: no active raid (DMRAID nor MD_ARRAY).

## Edited

```
So... Everyone se it yet?

To the OP:
- What Model Dell PowerEdge Server is this, of which Generation of that model?
- Is has a Dell PERC H710. This is not to be considered 'fake raid'. It is full-fleded hardware RAID. The SATA and or SAS drives are not seen by Linux unless htey are setup through through this controller. This controller does not have "JBOD", so if u setup single disks through this card, you set them up as single-disk RAID0 VD's...
 -- This is how these are setup right? 
*** This is just normal for Dell PowerEdge Servers and not a problem. May be a distraction, but... Just how that is...

I feel the problem is still the conflicting versions of Grub... but that might answer when Grub Legacy got installed...

*** "Somehow" this machine has Grub Legacy and Grub2 installed(???) That is what I see as the big problem ***that is confusing things***. Or at the least, Grub Legacy used to be ID'ed by the presence of the /boot/grub/menu.lst file, and  Grub2 by the presence of the /boot/grub/grub.cfg file... But this has both. I haven't heard that 'that' has changed, but... I just looked at the files on one of my Ubuntu 20.04 ARM64 servers tonight, where I found that it that also had both files, and it definitely does not have Grub Legacy on it. Hmmm.

This just gets me more interested and curious. If you could, please run  the UbuntuForums 'system-info" script in my signature line and upload  the report online to pastebin.ubuntu.com (just say yes at that question)  and post the link to it. That report will answer the history questions  of what media and version the system was originally installed from, and  when it was release upgraded... Besides a few more things...

---

### Post by kinser06 on 2022-01-16
Yea this is setup on hardware raid. It’s a older R420 chassis.

Paste bin for sys-info
[https://paste.ubuntu.com/p/wqhc57xZXb/](https://paste.ubuntu.com/p/wqhc57xZXb/)

---

### Post by MAFoElffen on 2022-01-16
> **kinser06 said:**
> Yea this is setup on hardware raid. It’s a older R420 chassis.

Paste bin for sys-info
[https://paste.ubuntu.com/p/wqhc57xZXb/](https://paste.ubuntu.com/p/wqhc57xZXb/)

Looking at the Report now, as I am getting ready to leave for work... This a lot clearer picture of what we are recommending answers for now.

You confirmed Hardware RAID, but didn't confirm if single disk RAID0 VD's or if other. PERC H720 does RAID 0, 1, 5, 6, 10, 50, 60...

---

### Post by kinser06 on 2022-01-16
Sda is a twin disk raid 1 VD.
Sdb is a single disk raid 0 that I manually mount to make backups to.

---

### Post by MAFoElffen on 2022-01-17
> **kinser06 said:**
> So it seems sda2 wasn't mounting to /boot on its own. I issues the mount command and was able to update the kernel to 5.4.

I then had to remove all the 5.11.x kernel's then re-enable the hwe. I am now booted on the newest HWE kernel.

i found that UUID commented out in the /etc/fstab file. I can't believe this system was running and stable as out of date this was...

Thank you everyone that commented and helped along the way. Your commands to interrogate the file system were fantastic and a great learning experience.

Thank you for your patience and persistence.

Is this "Solved" for now? Was it that the /boot was not mounted, because it was somehow commented out somewhere in it's lifecycle? Now that it is not commented out, it is working?

If it is "solved", then please use the "Thread Tools" link in the upper right of the page, to mark this thread as solved  so others can find your solution, to help them with their similar problem.

---

### Post by kinser06 on 2022-01-17
Yea that has fixed everything. Thanks again for the help.

---

