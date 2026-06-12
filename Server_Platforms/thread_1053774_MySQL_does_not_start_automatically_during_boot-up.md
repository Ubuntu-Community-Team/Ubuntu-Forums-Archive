---
title: "MySQL does not start automatically during boot-up"
date: 2009-01-29
forum: Server Platforms
---

### Post by wailynn on 2009-01-29
I have installed the servers below:
Apache, PHP and MySQL
When I ran phpmyadmin immediately after boot-up, the error message #2002 about the configuration of socket was shown. However, there would be no problems if I started mysql manually with "sudo /etc/init.d/mysql start" before running the phpmyadmin. Is there any way to let the mysql server start running automatically during boot-up?
Please advise.
wailynn

---

### Post by ibutho on 2009-01-29
Hi and welcome to the forum.

Try the following commands
```
sudo update-rc.d mysql remove
sudo update-rc.d mysql defaults
```
The first command removes all mysql start up scripts and the second one recreates them.

---

### Post by wailynn on 2009-01-29
Hi,
I have tried the commands, but the problem persists. Here are the messages displayed after the commands:
(a) After typing in "sudo update-rc.d mysql remove", I got the message "update-rc.d: /etc/init.d/mysql exists during rc.d purge (use -f to force)"
(b) After typing in "sudo update-rc.d mysql defaults", I got the message "System startup links for /etc/init.d/mysql already exist."
Please advise.
wailynn

---

### Post by TurboRush on 2009-01-29
Try making this minor tweak to use the force option...

```

sudo update-rc.d -f mysql remove
sudo update-rc.d mysql defaults

```

---

### Post by wailynn on 2009-01-31
Thanks ibutho and TurboRush.
I have removed and recreate the system startup links for mysql using the above commands, but the problem still persists. I need to start mysql manually.
Please advise.
wailynn

---

### Post by twelve17 on 2009-03-14
I'm having the same problem.  I believe for me it is because I have my mysql server bind to my wired network address.  By default I believe mysql only binds to the loopback address (or a socket).

So what's happening is that mysql tries to start before my computer is assigned its LAN network address.

Here is my syslog from boot:

```

Mar 14 18:10:03 austin kernel: [   33.614109] NET: Registered protocol family 10
Mar 14 18:10:03 austin kernel: [   33.616755] lo: Disabled Privacy Extensions
Mar 14 18:10:04 austin mysqld_safe[5248]: started
Mar 14 18:10:05 austin mysqld[5252]: 090314 18:10:05  InnoDB: Started; log sequence number 0 53881
Mar 14 18:10:05 austin mysqld[5252]: 090314 18:10:05 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Mar 14 18:10:05 austin mysqld[5252]: 090314 18:10:05 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Mar 14 18:10:05 austin mysqld[5252]: 090314 18:10:05 [ERROR] Aborting
Mar 14 18:10:05 austin mysqld[5252]: 
Mar 14 18:10:05 austin mysqld[5252]: 090314 18:10:05  InnoDB: Starting shutdown...
Mar 14 18:10:06 austin mysqld[5252]: 090314 18:10:06  InnoDB: Shutdown completed; log sequence number 0 53881
Mar 14 18:10:06 austin mysqld[5252]: 090314 18:10:06 [Note] /usr/sbin/mysqld: Shutdown complete

```

Then, way later in the boot process, my network card is assigned the address:

```

Mar 14 18:10:27 austin NetworkManager: <info>  starting... 
Mar 14 18:10:27 austin NetworkManager: <info>  eth0: driver is 'tg3'. 
Mar 14 18:10:27 austin NetworkManager: <info>  Found new Ethernet device 'eth0'. 
Mar 14 18:10:27 austin NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_XXXXXXXXXX 
Mar 14 18:10:27 austin NetworkManager: <info>  Trying to start the supplicant... 
Mar 14 18:10:27 austin NetworkManager: <info>  Trying to start the system settings daemon... 

```

Is there a way to change the order so mysql can start after network manager?

---

### Post by nikolaos on 2009-03-21
Change the bind address to all zeros

```
bind-address = 0.0.0.0
```

this sets the address to all interfaces.
Hence it (probably :confused:) covers everything!!! Mysql starts at boot and uses your LAN interface as well.

---

### Post by windependence on 2009-03-21
You can also achieve something like the Red Hat style rc.local using this tutorial:

[https://help.ubuntu.com/community/RcLocalHowto](https://help.ubuntu.com/community/RcLocalHowto)

This allows you to start processes or run commands as the last part of system startup. 

-Tim

---

### Post by grndamgt4 on 2010-02-18
thanks for the answers, changing the bind address from the machines assigned ip to 0.0.0.0 got mysql to start on boot.

---

