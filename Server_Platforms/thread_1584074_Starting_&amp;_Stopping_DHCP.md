---
title: "Starting &amp; Stopping DHCP"
date: 2010-09-28
forum: Server Platforms
---

### Post by keiffee30 on 2010-09-28
Could someone tell me if you can start, stop and restart the DHCP Server on a server from the command line ie....

For apache you would type in a terminal .....

**sudo /etc/init.d/apache2 restart**

is there a command line for the DHCP Server as i can not find it in the Documentation. 

OR 
is it just the case of typing in

**sudo /etc/init.d/dhcp3 restart**

stab in the dark here thats all.

---

### Post by koenn on 2010-09-28
> **keiffee30 said:**
> Could someone tell me if you can start, stop and restart the DHCP Server on a server from the command line ie....

For apache you would type in a terminal .....

**sudo /etc/init.d/apache2 restart**

is there a command line for the DHCP Server as i can not find it in the Documentation. 

OR 
is it just the case of typing in

**sudo /etc/init.d/dhcp3 restart**

stab in the dark here thats all.
I'd expect it to be something like
```
 /etc/init.d/dhcp3d restart
```
or
```
 /etc/init.d/dhcp3-server restart
```
you'd find the correct command by looking at filenames in /etc/init.d/

however, since recently, the recommended way of stopping and starting services would be
```
service dhcp3-server start  #[or stop, or restart, ...] 
```
again, the service names can be guessed from|found in /etc/init.d 

don't have an ubuntu dhcp server around here, so can't tell you the exact name

---

### Post by keiffee30 on 2010-09-28
ok thank you for your input. I have had a look in the 

**/etc/init.d/.....**

and it dose say dhcp3-server so it looks like i will be using this . 


sudo /etc/init.d/dhcp3-server restart
or 
sudo /etc/init.d/dhcp3-server start
or
sudo /etc/init.d/dhcp3-server stop

Many thanks for letting me know.

---

