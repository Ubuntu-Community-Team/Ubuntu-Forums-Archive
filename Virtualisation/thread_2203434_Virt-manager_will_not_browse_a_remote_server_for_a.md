---
title: "Virt-manager will not browse a remote server for an .iso file"
date: 2014-02-03
forum: Virtualisation
---

### Post by J Blain on 2014-02-03
I am running Ubuntu 13.10 Desktop on my PC

Ubuntu 13.10 server on a remote machine

I can ssh to the remote machine with public/private key without problem using my user name

I can start virt-manager on my desktop and connect either to the server or to my desktop machine (both have KVM/QEMU installed) without problems

I have copies of the .iso file for the OS I am trying to install (Windows 8.1) on both hard drives (the server's as well as my desktop's).

If I connect virt-manager to my local machine, I can select the local .iso file easely by using the "Browse Local" button in the "Locate Iso Media" dialog box.

However, I cannot on the remote server, because on that machine the "Browse Local" button is greyed out !!

What am I doing wrong ? How can I remotely create a virtual machine from a .iso OS file on a remote server ?

---

### Post by TheFu on 2014-02-06
Did you put the ISO file in the place that libvirt knows about?  It is usually under /var/lib/libvirt/ somewhere. In 12.04, they call them "storage pools" and if you want somewhere outside the default location, then it has to be setup globally for the VM host.

---

### Post by J Blain on 2014-02-06
Yes I did, I put the .iso file in /var/lib/libvirt/images. But then it is not listed in the virtual manager storage panel. Only the .img files are.

I know I am missing some fundamental info/insight here, but I just cannot find it...

Can I convert the .iso file into a .img one and then create a vm from that .img ?

Google finds me lots of ways to go the reverse route that is converting an .img file to an .iso. But I draw a blank trying to find out how to go from .iso to .img.

So I still cannot figure out how to remotely (virtual manager running locally on my machine and connect to a vm host over ssh) get an iso file onto my VM host server, to be used when creating new VMs.

Any help will be greatly appreciated

---

### Post by TheFu on 2014-02-06
After you put the ISO in the storage pool location, did you click "refresh?"

---

### Post by J Blain on 2014-02-07
Yes I did and I saw nothing yesterday. But curiously, this morning it is there and seems to be working very well. Thank you for your help it was much appreciated

---

### Post by TheFu on 2014-02-07
Please mark the thread as "solved" - seem my signature for directions.

---

