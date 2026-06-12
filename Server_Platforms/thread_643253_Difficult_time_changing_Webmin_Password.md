---
title: "Difficult time changing Webmin Password"
date: 2007-12-17
forum: Server Platforms
---

### Post by daniel981 on 2007-12-17
Ubuntu Server 7.10

I'm having a hell of a time trying to change the password for webmin.. I messed up on the install and typed in the wrong password, and now I have no idea what it is, hence the change.

So this is what I have done so far:

```
/root/webmin-1.380/changepass.pl /etc/webmin admin MyPassword
```

And I get this error:

```
The Webmin user admin does not exist
The users on your system are:admin
```

Its contradicting itself... It says that the user admin doesn't exist, but then says that my user is admin...:confused:

Any ideas?  Thanks.

---

### Post by Technophobia on 2007-12-17
I thought by default webmin uses the username and password of the user that installed it. so when you goto [https://YOUIP:10000](https://YOUIP:10000). If not remove and reinstall.

---

