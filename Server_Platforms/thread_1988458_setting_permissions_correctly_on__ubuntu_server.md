---
title: "setting permissions correctly on  ubuntu server"
date: 2012-05-27
forum: Server Platforms
---

### Post by badperson on 2012-05-27
Hi,
I did the version upgrade to my home ubuntu server in march, and since then have been unable to write to my samba share from other machines, and I've been unable to have a webapp I wrote write files to a shared folder. 

I get this from uname -a

> Linux ubuntu-server 3.0.0-14-server #23-Ubuntu SMP Mon Nov 21 20:49:05 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


Here are the permissions to one of the folders (in a folder shared by samba) I'm having trouble with: 
> 
drwxr-xr-x  3 nobody nogroup    4096 2011-03-27 12:45 app_data



here is what I have in my smb.conf file 
(btw, there was a conf file in two places...I added the following text in both: 

> [share]
        comment = Shared Drive
        path = /media/share
        browsable = yes
        guest ok = yes
        read only = no
        create mask = 0775
                            


What changed in the recent version of ubuntu server, and can you point me in the right direction in terms of how to set up the permissions correctly?

thanks!
bp

---

### Post by badperson on 2012-05-27
btw... chmod is not having an effect

---

### Post by Haneef Mubarak on 2012-05-27
How about:```
sudo chmod filename] 777
```

---

### Post by Morbius1 on 2012-05-27
> **badperson said:**
> btw... chmod is not having an effect
What do you mean chmod is not having an effect? It doesn't change permissions - like it's an ntfs partition. Or changing permissions doesn't resolve the problem.

What are the permission of /media/share ?

---

### Post by badperson on 2012-06-02
Hi,
I think it's actually not a permissions issue. I ssh'd into the machine and tried to create a folder using sudo mkdir, and got a message saying it couldn't create a file on a read-only system. 

[This post]("http://ubuntuforums.org/showthread.php?t=1857746") describes a similar issue. Looks like I need to verify my hardware is all ok and drives are mounted correctly.

---

### Post by oldos2er on 2012-06-02
Moved to Server Platforms.

---

### Post by SeijiSensei on 2012-06-02
If it's the root filesystem (the one mounted as /) that's read-only, follow the steps [here](http://ubuntuforums.org/showpost.php?p=11838980&postcount=21).

---

