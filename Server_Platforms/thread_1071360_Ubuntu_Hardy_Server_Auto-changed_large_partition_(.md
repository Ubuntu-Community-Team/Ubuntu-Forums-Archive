---
title: "Ubuntu Hardy Server: Auto-changed large partition (~4TB) after reboot"
date: 2009-02-16
forum: Server Platforms
---

### Post by mkrentovskiy on 2009-02-16
Hi,

I have AMD x86-64-based server with Ubuntu Hardy (Linux 2.6.24-19-openvz) anf large RAID0 disk with one partition ~4TB (ext3fs). This partiton was created by gnu-fdisk and working fine, but when I reboot the server, its auto-resize to 2T (like something write partition table on disk). Of couse its very unpleasent because I must recover it by hand every time. 

How can i fix it? May by some GRUB params?

WBR
Max

---

