---
title: "vsftpd automatically startup after connected to internet from NetworkManager"
date: 2010-05-17
forum: Server Platforms
---

### Post by apporc on 2010-05-17
I don't want my vsftpd startup itself.

But,though it won't startup itself during boot after I have changed that with 'update-rc.d',It still startup itself everytime I connect to internet with NetworkManager.

my ubuntu is 10.04 LTS
my NetworkManager is static IP ,and I won't let it connect automatically ,everytime i press that button to connect to internet myself.

command i used:
update-rc.d -f vsftpd remove;update-rc.d vsftpd start 91 3 5 . stop 9 0 1 2 4 6 .

I have not changed my /etc/network/interfaces.It just have this two line:
auto lo 
iface lo inet lookback

I always change my work place , So I need to choose how to connect to internet myself everytime I boot my computer.
At present I press the network icon on the top panel and choose "Wired connection" or "Wireless connection" myself.


------------------------------------------
Thank you all.Any reponse is appreciated.

---

### Post by cdenley on 2010-05-18
It already is started by upstart. It is not started by sysv. If you have it bind to a specific interface and have multiple interfaces, then it may fail to start if that interface isn't initialized first. You can edit /etc/init/vsftpd.conf to fix that.
```

# vsftpd - FTP Daemon
#

description     "vsftpd daemon"
author          "Chuck Short <zulcss@ubuntu.com>"

start on (filesystem
        and net-device-up **IFACE=eth0**)
stop on runlevel [!2345]
respawn

```
This would start when eth0 is brought up. By default, it attempts to start whenever an interface besides lo is brought up.

You should not configure your system to start it using the sysv compatibility scripts and upstart, or it will try to start it twice.

---

### Post by apporc on 2010-05-19
Thank you very very much.

---

