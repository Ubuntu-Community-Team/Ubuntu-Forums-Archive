---
title: "Media Server Problem"
date: 2007-10-23
forum: The Cafe
---

### Post by Black Mage on 2007-10-23
I am currently trying to set up a media server in Ubuntu and I've used the following tutorial:

[http://rubbervir.us/projects/ubuntu_media_server/](http://rubbervir.us/projects/ubuntu_media_server/)

Everything works fine except at the end when I try to add users using

```

root@dixon-server:/home/administrator# smbpasswd -a system_username
New SMB password:
Retype new SMB password:
Failed to modify password entry for user system_username

``` 

I can see the my folder in the directory but I just can't log into it and I can't modify the users. Can anyone help me?

---

### Post by tbroderick on 2007-10-23
Try putting single quotes around 'username'.

---

### Post by n3tfury on 2007-10-23
> system_username = "network username"

^

---

### Post by Black Mage on 2007-10-23
No, it still doesn't work.

---

### Post by n3tfury on 2007-10-23
without the quotes?

---

### Post by Black Mage on 2007-10-23
Yea, I've tried no qoutes, single qoutes, and double qoutes and they all fail for some reason.

---

### Post by n3tfury on 2007-10-23
so you've done this, but with your USERname?

```
root@dixon-server:/home/administrator# smbpasswd -a n3tfury
New SMB password:
Retype new SMB password:
Failed to modify password entry for user n3tfury
```

---

### Post by Black Mage on 2007-10-23
Ok, I did

```

root@ dixon-server:/home/administrator# smbpasswd -a Administrator
New SMB password:
Retype new SMB password:
root@dixon-server:/home/administrator# 

```


And that worked. How about adding other users besides the Administator? How can I do this?

---

### Post by n3tfury on 2007-10-23
sorry, man, i'm not sure.  it looks like you can only add users that have an account on that box, so create other users in users and groups?

---

