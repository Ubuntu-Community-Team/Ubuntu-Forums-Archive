---
title: "LVM setup"
date: 2011-01-18
forum: Server Platforms
---

### Post by Niels_Andersen on 2011-01-18
Thoughts on this...?
 My setup is like this (at the moment):
320gb sda
1tb sdb
1tb sdc
2tb sde

320gb sda:
250mb /boot, 1gb /swap, 8gb /root, 100gb /home, rest lvm (all except /boot is ext4)
sdb, sdc, sde is ext4 lvm.
This setup is my third or fourth try, still learning Linux/ubuntu :wink:, and i'm using Turnkey fileserver as my installmedia (basic ssh, webmin and other tools)

On one of my first tryouts i had 70-90mbps transfers over my lan, but with this setup i have only 30-50mbps transfers.

My guess is that the difference is that the fist install was a "total"  lvm (all drives at the same volumegroup(VG), and the /swap /root  /home and /data was logicalvolumes(LV) )

Could i be right on this assumption ?
I'm using this server as file/media server, and backups sit on another server.

---

