---
title: "error of  packegs instalation ."
date: 2008-10-06
forum: Server Platforms
---

### Post by darkmode on 2008-10-06
hello ,

last week i just installed the ubuntu 8.04 server edition  on my PC , but when i try to install some packegs the server gime some errors  

root@Unforgiven:~# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but it is not going to be installed
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
root@Unforgiven:~# 


my pc information is :
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.9
          slot: XU1 PROCESSOR
          size: 2800MHz
          capacity: 3200MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr

the CD-ROM and the USB-media cant be detected too .
any one can help ?

---

### Post by darkmode on 2008-10-06
i have an other error 

root@Unforgiven:~# apt-get install tree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.4kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Get:1 [http://ftp.udc.es](http://ftp.udc.es) hardy/universe tree 1.5.1.1-1 [28.4kB]
Fetched 28.4kB in 0s (72.1kB/s)
dpkg: dpkg - error: PATH is not set.

E: Sub-process /usr/bin/dpkg returned an error code (2)
root@Unforgiven:~#

---

### Post by lykwydchykyn on 2008-10-06
What command did you use to get to a root shell?  Somehow your PATH variable isn't being set.

Did you do apt-get update before trying to install?  Your package list might be out of date.

---

### Post by darkmode on 2008-10-07
yes i updated before install any package

---

