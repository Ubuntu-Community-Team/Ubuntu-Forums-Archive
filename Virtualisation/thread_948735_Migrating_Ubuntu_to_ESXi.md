---
title: "Migrating Ubuntu to ESXi"
date: 2008-10-15
forum: Virtualisation
---

### Post by self-defence on 2008-10-15
Hi,

I have got a HP ProLiant ML350 G5 server that I've been running Ubuntu on for the past 5 months as a web server. But I would now like to install VMWare ESXi on the server and have the Ubuntu run as a guest. But in order to install ESXi I'll need to delete the current Ubuntu from the server and re install. 
Anyone have any pointers on what I can backup in order to make the new installation more easier.
The main thing I have running is Apache with PHP support and a MySQL database that I wouldn't want to corrupt. And a Samba server but that's nothing special.

Any suggestions or tips on what I should watch out for and do so that I have the least work with reinstalling the guest Ubuntu and have it working in the shortest possible downtime.

Thanks for the help.
Bye

---

### Post by self-defence on 2008-10-20
Hi,

I'm pleased to report that the migration went of without a hitch.

Bye

---

### Post by ZooDirt on 2008-12-15
I'm looking at doing the same thing.  I could go back and learn how to do this all again, but if there is a way to avoid rebuilding everything that would be good.

Do you have any pointers?   I'm not an expert, but I have an AMD64 running CopperMine, MySql, Ushare, Samba, and various other things I can't really remember right now. My goal is to have my file/web/media server up and running and available, yet still be able to tinker with other installations.  

Any advice would be greatly appreciated.  Thanks!!!

---

### Post by self-defence on 2009-02-13
Hi,

I don't know if this is still relevant for you, but anyway.
The whole setup is still working very nicely. There are 8 VMs running, an ubuntu web server (www,php,mysql,mail), a development ubuntu web server, a freebsd as a gateway, a domain controller, a freebsd as a smb/nfs server and an IP telephony gateway system. The whole thing is working grate it. All of the VMs have almost the same uptime as the VM Server and it was rebooted only after installation and once again to test if all the VMs start automatically and never again. 
Actually the only thing I don't like about the ESXi is the administration that can only be installed on a Win machine and I have to reboot into a win system to administer the server. I hope they'll make something for linux soon.
I'll be happy to provide any other help or information, just tell me what you'd like to know.

Bye

---

### Post by tatster on 2009-07-02
Self-Defence,

Did you convert your existing install to a Virtual machine first in some way?  What steps did you need to go through?

Or did you scrap it all and start again from scratch?

Thanks,

Anthony

---

