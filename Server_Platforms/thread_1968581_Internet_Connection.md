---
title: "Internet Connection"
date: 2012-04-29
forum: Server Platforms
---

### Post by xb2003 on 2012-04-29
Let me start off by saying i know little about this, so im sure what im about to ask is very basic, but i cant figure it out.

I just installed Ubuntu Server 10.04 on a computer that will eventually be a small game server. Ive got it all installed, and when i setup the network stuff in the install process, i think i screwed it up. Anyways i think i either have no connection to the internet, or something in DNS is messed up. If i do "ping google.com" i get an error saying unknown host. But i pinged googles ip and it worked fine. Anyways, i know when i try to do "sudo apt-get update" which is the first step in the tutorial for this server, it will not connect to the server.

If you can help me with this problem, it would be great. THanks

---

### Post by CharlesA on 2012-04-29
Post the output of these commands please:

```
cat /etc/interfaces
```

```
cat /etc/resolv.conf
```

---

### Post by xb2003 on 2012-04-29
the first one says "no such file or directory" and the second is "nameserver 10.200.14.1"

When i went through the installation, the computer wasnt connected to the internet. I realized that after it was done. Anyways, i had to manually configure the network. Can i tell it to re run the DHCP?

---

### Post by CharlesA on 2012-04-29
Whoops, the first one should have been:

```
cat /etc/network/interfaces
```

The second one looks like a private IP for some reason.

Post the output of the above and we'll go from there.

---

### Post by xb2003 on 2012-04-29
```
"This file describes the network interfaces available on your system
and how to activate them. for more information, see interfaces(5).

THe loopback network interface
auto eth0
iface eth0 inet static
     address 10.200.14.111
     netmask 255.255.255.0
     network 10.200.14.0
     broadcast 10.200.14.0
     gateway 10.200.14.1
     dns-* options are implemented by the resolvconf package, if installed
     dns-nameservers 10.200.14.1"
```

I had to type that...so i hope i got it all right. I i figure all you really needed were the addresses, but i didnt think of that till after i got done typing it all.

---

### Post by CharlesA on 2012-04-29
That works. It is set for a static IP, so change it to read this:

```
auto eth0
iface eth0 inet dhcp
```

Run this to edit the file:

```
sudo nano /etc/network/interfaces
```

Reboot and see if you can ping google now.

---

### Post by xb2003 on 2012-04-29
Thank You So Much!!! I just got that update downloaded. I feel so dumb now, because it makes since that it would need to be changed to DHCP.....

Thanks again!!

DO you guys have a rep system here?

---

### Post by CharlesA on 2012-04-29
No rep system, but you can mark the thread as solved from the thread tools menu at the top.

---

