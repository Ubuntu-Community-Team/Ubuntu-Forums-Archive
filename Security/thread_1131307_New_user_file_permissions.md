---
title: "New user file permissions"
date: 2009-04-20
forum: Security
---

### Post by Ravey Dave on 2009-04-20
Hello all, can someone tell me why, when my users can acces each others files.  If I create two users test1 and test2, test2 can read test1 files.  This shouldn't be, it dosen't happen with redhat.

I tried changing the umask from 022 to 027, to see if this would make a difference, it didn't.

How can I change the default permissions on users home folders, so no other user can access them.

TIA Ravey Dave.

---

### Post by brian_p on 2009-04-20
> **Ravey Dave said:**
> 

How can I change the default permissions on users home folders, so no other user can access them.

[http://ubuntuforums.org/showthread.php?t=1125327](http://ubuntuforums.org/showthread.php?t=1125327)

---

### Post by Ravey Dave on 2009-04-20
I'm sorry that was really badly worded request.

I know how to change permissions, what I want is that when I create a user the permissions are already set, so I don't have to change them. I'd like the permisions for the home folder to be RWX for owner, RX for group, and nothing for everyone else.

Thanks for your help though.

Ravey Dave.

---

### Post by brian_p on 2009-04-21
> **Ravey Dave said:**
> 

I know how to change permissions, what I want is that when I create a user the permissions are already set, so I don't have to change them. I'd like the permisions for the home folder to be RWX for owner, RX for group, and nothing for everyone else.

```
sudo dpkg-reconfigure adduser
```

But you may want to read about the DIR_MODE option in

```
man adduser.conf
```

---

### Post by Ravey Dave on 2009-04-21
Brian_p, what a star, adduser.conf was just what I wanted. I'm not a Ubuntu man, my distro is redhat.  I was researching this for someone on another forum.  Thanks for your help.

Regards Ravey Dave

---

