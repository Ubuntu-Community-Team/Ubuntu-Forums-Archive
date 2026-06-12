---
title: "Problems running vsftpd"
date: 2010-05-29
forum: Server Platforms
---

### Post by markbahnman on 2010-05-29
I tried to install vsftpd on my server and while the installation went fine, I can't run

```
restart vsftpd
```As I the get error
```
restart: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
```Though I'm able to restart the service with

```
sudo /etc/init.d/vsftpd restart
``` with a warning telling me to use the service utility.

Not only that, but despite the port being open it won't allow me to log in, it just hangs, and I have local users enabled (I've used the default .conf file). Does dbus not come installed in 10.04, and if I did install it would it make a difference for restarting the service? Are there further steps needed not available in the tutorial on the Ubuntu Server Guide for 10.04 to enabling local user authentication?

-edit- Figured it out, dbus wasn't installed, vsftpd is working fine now.

---

### Post by duceduc on 2010-08-06
I am having the exact same problem. I am not sure which cmd to start/restart vsftpd either. The one cmd I input that did work gives me an error when I try to browse from the client machine. 

I am running Ubuntu Server 10.4.

---

### Post by borrisl on 2010-10-09
Same issue here as well.  In one respect I'm happy to see I am not the only one.

---

### Post by Keen101 on 2010-10-12
try

> sudo service vsftpd restart

That command worked for me to restart. (at least i think it restarted)

But, i'm also having trouble connecting to the server. I even tried anonymous just to see if that worked. I keep getting connection refused. IS there some sort of firewall preventing this on ubuntu?

I'm using nautilus to connect. >Places >System >Connect to server

EDIT: WOW, I figured it out for me. I just tried using port 21 instead of port 20. haha. But it totally said it was going to use port 20 on installation... Weird..

---

### Post by luvshines on 2010-10-12
Also check if the directory "/var/run/dbus/" actually exists or not.

If it's not, then if dbus is installed or not:
```
dpkg -l dbus
```

---

