---
title: "Lack of disk space crashes GDM."
date: 2008-04-24
forum: Virtualisation
---

### Post by jingo811 on 2008-04-24
I tried VMplayer on a 13 GB partition where I have used up 6 GB for base install.  Then I downloaded a 1 GB *.vmx file and ran the virtualization.
First time I do this everything is OK.  But when I reset the VMplayer and do a hard reboot on the PC then I get a blue screen saying GDM Error because I have run out of disk space.

Previously I had 40% of my 13 GB free.  Now the partition seems to be filled up to 90%.  It might be the virtualization that's taking up all this working space if so then everything is probably normal.

But I want to consider the fact that something else is filling up my partition.  How should I proceed in order to trace what is filling up my harddrive so dramatically?  Where should I look?

---

### Post by fjgaude on 2008-04-24
I wonder, did you do a snapshot of the VM? My Windows install in vmware server takes up about 14GB. I do have a snapshot. I'm not sure if a snapshot is made automatically or not.

I've never had a VM that was less than 12 GB.

In a command line you can use **df -h** to see where things are.

There are other commands that don't come to mind that shows disk space.

---

### Post by jingo811 on 2008-04-24
> **fjgaude said:**
> I wonder, did you do a snapshot of the VM? My Windows install in vmware server takes up about 14GB.

Hmmm... then I guess it was all normal that I ran out of disk space from 40% used to 90% used so quickly within 20 minutes.  Leading me to crash my SuSE SLES test partition, guess I was living too dangerous by making 13 GB for SuSE I should've made 23 GB instead.

The instructor told us to make 10 GB extra room on the harddrive and I did so on by making another partition 13+10 GB = 23 GB (combined).
The proper way in retrospect was to make my OS's root partition 23 GB (single) total not combined.

---

