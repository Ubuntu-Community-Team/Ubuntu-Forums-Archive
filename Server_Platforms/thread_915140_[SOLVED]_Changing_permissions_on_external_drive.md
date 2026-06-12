---
title: "[SOLVED] Changing permissions on external drive"
date: 2008-09-09
forum: Server Platforms
---

### Post by baudday on 2008-09-09
So I connected one of those MyBook external hard drives (1 TB!) to my server. I would like for users to be able to upload and download files to and from it. The problem is I don't know how to do that. Even if I try gksudo dolphin and then try to change the permissions, when I click OK then go back to the permissions tab, they're just reverted again. I also can't create a folder within and change it's permissions, same thing happens. Does anyone know how I can achieve what I'm trying? I would really appreciate it.

Thanks

---

### Post by erwall on 2008-09-09
> **baudday said:**
> So I connected one of those MyBook external hard drives (1 TB!) to my server. I would like for users to be able to upload and download files to and from it. The problem is I don't know how to do that. Even if I try gksudo dolphin and then try to change the permissions, when I click OK then go back to the permissions tab, they're just reverted again. I also can't create a folder within and change it's permissions, same thing happens. Does anyone know how I can achieve what I'm trying? I would really appreciate it.

Thanks
Figure out where it's mounted open a terminal
```
cd /media
sudo chown -R someuser.someuser mountpoint
```

---

### Post by baudday on 2008-09-09
Thank you for the reply.

This is what I got back:
```
chown: changing ownership of '/media/disk': Operation not permitted
```

---

### Post by 47_MasoN_47 on 2008-09-09
I usually do
```
sudo chmod 777 -R /media/disk
```
I'm sure that's not the most secure way to do it, but I don't want permissions being screwy between all the different PCs that I use so it works best for me.

---

### Post by baudday on 2008-09-09
That doesn't give an error or anything, so I assume that means it worked. But when I view the permissions I still get only the user able to read and write and everyone else can only view

---

### Post by 47_MasoN_47 on 2008-09-09
Something I should have asked first, is the drive formatted in EXT3?

---

### Post by baudday on 2008-09-09
no it's FAT32

---

### Post by 47_MasoN_47 on 2008-09-09
Ah there's your problem.  FAT32 doesn't do permissions.  Format it (preferably to EXT3) and try it again.  Should work like a charm.

---

### Post by baudday on 2008-09-09
sorry, this could be stupid, but when i open gparted and go to that drive, it won't allow me to format it. is there something i need to do first.

---

### Post by 47_MasoN_47 on 2008-09-09
First you have to unmount it, then format it.  Then unplug the drive and plug it back in is the easiest way.  It should come up 1TB media on the desktop and then you should be able to chmod or chown it.

---

### Post by baudday on 2008-09-09
well I unmounted it, and it's formatting now, I assume that will take a while since it's quite large. but thanks a lot for the help!

---

### Post by 47_MasoN_47 on 2008-09-09
It probably won't take too long, gparted is pretty dang fast at formatting.  Glad that I could be of some help, I know how frustrating stuff like this can be!

---

### Post by baudday on 2008-09-09
okay cool. It successfully formatted. Unfortunately I'm doing this from school, so one of my parents is going to have to unplug it. I'll update on whether it's working.

---

### Post by 47_MasoN_47 on 2008-09-09
Ah ok, you should be able to mount it again using sudo mount, but I rarely ever use that and don't know the mountpoint or anything of that drive so I wouldn't begin to know how to do it that way.  I hope it all works out for you though!

---

### Post by baudday on 2008-09-09
got someone to do it on the other end and it works great. thanks

---

### Post by 47_MasoN_47 on 2008-09-10
Glad to know that it's working for you now.

---

