---
title: "Can't access server via hostname"
date: 2009-11-25
forum: Server Platforms
---

### Post by zigmo on 2009-11-25
I setup a 9.10 server with a static IP address for a DAViCal project on my office network. I can access the server via SSH using it's IP address, but when I try via it's hostname, I get:

```
Could not resolve hostname [server's hostname]: Name or service not known.
```

Any suggestions as to where to look to resolve this would be appreciated.

---

### Post by almostalive2009 on 2009-11-25
if you edit /etc/hosts and add an ip address and a host name it will tell the computer where to go when you use that host name. sorry if this isnt the answer your looking for

---

### Post by sanderj on 2009-11-25
From Ubuntu to Ubuntu? If so, you can ssh to <hostname>.local.

So, something like "ssh superbox2.local. "

No DNS nor host file needed, just Bonjour/Zeroconf (which is in Ubuntu 9.10).

---

### Post by zigmo on 2009-11-26
I'm still pretty new to this, so all suggestions are helpful.
I'm using a linux workstation to access the linux server, so I'll try editing the hosts file for my own use and convenience.
The server is on my work network and the hostname shows up as ubuntu-server.[domainname].local - that's what I tried to SSH to. I'll try ubuntu-server.local and see if that works any better.
The big problem is that everyone else who will need to access this server will be on Windows or Mac systems. I'm not familiar with Bonjour/Zeroconf. Will it broadcast the server's hostname with it's IP address so other computers can access it with just the hostname?

---

### Post by sanderj on 2009-11-26
Yes, it will broacast the name. Don't forget the dot at the end.

Macs also speak Bonjour/Zeroconf. For Windows, you need to install it.

---

### Post by zigmo on 2009-11-30
Editing the hosts file worked like a charm ... for me. I've still got the other computers to consider.
I tried accessing from my ubuntu desktop via ubuntu-server.local (before editing the hosts file) and it didn't work. I've got the libnss-mdns package installed - do I need anything else?
I browsed on my mac and yep - there it was, so I guess bonjour/zeroconf broadcast is working.
This is my office network and I have access to our DNS. Can I make any changes there?

---

### Post by sanderj on 2009-11-30
> **zigmo said:**
> 


I tried accessing from my ubuntu desktop via ubuntu-server.local (before editing the hosts file) and it didn't work. I've got the libnss-mdns package installed - do I need anything else?

I browsed on my mac and yep - there it was, so I guess bonjour/zeroconf broadcast is working.


What is the name of the ubuntu server? Is it "ubuntu-server"? Check with "uname -n". Use that name (followed by '.local.' ) to ping to.

Which Ubuntu version is running on the ubuntu server.


One-liner of the day below:

```

sander@quirinius:~$ ping `uname -n`.local.

PING quirinius.local. (192.168.2.163) 56(84) bytes of data.
64 bytes from quirinius.lan (192.168.2.163): icmp_seq=1 ttl=64 time=0.082 ms
64 bytes from quirinius.lan (192.168.2.163): icmp_seq=2 ttl=64 time=0.085 ms
^C
--- quirinius.local. ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.082/0.083/0.085/0.009 ms
sander@quirinius:~$ 





```

---

### Post by zigmo on 2009-11-30
It's 9.10 and named "ubuntu-server." It was my first one and I wasn't feeling very creative. I verified the name with uname -n and the version with lsb_release -a.

When I ping, I get
```
ian@ubuntu-server:~$ ping `uname -n`.local
ping: unknown host ubuntu-server.local
```

I tried some tests from my desktop and got weird results (as you can see, I'm not very creative with machine names - I also redacted our domain name)

```
ian@ubuntu-desktop:~$ uname -n
ubuntu-desktop
ian@ubuntu-desktop:~$ ping `uname -n`.local
PING ubuntu-desktop.local (192.168.59.171) 56(84) bytes of data.
64 bytes from npi0e8456 (192.168.59.171): icmp_seq=1 ttl=64 time=0.079 ms
64 bytes from ubuntu-desktop.[domainname].local (192.168.59.171): icmp_seq=2 ttl=64 time=0.074 ms
64 bytes from npi0e8456 (192.168.59.171): icmp_seq=3 ttl=64 time=0.082 ms
64 bytes from ubuntu-desktop.[domainname].local (192.168.59.171): icmp_seq=4 ttl=64 time=0.085 ms
64 bytes from npi0e8456 (192.168.59.171): icmp_seq=5 ttl=64 time=0.083 ms
^C
```

Based on that, I tried:

```

ian@ubuntu-desktop:~$ ping ubuntu-server.[domainname].local
ping: unknown host ubuntu-server.pier59studios.local
```

I did verify that I can ping from the server to the desktop, but it only works when I ping ubuntu-desktop.[domainname].local

---

### Post by sanderj on 2009-11-30
On the machine not seeing bonjour/zeroconf, check /etc/nsswitch.conf; it should contain the mdns4 settings below:


```
sander@quirinius:~$ grep hosts /etc/nsswitch.conf 
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
sander@quirinius:~$ 
```

---

### Post by zigmo on 2009-11-30
I wasn't sure what you meant by "not seeing bonjour/zeroconf."
Is the desktop not seeing it because it can't ping the server or is the server not seeing it because it can't be pinged by the desktop? In either case, I sent the info from both machines:

```
ian@ubuntu-server:~$ grep hosts /etc/nsswitch.conf
hosts:          files dns

ian@ubuntu-desktop:~$ grep hosts /etc/nsswitch.conf
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Does this mean that the desktop can be *found* via zeroconf (thus the server being able to ping it)

---

### Post by sanderj on 2009-11-30
On both machines, what's the output of 

```
ps -ef | grep -i avahi
```

Here's mine:

```
sander@quirinius:~$ ps -ef | grep -i avahi
avahi      949     1  0 17:47 ?        00:00:00 avahi-daemon: running [quirinius.local]
avahi      950   949  0 17:47 ?        00:00:00 avahi-daemon: chroot helper
sander    4112  2656  0 20:09 pts/1    00:00:00 grep --color=auto -i avahi
sander@quirinius:~$ 

```

---

### Post by zigmo on 2009-11-30
Here you go:
```

ian@ubuntu-server:~$ ps -ef | grep -i avahi
ian       6550  5508  0 14:15 pts/0    00:00:00 grep --color=auto -i [COLOR="Red"]avahi[/COLOR]

ian@ubuntu-desktop:~$ ps -ef | grep -i avahi
avahi      771     1  0 09:20 ?        00:00:02 avahi-daemon: running [ubuntu-desktop.local]
avahi      772   771  0 09:20 ?        00:00:00 avahi-daemon: chroot helper
ian       2389  2189  0 14:17 pts/2    00:00:00 grep -i avahi
```

So, if I understand this correctly, the desktop is using bonjour/zeroconf (since the avahi-daemon is running) so the server can find it, but the server isn't running it, so the desktop can't find it - right?

---

### Post by sanderj on 2009-11-30
Yes, combined with the nsswitch which instructs to use mdns = zeroconf = bonjour = avahi for lookups.

So, install avahi (or avahi-daemon, I don't know). Afterward check that /etc/nsswitch.conf is OK.

---

### Post by sanderj on 2009-11-30
PS from [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

> Ubuntu 9.04 (Jaunty Jackalope)

Zeroconf is installed and configured by default in the **Desktop** version of Ubuntu 9.04.

<snip>

Ubuntu 7.04

Just install the package **avahi-daemon** to allow other hosts to see this host as hostname.local. (note the trailing dot). 

HTH

---

### Post by zigmo on 2009-12-01
Thanks for all the great help - it worked like a charm, plus I learned a lot about zeroconf.

---

### Post by sanderj on 2009-12-01
To let Windows machines join in this bonjour / zeroconf happiness, you need to install Bonjour for Windows: [http://support.apple.com/downloads/Bonjour_for_Windows](http://support.apple.com/downloads/Bonjour_for_Windows)

On Ubuntu, you can use avahi-discover to discover bonjour / zeroconf service on your network.

There is also a great Firefox Bonjour plugin bonjourfoxy, but alas the developer has stopped support for Firefox on Linux; it's now Mac and Windows only.

---

### Post by zigmo on 2009-12-01
Thanks for the extra info. It looks like everything can see everything now, but I'm having Apache problems now - I'm only seeing the default page and not the DAViCal setups ... but that's a question for another thread!

---

