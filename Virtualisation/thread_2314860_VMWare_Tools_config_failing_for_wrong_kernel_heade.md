---
title: "VMWare Tools config failing for wrong kernel header location"
date: 2016-02-24
forum: Virtualisation
---

### Post by ffxx68 on 2016-02-24
Installing and configuring VMWare Tools fails in my Ubuntu guest OS, because it can't find a valid kernel header location, seems like...
I have the build and headers packages installed:

```
$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.16.0-60-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

$ uname -a
Linux ubuntu 3.16.0-60-generic #80~14.04.1-Ubuntu SMP Wed Jan 20 13:37:48 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

$ ls -l /usr/src
total 32
drwxr-xr-x 24 root root 4096 feb 24 10:20 linux-headers-3.13.0-79
drwxr-xr-x  7 root root 4096 feb 24 10:20 linux-headers-3.13.0-79-generic
drwxr-xr-x 24 root root 4096 mar 17  2015 linux-headers-3.16.0-30
drwxr-xr-x  7 root root 4096 mar 17  2015 linux-headers-3.16.0-30-generic
drwxr-xr-x 24 root root 4096 gen 28 18:59 linux-headers-3.16.0-57
drwxr-xr-x  7 root root 4096 gen 28 18:59 linux-headers-3.16.0-57-generic
drwxr-xr-x 24 root root 4096 feb  8 18:10 linux-headers-3.16.0-60
drwxr-xr-x  7 root root 4096 feb 24 10:27 linux-headers-3.16.0-60-generic
```

Debugging a bit *vmware-config-tools.pl*, I managed to narrow the issue down to this failing command:

```
$ sudo /usr/lib/vmware-tools/sbin64/vmware-modconfig-console --build-mod -k 3.16.0-60-generic vmxnet '/usr/bin/gcc' '/usr/src/linux-headers-3.16.0-60-generic/include' misc vmxnet -- -l "/usr/lib/vmware-tools"
[COLOR=#b22222]
Provided kernel information will not work with the running kernel[/COLOR].
```

Anyone with a clue for this error?

Thanks !

---

