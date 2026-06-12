---
title: "user SSH login problem via putty"
date: 2014-07-01
forum: Server Platforms
---

### Post by mlinux508 on 2014-07-01
Ubuntu server 12.04 lts
webmin 1.69

A newly setup server and with all the new users created via Webmin but when I try using putty to connect to server, it ended up with the following message:

```
Last login: Tue Jul  1 14:43:20 2014 from 192.168.0.244
Could not chdir to home directory /home/test: Permission denied
$
```

Only user with sudo right able to use the home directory. Although all users no problem access samba server via window, I just wanted find out what's wrong with the server setting? Thanks for the help.

---

### Post by nerdtron on 2014-07-01
Samba credentials can be different from local user accounts.
Log in to the server and you should change the permissions of the home folders or each user.
Example: 
sudo chown -R [user]:[group] /path/to/home/folder
In your case for the test user:
sudo chown -R test:test /home/test

---

### Post by mlinux508 on 2014-07-01
Still the same.

```
drwxr-xr-x 2 test     users   4096 Jul  1 14:42 test
```

Also I try chmod to 777 just to confirm it is not the directory permission issue with no luck. Prior to this, I do change the server IP and hostname and re generate the SSL cert. Can this affect the user account login?

---

### Post by nerdtron on 2014-07-01
Changed the server IP? As long as you ssh to the correct IP it should connect. Hostname don't affect logins via ssh. I'm not sure about the ssl cert but I think it shouldn't affect logins as well.

---

### Post by mlinux508 on 2014-07-01
The funny thing is the user landed at the root directory and no permission to cd home but can cd to www and list all the php scripts, not very good sign. Need to do something before some hack into the system.

---

### Post by mlinux on 2014-07-01
Found the problem, the home directory permission was set to no access for world. Not sure why 12.04 installation set it to no access. It is working now.

```
drwxr-xr-x  18 root root  4096 Jul  1 14:42 home
```

Can't find how to mark as SOLVED!

---

