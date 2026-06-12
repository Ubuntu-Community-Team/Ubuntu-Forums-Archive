---
title: "RAID5 Windows to Ubuntu"
date: 2007-03-31
forum: Server Platforms
---

### Post by c8h10n4o2 on 2007-03-31
I have a RAID5 set up via HighPoint RocketRAID 1820A & SATA & Windows 2000. I have installed Kubuntu on the drive as step 1 for removing Windows from this box. I do not see my RAID array anywhere and the only instructions I find on the web are for setting up a new RAID array. I have a lot of data on this array and cannot loose it. On the other hand I really want to get Windows off this server. What am I missing? Why can I not see the existing RAID 5 array? This is a hardware RAID 5, not software.

Any help greatly appreciated.

---

### Post by elst on 2007-04-01
FWIW, there are Linux drivers and a management utility here:

[http://www.highpoint-tech.com/USA/bios_rr1820a.htm](http://www.highpoint-tech.com/USA/bios_rr1820a.htm)

---

### Post by c8h10n4o2 on 2007-04-01
Thanks. I saw that after I posted here and forgot to come back & post. I now need to purchase a floppy drive as I've not had one for 3 years.

---

### Post by va1ha11a on 2007-06-13
Did you get this working?...i am having all sorts of problems

---

### Post by c8h10n4o2 on 2007-06-13
I finally got the driver compiled and it still would not allow me to mount my RAID array without also formating. It touched one of the drives destroying the RAID so I had to go into Windows and rebuild the array. My final conclusion from all this is a project I'm in the middle of. I purchased enough hard drives to back up everything. I'm planning to format and set that RAID up from scratch. However, I'm not planning on using Ubuntu; I'm planning on using Fedora Core as it is more server based in general. I'm using Ubuntu on my desktop but don't think it is worthy of a true file server yet...... Windows may suck as a server but at least it works and can read my RAID. Working 60 hrs a week and having 3 kids, I don't have time to get it working with the downtime required. 

If you ever figure anything out let me know.

---

### Post by va1ha11a on 2007-06-13
I *Think * I got the driver compiled, but I cant figure out how to test it...my array is empty so I dont mind formatting

Will keep hacking away, any advice on testing the driver would be good.

---

