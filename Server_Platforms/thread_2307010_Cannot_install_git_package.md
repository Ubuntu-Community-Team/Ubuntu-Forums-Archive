---
title: "Cannot install git package"
date: 2015-12-21
forum: Server Platforms
---

### Post by drzeus213 on 2015-12-21
I am currently running Ubuntu Server 14.04.3 LTS and I am trying to install the git package via the command:

```
sudo apt-get install git
```
However, when I run it the following is returned:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 git : Depends: liberror-perl but it is not going to be installed
       Depends: git-man (> 1:1.9.1) but it is not going to be installed
       Depends: git-man (< 1:1.9.1-.) but it is not going to be installed
 linux-image-extra-3.19.0-42-generic : Depends: linux-image-3.19.0-42-generic but it is not going to be installed
 linux-signed-image-3.19.0-42-generic : Depends: linux-image-3.19.0-42-generic (= 3.19.0-42.48~14.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Here is what I get when I run:

```
sudo apt-get -f install
```

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-31 linux-headers-3.19.0-31-generic
  linux-headers-3.19.0-32 linux-headers-3.19.0-32-generic
  linux-headers-3.19.0-33 linux-headers-3.19.0-33-generic
  linux-headers-3.19.0-41 linux-headers-3.19.0-41-generic
  linux-image-3.19.0-31-generic linux-image-3.19.0-32-generic
  linux-image-3.19.0-33-generic linux-image-3.19.0-41-generic
  linux-image-extra-3.19.0-31-generic linux-image-extra-3.19.0-32-generic
  linux-image-extra-3.19.0-33-generic linux-image-extra-3.19.0-41-generic
  linux-signed-image-3.19.0-31-generic linux-signed-image-3.19.0-32-generic
  linux-signed-image-3.19.0-33-generic linux-signed-image-3.19.0-41-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.19.0-42-generic
Suggested packages:
  fdutils linux-lts-vivid-tools
The following NEW packages will be installed
  linux-image-3.19.0-42-generic
0 to upgrade, 1 to newly install, 0 to remove and 17 not to upgrade.
12 not fully installed or removed.
Need to get 0 B/16.7 MB of archives.
After this operation, 47.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 245793 files and directories currently installed.)
Preparing to unpack .../linux-image-3.19.0-42-generic_3.19.0-42.48~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-42-generic (3.19.0-42.48~14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.19.0-42-generic_3.19.0-42.48~14.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.19.0-42-generic' to '/boot/vmlinuz-3.19.0-42-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.19.0-42-generic_3.19.0-42.48~14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

any help solving this issue would be great!
Thanks
-Drzeus213

---

### Post by veddox on 2015-12-21
```
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.19.0-42-generic_3.19.0-42.48~14.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.19.0-42-generic' to '/boot/vmlinuz-3.19.0-42-generic.dpkg-new': failed to write (**No space left on device**)
No apport report written because the error message indicates a disk full error
```

The problem appears to be that you don't have any space left on your /boot partition. (I'm assuming that you set up /boot as a separate partition?)
This can be caused by old (and no longer needed) vmlinuz files accumulating.

I suggest that you have a look at your /boot directory and check up. If you see a lot of vmlinuz* files, you can safely remove most of the old ones
to give you back some free space. (Obviously do a backup first, just in case anything goes wrong, but I've done it before, it should be fine. Just
make sure you don't delete the newest version...) Here's a related thread: [http://ubuntuforums.org/showthread.php?t=2098490](http://ubuntuforums.org/showthread.php?t=2098490)

When you've done that, you can run

```
sudo apt-get -f install
```

and then 

```
sudo apt-get install git
```

That ought to work :-)

---

### Post by ian-weisser on 2015-12-21
Ah, good old [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"). Please click the 'affects me too' link at the top of the bug report.

Another way is to fix is to use dpkg or Synaptic to remove one or two old kernels.
The goal is simply to free enough space for apt to complete installing the kernels, so the package manager works again and you can install git.

After apt works again, there are two ways to prevent the problem in the future:
1) Mark your wall calendar, and run 'autoremove' every month or so.
2) Use the unattended-upgrades package to regularly run autoremove for  you. Edit the autoremove setting in  /etc/apt/apt.conf.d/50unattended-upgrades from 'false' to 'true'

---

### Post by drzeus213 on 2015-12-23
Is there a way for me to increase the size of the /boot partition? Would modifying the partitions via my windows machine work? Or would I need to do something else?

---

### Post by ian-weisser on 2015-12-23
DO NOT modify Linux partitions using Windows. That's a great way to destroy both installs at once.

Don't focus on the *size* of your /boot partition (do you actually have one? You haven't confirmed).
Increasing the size of /boot is a temporary solution - you must *maintain* the kernels you have in boot. A bigger /boot simply means you run maintenance a bit less often.
...if indeed you have a separate boot partition. You have not confirmed that yet.

---

### Post by drzeus213 on 2015-12-24
> DO NOT modify Linux partitions using Windows. That's a great way to destroy both installs at once.
Thanks for the heads up! That's not something I will be doing then!

Also I do have a boot partition, I wasn't able to confirm it last time I posted because I didn't have access to my server (I had to move the machine for some maintenance) however based on your last post it does not seem important to change the size. I managed to clear some space in my /boot partition and I have installed git and autoremove and it is currently removing the redundant kernels. Thanks for your help!

---

### Post by veddox on 2015-12-24
Great!

Don't forget to mark this thread as "Solved" when it is :-)

---

