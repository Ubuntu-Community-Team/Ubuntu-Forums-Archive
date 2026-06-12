---
title: "Bash script is not executing after reboot command Ubuntu 14.04"
date: 2016-02-02
forum: Server Platforms
---

### Post by Chris_McMillan on 2016-02-02
I've tried using a /etc/init.d/ script, an upstart script, crontab, etc.  None of the above are causing the script to execute on boot.
The service I am attempting to automatically start on boot is Upsource 2.0
The /etc/init.d/upsource script is executable, and I can run it using 

```
service Upsource start
```

The contents of /etc/init.d/Upsource are as follows

```
#!/bin/sh
# /etc/init.d/Upsource
# Required-start:     $all
 /opt/Upsource/bin/upsource.sh start
```


I have already run 

```
update-rc.d Upsource defaults
```


The contents of /etc/init/upsource.conf are as follows

```
#Upsource

start on filesystem and net-device-up IFACE=eth0
stop on runlevel [016]

respawn
expect fork

exec /opt/Upsource/bin/upsource.sh start
```


The last lines of crontab -e is as follows

```
@reboot service Upsource start
@reboot echo "hello" > /root/downloads/test.txt
```


I can see /root/downloads/test.txt, and using cat on it results in "hello" being displayed, so I know it's running.  When I issue reboot to the server the Upsource service is not automatically started, I have to issue the command manually for the service to start.

/etc/rc.local contains the following:

```
service Upsource start || exit 1 
 exit 0
```

---

### Post by ian-weisser on 2016-02-02
What release of Ubuntu? 12.04? 14.04? 15.10?
What does Upsource do? Does it require environment variables? A display?  Any other services beyond eth0?
Is eth0 really your primary network connection?

---

### Post by Chris_McMillan on 2016-02-02
Per the title, 14.04.  Upsource allows developers to perform code review.  All environment variables are contained within a separate conf file.  Per ifconfig, eth0 is the only interface.

---

### Post by ian-weisser on 2016-02-02
Let's see.

According to [their help site]("https://www.jetbrains.com/upsource/help/2.0/install_on_linux.html"),
> When you run Upsource for the first time, it will open Configuration Wizard in your default browser

Opening a web browser, or any action affecting the user display, cannot occur until after login.
You can start them before login, but they will promptly fail or crash since no display is available to them yet.
This is different from Windows behavior.

Try launching the application after login instead of before login. (~/.config/upstart or ~/.config/autostart)

---

