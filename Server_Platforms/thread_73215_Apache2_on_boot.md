---
title: "Apache2 on boot"
date: 2005-10-08
forum: Server Platforms
---

### Post by duffydack on 2005-10-08
Ive looked around google and seen having a script in etc/init.d and stuff but i just cant get it to start at boot.
I installed apache2 with prefix /usr/local/apache2 
Can someone tell me how i start at boot as im going crazy 
thanks

---

### Post by heimo on 2005-10-08
Does:
```

sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop
``` start/stop Apache properly? If so, you need to have symlink starting with S in /etc/rcX.d directory, where X is your default initlevel (normally 2). This should take care of it: 

```
sudo update-rc.d -f apache2 remove
sudo update-rc.d apache2 defaults 91
```

---

### Post by duffydack on 2005-10-12
there is no apache2 in there so it does not work
what do i have to do now (lamer)

thanks

---

### Post by heimo on 2005-10-12
How did you install Apache2? I would suggest trying to install from repository unless you have some very compelling reason not to. Uninstall the version you have now, and then use Synaptic Package Manager to install apache2. That's how I do it on my webservers and it makes life very easy (updates through package management, integration to other packages / system - very little to configure).

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by duffydack on 2005-10-13
I compiled zlib and openssl into it (following a guide).  is it just a matter linking and simple scripts, i can do that.

---

### Post by heimo on 2005-10-13
Yes. :) It's pretty easy to make initscripts (or rather: take some existing ones and modify) and use update-rc.d to create links. Sorry - no specific instructions just now, but if needed, I can post something later.

---

