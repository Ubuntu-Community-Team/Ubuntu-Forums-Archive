---
title: "Virtualization - I want to tie the ends...."
date: 2008-08-11
forum: Virtualisation
---

### Post by ProgramErgoSum on 2008-08-11
Hi,
The following are the steps (based on quite a good deal of study on the net) I would like to follow. Please correct me wherever I am wrong.

Let me begin from the scratch - literally.

Suppose, I have a old desktop with a PII processor. The aim is to make this a web server with several VMs that will share the load of the web server. The names of s/w below can be different but essentially the following types are required.

[LIST=1]
[*]Install OS [Ubuntu Server Edition]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").
[*]Does the processor support Virtualization ? Use code below. If messages are displayed, then install [Xen]("https://help.ubuntu.com/community/Xen") or [VMWare]("http://www.vmware.com/"). Else.... (This is where my confusion begins...I don't know if [QEMU]("http://en.wikipedia.org/wiki/QEMU") etc. are the answers here.)
```
grep '(svm|vmx)' /proc/cpuinfo 
``` 
[*]Install other VMs (if Linux only) either [JeOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") or [Damn Small Linux]("http://www.damnsmalllinux.org/") or etc.
[*]For load balancing, use [Linux Virtual Server]("http://www.linuxvirtualserver.org/") and [Heartbeat]("http://www.linux-ha.org/Heartbeat").
[*]Manage the VMs with [Google's Ganeti]("http://code.google.com/p/ganeti/").
[/LIST]

Thanks,
N.

---

### Post by LowSky on 2008-08-11
I seriously doubt that a P2 can handle the kind of load you are looking to get out of it? For what reason do you need to run several VM's. why can't you do the processes from one server? And Finally its a P2, the top model didn't run any faster than 450Mhz, I doubt it can handle very much

---

### Post by ProgramErgoSum on 2008-08-11
Hi,
> I seriously doubt that a P2 can handle the kind of load you are looking to get out of it?
That's exactly kind of information, I seek. I keep coming across bits of (high quality) information wrt virtualization, but, I do not know how to "connect the dots."

Anyway, my intention is still to have a web server (Apache httpd) with atleast one more VM hosting the webserver as a failover. Ignoring PII part, would you think the other steps I mention are correct ?

---

### Post by Vivaldi Gloria on 2008-08-11
> **ProgramErgoSum said:**
> Suppose, I have a old desktop with a PII processor. 

Don't forget that Ubuntu Server Edition requires a minimum of 128Mb of RAM

---

### Post by ProgramErgoSum on 2008-08-11
Ok, let us just ignore the PII part.

Can you please tell me if the steps I mention in my first post in this thread are correct ?

---

### Post by cariboo on 2008-08-11
If your system fails a vm is not going to keep running, as a vm needs a running system to work, you would be better off finding another computer to use as a back up server. A P2 will work ok if you are serving static pages. it will take quite a bit of load to stop your server dead if you are serving static pages. As a point of interest, I've been fooling around with a 400Mhz celeron that started out with 96MB ram, it served static web pages quite well, but as soon as I installed gallery2 and tried viewing the picture gallery , it slowed to a crawl.I upped the ram to 128MB, it helped a little, but it is not something I would even consider to put into production.

Jim

---

### Post by ProgramErgoSum on 2008-08-11
Thanks, Jim.> 
If your system fails a vm is not going to keep running, as a vm needs a running system to work, you would be better off finding another computer to use as a back up server.

ah, yes, of course. Silly of me to suggest that.

Can you please tell me how to get virtualization done when the CPU is not enabled for it ? Should QEMU be used ?

---

### Post by mlentink on 2008-08-11
> **ProgramErgoSum said:**
> 
Can you please tell me how to get virtualization done when the CPU is not enabled for it ? Should QEMU be used ?

Only a few modern CPUs were designed with virtualization in mind. My Core 2 Duo wasn't, not really. But virtualization works nonetheless. I run VirtualBox quite happily on it, for those occasions customers require me to work in a MS environment. 
Although the reqs are more modest for a web server, the MS experience has taught me to look carefully at the amount of RAM to be able to run the VM effectively.

---

### Post by bodhi.zazen on 2008-08-11
> **ProgramErgoSum said:**
> Hi,
The following are the steps (based on quite a good deal of study on the net) I would like to follow. Please correct me wherever I am wrong.

Let me begin from the scratch - literally.

Suppose, I have a old desktop with a PII processor. The aim is to make this a web server with several VMs that will share the load of the web server. The names of s/w below can be different but essentially the following types are required.

[LIST=1]
[*]Install OS [Ubuntu Server Edition]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition").
[*]Does the processor support Virtualization ? Use code below. If messages are displayed, then install [Xen]("https://help.ubuntu.com/community/Xen") or [VMWare]("http://www.vmware.com/"). Else.... (This is where my confusion begins...I don't know if [QEMU]("http://en.wikipedia.org/wiki/QEMU") etc. are the answers here.)
```
grep '(svm|vmx)' /proc/cpuinfo 
``` 
[*]Install other VMs (if Linux only) either [JeOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") or [Damn Small Linux]("http://www.damnsmalllinux.org/") or etc.
[*]For load balancing, use [Linux Virtual Server]("http://www.linuxvirtualserver.org/") and [Heartbeat]("http://www.linux-ha.org/Heartbeat").
[*]Manage the VMs with [Google's Ganeti]("http://code.google.com/p/ganeti/").
[/LIST]

Thanks,
N.

First, I think the real question is what do you want to accomplish with virtualization ? Once you identify that, then ask what is the best tool for the job.

Second, see the sticky at the top of this forum, it discussed several options ...

Third, at least on the low end machines, I suggest apache or lighttpd, both will handle virtual web pages without the over head of virtual machines.

Essentially you put your sites in /var/www

/var/www/site1.com/httpdocs
/var/www/site2.com/httpdocs

The define your sites in the config files (exact syntax varies with server). Viola, two separate sites running in 1 instance of apache/lighttpd.

For what you are describing, if you want to go with virtualization, I suggest OpenVZ.

QEMU is very very slow and I would not consider it an option. VMWare Server comes with a web interface to manage you machines.

Proxmox : [http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

Promox is a debian install + KVM + OpenVZ + a web interface.

KVM is hardware virtualization and unless you have a more modern CPU is not an option.

---

### Post by ProgramErgoSum on 2008-08-17
Sorry...I was away for some personal engagements.

Hi bodhi.zazen,
My main aim is to have a web server that would handle heavy traffic (not upto the slashdotted level, though !). Apart from what you mention below (and, thanks for that !) I thought, a virtual machine would have been the answer.
> Essentially you put your sites in /var/www

/var/www/site1.com/httpdocs
/var/www/site2.com/httpdocs

The define your sites in the config files (exact syntax varies with server). Viola, two separate sites running in 1 instance of apache/lighttpd.

However, I have a few more nagging questions in my mind. I think, I will open a new thread (after doing some more reading) than hi-jacking the discussion here.

Thanks everyone !

---

### Post by bodhi.zazen on 2008-08-19
[ProgramErgoSum]("http://ubuntuforums.org/member.php?u=641859") : It all depends on what you wish to accomplish with virtualization.

If you want an isolated server, with low overhead, I like OpenVZ.

---

### Post by ProgramErgoSum on 2008-08-20
Hi bodhi.zazen,
Right now, my only intention is to "experiment". The "web server" thing was probably not a good idea. Let me do some more reading and come up with a "better experiment".

Thanks again !

---

