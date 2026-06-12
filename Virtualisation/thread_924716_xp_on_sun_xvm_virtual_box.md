---
title: "xp on sun xvm virtual box"
date: 2008-09-19
forum: Virtualisation
---

### Post by blastedmax on 2008-09-19
hey i wanted kno how to run xp from my harddrive on ubuntu virtual box but i want my xp that is on the harddirve so wut am i doing wrong

---

### Post by trmentry on 2008-09-20
I'm not exaclty sure what you are asking.  But this is what I'm thinking.
You have a dual boot machine or something. 

You would like to run your windows xp install that is on your hard drive with sun xvm or virtualbox.  Right?

I'm not exaclty sure if this is possible.  I've never heard of that before, being able to run a physical machine in a vm.

However that being said.  VMWware has a utility called VMware Converter.  It can take a physical machine and convert to a vm.  However I don't know if the free one can.  I believe it can, but never tried.  

[http://www.vmware.com/download/converter/](http://www.vmware.com/download/converter/)


That being said... Sun has said that XVM will not have it's own file formats.  

[http://www.virtualization.info/techtalk/2008/01/sun-virtualization-strategy.html](http://www.virtualization.info/techtalk/2008/01/sun-virtualization-strategy.html)
> 
VI: How do you plan to migrate virtual machines from 3rd party hypervisors to xVM Server? Can we expect a P2V/V2V migration tool?

SW: We've decided to avoid creating any new file formats for virtual machines, and instead will be directly supporting the native formats of both VMware's ESX Server and Microsoft's Hyper-V. If you have VMs today, they should run unmodified inside xVM Server.


so you should be ok to use the vmware converter to convert your machine to a vm.  But it will be it's own separate machine when it's up and running in xvm.  You won't have your changes, etc in the physical machine.

Hope this helps.

---

