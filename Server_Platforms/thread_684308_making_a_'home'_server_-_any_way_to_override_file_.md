---
title: "making a 'home' server - any way to override file permissions?"
date: 2008-01-31
forum: Server Platforms
---

### Post by zombiepig on 2008-01-31
I'm in the process of setting up a basic file server to serve to 2 laptops and a htpc. I can handle all the samba setup/etc that I need to do - but one thing i'm not sure of is if there is an easy way to automatically override file permissions when files are copied to the server.

For instance,
- My wife makes a file on her laptop, which will default to being owned by her and only giving read permissions to everyone else
- If she copies this file to a share on the server, i need it to overwrite it's current permissions with something like 777 - so everyone has read/write access to this file

Is this possible? How can I setup my server this way?

---

### Post by techstop on 2008-02-01
You don't need to worry about permissions, let the server handle that for you. Have a read of this thread;

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

In particular the section titled "Permanent Mount".

---

### Post by cdenley on 2008-02-01
If you want to give everyone read/write access to files and directories created on a particular share, add this to /etc/samba/smb.conf under [share_name].

```

create mask = 0666
directory mask = 0777

```

---

### Post by zombiepig on 2008-02-01
> **cdenley said:**
> If you want to give everyone read/write access to files and directories created on a particular share, add this to /etc/samba/smb.conf under [share_name].

```

create mask = 0666
directory mask = 0777

```

Thanks - that's exactly what i needed :D

---

