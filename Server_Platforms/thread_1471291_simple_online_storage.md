---
title: "simple online storage"
date: 2010-05-03
forum: Server Platforms
---

### Post by nicesites on 2010-05-03
Here's my scenario, I've looked and haven't found a tutorial on it.

I replaced my old desktop with a new one. Now, I beefed it up when I had it and here are some specs:

P4 2.53ghz
2GB rAm
160Gb HDD/ 200GB HDD
256MB Radeon 9000 series (*9350 I THINK)


Ok, now seeing as it isn't "dying" and still runs windows XP Vista, 7 and ubuntu fine I just don't want to throw it out. I want to make a Dropbox out of it. 260GB of online storage would beat just about whatever else is out there. 

Would this be easy to accomplish? I'd rather not have a monitor hooked up to it, just a box with deep pockets I can store files and or videos/pictures on.

You don't have to answer this just point me where I need to go

---

### Post by cariboo on 2010-05-04
The easiest way would be to create a file server and install openssh-server. The setup the private keys using [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") howto. The portforward port 22 to your router. 

Once that is done, from outside your home network open nautilus and type in the location bar:

```
sftp://user@external_ip_address
```

where user is your username and external_ip_address = your exteranl ip address.

---

