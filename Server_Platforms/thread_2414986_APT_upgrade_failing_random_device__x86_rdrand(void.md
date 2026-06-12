---
title: "APT upgrade failing: random_device::__x86_rdrand(void)"
date: 2019-03-18
forum: Server Platforms
---

### Post by m-dw on 2019-03-18
This is not a new issue. but it resolved itself for a while. Now it has  recurred, and I've not received any software updates for over a month on  my server. 

The server is running[INDENT]Ubuntu 18.04 LTS
Intel Atom C3758 with 16GB RAM
Standard Kernel
HWE kernel currently 4.18.0-1
[/INDENT]

Running ```
sudo apt update
``` results in the following output:
```

david@srvbuntu:~$ sudo apt update
Hit:1 http://ppa.launchpad.net/iconnor/zoneminder-1.32/ubuntu bionic InRelease
Hit:2 http://archive.ubuntu.com/ubuntu bionic InRelease                                                                     
Hit:4 http://ppa.launchpad.net/uroni/urbackup/ubuntu bionic InRelease                                                                                    
Get:3 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                             
Get:5 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]         
[B]Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]         
0% [1 InRelease gpgv 20.7 kB] [6 InRelease 2,269 B/88.7 kB 3%]terminate  called after throwing an instance of 'std::runtime_error'
  what():  random_device::__x86_rdrand(void)
Aborted[/B]

```

When I originally suffered this issue, I raised a bug report on Launchpad here: [URL="https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1784796"]https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1784796

[/URL] The issue recurred after a kernel upgrade to 4.15.0-45. I was able  to boot into a previous kernel which allowed me to run update again and  install the HWE kernel, and that allowed subsequent updates, but now it  is failing consistently.

Any suggestions and/or workarounds greatly appreciated.

---

### Post by m-dw on 2019-03-20
Does **_no-one_** experience this?

---

