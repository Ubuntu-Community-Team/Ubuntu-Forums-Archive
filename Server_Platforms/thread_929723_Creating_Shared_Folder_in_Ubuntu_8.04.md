---
title: "Creating Shared Folder in Ubuntu 8.04"
date: 2008-09-25
forum: Server Platforms
---

### Post by Helix_Spear on 2008-09-25
Hi Guys,

I'm Trying to create a file server using Hardy Heron. I have installed it in my old dell PC. I manage to mount other NTFS partition using ntfs-3g. I have installed samba when i try to share one of the folder. In the end the folder is actually owned by root. Its not allowing me to share it out. I get an error: 

"net usershare returned error 255: net usershare add: cannot share path /media/downloads as we are restricted to only sharing directories we own."

Anyone there have any solution for this. Appericated alot for your help.

Regards

Helix

---

### Post by fjgaude on 2008-09-25
In Ubuntu, can't you simply change the root of the path, the folder to whatever you wish?

```
sudo chmod -R 755 /media/downloads
```

That changes the priority and this changes the owenership:

```
sudo chown -R user:user /media/downloads
```

Or something like that?

---

### Post by Helix_Spear on 2008-09-27
Hi Frank and all,

Thanks for your reply. I did tried the steps yet i am not able to change the permissions and ownership. Is there a way i can use terminal to share out my nfts partitions. Will be very helpful.

Regards,

Helix

---

### Post by baudday on 2008-09-27
Just to be sure, are you replacing user:user in the command
```
sudo chown -R user:user /media/downloads/
```
with your real username. For instance if your username was john you'd put john:john.

---

### Post by Helix_Spear on 2008-09-29
My user name is user itself. I did the steps accordingly in both mode sudo and in root in terminal.

---

