---
title: "2x Ubuntu on VMware, access disk drive"
date: 2011-01-10
forum: Server Platforms
---

### Post by JBtje on 2011-01-10
Greetingz,
 
I'm the proud owner of a new 1U server, thought dont really know how to handle the next problem.
The server runs VMWare ESXi 4.x and currently contains two virtual machines with Ubuntu server 10.04 installed on them. Both the virual machines have 50GB of Harddrive, thought one had another 1TB to use.
 
One of these virtual machines is going to be a fileserver (and has the 1TB for that reason) while the other machine is purely going to be used as webserver.
The system uses one harddiskdrive of 1.5TB (hardware raid 1 configured)
 
The fileserver will contain images, which should be shown on the webserver. Therefor I need to setup a link between the images directory on the fileserver, so it can be accessed by the webserver. Now this is one and the same harddisk, but the partition is only availeble in the fileserver.
 
How can i configure this directory, so it can be accessed by the webserver automatically (e.g. that I dont have to remount the directory, after the fileserver has been down for whatever reason)
 
My best regards,
Jeffrey
 
p.s. I'm pretty much new to Ubuntu.... :o

---

