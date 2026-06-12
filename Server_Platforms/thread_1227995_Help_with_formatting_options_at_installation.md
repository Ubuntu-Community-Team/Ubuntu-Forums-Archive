---
title: "Help with formatting options at installation"
date: 2009-07-31
forum: Server Platforms
---

### Post by Alexanderfoto on 2009-07-31
When installing Ubuntu Server I get a couple of options on how I want to format my disks, and I'm unsure on which option suits me the best.

I have a Dell Poweredge 2900 iii. There are 6x1TB SAS drives installed. When I installed Ubuntu I went for the recommended use "Use entire disk with LVM". 

Two of the 6 disks are set up with Raid 1. The rest are plain. 

It seems like Ubuntu is having trouble recognizing the other disks. Does anyone have any formatting tips? 

Thank you very much. I've been Googling it but this is a server we need to get up fast and I'm a little over my head so I'm looking for quick help.

Once again, thanks.

---

### Post by Macchi on 2009-07-31
LVM and RAID are different things and can be used together. It depends on your goals and application areas. Beware of a risk for a steep learning curve maintenance of that system.
 
* How/where are you going to use the (mirrowed) RAID 1? 

* LVM will let you gather all those 1TB disks into one large virtual partition, for instance one unit with 6TB of continuous space.


SUGGESTION: If the server is for a production environment you could use RAID 5. It would give you a large partition that is both fast and very reliable.  

Eventually you could add LVM on top of that, but it complicates things for a just fast system installation ...

---

