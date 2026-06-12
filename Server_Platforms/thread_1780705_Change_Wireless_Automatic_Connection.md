---
title: "Change Wireless Automatic Connection"
date: 2011-06-12
forum: Server Platforms
---

### Post by darkeale on 2011-06-12
Hi,

I have just managed to get my wireless working with Ubuntu Server 10.04.  However, I was wandering if anyone knows how to change the auto connection settings?  I would either like to tell it which network to connect to (at the moment it automatically connects to the wrong one) or disable automatic connection.

Thanks,
Alex

---

### Post by jramshu on 2011-06-12
Right click connection manager,click edit connections, click on wireless, click on the connection, click edit. It will have the auto connect options.

---

### Post by darkeale on 2011-06-12
Hi,

Sorry I forgot to mention, I don't have the GUI installed, so everything must be done from the command line.

Thanks,
Alex

---

### Post by jramshu on 2011-06-12
I should have seen that, got in too big of a hurry. My bad.

---

### Post by jramshu on 2011-06-12
It's going to be a setting in the /etc/networks/interfaces. I think all you have to do is comment out wlan. The down side, this will stop the wireless card from working.

---

### Post by volkswagner on 2011-06-12
First create a backup of your interface file.

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```

Then edit the file for your new network config.

```
sudo nano /etc/network/interfaces
```

Here is a sample from mine, your device name may be different, which can be found by running:

```
iwconfig
```

Sample File:

```
auto eth0
iface eth0 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid MyHomeNet
        wireless-key1 365537ea2

```

Save file by: ctrl+o and exit by ctrl+x.

Restart networking

```
sudo /etc/init.d/networking restart
```

---

### Post by darkeale on 2011-06-12
Thanks!  That is just what I was after!

Alex

---

