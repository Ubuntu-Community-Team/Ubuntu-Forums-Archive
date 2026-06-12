---
title: "Problem installing LAMP, urgent help needed."
date: 2009-11-23
forum: Server Platforms
---

### Post by sislekdemir on 2009-11-23
Hello to everybody,

i have a strange problem, i just installed Ubuntu 9.10 and the first thing i tried to install was LAMP server by command 
```
sudo apt-get install lamp-server^

```

till now, all looks fine, but i am getting an error about libapache2-mod-php5

```
Setting up libapache2-mod-php5 (5.2.10.dfsg.1-2ubuntu6) ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libapache2-mod-php5 (5.2.10.dfsg.1-2ubuntu6) ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 libapache2-mod-php5


```

so apache cant handle php...

does anybody have any idea? i tried to change the server, uninstall everything and clearing package cache, and tring to install it manually from synaptic.. still not solution...

---

