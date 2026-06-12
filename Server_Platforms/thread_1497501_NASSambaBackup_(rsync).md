---
title: "NAS/Samba/Backup (rsync)"
date: 2010-05-30
forum: Server Platforms
---

### Post by AoDZelda on 2010-05-30
Is there really a difference between any of these? If so, what are the key differences?

I'm looking to build a server to share files and backup. I would like to share files on the LAN and be able to share over the WAN. Also between Linux, MacOS and Windows machines.

Is Samba server only for sharing files that are on the LAN? If I needed to use the WAN, would I create a VPN or SFTP server for users outside the LAN?

In creating a VPN server, total users simultaneously could be 5. I have a router that will support VPN tunneling using the DD-WRT firmware.

These are some of the basic questions I have at this "planning" stage. I have many more to come if I can get some assistance with what method(s) would be the simplest and the most efficient in creating a server. 

Thanks in advance. (I tried to give you the most information needed in determining my plan for the server)

---

### Post by AoDZelda on 2010-05-30
The next series of questions would be involving hardware. (which I have specs for) and then whether to use physical or vms to accomplish this.

---

### Post by Vegan on 2010-05-30
Depending on the amount of data will dictate how much storage is needed on the replication server.

If you have the bandwidth then you can use anything within reason to act as a rsync target.

---

