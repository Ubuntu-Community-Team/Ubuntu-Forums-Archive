---
title: "VMware Tools install problem and VM guest/host folder sharing"
date: 2017-11-15
forum: Virtualisation
---

### Post by ncdoody2 on 2017-11-15
I'm trying to upgrade/reinstall VMware tools to get folder sharing working again, but I'm running into the issue in the listing below.  Used to have a shared folder at /mnt/hgfs.  Sharing folders between guest and host does depend on VMware tools, right?  It appears I am unable to stop VMware services prior to actual configuration.  Thoughts?  Should I try stopping VMWare services manually first?  If so, how do I do so?
```
host: Windows 7 Home Premium, 64 bit 6.1.7601, Service Pack 1
guest: ubuntu 16.04 LTS 32bit running on VMWare Player 6.0.7 build-2844087
```
x@ubuntu:~$ sudo /usr/bin/vmware-config-tools.pl
[sudo] password for x: 
Initializing...

Making sure services for VMware Tools are stopped.

Stopping Thinprint services in the virtual machine:
       Stopping Virtual Printing daemon:                                                                        done
Stopping VMware Tools services in the virtual machine:
       Guest operating system daemon:                                                                               done
       VMware User Agent (vmware-user):                                                                           done  
       Blocking file system:                                                                                          done
       Unmounting HGFS shares:                                                                                  done
       Guest filesystem driver:                                                                                      done
       VM communication interface socket family:                                                           done
       VM communication interface:                                                                               failed
Unable to stop services for VMware Tools

Execution aborted.
x@ubuntu:~$

---

