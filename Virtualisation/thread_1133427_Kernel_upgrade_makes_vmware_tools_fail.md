---
title: "Kernel upgrade makes vmware tools fail"
date: 2009-04-22
forum: Virtualisation
---

### Post by bartcramer on 2009-04-22
Hi all, 

I am having the following issue with my Intrepid VM in Fusion, and was hoping one of you guys could help. 

I upgraded my kernel. That was a bad idea: now vmware-tools does not recognize my kernel anymore. 

```

Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
   Virtual Printing daemon:                                            done
   VM communication interface socket family:                           done
None of the pre-built vmmemctl modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmmemctl module 
for your system (you need to have a C compiler installed on your system)? 
[no] 

[...etc...]

```

I am using version 7.9.3 build-159196 of the tools, of which I suppose it is the latest one. 

Worse, when it restarts the X server, things go wrong: 

```

Detected X.org version 7.4.2.

 * Restarting Hardware abstraction layer hald                                   
                                                                         [ OK ]

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-11-server #1 SMP Wed Apr 1 21:34:13 UTC 2009 x86_64
Build Date: 09 March 2009  01:06:41PM
xorg-server 2:1.5.2-2ubuntu3.1 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/vmware-config0/XF86ConfigLog.5629", Time: Wed Apr 22 22:58:44 2009
(++) Using config file: "/etc/X11/xorg.conf"
error setting MTRR (base = 0xd0000000, size = 0x03e80000, type = 1) Invalid argument (22)

X is running fine with the new config file.

error setting MTRR (base = 0xd0000000, size = 0x03e80000, type = 1) Invalid argument (22)
   Checking acpi hot plug                                              done
Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   VM communication interface socket family:                          failed
   Guest operating system daemon:                                      done
   Virtual Printing daemon:                                            done
Unable to start services for VMware Tools

Execution aborted.

```

I tried downgrading my kernel, to no avail. Can someone give me a nudge in the right direction? Or should I report a bug at Vmware? 

Thanks for your help!

---

### Post by bartcramer on 2009-04-22
Never mind. 

It turns out that uninstalling and installing instead of 'over-installing' is the trick. Still weird, but the issue is solved. 

Bart.

---

### Post by hercules@igf.edu.pl on 2009-05-15
You don't need to reinstall, just reconfigure:

 ```
vmware-config-tools.pl -d
```

-d option sets the defaults so you don't need to press [ENTER] many times... :)

---

