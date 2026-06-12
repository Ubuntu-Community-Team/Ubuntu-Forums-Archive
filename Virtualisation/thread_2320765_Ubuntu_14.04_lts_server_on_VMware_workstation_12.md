---
title: "Ubuntu 14.04 lts server on VMware workstation 12"
date: 2016-04-17
forum: Virtualisation
---

### Post by alberto11 on 2016-04-17
I've installed Ubu-server on VMware all ok ,
but I can not install MysqlServer ,
I must have done something wrong......[ATTACH=CONFIG]268424[/ATTACH]

---

### Post by MAFoElffen on 2016-04-17
Wait one, lets back up a step.

Let me say what you said in my own words, and correct me if I am wrong:
- You said you 'just' installed Ubuntu server within VMware Workstation 12.
- You then said you are having troubles installing MySQL to your virtual server... So with that statement, I would follow that you did not install MySQL while you were installing the OS.

Then your screenshot:
If MySQL is not installed, why would you try to log into MySQL? (It would not be there yet...)

The process to install MySQL to your freshly installed server, would be to first refresh your apt cache to find current packages > upgrade to ensure you are using the current kernel and system packages > reboot to be running on that current kernel > refresh the apt-cache for good measure > install MySQL by installing the package for...
```

sudo apt-get update && sudo apt-get dist-upgrade
sudo shutdown -r now
sudo apt-get update
sudo apt-get install mysql-server
sudo netstat -tap | grep mysql

```
That last command would ensure that the service was autostarted (by default on the install) and that the listener for the service is working...

---

### Post by alberto11 on 2016-04-17
solved ,  it's all OK
many thanks

---

