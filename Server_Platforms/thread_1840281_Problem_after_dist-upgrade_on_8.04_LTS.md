---
title: "Problem after dist-upgrade on 8.04 LTS"
date: 2011-09-07
forum: Server Platforms
---

### Post by thebuggy83 on 2011-09-07
Dear Forum!

I ran into a problem after performing
apt-get update
apt-get upgrade
apt-get dist-upgrade

The dist-upgrade crashed because during updating kernels space on the boot partition ran out. So I manually remove with apt-get remove linux-image-2.6.24-19-server and ...-24-server the old kernel that there will be enough space, for the new one.

This worked but when I ran apt-get dist-upgrade again the following error messages appear:

```
root@flo:/boot# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-server linux-ubuntu-modules-2.6.24-29-server
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 34.2MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 52414 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-server ...
WARNING: Couldn't open directory /lib/modules/2.6.24-19-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-19-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server
Cannot find /lib/modules/2.6.24-19-server
update-initramfs: failed for /boot/initrd.img-2.6.24-19-server
dpkg: error processing linux-ubuntu-modules-2.6.24-19-server (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-29-server ...
WARNING: Couldn't open directory /lib/modules/2.6.24-29-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-29-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-29-server
Cannot find /lib/modules/2.6.24-29-server
update-initramfs: failed for /boot/initrd.img-2.6.24-29-server
dpkg: error processing linux-ubuntu-modules-2.6.24-29-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-server
 linux-ubuntu-modules-2.6.24-29-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The module directories and the Kernel files are not there anymore, it seems only the knowledge that the package was installed ist still there.

I tried different things I found on the net like:
dpkg --purge --force-all linux-ubuntu-modules-2.6.24-19-server
dpkg --force-all -r linux-ubuntu-modules-2.6.24-19-server 
dpkg --remove linux-ubuntu-modules-2.6.24-19-server
apt-get install --reinstall linux-ubuntu-modules-2.6.24-19-server linux-image-2.6.24-19-server linux-ubuntu-modules-2.6.24-29-server linux-image-2.6.24-29-server
apt-get install linux-ubuntu-modules-2.6.24-19-server linux-image-2.6.24-19-server linux-ubuntu-modules-2.6.24-29-server linux-image-2.6.24-29-server
apt-get -f remove linux-ubuntu-modules-2.6.24-19-server   

Does anyone has an idea how to resolve this problem ?
Thanks in advance

Best regards

Markus

---

### Post by arrrghhh on 2011-09-07
Hrm.

Did you try ```
sudo apt-get autoremove
```or ```
sudo apt-get autoclean
```?

Have you tried to do the update or upgrade again, before attempting the dist-upgrade..?

I'll try to think of the others - will update this post ;).

---

### Post by thebuggy83 on 2011-09-07
> **arrrghhh said:**
> 
```
sudo apt-get autoremove
```


returns
```
root@flo:/lib/modules# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-server linux-ubuntu-modules-2.6.24-29-server
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 34.2MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 52414 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-server ...
WARNING: Couldn't open directory /lib/modules/2.6.24-19-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-19-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server
Cannot find /lib/modules/2.6.24-19-server
update-initramfs: failed for /boot/initrd.img-2.6.24-19-server
dpkg: error processing linux-ubuntu-modules-2.6.24-19-server (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-29-server ...
WARNING: Couldn't open directory /lib/modules/2.6.24-29-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-29-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-29-server
Cannot find /lib/modules/2.6.24-29-server
update-initramfs: failed for /boot/initrd.img-2.6.24-29-server
dpkg: error processing linux-ubuntu-modules-2.6.24-29-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-server
 linux-ubuntu-modules-2.6.24-29-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

> **arrrghhh said:**
> 
```
sudo apt-get autoclean
```

returns

```
root@flo:/lib/modules# apt-get autoclean
Reading package lists... Done
Building dependency tree
Reading state information... Done
root@flo:/lib/modules# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-server linux-ubuntu-modules-2.6.24-29-server
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 34.2MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 52414 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-server ...
WARNING: Couldn't open directory /lib/modules/2.6.24-19-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-19-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server
Cannot find /lib/modules/2.6.24-19-server
update-initramfs: failed for /boot/initrd.img-2.6.24-19-server
dpkg: error processing linux-ubuntu-modules-2.6.24-19-server (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-29-server ...
WARNING: Couldn't open directory /lib/modules/2.6.24-29-server: No such file or directory
FATAL: Could not open /lib/modules/2.6.24-29-server/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-29-server
Cannot find /lib/modules/2.6.24-29-server
update-initramfs: failed for /boot/initrd.img-2.6.24-29-server
dpkg: error processing linux-ubuntu-modules-2.6.24-29-server (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-server
 linux-ubuntu-modules-2.6.24-29-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@flo:/lib/modules#

```

Thanks for the quick response

Markus

---

### Post by nothingspecial on 2011-09-07
I'd hand on before you do this because I am not sure but......



I think you are going to have to chroot from a live cd and inatall a working kernel.

Info here

[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

---

### Post by thebuggy83 on 2011-09-07
I have two working kernels:

linux-image-2.6.24-24-xen and -29-xen.

I just have the package problem to continue the dist-upgrade.

Thanks

Markus

---

### Post by arrrghhh on 2011-09-07
Hrm, this sounds dumb but maybe we can trick the system into thinking the files are there, so it can be happy and "remove" the package.

Try to ```
touch /lib/modules/2.6.24-19-server/modules.dep.temp
```You might have to mkdir the /lib/modules/2.6.24-19-server/ directory.  Yes, I'm now at the grasping-at-straws stage ;).

---

### Post by thebuggy83 on 2011-09-07
You are my hero. I am so dumb that I did not try that myself.

Thanks 

Markus

---

### Post by arrrghhh on 2011-09-07
> **thebuggy83 said:**
> You are my hero. I am so dumb that I did not try that myself.

Thanks 

Markus

lol, glad it's fixed.  Sometimes the dumb things work :p.

---

### Post by masuch on 2012-04-27
Hi,

thanks to excelent tip I have rid off similar problem but I have another  similar if you can help.

I have faked /boot/config-3.3.1 and /lib/modules/3.3.1
But because I do not need it any more How can I remove it completely. If I simply deleted it - I have got into the same problem described here.

thank you for any advice,
kind regards,
Martin

---

