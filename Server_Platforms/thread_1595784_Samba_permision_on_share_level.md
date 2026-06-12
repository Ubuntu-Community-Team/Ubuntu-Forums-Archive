---
title: "Samba permision on share level"
date: 2010-10-13
forum: Server Platforms
---

### Post by Sandy Malteser on 2010-10-13
Hey,

I'm trying to set up my samba server so that all the shares are visible to everybody but that some shares can only be accessed by certain users. I have a folder Video that everybody can access without a username or password. I now want to create a share that only i can access called webserver.

this is my samba.conf
```

[global]
    dns proxy = No
    netbios name = DATABOX
    guest account = nobody
    restrict anonymous = no
    browseable = yes
    server string = server
    workgroup = WORKGROUP
    public = yes
    security = share

[Video]
    writeable = yes
    path = /media/data/Video
    public = yes

[webserver]
    writeable = yes
    public = no
    user = malteser
    path = /media/data/Webserver

```

Windows does not let me enter a username or password. what am i doing wrong? i'm pretty sure this used to work

---

### Post by kgatan on 2010-10-13
I think what your looking for is ACL, Access client lists.
Im not sure how it works but i guess there are many google guides.

---

