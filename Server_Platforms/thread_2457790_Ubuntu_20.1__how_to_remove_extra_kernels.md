---
title: "Ubuntu 20.1  how to remove extra kernels?"
date: 2021-02-09
forum: Server Platforms
---

### Post by deepakdeshp on 2021-02-09
I have 61 kernels installed on my Ubuntu server. How do I remove the extra 60 kernels?


```
sudo dpkg --list | egrep -i --color 'linux-image|linux-headers'|wc -l
61
sudo apt-get autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.



```

---

### Post by LHammonds on 2021-02-09
How much free space do you have on /boot?   If you have run out of space, normal commands will not work until you manually free up space.

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by ameinild on 2021-02-09
Please provide the output of this command:

```
dpkg --list 'linux-image*'
```

Just because you have 61 kernel packages doesn't mean they're all installed.

For instance on my system, I get the following:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version      Architecture Description
+++-=====================================-============-============-=================================
un  linux-image                           <none>       <none>       (no description available)
rc  linux-image-5.4.0-29-generic          5.4.0-29.33  amd64        Signed kernel image generic
rc  linux-image-5.4.0-31-generic          5.4.0-31.35  amd64        Signed kernel image generic
rc  linux-image-5.4.0-33-generic          5.4.0-33.37  amd64        Signed kernel image generic
rc  linux-image-5.4.0-37-generic          5.4.0-37.41  amd64        Signed kernel image generic
rc  linux-image-5.4.0-39-generic          5.4.0-39.43  amd64        Signed kernel image generic
rc  linux-image-5.4.0-40-generic          5.4.0-40.44  amd64        Signed kernel image generic
rc  linux-image-5.4.0-42-generic          5.4.0-42.46  amd64        Signed kernel image generic
rc  linux-image-5.4.0-45-generic          5.4.0-45.49  amd64        Signed kernel image generic
rc  linux-image-5.4.0-47-generic          5.4.0-47.51  amd64        Signed kernel image generic
rc  linux-image-5.4.0-48-generic          5.4.0-48.52  amd64        Signed kernel image generic
rc  linux-image-5.4.0-51-generic          5.4.0-51.56  amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic          5.4.0-52.57  amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic          5.4.0-53.59  amd64        Signed kernel image generic
rc  linux-image-5.4.0-54-generic          5.4.0-54.60  amd64        Signed kernel image generic
rc  linux-image-5.4.0-56-generic          5.4.0-56.62  amd64        Signed kernel image generic
rc  linux-image-5.4.0-58-generic          5.4.0-58.64  amd64        Signed kernel image generic
rc  linux-image-5.4.0-59-generic          5.4.0-59.65  amd64        Signed kernel image generic
rc  linux-image-5.4.0-60-generic          5.4.0-60.67  amd64        Signed kernel image generic
rc  linux-image-5.4.0-62-generic          5.4.0-62.70  amd64        Signed kernel image generic
ii  linux-image-5.4.0-64-generic          5.4.0-64.72  amd64        Signed kernel image generic
ii  linux-image-5.4.0-65-generic          5.4.0-65.73  amd64        Signed kernel image generic
ii  linux-image-generic                   5.4.0.65.68  amd64        Generic Linux kernel image
un  linux-image-unsigned-5.4.0-29-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-31-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-33-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-37-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-39-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-40-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-42-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-45-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-47-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-48-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-51-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-52-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-53-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-54-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-56-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-58-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-59-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-60-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-62-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-64-generic <none>       <none>       (no description available)
un  linux-image-unsigned-5.4.0-65-generic <none>       <none>       (no description available)
```

As you can see, only the 2 latest images are installed. By default, Ubuntu will leave the last 2 kernel images and remove older ones.

---

### Post by LHammonds on 2021-02-09
@ameinild, I guess it would help if I actually took the time to "read" what he typed rather than make assumptions.  LoL

FYI - By default, Ubuntu 20 usually keeps 2 kernels installed.  The currently active kernel and the prior kernel.  When new kernels are released, you will have 3 kernels for a brief time.

You can also see how many kernel files exist by looking in the /boot folder.

I run Ubuntu in virtual environments so the following command will show me the kernel files:

```
ls -l /boot/vm*
```

I can then see which one is currently active with this command:

```
uname -r
```

If a kernel is installed that is newer than the currently active kernel, then it is likely there was an update and you have yet to reboot.  You can see if there is an impending reboot needed by seeing if 2 files exist with this command:

```
ls -l /var/run/reboot*
```

If there is a reboot and description file there, then the system is waiting for a reboot to apply updates that can only happen during a reboot (such as kernel updates)

LHammonds

---

### Post by rsteinmetz70112 on 2021-02-09
I had this situation on one of my servers and after I got brave enough I was able to resolve it the following way:
I've experienced no problems.

First you might try```
 sudo apt autoremove
``` and see what it does.

If that doesn't work you can remove the kernels with
```
sudo apt-get remove '*5.4.0-29.33*'
```
I found that in my case most of the kernels weren't actually installed only the images in /boot.
If no kernel is found or after it is removed you can simply delete the files in /boot
```
sudo rm /boot/'*5.4.0-29.33*
```

When you finish you should run update-initramfs. The next time the kernel updates it will rebuild itself.
If you decide to do this be very careful not to delete the two most recently installed kernels.

---

### Post by Doug S on 2021-02-09
there are a couple of excellent kernel removal management tools available. The best one (my opinion) is [here]("https://launchpad.net/linux-purge").
I often have a great many kernels installed, and also want to selectively purge them, because I typically keep a few older versions for regression tests. This tool has been so very helpful.

Example screen shot, and yes I do not have the little package that will make the border pretty installed (don't care about pretty) (oh, and I just deleted about 50 kernels a few days ago, so don't have many at the moment):

[ATTACH=CONFIG]287937[/ATTACH]

and if I select a couple of kernels to purge, I'll get, for example:

```
doug@s18:~/linux-purge/linux-purge$ sudo ./linux-purge --choose
[sudo] password for doug:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdns-export1107 libicu65 libisc-export1104 libllvm10 libllvm9 linux-headers-5.4.0-60 linux-headers-5.4.0-60-generic linux-image-5.4.0-60-generic
  linux-modules-5.4.0-60-generic linux-modules-extra-5.4.0-60-generic python3-nacl python3-pymacaroons python3.7 python3.7-minimal ruby-did-you-mean
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-5.4.0-56* linux-headers-5.4.0-56-generic* linux-headers-5.4.0-58* linux-headers-5.4.0-58-generic* linux-image-5.4.0-56-generic*
  linux-image-5.4.0-58-generic* linux-modules-5.4.0-56-generic* linux-modules-5.4.0-58-generic* linux-modules-extra-5.4.0-56-generic*
  linux-modules-extra-5.4.0-58-generic*
0 upgraded, 0 newly installed, 10 to remove and 54 not upgraded.
After this operation, 721 MB disk space will be freed.
Do you want to continue? [Y/n]

```

---

### Post by deepakdeshp on 2021-02-12
> **LHammonds said:**
> How much free space do you have on /boot?   If you have run out of space, normal commands will not work until you manually free up space.

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

I don't ha e a separate boot partition

---

### Post by deepakdeshp on 2021-02-12
> **rsteinmetz70112 said:**
> I had this situation on one of my servers and after I got brave enough I was able to resolve it the following way:
I've experienced no problems.

First you might try```
 sudo apt autoremove
``` and see what it does.

If that doesn't work you can remove the kernels with
```
sudo apt-get remove '*5.4.0-29.33*'
```
I found that in my case most of the kernels weren't actually installed only the images in /boot.
If no kernel is found or after it is removed you can simply delete the files in /boot
```
sudo rm /boot/'*5.4.0-29.33*
```

When you finish you should run update-initramfs. The next time the kernel updates it will rebuild itself.
If you decide to do this be very careful not to delete the two most recently installed kernels.

```
sudo dpkg --list | egrep -i --color 'linux-image|linux-headers'|wc -l
8

```

I ran sudo linux-purge --choose to purge the kernels.

Earlier the number was 61 instead of 8. The numbers here surely dont indicate number of kernels. I am not sure what they indicate. Now in grub advenced options only 2 kernels are given as options. Only 200 MB space was saved.

---

### Post by deadflowr on 2021-02-12
> I ran sudo linux-purge --choose to purge the kernels.

Earlier the number was 61 instead of 8. The numbers here surely dont indicate number of kernels. I am not sure what they indicate. 
Your first output included already removed kernels, marked with the rc status.
rc stands for packages that were removed, but the system still as leftover configuration files.

If you want to see what it actually installed run this
```
dpkg -l | grep linux-image | awk '/^ii/{print $1,$2}'
```

The issue with the rc status is that the apt command "remove" removes packages but doesn't flush out the package's configurations.
This also applies to the "autoremove" command.

I find this is the easiest way to clear all those pesky rcs away
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y
```
This command finds all the rc packages on the system then appends the list to apt purge.
Unlike apt's remove command, purge does remove leftover configurations.

Another thing you can do is "autoremove" can be run with the --purge option which will autoremove the packages marked as such but it will also clear out the configs
at the same time, so you don't have to deal with them at a later date.

---

### Post by Doug S on 2021-02-12
yes, the linux-purge program takes care of all the stuff deadflowr just mentioned, and more. As the OP observed. It is the easy selectivity of which kernels to delete that I like. Kernel management used to take me a lot of time, now it is trivial.

---

