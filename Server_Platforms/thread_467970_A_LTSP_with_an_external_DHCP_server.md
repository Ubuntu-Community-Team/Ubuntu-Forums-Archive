---
title: "A LTSP with an external DHCP server"
date: 2007-06-08
forum: Server Platforms
---

### Post by dupa on 2007-06-08
I am in a network that already have a DHCPD server (on  a ubuntu box).
I cannot install LTSP server on that box or any LTSP related stuff, the only thing i can do, is just a little edit to the DHCP config file

I have a separate box on which the LTSP will run.

I am reading this guide: 

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

In the tips section it says exactly what i'm looking for...

> 
If you have a separate DHCP that you do not want to install LTSP on you can just redirect the thin-client to boot off a different server.

In your DHCP server's dhcpd.conf:
```

next-server 192.168.0.3; 

```
where 192.168.0.3 is the address of your LTSP server


Ok, on the LTSP server i have already executed:

```
sudo apt-get install ltsp-server 
```

and

```
sudo ltsp-build-client 
```

I don't understand where I should write these lines:
```

filename "/ltsp/pxelinux.0";
option root-path "/opt/ltsp/i386";
```

I think these lines are related to the DHCPD server, but at the same time they refer to files related to the LTSP server...
And as I told you, i have a DHCPD server what need to be completly separated from LTSP stuff...

Can someone help me?
thanks

---

