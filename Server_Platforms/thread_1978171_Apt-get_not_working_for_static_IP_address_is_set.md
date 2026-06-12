---
title: "Apt-get not working for static IP address is set"
date: 2012-05-11
forum: Server Platforms
---

### Post by hipertrofia on 2012-05-11
I have Ubuntu server 12.04.

As in the title, when I set a static IP address, apt-get can't connect to the servers. This does not happen for dhcp.

Other than apt-get, I have normal access to internet with the static address for every other application.

Does anybody know a fix for this?

---

### Post by darkod on 2012-05-11
Are you sure you have normal internet access for everything else with a static IP?

It sounds like issue with the static settings but that would affect everything, not just apt-get.

Do you have the correct netmask, gateway and dns set up?

If you try to ping a domain, not an IP, does it work? Like ping [www.google.com](www.google.com)

---

### Post by a2j on 2012-05-11
what does ```
cat /etc/network/interfaces
``` say?


can you ping your default gateway, isp gateway, isp dns or any other hostname or ip address in the Internetz?

---

### Post by hipertrofia on 2012-05-11
Hi there. I would swear that other internet services used to work and it was only apt-get. Well, right now nothing outside my intranet works for the static IP configuration (it works fine for dhcp).

My interfaces file is

```

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.16
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.1
broadcast 192.168.1.255

```

I commented out the dhcp line and entered the rest following instructions that I found online.

My router's IP is 192.168.1.1 and inside my network I can ping all the computers connected to it, including the router...

---

### Post by darkod on 2012-05-11
Delete the network and broadcast lines, they are not needed (it calculates them automatically).

Anyway, I think you have error in specifying network, it should be like 192.168.1.0. You used the same as your gateway (router ip).

As said above, best to remove these lines. Restart networking with:
sudo /etc/init.d/networking restart

Try apt-get again.

---

### Post by hipertrofia on 2012-05-11
Nevermind... The above configuration works fine when I add the dns explicitly to the interfaces file as

```

dns-nameservers xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy

```

I think for some reason my router wasn't "telling" my computer what the DNS were...

Thanks to those who replied.

---

### Post by LHammonds on 2012-05-11
> **hipertrofia said:**
> Nevermind... The above configuration works fine when I add the dns explicitly to the interfaces file as

```

dns-nameservers xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy

```I think for some reason my router wasn't "telling" my computer what the DNS were...

Thanks to those who replied.
The DNS entries being moved from /etc/resolv.conf to /etc/network/interfaces is the main difference between an installation for Ubuntu Server 10.04 LTS and 12.04 LTS.

It had me scratching my head too for a little while (further compounded by my misspelling of dns-nameservers as dns-servers.  lol)

---

### Post by darkod on 2012-05-11
> **hipertrofia said:**
> Nevermind... The above configuration works fine when I add the dns explicitly to the interfaces file as

```

dns-nameservers xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy

```I think for some reason my router wasn't "telling" my computer what the DNS were...

Thanks to those who replied.

Yeah, slipped my mind although I mentioned DNS earlier.

The router (or more exactly the dhcp server running on the router) will configure the dns servers only when you use dhcp. As soon as you start using static, it's your job to set the interface up, including dns servers.

---

