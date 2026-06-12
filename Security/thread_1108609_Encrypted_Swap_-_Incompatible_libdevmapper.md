---
title: "Encrypted Swap - Incompatible libdevmapper?"
date: 2009-03-27
forum: Security
---

### Post by tges on 2009-03-27
Hi,

First up I've just installed 8.10 Intrepid and it works great. I've followed the guide below to setup an encrypted swap (thanks go to the original author). 

[http://ubuntuforums.org/showthread.php?t=302167](http://ubuntuforums.org/showthread.php?t=302167)

However now I get the following error, which I have searched for a solution to no avail. Seems to be a bug in 64bit version of Intrepid from what I have read.

> 
~$ dmsetup targets | grep crypt
/dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.
/dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.
Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver 
Command failed

However if I do the following I can see the mapped swap. Also the crypt modules are loaded

> ~$ ls /dev/mapper
control  cswap

~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/mapper/cswap                       partition	4000144	0	-1

~$ sudo dmsetup targets
crypt            v1.6.0
striped          v1.1.0
linear           v1.0.3
error            v1.0.1

Then I try checking the encrypted swap
> 
~$ cryptsetup status cswap
mlockall failed: Cannot allocate memory
WARNING!!! Possibly insecure memory. Are you root?
Command failed: Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver

~$ sudo cryptsetup status cswap
/dev/mapper/cswap is active:
  cipher:  aes-cbc-plain
  keysize: 256 bits
  device:  /dev/sda6
  offset:  0 sectors
  size:    8000307 sectors
  mode:    read/write

I'm new to linux and am not 100% following the posts I'm reading on this issue. Any help or solutions for this problem? :confused:

Thanks in advance! :)

---

### Post by hyper_ch on 2009-03-28
see my guide how I do it.

[http://ubuntuforums.org/showthread.php?t=848691](http://ubuntuforums.org/showthread.php?t=848691)

Especially see this here:

[http://ubuntuforums.org/showpost.php?p=5314770&postcount=9](http://ubuntuforums.org/showpost.php?p=5314770&postcount=9)

---

### Post by HermanAB on 2009-03-28
BTW, the easiest way to encrypt swap, is to make an encrypted /home, then configure swap to be a swapfile on /home (using the swapon program), then you don't need /swap anymore.

---

