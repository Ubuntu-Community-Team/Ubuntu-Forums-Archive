---
title: "Samba server - read only AND read/write"
date: 2007-12-04
forum: Server Platforms
---

### Post by jimzat on 2007-12-04
I am running an Ubuntu box (Feisty) within a Windows Domain environment and am having som difficulties setting up a Samba server.

What I'd like to do is allow anonymous read-only access to shared resources and ALSO allow certain users full-access.

At this point, I have been able to allow anonymous read-only access OR user based read-write access, but I can't figure out how to offer both simultaneously.

Is this possible?

jimzat

---

### Post by dfreer on 2007-12-04
I just struggled with this myself, so hopefully I can help you out.

Ok, basically, this is the relevent parts of my samba settings:
```
   
   security = user
   map to guest = Bad Password

[public]
        comment = Public Read-only Share
        path = /data/media/
        guest only = Yes
        guest ok = Yes

[private]
        comment = Private Share
        path = /data/media/
        write list = my_samba_username, @my_samba_username

```

Ummm, beyond this you need to create a samba user as normal, and I'm trying to remember, I think I had to create a samba user named "guest" and I had to map it to the linux user name "nobody".
You'll want to make sure that the files in the Public share cannot be written by the user "nobody", but readable.

---

