---
title: "Removed apache2 but it's still there?"
date: 2011-03-07
forum: Server Platforms
---

### Post by jerome1232 on 2011-03-07
I'm very baffled by this, I was setting up my mumble server since my old one had a hard disk failure. I was messing around with web registration but decided I didn't want it since this server is really only for a few friends.

So I removed all the mumble-django and apache2 packages required for web registration, but for some reason apache2 is still on my system and listening for connections.

terminal output below to further clarify.


```
Linux voiceserv 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
jeremy@voiceserv:~$ sudo lsof -i -n -P
[sudo] password for jeremy:
COMMAND    PID          USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient3  746          root    4u  IPv4   7152      0t0  UDP *:68
avahi-dae  796         avahi   13u  IPv4   7295      0t0  UDP *:5353
avahi-dae  796         avahi   14u  IPv6   7296      0t0  UDP *:5353
avahi-dae  796         avahi   15u  IPv4   7297      0t0  UDP *:42515
avahi-dae  796         avahi   16u  IPv6   7298      0t0  UDP *:36531
sshd       828          root    3r  IPv4   7691      0t0  TCP *:22 (LISTEN)
sshd       828          root    4u  IPv6   7695      0t0  TCP *:22 (LISTEN)
[COLOR="Red"]apache2    878          root    3u  IPv4   7736      0t0  TCP *:80 (LISTEN)
apache2    883      www-data    3u  IPv4   7736      0t0  TCP *:80 (LISTEN)
apache2    884      www-data    3u  IPv4   7736      0t0  TCP *:80 (LISTEN)[/COLOR]
murmurd    945 mumble-server   14u  IPv4   7794      0t0  TCP 127.0.0.1:6502 (LISTEN)
murmurd    945 mumble-server   18u  IPv6   7926      0t0  TCP *:64738 (LISTEN)
murmurd    945 mumble-server   19u  IPv6   7930      0t0  UDP *:64738
sshd       971          root    3r  IPv4   7940      0t0  TCP 75.15.228.161:22->192.168.1.65:53435 (ESTABLISHED)
sshd      1056        jeremy    3u  IPv4   7940      0t0  TCP 75.15.228.161:22->192.168.1.65:53435 (ESTABLISHED)
jeremy@voiceserv:~$ sudo apt-get remove apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeremy@voiceserv:~$ sudo killall apache2
jeremy@voiceserv:~$ sudo lsof -i -n -P
COMMAND    PID          USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient3  746          root    4u  IPv4   7152      0t0  UDP *:68
avahi-dae  796         avahi   13u  IPv4   7295      0t0  UDP *:5353
avahi-dae  796         avahi   14u  IPv6   7296      0t0  UDP *:5353
avahi-dae  796         avahi   15u  IPv4   7297      0t0  UDP *:42515
avahi-dae  796         avahi   16u  IPv6   7298      0t0  UDP *:36531
sshd       828          root    3r  IPv4   7691      0t0  TCP *:22 (LISTEN)
sshd       828          root    4u  IPv6   7695      0t0  TCP *:22 (LISTEN)
murmurd    945 mumble-server   14u  IPv4   7794      0t0  TCP 127.0.0.1:6502 (LISTEN)
murmurd    945 mumble-server   18u  IPv6   7926      0t0  TCP *:64738 (LISTEN)
murmurd    945 mumble-server   19u  IPv6   7930      0t0  UDP *:64738
sshd       971          root    3r  IPv4   7940      0t0  TCP 75.15.228.161:22->192.168.1.65:53435 (ESTABLISHED)
sshd      1056        jeremy    3u  IPv4   7940      0t0  TCP 75.15.228.161:22->192.168.1.65:53435 (ESTABLISHED)
jeremy@voiceserv:~$ sudo service apache2 start
 * Starting web server apache2
   ...done.
jeremy@voiceserv:~$ sudo lsof -i -n -P
COMMAND    PID          USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient3  746          root    4u  IPv4   7152      0t0  UDP *:68
avahi-dae  796         avahi   13u  IPv4   7295      0t0  UDP *:5353
avahi-dae  796         avahi   14u  IPv6   7296      0t0  UDP *:5353
avahi-dae  796         avahi   15u  IPv4   7297      0t0  UDP *:42515
avahi-dae  796         avahi   16u  IPv6   7298      0t0  UDP *:36531
sshd       828          root    3r  IPv4   7691      0t0  TCP *:22 (LISTEN)
sshd       828          root    4u  IPv6   7695      0t0  TCP *:22 (LISTEN)
murmurd    945 mumble-server   14u  IPv4   7794      0t0  TCP 127.0.0.1:6502 (LISTEN)
murmurd    945 mumble-server   18u  IPv6   7926      0t0  TCP *:64738 (LISTEN)
murmurd    945 mumble-server   19u  IPv6   7930      0t0  UDP *:64738
sshd       971          root    3r  IPv4   7940      0t0  TCP 75.15.228.161:22->192.168.1.65:53435 (ESTABLISHED)
sshd      1056        jeremy    3u  IPv4   7940      0t0  TCP 75.15.228.161:22->192.168.1.65:53435 (ESTABLISHED)
apache2   4058          root    3u  IPv4  11542      0t0  TCP *:80 (LISTEN)
apache2   4061      www-data    3u  IPv4  11542      0t0  TCP *:80 (LISTEN)
apache2   4062      www-data    3u  IPv4  11542      0t0  TCP *:80 (LISTEN)
jeremy@voiceserv:~$ sudo apt-get remove apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeremy@voiceserv:~$

```

---

### Post by wojox on 2011-03-07
There's more to remove. Try:

```
sudo apt-get purge apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5
```

---

### Post by jerome1232 on 2011-03-07
Ahh that got it thanks.

May I ask how you came up with that list of packages to remove?

---

### Post by wojox on 2011-03-08
That's all the packages I have installed for Apache2. :P

---

