---
title: "&quot;Combine&quot; Hard drives in server?"
date: 2010-10-23
forum: Server Platforms
---

### Post by Phildough on 2010-10-23
So  I just set up my first linux server, using ubuntu server. I set it up on a 120 GB hard drive, which I soon found out to be too small for 6 college kids..
So we found another hard drive layin' around (80 GB) and plugged it in to the slave connector. It's accessible and mounts fine, but it's kind of annoying to have to select which hard drive you want to save anything to. 

Question:
Is there any way I can "connect" the hard drives so it treats the 120 GB and the 80 GB HDD as a single 200 GB HDD? If so, would it require removing and reinstalling everything?

---

### Post by psusi on 2010-10-23
I you installed with lvm, then yes, otherwise, no.

---

### Post by SeijiSensei on 2010-10-23
> **Phildough said:**
> Question:
Is there any way I can "connect" the hard drives so it treats the 120 GB and the 80 GB HDD as a single 200 GB HDD? If so, would it require removing and reinstalling everything?

Maybe.  The best solution would be to compress the Ubuntu installation on the 120 GB drive down to about 40GB with gparted.  Then you'll have two 80 GB partitions.  You can create a single 160GB filesystem using RAID0 or a mirrored RAID1 filesystem of 80GB.  The best place to mount the extra space is under /home so it will be available to all the users.

If you decide to reinstall, use the 80 as the boot drive, keep 60 GB free and combine it with the 120 using RAID0.

Frankly, though, if there are six of you, you should all just chip in and buy a large external HDD.  [Here are some examples]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007601+600030763&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=414&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=").

---

### Post by Phildough on 2010-10-23
Shoot- didn't use lvm :/

And yeah, I don't really want to go through the trouble of reinstalling/setting up/downloading everything that's already on it again... So looks like it's stuck as-is. 

Thanks anyways though! Good to know for future servers!

---

### Post by BkkBonanza on 2010-10-24
LVM is the most flexible way to do this but if that's not an option for now then careful choice of mount points can work. If you analyze where your disk usage is then usually you can find a convenient mount point that will "almost" work as if transparent.

For example, lets say you have a directory /torrents - you use,

**du -h --max-depth=1 /torrents**

to see where the big chunks of usage are and find music contains over 100GB... so you work out how to copy all the music to the second drive and then you can mount your second drive as /torrents/music. Now it looks as if one big mount.

This is just an example as the details will be specific to your own use and how the files are grouped. Just remember with linux a drive does not have to mount at root - you can mount your second drive down the file tree somewhere that it makes sense. eg. You can mount it as /home/joe and that drive will just have the stuff for joe. Usually in a pinch you can find an optimal mount point such that it all behaves as if one big drive.

---

