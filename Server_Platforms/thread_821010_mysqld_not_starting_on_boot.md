---
title: "mysqld not starting on boot"
date: 2008-06-06
forum: Server Platforms
---

### Post by coder_cotton on 2008-06-06
how can I set mysql server to start on boot?  for some reason it isn't on the default install...

I see this in /etc/init.d/mysql:

# Default-Start:     2 3 4 5

I'm assuming it should start on the default runlevel but alas it isn't.

TIA,
Cotton

---

### Post by quelx on 2008-06-06
```
sudo rc-update.d mysql defaults
```

---

### Post by coder_cotton on 2008-06-06
```
cotton@dell:/mnt$ sudo rc-update.d mysql defaults

sudo: rc-update.d: command not found
```

---

### Post by quelx on 2008-06-06
> **coder_cotton said:**
> ```
cotton@dell:/mnt$ sudo rc-update.d mysql defaults

sudo: rc-update.d: command not found
```

lol, sorry, it's **update-rc.d**

---

### Post by coder_cotton on 2008-06-06
```
cotton@dell:/mnt$ sudo update-rc.d mysql defaults

 System startup links for /etc/init.d/mysql already exist.

cotton@dell:/mnt$ 
```

haha, that works better... but it's already there, would the syslog have the startup failure in it??

edit: a quick look through /var/log/messages shows nothing, and the mysql logs are empty... any other ideas?

---

### Post by quelx on 2008-06-06
erm... is your server picking up its ip address by way of DHCP?

[https://answers.launchpad.net/ubuntu/+question/10644](https://answers.launchpad.net/ubuntu/+question/10644)

---

### Post by coder_cotton on 2008-06-06
> **quelx said:**
> erm... is your server picking up its ip address by way of DHCP?

[https://answers.launchpad.net/ubuntu/+question/10644](https://answers.launchpad.net/ubuntu/+question/10644)

As it happens, yes.  Thanks for the link/insight.

Cotton

---

### Post by moloth on 2008-09-29
I found that it had a network error that prevented it from starting first time.

cat /var/log/messages | grep mysql

In /etc/mysql/my.cnf I had the following:

bind-address = 127.0.0.1
bind-address = 192.168.0.195

the latter being the one my dhcp server assigned my test server.
However in my /etc/network/interfaces I only had:

auto lo
iface lo inet loopback

No mention of eth0! So in System > Administration > Network
I changed my wired connection from roaming to straight dhcp and MYSql worked on reboot. This is because it changed my /etc/network/interfaces to the following:

auto lo
iface lo inet loopback
iface eth0 inet dhcp

I also changed System > Administration > Services > Database Server(mysql)> (right click) Properties > Priority to 95 for runlevels 2,3,4,5. to give the DHCP Client a bit more time to get an address.

---

### Post by cariboo on 2008-09-30
It might be a better idea to give your server a static ip address, as that makes remote access way easier if the ip address is the same all the time.

Jim

---

