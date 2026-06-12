---
title: "multipass 1.9.0 jammy instance can't boot 5.15.0-30 after reboot - boots 5-15.0-27"
date: 2022-05-19
forum: Virtualisation
---

### Post by tech-netharmonix on 2022-05-19
I think that this may be a bug or me not knowing the correct commands. ](*,)

```
ENV: Mac OS 11.6.5 64GB 
multipass 1.9.0
Ubuntu jammy 22.04
multipass launch jammy  --name testA --cpus 2 -m 8G -d 12G
multipass shell testA 

apt update && apt upgrade 
apt-get install snap 

```
I'm getting this message:
```
                                         Pending kernel upgrade
  &#9474; Newer kernel available                                                   &#9474; 
  &#9474;                                                                          &#9474; 
  &#9474; The currently running kernel version is 5.15.0-27-generic which is not   &#9474; 
  &#9474; the expected kernel version 5.15.0-30-generic.                           &#9474; 
  &#9474;                                                                          &#9474; 
  &#9474; Restarting the system to load the new kernel will not be handled         &#9474; 
  &#9474; automatically, so you should consider rebooting.   

sudo reboot 
```

The reboot does not boot the newly upgraded KERNEL
Using the command line how do I get it to boot the new kernel 5.15.0-30 and not the shipped kernel 5.15.0-27? 

```
uname -a
Linux testA 5.15.0-27-generic #28-Ubuntu SMP Thu Apr 14 04:55:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

Rebooting does not install the new image.
```
ll /boot
total 95381
drwxr-xr-x  4 root root     4096 May 18 14:37 ./
drwxr-xr-x 19 root root     4096 May 19 08:47 ../
-rw-------  1 root root  6241791 Apr 14 00:46 System.map-5.15.0-27-generic
-rw-------  1 root root  6241208 May  5 05:45 System.map-5.15.0-30-generic
-rw-r--r--  1 root root   260489 Apr 14 00:46 config-5.15.0-27-generic
-rw-r--r--  1 root root   260559 May  5 05:45 config-5.15.0-30-generic
drwx------  3 root root      512 Dec 31  1969 efi/
drwxr-xr-x  6 root root     4096 May 18 15:45 grub/
lrwxrwxrwx  1 root root       28 May 18 14:37 initrd.img -> initrd.img-5.15.0-30-generic
-rw-r--r--  1 root root 31077548 May  6 03:19 initrd.img-5.15.0-27-generic
-rw-r--r--  1 root root 31431946 May 18 14:37 initrd.img-5.15.0-30-generic
lrwxrwxrwx  1 root root       28 May  6 03:19 initrd.img.old -> initrd.img-5.15.0-27-generic
lrwxrwxrwx  1 root root       25 May 18 14:37 vmlinuz -> vmlinuz-5.15.0-30-generic
-rw-------  1 root root 11064224 Apr 14 00:47 vmlinuz-5.15.0-27-generic
-rw-------  1 root root 11066784 May  5 05:46 vmlinuz-5.15.0-30-generic
lrwxrwxrwx  1 root root       25 May  6 03:19 vmlinuz.old -> vmlinuz-5.15.0-27-generic
```

How do I get it to boot the new 5.15.0-30 and not 5.15.0-27

---

