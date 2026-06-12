---
title: "xen unable to run 64bit hvm domu"
date: 2009-09-17
forum: Virtualisation
---

### Post by kameleon25 on 2009-09-17
Hello all. I am having an issue with my xen server. I have Ubuntu 8.04 installed with xen-server installed from the backport repository (was from the plain repository until yesterday due to this issue). I believe it is 3.3.x or something. This is running on a machine that has an AMD Athlon X2 4600+ that has the SVM capabilities when I do the 
```
cat /proc/cpuinfo
```
And I currently have 3 PV ubuntu, 1 HVM win2k3 server, and one PV centos 5.2 domu's installed. The problem is they are all 32-bit os's as that is all I needed at the time.

Yesterday I went to install the 64-bit Windows 7 RC1 to mess around with and it tells me I do not have a 64-bit cpu. I know this is xen telling it that it is only 32-bit so I did some digging. I ran
```
xm info
```
and found where the cpu is showing as an i686 instead of the needed x86_64. Also my capabilities listed are as follows:
```
xen_caps               : xen-3.0-x86_32p hvm-3.0-x86_32 hvm-3.0-x86_32p

```
Nothing about 64-bit in there. So I read some and saw that there was an update in the latest xen that allowed whatever so I enabled the backport repo and did an upgrade only to see the same issue. I cannot even install a 64-bit PV domu. What do I need to do to get full 64-bit capabilities on my xen setup?

---

### Post by __p1n__ on 2009-09-18
You need to configure/install/run the 64bit xen hypervisor to run a 64bit PVM domu or HVM domu.

Those domu's are not supported by the 32bit xen hypervisor.

---

### Post by kameleon25 on 2009-09-18
When I installed the xen-server package it contained the virtual packages for the amd64 and i386 hypervisor. Problem is I see no way to enable the amd64 one. I have searched high and low and am asking for any assistance.

---

### Post by __p1n__ on 2009-09-18
Instead of pulling it from a repository have you tried simply downloading the source 3.4.1 hypervisor from the project page and configuring/building/installing it manually? 

Please note that any package-oriented update that you do will simply upgrade the existing 32bit hypervisor on your system to a later-release 32bit hypervisor if you don't configure and install it.

---

### Post by srivo on 2009-09-20
Did you installed the Ubuntu 8.04 64 bit version? Xen can only run in 32 bit if it was installed in a 32 bit system and same for the 64 bit version. If you install a 64bit OS it will only virtualize 64bit system.

---

