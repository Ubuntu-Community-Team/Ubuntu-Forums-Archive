---
title: "vmware permissions on Edgy"
date: 2007-02-21
forum: Server Platforms
---

### Post by caryb on 2007-02-21
I have been having troubles setting up a copied Win2k3 server on vmware on Edgy server, I already have a Ubuntu & Win server running all Ok! but this one I created with the Vm convertor & ftp'd the files accross. It comes up with an error "cannot open the disk '/var/vm/sky01/sky01.vmdk' or one of it's snapshot disks it depends on. Reason Failed to lock the file" and then I get Cannot open/create the log file 'var/vm/sky01/vmware.log 

Does anyone know what permissions I need to rectify this problem? I created 2G files for the disks when I exported/converted the server.


TIA Cary

---

### Post by veloce on 2007-02-21
It may not be a permissions issue.  I had  similar issues copying a vm from one windows machine to another.  Somehow the vm got confused and decided there was a snapshot or something that was not transferred.  If you're using multiple 2G files for the virtual disk, it may be looking in the wrong place for some of them. 

Sorry I don't have a solution, in the end I deleted that vm and used another one.

---

### Post by danielbcr on 2007-05-03
U can find a solution on this page

[http://www.vmware.com/community/thread.jspa?threadID=80554&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=80554&tstart=0)

Visit my blog: danielbcr.blogspot.com

---

