---
title: "Cannot install vmware, missing directory errors."
date: 2008-09-03
forum: Virtualisation
---

### Post by AceRimmer on 2008-09-03
Hello.  Last night I tried to install Vmware server from the repos.  It was ok but I had the serial number wrong and it just hung at that point, wouldn't let me go back and retry it.  So I shut down synaptic and tried to reinstall, well it went through but then I couldn't get it to start.  So I thought that maybe I had some corrupted/bad config files left over from the first botched install so I figured I'd uninstall it and then do it again.  To make sure I removed all the old stuff I went and looked for VMware folders and deleted them, I deleted the etc/vmware folder.  Now I can't even reinstall it since it keeps trying to point to that folder.  So now I know I screwed that up, how can I fix it?  Here is the latest error message. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  vmware-server-kernel-modules vmware-server-kernel-modules-2.6.22-14 
The following NEW packages will be installed:
  vmware-server vmware-server-kernel-modules vmware-server-kernel-modules-2.6.22-14 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/80.6MB of archives. After unpacking 134MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package vmware-server-kernel-modules-2.6.22-14.
(Reading database ... 130089 files and directories currently installed.)
Unpacking vmware-server-kernel-modules-2.6.22-14 (from .../vmware-server-kernel-modules-2.6.22-14_2.6.22.0-1_i386.deb) ...
Selecting previously deselected package vmware-server-kernel-modules.
Unpacking vmware-server-kernel-modules (from .../vmware-server-kernel-modules_2.6.22.0-1_i386.deb) ...
Selecting previously deselected package vmware-server.
Unpacking vmware-server (from .../vmware-server_1.0.4-1gutsy2_i386.deb) ...
Setting up vmware-server-kernel-modules-2.6.22-14 (2.6.22.0-1) ...

Setting up vmware-server-kernel-modules (2.6.22.0-1) ...
Setting up vmware-server (1.0.4-1gutsy2) ...
/etc/init.d/vmware-server: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vmware-server (1.0.4-1gutsy2) ...
/etc/init.d/vmware-server: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done  
```I figured the etc/vmware folder would just be recreated if I did an install, apparently not.  Now I can't do any install or remove of the vmware files since that folder isn't there.

---

### Post by AceRimmer on 2008-09-04
Still no luck getting it to reinstall properly.

---

