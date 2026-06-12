---
title: "Hyper-v &amp; Ubuntu 11.04"
date: 2011-07-04
forum: Server Platforms
---

### Post by mjo1989 on 2011-07-04
Hi all,

Having a few issues installing Ubuntu ver 11.04 on a Hyper-V platform. 

I've managed to install it without any problems, everything seems to be working apart from networking. It managed to get an IP address from my DHCP server but I can't access or ping anything else on the network. 

There were no errors during installation and ifconfig shows the adapter has all the correct details and under RX packets it shows thousands of dropped packets.

Have tried a few clean installs and each time the same thing happens,  tried setting static IP's and restarting the networking service etc.. without any luck.

Has anyone come across this before?

Many Thanks

---

### Post by arrrghhh on 2011-07-04
Have you tried VirtualBox?

I doubt you'll get a lot of Hyper-V help here, sorry.

---

### Post by Gyokuro on 2011-07-04
Not a lot of experience with Windows but have a look here: [http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx](http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx)

maybe it helps - however it's better you post your question on [http://social.technet.microsoft.com/Forums/en-US/windowsserver2008r2virtualization/threads](http://social.technet.microsoft.com/Forums/en-US/windowsserver2008r2virtualization/threads)

as I have only knowledge the other way round: Linux is hosting Windows :-)

---

### Post by rubylaser on 2011-07-04
We've tried Ubuntu Server 10.04 (not as well supported as 10.10) on Hyper-V at work (you need to load some kernel modules to get it working), but frankly, it's slow, and breaks the virtual just about every time we try to update it.  I'd much rather go with ESXi or Proxmox for my Ubuntu Virtualization platform.  Here are some newer directions, and basically what I did to get ours working.

[http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx]("http://blogs.msdn.com/b/virtual_pc_guy/archive/2010/10/21/installing-ubuntu-server-10-10-on-hyper-v.aspx")

---

### Post by spynappels on 2011-07-05
I've also had major problems getting any flavour of Ubuntu Server to work well with Hyper-V, so much so that I ended up installing Virtual Box on the Win2k8 server I was working on. 

Sorry I can't be of more help....

---

### Post by mjo1989 on 2011-07-05
Took a while but eventually got it working with the LTS version. All working well now. :P

---

### Post by rubylaser on 2011-07-05
I hope 10.04 LTS works better for you than it did for my company.  We ended up abandoning it, because of the random read only filesystems that happened, and the subsequent fscks that needed to be done to fix them.  Not exactly desirable behavior for a production virtualization platform.

---

### Post by kevinthecomputerguy on 2011-07-05
I second Ruby Lasers ProxMox and ESXi suggestion. Install ProxMox, then treat the ProxMox box like a normal linux box, login via ssh, install samba and webmin, and have the best of both worlds.
 
ESXi is amazing!!!, but with a little reading and a little extra effort, ProxMox can do everything ESXi does.
 
-Kevinthecomputerguy

---

