---
title: "services manual start"
date: 2010-01-23
forum: Server Platforms
---

### Post by saravanaspeed on 2010-01-23
[SIZE="4"]I am using ubuntu 9.10 desktop 
I installed apache,php,mysql from ubuntu server 9.10 cd.
The services for apache,mysql start automatically when system boots.I have only 512 mb ram .
I want to manually start services when i want and not automatically 
How to do it.
Please help[/SIZE]

---

### Post by ICEB3AR on 2010-01-23
```

**# BUT BE CAREFUL NOT TO DELETE ANY IMPORTANT SERVICE LINKS**
# update-rc.d -f <service> remove
# e.g. for mysql:
sudo update-rc.d -f mysql remove
# if you would like to automatically start:
sudo update-rc.d mysql defaults 19
# number says in which order they start look in /etc/rc<runlevel>.d to check
# out which other numbers are used.

```

---

### Post by d3v1150m471c on 2010-01-23
Download BUM with your synaptic package manager. It's a graphical boot-up manager that's easy to use and can be accessed in your system section. Be very careful with that you set to manually activate.

---

