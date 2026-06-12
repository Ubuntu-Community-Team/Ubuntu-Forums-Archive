---
title: "dhcpd.conf broke eth0?"
date: 2009-08-08
forum: Server Platforms
---

### Post by ilikeyourflannel on 2009-08-08
Hello ubuntu community!

I have been using ubuntu for about a year, I help administer a small office network and am studying for my CCNA.  In other words I know enough to be quite dangerous.

I recently setup an ubuntu server to move away from the current workgroup environment.  Setup samba to share files.  All of our win2k & xp machines can access shares.  Wonderful.

After saving the dhcpd.conf file my ssh session dropped out.  A ping to the server times out.  Just for kicks I tried to see if I would be served an address and indeed I was. However, with the dhcp served address ping returns destination network unreachable for any external network, while local resources were still accessible.  Every client in the network is currently setup statically, and no part of the address pool is in use.  

I would have provided you with the exact config file but the dhcp server in question is not at my work site and I won't be able to physically access the server again until the middle of next week.  

[This]("http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_192.html") was my reference for the config, though I have a feeling that the problem may lie with a line I added "option netbios-node-type 8;"

I know, not a lot of information to work with but I'm really confused why anything you could put into the dhcpd.conf file would cause the server to time out like this.

Any ideas on why this happened would be much appreciated!

---

### Post by Vegan on 2009-08-08
Hard to see without the file being posted......

:mrgreen:

---

### Post by Iowan on 2009-08-09
I didn't see the "option netbios-node-type 8;" mentioned in the link you provided. I'm also a bit confused why the changes would take effect immediately after saving the file (without restarting the DHCP server).

---

### Post by ilikeyourflannel on 2009-08-12
As Iowan probably anticipated, an inspection of my command log showed that it dropped after I restarted dhcp.  Not after I saved the conf as I had previously stated. To clarify, the article I linked to wasn't my only source of info.  I'm also using the O'reilly Linux Network administrator's guide.

I do not have DNS setup on the server yet.  The IP of the server is 192.168.1.253 and the name is NorthServer.  I have several static hosts setup but since they are all the same format I figured one would show the syntax I'm using.  Perhaps the .local being pseudo top level is causing issues? 

I understand quite a few of the parts but the big picture isn't quite there for me yet.  Any help/suggestions/ideas are much appreciated.

Thanks!

[this is the full conf with the default comments removed]
```
ddns-update-style none;
log-facility local7;

option ntp-servers 192.168.1.253;
option netbios-name-servers 192.168.1.253;
option netbios-node-type 8;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.100 192.168.1.200;
    option domain-name-servers NorthServer.north.local;
    option domain-name "north.local";
    option routers 192.168.1.254;
    option broadcast-address 192.168.1.255;
    default-lease-time 86400;
    max-lease-time 172800;
    allow unknown-clients;
}
host xx {
    hardware ethernet 00:00:00:00:00:00;
    fixed-address 192.168.1.1;
}

```

---

### Post by ilikeyourflannel on 2009-08-21
I hate to make my third post a bump but I'm still scratching my head.  Any thoughts?

Thanks!

---

