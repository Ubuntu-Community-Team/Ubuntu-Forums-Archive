---
title: "vsftpd in VMWare problems"
date: 2012-11-22
forum: Server Platforms
---

### Post by Mikeee404 on 2012-11-22
I recently went from a physical server running Ubuntu Server 10.04, an old Pentium 4 machine to a trying a Virtual Server on my desktop. My desktop has a 6-Core AMD, 16GB of RAM, and 6TB RAID 10 Array. The server is now using Ubuntu Server 12.04 64bit. I allocated 2-cores and 4GB of RAM just for it. The server has no problems communicating via SSH and I have had no problems mapping Windows shared folders to it. The problem I am having is with a fresh install of vsftpd, using the same configuration setting I used on my old physical server, it will not connect to external clients. My network firewall has all of the necessary ports forwarded to it, the same ones used with the old server just had to adjust the IP used by the new server. I can establish a connection with the ftp client on my phone, but then I get an error saying the server had an unexpected error and closed the session. Nothing I try seems to change this. I am running a second pci-express network card with VMWare bridged to this  for a eth0. Has anyone heard of problems like this running a server in VMWare 9 or is this likely a config problem in the server itself?

---

### Post by Mikeee404 on 2012-11-22
Ok, just for the heck of it I installed 12.04 Desktop edition and installed Samba service and vsftpd, set the same exact settings in the corresponding config files as I had in the server platform.....odd thing happened.....it works. Not sure what the difference is at all, but until I sort out the issue I guess I will stick with that for the moment. Any input is still greatly appreciated.

---

