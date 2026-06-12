---
title: "NAT/File sharing setup help?"
date: 2005-10-12
forum: Server Platforms
---

### Post by jcmcbeth on 2005-10-12
I have a computer that has two harddrives in it, one is just for storage and one has ubuntu on it.  It also has two nic cards, one is connected to the internet and the other is connected to a switch.

The other computers that are going to be on my network are going to be running windows.  I want my linux machine to be a file server and have a NAT or whatever is the equiv. to windows internet connection sharing.

When I installed ubuntu I did not select the server installation.

I also eventually want to install an apache webserver and like mysql and stuff.  But for now i'd need to know what to do to be able to get my network working with file sharing and internet sharing.

---

### Post by drogoh on 2005-10-12
Since you want Ubuntu to play router, you need a DHCP server installed.  You also need to see about setting up some firewall rules.  NAT isn't particularly needed unless you're hosting things on the internal machines or otherwise wish to allow connections to your internal network.  I advise against this unless you need it.

Now for the file sharing, you have two choices:

1) Install and set up SAMBA so you can browse your files through Explorer (SWAT is a very good thing with SAMBA, it's pretty straightforward and does what you need)
**_OR_**
2) If you're running XP Professional or anything other than Home and want to be more advanced, you can use Services for Unix and use NFS, but it isn't advised as SFU requires more arm twisting than SAMBA.

---

### Post by jcmcbeth on 2005-10-13
I'm trying to set up my dhcp server and i'm using the site [http://www.ubuntuguide.org/#installdhcpserver](http://www.ubuntuguide.org/#installdhcpserver).  And it tells me to update the config file for the dhcp server to have something like this in it:
```
# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 202.188.0.133, 202.188.1.5;
  option domain-name "tm.net.my";
  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}
```

But I don't think
```
  option domain-name-servers 202.188.0.133, 202.188.1.5;
  option domain-name "tm.net.my"
```

applies to me, what should I put there?

---

### Post by LordHunter317 on 2005-10-13
[QUOTE=drogoh]. NAT isn't particularly needed unless you're hosting things on the internal machines or otherwise wish to allow connections to your internal network.  I advise against this unless you need it.[/quote]NAT is required if you want multiple machines on a network to share the same Internet facing IP.  What you're thinking of is port redirection, a related technique.

For the domain-name-servers option, put in the IP addresses of your ISP's DNS servers.

The domain-name is probably best left blank.  If you put something in, make sure it's not real-world resolvable.

---

