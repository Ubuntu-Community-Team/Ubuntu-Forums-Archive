---
title: "FTP and Samba on seperate NICs"
date: 2006-10-23
forum: Server Platforms
---

### Post by NewbieNik on 2006-10-23
Aaarrggghhh, help me please someone. Take me by the hands and lead me through the streets of Ubuntu...
I have:-
6.02LTS Desktop (Sorry, need Gnome as I'm a relative Newbie)
Samba, Swat, ProFTP and Firestarter from repository
Two NICs, Eth0 on External Network fixed IP Eth1 on LAN with DHCP
Firestarter restricting traffic on Eth0 to FTP only and allowing ALL traffic on Eth1 from specified IP ranges.

I can get ProFTPd working fine with GProFTPd and users can access through Internet connection to FTP folders with no issue.
I set up Samba and Bind to Eth1 and set share on FTP folders and the FTP drops off. Network starts using Eth1 as default gateway.

If I reconfigure the ProFTP to work again Samba shares dissappear. Please can some one help me to get both working through seperate NICs? Or am I being much too ambitious?

---

