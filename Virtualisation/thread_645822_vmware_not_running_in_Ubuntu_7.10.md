---
title: "vmware not running in Ubuntu 7.10"
date: 2007-12-20
forum: Virtualisation
---

### Post by Daniao on 2007-12-20
Hallo,

I have an Ubuntu system recently upgraded to 7.10 running on a IBN ThinkPad t43.

I have installed vmware, gone through all configuration steps, compiling the module for my kernel etc ...

But when I click on the vmware icon, or simply type vmware on a console, nothing happens.

Any idea ?

Regards

Daniel

---

### Post by alexdbkim on 2008-01-21
have you checked your process list? If there is no process of vmware or vmnet, then I think you should reinstall vmware again.

Cheers,

---

### Post by dpj23 on 2008-01-21
Required Configuration Changes
Configuration with vmware-config.pl is required in the following circumstances:

1. when you install VMware the first time.
&#56256;
2. when you upgrade your version 
&#56256;
3. when you upgrade your host operating system kernel. (It is not necessary to
reinstall Workstation after you upgrade your kernel.)
&#56256;
4. To reconfigure the networking options for Workstation—for example, to add or remove host&#8208;only networking.

---

### Post by RU-In? on 2008-02-03
Hi, I ran across this thread looking for a solid solution to my problem. I found one here in some google group thread 

[http://groups.google.com/group/comp.os.linux/browse_thread/thread/fb091e68458ca1b0]("http://groups.google.com/group/comp.os.linux/browse_thread/thread/fb091e68458ca1b0")

My problem is that every time I reboot my system (not often though) I have to re-run the vmware-config.pl (as sudo of course). for some reason the conif gets messed up, appearantly from the etc/inet.d/vmware file (I was told of this at the linux-fest back in Sept '07), but am just now getting around to fixing it. You can confirm..., if you click the vmware from the menu and nothing eventually happens...then try from a terminal, '$ vmware' or '$ vmware-server' and you may get the message I get, "vmware not configured..." something like that, and it instructs you to run 'vmware-config.pl'. If the vmware-config.pl comes back with a 'cannot stop all virtual services' then you can 'kill' them w/ the process manager, and then re-run 'vmware-config.pl'. But I am looking for a little more before I change the init.d script, although the post from the link above sounds just like what another nixer @ the linux-fest said would be the fix. Good Luck

---

