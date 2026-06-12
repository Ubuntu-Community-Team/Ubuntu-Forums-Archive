---
title: "Can virtual machines use the host file system?"
date: 2010-07-30
forum: Virtualisation
---

### Post by derryt on 2010-07-30
Hi all,
 
I'm looking to install Itunes in windows on a vmware player, but rather than fill up my windows VM effectively duplicating my music/videos etc.. between the host and guest, can I have the itunes folder point towards a folder to access all the music in my Karmic drive?
 
I'm assuming the answer will likely be no, and I can't use rhythmbox/amarok etc as I have an iphone and also need to store apps as well as music and videos.
 
Any advice gratefully received!
 
Also, since I've updated to the latest updates in Karmic my computer now hangs on shutdown and will not turn off- it goes through the shutdown process and then goes to a black screen and just stays there- any ideas?

---

### Post by philinux on 2010-07-30
Moved to the Virtualization forum.

---

### Post by Meow27 on 2010-07-30
the answer lies somewhere in shared folders... i dont know how to do that with vmware though

---

### Post by dcstar on 2010-07-31
> **Meow27 said:**
> the answer lies somewhere in shared folders... i dont know how to do that with vmware though

Shared folders have nothing whatsoever to do the the VM system, they are purely a function of the Host and Guest OSs.

There are already many posts on how to do this, including the ones at the top of this forum **that people should read first.**

---

### Post by Meow27 on 2010-07-31
> **derryt said:**
> Hi all,
 
I'm looking to install Itunes in windows on a vmware player, but rather than fill up my windows VM effectively duplicating my music/videos etc.. between the host and guest, can I have the itunes folder point towards a folder to access all the music in my Karmic drive?
 
I'm assuming the answer will likely be no, and I can't use rhythmbox/amarok etc as I have an iphone and also need to store apps as well as music and videos.
 
Any advice gratefully received!
 
Also, since I've updated to the latest updates in Karmic my computer now hangs on shutdown and will not turn off- it goes through the shutdown process and then goes to a black screen and just stays there- any ideas?
(change to an earlier kernel version? i think you have to mash f2 when grub is loading to get the list)
> **dcstar said:**
> Shared folders have nothing whatsoever to do the the VM system, they are purely a function of the Host and Guest OSs.

how so?! from the way your post reads, this is exactly what the OP was looking for! heare trying to access your music from an area on the host (karmic) and access it in a windows guest. in virtualbox this can either be a read only or read and write folder access. again dont know how to do it in vmware

---

### Post by dcstar on 2010-08-01
> **Meow27 said:**
> 
........
from the way your post reads, this is exactly what the OP was looking for! heare trying to access your music from an area on the host (karmic) and access it in a windows guest. in virtualbox this can either be a read only or read and write folder access. again dont know how to do it in vmware

Do people **EVER** read the posts at the top of this forum - ever?:

[http://ubuntuforums.org/showpost.php?p=6122148&postcount=5](http://ubuntuforums.org/showpost.php?p=6122148&postcount=5)

---

