---
title: "vmdk in virtualbox; Loading, please wait..."
date: 2010-07-22
forum: Virtualisation
---

### Post by senor_smile on 2010-07-22
I am running ubuntu server 8.04 as a vm on an old installation of vmware server also on ubuntu 8.04.  I need to run this on another box to upgrade the old virtualization server.  I have virtualbox running on xp sp2 and would like to import the vmdk to run it temporarily here.  

I shut down the vm, transferred the vmdk file to the xp machine and set up a new machine with that vmdk file as its hard disk.  No matter what I do, it stalls at a screen saying: 

> Starting up ...
Loading, please wait...

I have tried with PAE/NX on and off, IO APIC on and off, different combinations.  I removed the cd rom and turned off usb.  any ideas what could be going wrong?  

I restarted the vm on the original vmware server and it still runs just fine.  I also tried deleting the transferred vmdk file and transferring it again, thinking that maybe it didn't transfer right.  Same thing.

---

