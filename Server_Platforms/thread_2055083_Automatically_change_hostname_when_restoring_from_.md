---
title: "Automatically change hostname when restoring from Clonezilla."
date: 2012-09-08
forum: Server Platforms
---

### Post by darthpenguin on 2012-09-08
I set up a server with DRBL. I have saved an image of one machine which had a slightly-customized Ubuntu Desktop install. I want to deploy the image to over 100 machines. But I have a problem. Every system I restore from the image has the same hostname as the source machine. I understand that "cloning" a system means creating an *exact* copy of the source disk (including the hostname) but -- at the same time -- Clonezilla is specifically designed to deploy a standard image across multiple workstations. So it must have the capacity to change the hostname of each machine it restores. Or am I using the wrong tool for this task? How can I change the hostname of every machine I restore? I'm looking for an automated solution here. I have no desire to manually edit the hostname file of every machine.

---

### Post by DJ_Max on 2012-09-09
According to the website
> Due to the image format limitation, the image can not be explored or mounted. You can _NOT_ recovery single file from the image. However, you still have workaround to make it, read this.

So my guess is make a script that changes the hostname after all is done.

---

### Post by volkswagner on 2012-09-09
I would not know how to script this but a possible work flow could be like the following:


Prior to creating your Clonezilla image do the following on the host machine.
[LIST=1]
[*]Create a script for the hostname change, you could possible use [fixedname]+[last six digits of mac address] or use a similar way to create a unique name.
[*]create a script as a run once that calls the above script, add this new script to rc.local.  This script will call the first script >> then remove the rc.local entry so it does not run again.
[/LIST]

Just some ideas to get the brainstorm going.

Alternatively you asked about a different approach.  You could remaster .iso and create your own OEM install or possibly a seed file for the installer.

---

