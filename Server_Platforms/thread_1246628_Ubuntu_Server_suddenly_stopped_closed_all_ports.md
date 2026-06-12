---
title: "Ubuntu Server suddenly stopped closed all ports"
date: 2009-08-21
forum: Server Platforms
---

### Post by Jcarr_toonist on 2009-08-21
I rebooted my server the other day and afterwards I was unable to ssh, access my samba shares or fetch webpages. Ssh, for example, says > port 22: connection refused. 

I ran nmap on the device and it said that all my ports are closed. 

Is there a way to reopen the ports? or to find out what happened?

Thanks in advance.

---

### Post by cariboo on 2009-08-22
It looks like your servers didn't start when you rebooted. You can start the services manually, they are all located in /etc/init.d:

```
[list=1]
[*]sudo /etc/init.d/apache2 start
[*]sudo /etc/init.d/samba start
[*]sudo /etc/init.d/ssh start
[/list]
```

Check to see if they are located in /etc/rc*.d, if they are you can add them by using:

```
sudo update-rc.d
```

just type it at the prompt, and it will give you the options.

---

