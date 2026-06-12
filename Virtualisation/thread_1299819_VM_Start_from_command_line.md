---
title: "VM Start from command line"
date: 2009-10-24
forum: Virtualisation
---

### Post by ant2ne on 2009-10-24
I used to run the following script as a cron job.
```
#!/bin/sh
vmware-cmd "/data/vm/Ubuntu9.04/Ubuntu64-bit/Ubuntu64-bit.vmx" start
vmware-cmd "/data/vm/Server03/Windows Server 2003 Enterprise Edition 2.vmx" start
vmware-cmd "/data/vm/XP Pro x64/XP Pro x64/XP Pro x64.vmx" start

``` With the new version, the command vmware-cmd seems to be broken. What would the new command look like?

---

### Post by cilynx on 2009-10-25
Can you give us the error(s) from running these commands manually?

---

### Post by ant2ne on 2009-10-25
> **cilynx said:**
> Can you give us the error(s) from running these commands manually?
ant2ne@2ne-buntu:~$ sudo vmware-cmd --help
sudo: vmware-cmd: command not found
ant2ne@2ne-buntu:~$

---

### Post by ant2ne on 2009-11-01
Notta?

---

### Post by ant2ne on 2009-11-06
[http://unixfoo.blogspot.com/2008/11/vmware-20-cli-management-utility.html](http://unixfoo.blogspot.com/2008/11/vmware-20-cli-management-utility.html)

> Power off a virtual machine :

[root@foo-vm12 bin]# /usr/vmware/bin/vmware-vim-cmd vmsvc/power.off 128
Powered off
[root@foo-vm12 bin]#

Power on a virtual machine :

[root@foo-vm12 bin]# /usr/vmware/bin/vmware-vim-cmd vmsvc/power.on 128
Powered on
[root@foo-vm12 bin]#

Also

You have to make sure that root has an "Administrator" role under permissions in the 
web interface.

[http://ubuntuforums.org/showthread.php?t=998271](http://ubuntuforums.org/showthread.php?t=998271)

---

