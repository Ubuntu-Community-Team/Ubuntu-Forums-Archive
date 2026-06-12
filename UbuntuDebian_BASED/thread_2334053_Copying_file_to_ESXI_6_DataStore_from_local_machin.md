---
title: "Copying file to ESXI 6 DataStore from local machine"
date: 2016-08-16
forum: Ubuntu/Debian BASED
---

### Post by Dr Spliff on 2016-08-16
Having quite a bit of an issue trying to install Kali 2 on my ESXI server.  Logging in with Vsphere and installing with a local Kali2 image (verified with SHA1) results in a freeze during 4-6% of the install process.  Hence, I'm trying to add the ISO to the datastore from my Ubuntu machine and then install from Vsphere from the datastore.  I am having a problem using scp to copy locally to the datastore I'm trying to reach.  

Datastore resides on a 64GB USB 3.0.  I manually found the end sector and formatted with VMFS5, the drive shows up in the datastore in Vsphere Storage tab.  After disconnecting all the disks besides the ESXI filesystem (mpx.vmhba32) SSHing into the server, and going to disks I find the datastore is 

[HTML][root@localhost:/dev/disks] ls
mpx.vmhba32:C0:T0:L0                    vml.0000000000766d68626133323a303a30
mpx.vmhba32:C0:T0:L0:1                  vml.0000000000766d68626133323a303a30:1
mpx.vmhba33:C0:T0:L0                    vml.0000000000766d68626133333a303a30
mpx.vmhba33:C0:T0:L0:1                  vml.0000000000766d68626133333a303a30:1
mpx.vmhba33:C0:T0:L0:5                  vml.0000000000766d68626133333a303a30:5
mpx.vmhba33:C0:T0:L0:6                  vml.0000000000766d68626133333a303a30:6
mpx.vmhba33:C0:T0:L0:7                  vml.0000000000766d68626133333a303a30:7
mpx.vmhba33:C0:T0:L0:8                  vml.0000000000766d68626133333a303a30:8
mpx.vmhba33:C0:T0:L0:9                  vml.0000000000766d68626133333a303a30:9
[/HTML]

So the datastore I'm trying to access is mpx.vmhba33:C0:T0:L0.  

Logically, then, scp iso from local machine to root@ipaddress /dev/disks/diskid.  

[HTML]$ sudo scp kali-linux-2016.1-amd64.iso root@192.168.1.88:/dev/disks/mpx.vmhba33:C0:T0:L0:1
Password:
Password: 
kali-linux-2016.1-amd64.iso                   100% 2809MB  18.7MB/s   02:30    
scp: /dev/disks/mpx.vmhba33:C0:T0:L0:1: Input/output error[/HTML]

I originally thought permissions error, so chmod ug+x to vmhba33.  Same result.  It appears there is no problem copying the file, but the code hinders the file from being copied to the datastore.  :confused:

---

### Post by wildmanne39 on 2016-08-16
*Thread moved to **Ubuntu/Debian BASED**.*

---

