---
title: "Auto start a program as a user"
date: 2008-04-02
forum: Server Platforms
---

### Post by lucaspr on 2008-04-02
In a server enviroment (Home server) 

I've succesfully installed Zimbra and configured Fetchmail (with crontab).  The only thing that doesn't work is SABnzbd. Which has to be run as a user, not as root. 

I've set up samba in such a way that all users are forced to be the user 'luuk' . Now I need SABnzbd to run as user luuk to run properly. 

I've done some searching and found a bunch of topics which do auto start programs... as an user.... in a X enviroment.. Which I don't have. Now to start a program and maybe even auto login a user...

Could someone please help me out here?
And I hope my question is clear!

---

### Post by cdenley on 2008-04-02
If you just want to run a command as luuk...
```

sudo -u luuk anycommand

```
If this is run as root, you won't need to enter a password, so it can be run from a script.

---

