---
title: "TZdata update problems (really serious)"
date: 2008-04-04
forum: Server Platforms
---

### Post by Newmaniese on 2008-04-04
I use Ubuntu servers at work and love them and the general lack of maintenance that they require. However last night into today I was preparing to update my production server and my development server started really having some issues. It appears when I ran 'sudo apt-get upgrade' tzdata seems to be giving me problems. Here are the errors I am getting right now when I run 'apt-get update':

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-server
dpkg: subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
```
mnewman@DEVELOPMENT:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mnewman@DEVELOPMENT:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Setting up tzdata (2008a-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-server
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-server
dpkg: subprocess post-installation script returned error exit status 1

```

Last night I did try 'apt-get remove tzdata' figuring that I would be able to reinstall it and util-linux fresh. It didn't fix the problem and util-linux is still not reinstalled. I saw many posts about the upgrade to fiesty giving people problems with tzdata and how changing the time zone can help, but that isn't doing anything. 

I am at a loss for what to do right now. This is serious. I am glad it is happening on the dev server before I am doing it on the production server. I really hope that we can fix this problem and anticipate the problem when I update and upgrade my production server.  

Thanks in advance for any help that might be given,

Michael

---

### Post by Newmaniese on 2008-04-04
I believe that I have fixed this problem by downloading the tzdata package directly from [http://packages.debian.org/sid/all/tzdata/download](http://packages.debian.org/sid/all/tzdata/download) debian source and then reinstalling it with dpkg -i --force-all <package_name>. This is really ugly. Anyone have a guess as to what apt broke so badly?

---

