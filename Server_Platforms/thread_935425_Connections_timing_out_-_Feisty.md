---
title: "Connections timing out - Feisty"
date: 2008-10-01
forum: Server Platforms
---

### Post by ptolemytoo on 2008-10-01
Hi all

I have had the strangest thing happen; apparently out of the blue.

I'm running a Dell Dimension XPS R400. 400Mhz Pentium 2 with 512 MB of non matching RAM and two HDD's a 10GB Maxtor & a 3 GB Western Digtal.

I have the standard, non GUI LAMP installation of Feisty 7.04 to which I have added Secure Shell server and VSFTP server, Emacs and the basic development tools, build-essential and Lynx web browser, all via apt-get I've also installed DosEMU. And I've installed the Alpine mail program via Debian package installation. And one or two minor utilities, like bc. In my opinion, nothing that would break the installation.

I also created a root account. I don't like sudo.

I was able to log into the machine via Putty and WinSCP from my XP box. The home page came up in the browser, no problem. Everything was working splendidly. Then this morning, out of the blue, all attempts to log into the box failed, with a "timed out" message. 

In fact I was logged in and had left it in Emacs, editing the index page. It had stopped with an error message saying a network error had caused...blah blah.

Ping also times out. And I am no longer able to get to the home page via a browser. All timed out.

At first I thought there may have been a power glitch, so I just hard rebooted. No luck.

I had it running headless, so I connected a monitor and keyboard and was able to watch it boot normally. I was able to log in normally. Everything appeared normal. All server daemons as well as MySQL and Apache loaded normally as far as I could tell.

From the server, I can ping my PC as well as the outside world. I can raise Google via Lynx. So the LAN is functioning OK. No network card problems. However, it cannot ping itself; not by the IP address, nor the computer name. Nor will it find the home page via Lynx. But it will find the home page via localhost.

I looked at the /var/log/messages file; all seems OK, although I confess I don't understand everything.

I'm at a complete loss. Any ideas?

Thanks

Harry

---

### Post by gombadi on 2008-10-01
Sounds like the machine has an ip address but it may not be the correct one - It works ok outbound and ok for localhost but things can't connect to it.

Have a look at the output of the following to see that it all looks fine -
```

sudo ifconfig -a
sudo iptables -vnL
sudo netstat -plntu
cat /etc/resolv.conf
cat /etc/hosts

```

---

### Post by ptolemytoo on 2008-10-01
Thanks very much gombadi. 

You have helped me solve the immediate connectivity problem but left me with another mystery. The IP address is meant to be fixed 10.0.0.101 but it has mysteriously become 10.0.0.102. How did this happen?

My /etc/network/interfaces file reads as follows: 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
address 10.0.0.101
netmask 255.255.255.0
gateway 10.0.0.2
dns-nameservers 196.41.124.10 196.41.124.11

And the /etc/host files looks like this:

127.0.0.1       localhost
10.0.0.101      plato
10.0.0.100      socrates

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Yet after several reboots, it still binds to 10.0.0.102. How is this possible? Any Ideas

Thanks again

Harry

---

### Post by gombadi on 2008-10-01
> 
iface eth0 inet dhcp


For a static ip address this should be -
```

iface eth0 inet static

```

The 10.0.0.102 ip address must be coming from a dhcp server somewhere on your network.

---

### Post by ptolemytoo on 2008-10-01
Oops! Missed that. And now also know what happened. 

I reset the router-cum-dhcp-server last night at midnight. Obviously I had not shut it down since setting up this box. I thought I had set up a static address but it was infact dynamically allocated by the dhcp server. It happened to be the next available address according to how I had set up the router software.

Thanks again.

Cheers

Harry

---

