---
title: "Public SAMBA share for video access"
date: 2011-08-04
forum: Server Platforms
---

### Post by Juggler00 on 2011-08-04
I'm running Ubuntu Server 10.04 and have just installed and tried to get SAMBA working. My goal is to create a share that can be mounted by my WD Live TV to play .iso.

In /etc/samba/smb.conf, I've added the following 2 listings at the end and made no other changes to the default:
```
[share]
    comment = Ubuntu File Server Share
    path = /home/shared/video/iso
    browsable = yes
    guest ok = yes
    read only = yes
    public = yes

[share_tmp]
    comment = Ubuntu File Server Share
    path = /tmp/shared
    browsable = yes
    guest ok = yes
    read only = yes
    public = yes
```

The corresponding permissions are:
```
shamus@EkonServer:/home/shared/video/iso$ ll
total 23865656
drwxrwxr-x 2 nobody nogroup       4096 2011-07-30 21:42 ./
drwxrws--- 6 shamus shared        4096 2011-07-30 20:13 ../

shamus@EkonServer:/tmp/shared$ ll
total 132896
drwxrwxr-x 2 nobody nogroup      4096 2011-08-02 22:04 ./
drwxrwxrwt 6 root   root         4096 2011-08-04 06:37 ../
```

I am able to mount and browse /tmp/shared, but /home/shared/video/iso is not working. Can anyone offer any insight?

cheers,
   J.

---

### Post by Morbius1 on 2011-08-04
/home/shared/video/iso has the following permissions:
> drwxrwxr-x 2 nobody nogroupThat's fine and it will allow remote guests to access the share.

/home/shared/video has the following permissions:
>  drwxrws--- 6 shamus sharedThe last three "---" is what the remote guest can do and that's nothing. The remote guest is not allowed to get to the "iso" folder so you can either change permissions:
```
sudo chmod 775 /home/shared/video
```[COLOR=Blue]***EDIT: Sorry didn't see the "s" in the original permissions:***[/COLOR]
```
 sudo chmod 2775 /home/shared/video
```
Or change the remote guest to shamus:
> [share]
    comment = Ubuntu File Server Share
    path = /home/shared/video/iso
    browsable = yes
    guest ok = yes
    read only = yes
**[COLOR=Blue]    force user = shamus[/COLOR]**
    public = yesOr change the remote guest's group to shared
> [share]
     comment = Ubuntu File Server Share
     path = /home/shared/video/iso
     browsable = yes
     guest ok = yes
     read only = yes
 **[COLOR=Blue]    force group = shared[/COLOR]**
     public = yes

---

### Post by Juggler00 on 2011-08-04
That did the trick... thanks!

---

### Post by maverickaddicted on 2011-08-05
Help me with this

[http://ubuntuforums.org/showthread.php?t=1813689](http://ubuntuforums.org/showthread.php?t=1813689)

---

