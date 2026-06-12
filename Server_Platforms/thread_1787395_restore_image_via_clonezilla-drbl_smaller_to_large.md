---
title: "restore image via clonezilla-drbl smaller to larger disk"
date: 2011-06-21
forum: Server Platforms
---

### Post by salento9 on 2011-06-21
Hello all,

 My question is:

 I have an Ubuntu server and i've installed drbl-clonezilla to clone and restore pc,
I have a 40 gigabyte image to be deployed on other pc's with larger hard drive  ex. 160 GB or 240giga, my problem is that when I deploy the image on a larger disk I end up with a disk with a partition of 40 GB and the rest unallocated,
 how can i restore the the disk  and use full disk space, the goal is to automate the process.

 In clonezilla-drbl there is the possibility to start a "prerun" and "postrun" fonction that could help complete the deployment process.

 Thank you in advance.

Salento

---

### Post by dannymagat on 2011-08-02
i am also having this issue...

from 8GB i am unable to maximize the disk space if i will 
restore it on 40GB.

How can use the maximum hardisk space. using clonezilla.

Thanks

---

### Post by aeiah on 2011-08-02
you'll have to write a script that'll grow the partition to the full size of the disk (or however big you want it), and set clonezilla to launch it on postrun.

you could use several command line apps in your script to perform the resize, but i guess gnu parted is a good place to start, specifically see the command: ```

parted help resize
```

---

