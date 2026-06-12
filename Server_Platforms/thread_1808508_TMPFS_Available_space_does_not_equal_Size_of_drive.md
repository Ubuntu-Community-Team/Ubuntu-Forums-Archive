---
title: "TMPFS Available space does not equal Size of drive"
date: 2011-07-20
forum: Server Platforms
---

### Post by thiesdiggity on 2011-07-20
I have a quick question. I have a 64bit Ubuntu 10.04 server  with 24GB of RAM and is used as a VMWare Workstation 7.1 host. I would  like to use an in-memory drive for the VM Memory location, which I setup  as the following:


  tmpfs /mnt/vmware tmpfs defaults,size=100% 0 0
  

That all works. Next I want to allocate 16GB of RAM to the VM, I know  its a lot but we do a lot of processing that needs a lot of RAM.
  

After the VM is started and I run df -h, I get the following for that drive: 
  

Filesystem Size Used Avail Use% Mounted On 
  tmpfs        24G 11G  14G   44%  /mnt/vmware


  Why is it that the Available (14GB) size does not equal the Size  (24GB) of the drive? And why wouldn't the whole 16GB get allocated to  the memory space, which is what i set in the vmware guest .vmx file? Is  there a limit to the space that can be allocated to a tmpfs file system?  I think this is causing performance problems on the guest.
  Thanks for your time.

---

