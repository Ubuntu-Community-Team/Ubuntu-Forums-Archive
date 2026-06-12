---
title: "Securing /home"
date: 2008-02-01
forum: Server Platforms
---

### Post by Uzelth on 2008-02-01
Heya,

What's the best way to go about making /home unreadable to normal users (except in their own home directory, of course)? Something as simple as chmod 0600 /home ?

---

### Post by Miademora on 2008-02-01
By default users are only allowed to read their own homedirectory.

---

### Post by Uzelth on 2008-02-01
Hmm,  I've just been able to see everything in /home and cat a file from another users home directory from a standard user account :\

---

### Post by cdenley on 2008-02-01
I think the command you want is
```

sudo chmod -R o-rx /home/*

```

This will allow only the user and the user's group to read files from everyone home directory. However, this will not affect files and directories created after you run the command. I think you want to change the umask in /etc/profile. Change "umask 022" to "umask 027". This will affect all files create by everyone, not just their home directory.

---

### Post by Uzelth on 2008-02-01
That's *almost* what I need...

I tried that, now lighttpd returns ISE 500 errors all the time :\

---

