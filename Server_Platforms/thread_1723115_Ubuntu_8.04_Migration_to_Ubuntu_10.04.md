---
title: "Ubuntu 8.04 Migration to Ubuntu 10.04"
date: 2011-04-06
forum: Server Platforms
---

### Post by lightninhopkins on 2011-04-06
I've built a new server and wanted to migrate a site running on 8.04 to the new 10.04. 

I'm going to place the old drive as a 2nd drive in the new setup (sdb) and rsync directories over. 

I've never done this and I'm curious which directories I should NOT rsync. 

The server is running a basic LAMP setup, and prior to removing the old drive, MySQL, Apache, and PHP were upgraded to the latest versions. 

Any tips, tricks, or advice would be appreciated.


EDIT:

The new server install (not OS) was on a RAID on /dev/sda and the old standalone Ubuntu was /dev/sda

So I booted the new install to a rescue disk, and am in the process of doing a dd from the old drive to the new raid. Hope it works. Servers had the same guts.

---

