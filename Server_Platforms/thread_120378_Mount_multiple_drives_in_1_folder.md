---
title: "Mount multiple drives in 1 folder?"
date: 2006-01-21
forum: Server Platforms
---

### Post by MetalMusicAddict on 2006-01-21
Im putting together my server and Im wondering if there is a way to make seperate physical drives mount in 1 folder? Or mount them so as they *look* to be 1 drive/folder. I want to do this so sharing them is easier.

_example:_
I have video spread out over multiple drives. If I could mount them in 1 folder called "Video" I could just share that folder on the network and have access to everything without having multiple shares leading to all my video.

---

### Post by localzuk on 2006-01-21
I think the easiest thing would be to mount them as subdirectories of one spot. For example, I have a directory /multimedia and then 3 other hdd's mounted as /multimedia/video /multimedia/audio /multimedia/images

I then share /multimedia and everyone can get to all 3. The other solution would be to create a raid array of the drives you wish to use together (which involves wiping them) and then mounting the array at one point - but I don't think this will be what you will be looking for.

---

### Post by spectre_25gt on 2006-01-23
Another problem with doing raid is that budgetary considerations would probably make you look toward raid 0 which is inherently unsafe. If one drive dies then all of your data is gone. Also, the drives should be the same size (some would say same model) for raid 0.

---

### Post by Glut on 2006-01-23
[QUOTE=MetalMusicAddict]Im putting together my server and Im wondering if there is a way to make seperate physical drives mount in 1 folder? Or mount them so as they *look* to be 1 drive/folder. I want to do this so sharing them is easier.[/QUOTE]

As above, you can RAID 0 or RAID JBOD (Just a Bunch of Disks). JBOD has the advantages that you can use disks with differing sizes and if one drive fails you [i]may[i] be able to recover some of the data from other disks. 

I personally feel that the safest option is that of the original reply and mounting sub-directories.

---

### Post by superm1 on 2006-01-24
You may also want to look into LVM (Logical Volume Management).  Its setup very similar to JBOD, but easier to add several drives to the mix as needed and dynamically remove as needed.  I use 5 drives for my mythtv setup all mount at one mount point this way.

---

