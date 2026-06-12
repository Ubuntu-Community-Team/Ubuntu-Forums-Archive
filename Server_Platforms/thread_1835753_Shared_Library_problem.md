---
title: "Shared Library problem"
date: 2011-08-29
forum: Server Platforms
---

### Post by WTM on 2011-08-29
Bit stuck here...

An ubuntu webserver VM of mine was running on it's host quite happily before becoming completely unresponsive.

I unfortunately had to undertake a hard reset, but on rebooting the machine is suffering a kernel panic.

The error message I'm getting is as follows:
"sbin/init: error while loading shared libraries: libdbus-1.so.3: cannot open shared object file: Input/output error
[   2.833050] Kernel panic - not syncing: attempted to kill init!"

I've fired up rescue mode (using live CD (iso)) but have found tools such as apt-get are unavailable due to the library problem.

Advice on how to fix this would be appreciated.

System info
[LIST]
[*]LTS 10.04 Server 64bit running as a XEN VM on a Centos host.
[*]256mb of memory assigned 
[*]Been running approx 4-6 months since installation.
[/LIST]

---

### Post by Bachstelze on 2011-08-30
When the system is unable to read a file due to I/O errors, it's most often a faulty hard drive.

---

### Post by WTM on 2011-08-30
Had half thought that, but the host is still running fine, as are all the other virtual machines running on the same server, so had semi-discounted that.  

Unless a image file getting corrupted would generate the same errors?

I have gone ahead and rebooted the other VMs hosted on the same physical set of drives, with no issues restarting any of them. So not suspecting hardware failure at this point.

I'm wondering, would killing a file system check incorrectly cause the problems I'm experiencing?

---

