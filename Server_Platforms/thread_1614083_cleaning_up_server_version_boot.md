---
title: "cleaning up server version /boot"
date: 2010-11-05
forum: Server Platforms
---

### Post by bobwdn on 2010-11-05
I am running a 10.04.1 server (non-gui) and my /boot has dependencies from old kernels still in it.

```
server:/$ ls -alh /boot
total 55M
drwxr-xr-x  6 root root 3.0K 2010-10-20 08:18 .
drwxr-xr-x 23 root root 4.0K 2010-09-28 06:42 ..
-rw-r--r--  1 root root 616K 2010-05-26 23:21 abi-2.6.31-22-generic
-rw-r--r--  1 root root 626K 2010-06-03 20:56 abi-2.6.32-22-generic
-rw-r--r--  1 root root 637K 2010-09-16 13:14 abi-2.6.32-24-generic
-rw-r--r--  1 root root 637K 2010-10-16 18:46 abi-2.6.32-25-generic
-rw-r--r--  1 root root 109K 2010-05-26 23:21 config-2.6.31-22-generic
-rw-r--r--  1 root root 114K 2010-06-03 20:56 config-2.6.32-22-generic
-rw-r--r--  1 root root 114K 2010-09-16 13:14 config-2.6.32-24-generic
-rw-r--r--  1 root root 114K 2010-10-16 18:46 config-2.6.32-25-generic
drwxr-xr-x  3 root root 6.0K 2010-10-20 08:19 grub
drwxr-xr-x  2 root root 5.0K 2010-08-20 08:02 grub_OLD
drwxr-xr-x  4 root root 6.0K 2010-08-21 16:46 grub_OLD2
-rw-r--r--  1 root root 7.1M 2010-09-01 17:08 initrd.img-2.6.31-22-generic
-rw-r--r--  1 root root 7.6M 2010-09-01 17:07 initrd.img-2.6.32-22-generic
-rw-r--r--  1 root root 7.6M 2010-09-18 07:32 initrd.img-2.6.32-24-generic
-rw-r--r--  1 root root 7.6M 2010-10-20 08:18 initrd.img-2.6.32-25-generic
drwx------  2 root root  12K 2010-01-01 20:04 lost+found
-rw-r--r--  1 root root 157K 2010-03-23 04:37 memtest86+.bin
-rw-r--r--  1 root root 1.6M 2010-05-26 23:21 System.map-2.6.31-22-generic
-rw-r--r--  1 root root 1.7M 2010-06-03 20:56 System.map-2.6.32-22-generic
-rw-r--r--  1 root root 1.7M 2010-09-16 13:14 System.map-2.6.32-24-generic
-rw-r--r--  1 root root 1.7M 2010-10-16 18:46 System.map-2.6.32-25-generic
-rw-r--r--  1 root root 1.2K 2010-05-26 23:23 vmcoreinfo-2.6.31-22-generic
-rw-r--r--  1 root root 1.2K 2010-06-03 20:58 vmcoreinfo-2.6.32-22-generic
-rw-r--r--  1 root root 1.2K 2010-09-16 13:16 vmcoreinfo-2.6.32-24-generic
-rw-r--r--  1 root root 1.2K 2010-10-16 18:47 vmcoreinfo-2.6.32-25-generic
-rw-r--r--  1 root root 3.8M 2010-05-26 23:21 vmlinuz-2.6.31-22-generic
-rw-r--r--  1 root root 3.9M 2010-06-03 20:56 vmlinuz-2.6.32-22-generic
-rw-r--r--  1 root root 3.9M 2010-09-16 13:14 vmlinuz-2.6.32-24-generic
-rw-r--r--  1 root root 3.9M 2010-10-16 18:46 vmlinuz-2.6.32-25-generic
```

I keep two most current versions of kernel on all my computers.

When I try ```
server:/$ sudo apt-get remove --purge 2.6.31-22-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.31-22-*
```

I have also tried ```
server:/boot$ sudo aptitude remove linux-image-2.6.31-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
``` and the dependencies remain un-removed.

So, why weren't these dependencies removed when I purged the *linux-image-2.6.*-*-generic* the first time? (To be honest here, it's been a while since I purged these old kernels and I may have done it incorrectly.)

I am not finding much on this issue when it pertains to a command line server version. Everything (I found so far) references a desktop gui removal process.

How do I purge these old kernels dependencies, now? One at a time?

---

### Post by CharlesA on 2010-11-05
You need to use the full name of the package when removing it.

```
sudo apt-get purge vmlinuz-2.6.31-22-generic vmlinuz-2.6.32-22-generic
```

See here as well: [http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

---

### Post by bobwdn on 2010-11-05
Thanks for your suggestion.

I tried ```
dpkg -l | grep ^ii | grep 2.6.31-22 | awk -F' ' '{ print $2 }'
``` and got nothing, as in no output of code. Same with the *2.6.32-22* kernel.

So, I am guessing (remember it's been a while since I removed these kernels) that these are leftover because I remove the kernel incorrectly or should I say *--purge* the kernel. I think that is my mistake, I did NOT *--purge* properly.

So, I cannot reinstall the *2.6.31-22* kernel because it is not available anymore. (I have not tried the *2.6.32-22* kernel yet, but I suspect it is not available anymore either.)

So, is it as simple as *--purge* each file one by one? Or simply *remove* each file?

---

### Post by CharlesA on 2010-11-05
Try running apt-get autoclean or apt-get autoremove to see if it'll remove the extra junk. If not, you can always remove them manually.

---

### Post by bobwdn on 2010-11-18
Due to an injury accident, I have not had the opportunity to complete this issue until today.

Within the /boot directory, I simply ```
rm -f [filename]
``` the file manually and my space problem is solved.

Thanks for everyone suggestions and help.

---

### Post by CharlesA on 2010-11-18
Glad you got it fixed. Don't forget to mark the thread as solved. :)

---

### Post by SeijiSensei on 2010-11-18
You might want to browse /lib/modules as well.  The kernel modules are kept in separate versioned directories some of which may now correspond to versions you've deleted in /boot.

---

