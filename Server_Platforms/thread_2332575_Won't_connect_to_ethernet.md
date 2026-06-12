---
title: "Won't connect to ethernet"
date: 2016-08-01
forum: Server Platforms
---

### Post by connorb08 on 2016-08-01
Hi, I'm running Ubuntu Server on the Raspberry Pi using the ARM version of the OS. I'm running the Raspberry Pi in headless as I don't have a monitor to plug it into. I ran into a problem a few hours ago when I was setting up a LEMP stack. I installed Nginx, PHP, and MariaDB using headless by connecting my Raspberry Pi to my router using ethernet and sshing into it from my laptop. After messing with the configs I restarted the Raspberry Pi from ssh instead of reloading nginx because it's easier to do. When the Raspberry Pi rebooted, it would not connect to the network, so I tried restarting it many times and using two different ethernet cables and 3 different ethernet jacks on my router. Anyone know what could be wrong or how to fix it?

---

### Post by papibe on 2016-08-01
Hi connorb08.

We would need you to run some commands and post some logs. To do that you need to get access to the Rpi.

Are you able to connect via ssh? If not, try connecting a keyboard and a monitor.

Regards.

---

### Post by connorb08 on 2016-08-01
I can hook it up to my TV.

---

### Post by connorb08 on 2016-08-02
I fixed it by reinstalling ubuntu.

---

### Post by ohthreefive on 2016-08-09
I have the same issue as this guy.

Installed 16.04 server for Pi2 and installed. `apt update && apt upgrade` performed. Rebooted and since then can't access the server over my local network.

`nmap -pN <address>` says the host is up but all 1000 scanned ports are filtered.

My wireless router webmin does not 'detect' the server.

I attached a monitor and keyboard and found the server to be at a login prompt. I tried the default (ubuntu/ubuntu) then the password I changed before doing `apt update && apt upgrade` But both were deemed incorrect.

I edited [EMAIL="getty@tty1.servic"]getty@tty1.servic[/EMAIL]e to login as root by default and re-started the Pi again. So now I'm logged in as root but still can't do *anything.* I've run a few simple apt commands and I can't access the Internet from the server.

So the default user (ubuntu) no longer has the default password or the password to which I changed this.
The server is up according to nmap but all ports are filtered.
My router does not detect a connected device (Ethernet btw) and I can't `ssh` to it.
I also can't access the Internet from the server.

I've repeated the process from flashing the image to `apt upgrade` once already. I'd like to solve it now rather than start again!

What commands were you going to suggest to Connor? Thanks

---
OK I ran some commands and was prompted to try `systemctl status networking.service` which I did. Among the error messages generated was 'Failed to start Raise network interfaces' and 'failed to bring up eth0'

It also suggested `journalctl -xe` which gave a huge output including 'error getting hardware address for eth0: no such device'

Elsewhere it says:
ubuntu kernel: smsc95xx 1-1.1:1.0 enxb827eb01b4de: hardware isn't capable of remote wakeup
(interestingly 'enxb827eb01b4de' is the first line returned by `ifconfig -a` where 'eth0' usually is)
ubuntu kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enxb827eb01b4de: link is not ready

So is this a networking.service issue with eth0 not being found?

I'm sure I have a wireless adapted somewhere to test...

---

### Post by darkod on 2016-08-10
Maybe the issue is that since 16.04 ubuntu changed the naming of the network interfaces. The primary is not eth0 any more but something like ens0 or ens0p3, etc...

If you are logged in, a command that can show you the interfaces is:
```
sudo lshw -short | grep network
```

If there is a wrong interface name in /etc/network/interfaces it will not bring it up simply because it can't find the device name. Since Pi usually does images based on ubuntu but it is not the default ubuntu iso, I have no idea how the image you are using is created. And whether apt-get update/upgrade/dist-upgrade can mess up the network config.

---

