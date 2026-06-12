---
title: "Could not resolve FQDN hostname"
date: 2010-11-16
forum: Server Platforms
---

### Post by dalitso on 2010-11-16
I am following an rsync tutorial on this link [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync) and it requires me to use FQDN for the setup. How ever my ubuntu 10.04 box cannot resolve to its host name hurricane.thunzicn.com but it works with the IP address and hurricane.local
```
root@dalitso:/home/martin# rsync -avz -e ssh jhbs@hurricane.thunzicon.com:/home/all2 /home/martin/all2/
ssh: Could not resolve hostname hurricane.thunzicon.com: Name or service not known

```
```
root@dalitso:/home/martin# rsync -avz -e ssh jhbs@hurricane:/home/all2 /home/martin/all2/
The authenticity of host 'hurricane (192.168.1.100)' can't be established.
RSA key fingerprint is 41:71:8d:bb:55:2e:20:97:ac:9b:dd:c7:cb:9b:66:b5.
Are you sure you want to continue connecting (yes/no)?
```

Heres my setup: ADSL router with ip 192.168.1.254 ---> Dlink Switch ---> ubuntu server with ip 192.168.1.100

I am also accessing the server using an ubuntu desktop connected to the same switch

And here are some configuration files

```
root@hurricane:~# nano /etc.hosts
127.0.0.1	localhost.localdomain localhost
192.168.1.100	hurricane.thunzicon.com hurricane

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

```
root@hurricane:~# nano /etc/resolv.conf
nameserver 192.168.1.254
nameserver 127.0.0.1


```

```
/etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

#hosts:	files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:	files wins dns 
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

```
root@hurricane:/home/jhbs# hostname
hurricane.thunzicon.com

```

The server was setup with webmin so Bind DNS server has got only Root, localhost, 0, 127, 255 zones.

Help me get the hostname resolved, the tutorial said something like, it will only work when a FQDN is used.
Let me know if you need me to post more information.

---

### Post by CharlesA on 2010-11-16
The hostname shouldn't be the FQDN, so that's probably what is causing the problem.

If hurrican.local is working, then it's a DNS problem.

You don't really need to use the FQDN for local communications, any particular reason you want to use it?

EDIT: Are you using virtualmin by chance?

---

### Post by dalitso on 2010-11-16
The only reason I want to use FQDN is because the tutorial said I should for it to work.

I only have webmin installed but I can install virtualmin if its going to solve my problem. I am guessing you asked about virtualmin because it can create DNS records with a few entries and mouse clicks, right?

---

### Post by CharlesA on 2010-11-16
Just asked about virtualmin since it was mentioned that the FQDN needed to be set as the "hostname" for it work for some reason. *shrug*

What tutorial are you looking at?

Post the output of this:

```
hostname -f
```

---

### Post by dalitso on 2010-11-16
I am looking at this tutorial for rsync [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)
Its for rsync ssh auto login and cron

here's the output of hostname -f

```
root@hurricane:~# hostname -f
hurricane.thunzicon.com

```

---

### Post by CharlesA on 2010-11-16
If you are backing up over the internet, then, yes you'd need the FQDN, but if it's just local, you'd be fine just to use the hostname.

The FQDN is used when you are accessing a machine from outside yer local network, and that's why it's not needed for local communication.

---

### Post by dalitso on 2010-11-16
I need this setup to be used on two remote servers. One server on ADSL and the other on VSAT. Now the problem is that the VSAT has no port forwarding or remote access features. Its in a rural area where they still have no ADSL. I am not sure if I can place a router between the vsat and the LAN that would make it have some Dynamic DNS access feature. I haven't yet worked on the VSAT.

So the setup for now is like this: the server on ADSL has OpenVPN installed, so that the server on VSAT can connect to it. By the way, I am now simulating the setup using an ADSL line, the server is not yet on the VSAT site. So far the openvpn connection is working fine, but I cannot use the hostnames, only ip addresses for rsync.

I am going to go ahead with the setup using ip addresses and see where it takes me.

---

### Post by CharlesA on 2010-11-16
Good luck.

That's probably the best way to start it, worry about using hostnames after you get it working. :)

---

### Post by redmk2 on 2010-11-16
> **charlesa said:**
> good luck.

That's probably the best way to start it, worry about using hostnames after you get it working. :)

:)

---

### Post by dalitso on 2010-11-16
Thanks, will let you know how it goes

---

### Post by apalacheno on 2011-08-17
Ubuntu has a problem with .local. It seems to be reserved for something and breaks traditional resolving.

Don't use .local as domain name suffix, it will cause many hard to detect problems (been there, done that... as soon as I switched to another suffix, everything worked as expected).

---

### Post by dalitso on 2011-08-18
Thank you everyone for all your help. Sorry for taking so long to come back to you. I resorted to using IP addresses and everything worked fine. I used rsync over ssh and ssh keys.

---

