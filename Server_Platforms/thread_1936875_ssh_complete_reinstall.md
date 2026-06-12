---
title: "ssh complete reinstall"
date: 2012-03-06
forum: Server Platforms
---

### Post by gishaust on 2012-03-06
hi ubuntu people

I need to completely remove ssh from my ubuntu server it will not accept any connections I am able to access it from the server terminal or a client machine

I have tried sudo apt-get remove --purge ssh to try and remove but I will not work

If I type in cd /etc/ssh it says there is no file or directory but I know that is where the config files should be 

If I type sudo apt-get install ssh it says the latest version is installed 

help

---

### Post by nothingspecial on 2012-03-08
*Thread moved to **Server Platforms**.*

---

### Post by bubylou on 2012-03-08
I believe its suppose to be sudo apt-get purge openssh-server. Also try to run these to get rid of any left over packages. 
sudo apt-get autoremove
sudo apt-get autoclean

Also, what steps have you taken in your attempt to connect to the server.

---

### Post by CharlesA on 2012-03-08
```
sudo apt-get purge openssh-server
```

The ssh package contains the client and the server as far as I know.

If the /etc/ssh directory doesn't exist, then none of the config files are there, so run the above command and see what happens.

---

### Post by pavi_elex on 2012-03-09
```
sudo apt-get remove --purge openssh-server && sudo apt-get install openssh-server
```

---

