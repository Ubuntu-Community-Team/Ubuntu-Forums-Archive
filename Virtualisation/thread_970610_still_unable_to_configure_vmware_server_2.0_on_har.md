---
title: "still unable to configure vmware server 2.0 on hardy"
date: 2008-11-04
forum: Virtualisation
---

### Post by remy06 on 2008-11-04
Hi all,I got the following error after install:

```
Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.2.3", while you are trying to use 
"/usr/bin/gcc" version "4.2.4". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.2.4" anyway? [no] 

Execution abort

```

export doesnt seem to work
```
export CC=gcc-4.2
```

output of /usr/bin/gcc* is
```
user@hardy6856:~$ ls -ali /usr/bin/gcc*
459082 lrwxrwxrwx 1 root root      7 2008-11-05 02:24 /usr/bin/gcc -> gcc-4.2
458900 -rwxr-xr-x 1 root root 193372 2008-10-11 03:41 /usr/bin/gcc-4.2
459084 -rwxr-xr-x 1 root root   2018 2007-06-05 08:59 /usr/bin/gccmakedep
```

Any solutions??

---

### Post by HermanAB on 2008-11-04
Download the kernel source, compile and install it, then reboot with the new kernel.  VMware will then build and install without problems.

---

### Post by remy06 on 2008-11-06
I tried selecting "yes" and proceeded with the configuration and it seems to work.no particular errors reported after that.Tried it and installed a guest os to test.Seems to be working ok.Hopefully won't have any further issues..

---

