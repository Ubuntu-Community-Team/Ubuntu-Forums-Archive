---
title: "SAMBA fails to accept 'some' domain clients"
date: 2016-10-07
forum: Server Platforms
---

### Post by terryls714 on 2016-10-07
I did review similar questions. No real solution. SAMBA 3.4.7 Ports 137 and 139 are open. smb.conf has bind interfaces only &#8211; No Restarted the smbd and nmbd services Rebooted the SAMBA server.
From a Windows machine connected to the domain and a new install of Ubuntu on another machine, What you CAN do: Map a drive to the server (net use) and view files/folders 'See' the server in the network list SSH in to the server. What you CAN'T do: In Windows Explorer, see the server but can't click on the server to get a list of directories. (on some systems the server is does not show up) Add new machines to the SAMBA server domain. The server is available to 15-20 people as a default map.bat file maps their drives. Is there a specific log in /var/log/ that might pertain to this? smbd.log or nmbd.log ? ...there is also log.smbd and log.nmbd confusing. Thank you askubuntuers for viewing.

---

