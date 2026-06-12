---
title: "Server cannot be seen on Network"
date: 2010-09-14
forum: Server Platforms
---

### Post by Jcarr_toonist on 2010-09-14
Recently my OS hard drive died on my wonderful ubuntu server, so I took that chance and upgraded it to 10.04 ...  

Everything works great except I cannot get any other computer in the house(windows and linux) to see the computer or the samba shares. It is not just the shares that are missing but the server itself does not show up. For my windows machine I verified the workgroup is correct and it still does not show up as a device on the network, ditto for my ubuntu desktop install. 

Here is my smb.conf

```
 [global]
workgroup = SWARM

[Net Drive]
path = /media/netdrive
read only = Yes
guest ok = Yes
```

Its basic, but I have tried the default smb.conf with similar results. Here is the output of smbclient -L

```
Domain=[SWARM] OS=[Unix] Server=[Samba 3.4.7]

        Sharename       Type      Comment
        ---------       ----      -------
        Net Drive       Disk
        IPC$            IPC       IPC Service (Samba 3.4.7)
Domain=[SWARM] OS=[Unix] Server=[Samba 3.4.7]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        WORKGROUP            WRT610N

```

Having my WRT610N listed as the Master seems strange to me but I not really sure what the Master is so that could be perfectly alright.

---

### Post by CharlesA on 2010-09-14
Can you connect via ip from a Windows box?

\\ipaddressgoeshere\share

Able to ping it by hostname or ip?

My bet is that you need some sort of DNS server.

I just tried that basic smb.conf on my test VM and I was able to see the share fine.

My environment has a local DNS server. :)

---

### Post by Jcarr_toonist on 2010-09-15
> My bet is that you need some sort of DNS server.

Thanks :D That seemed to do the trick. I opted to not install the DNS server during installation because I didn't think I would need it. Live and learn I suppose.

---

### Post by CharlesA on 2010-09-15
> **Jcarr_toonist said:**
> Thanks :D That seemed to do the trick. I opted to not install the DNS server during installation because I didn't think I would need it. Live and learn I suppose.

dnsmasq is a nice dns server to use for small networks. You don't need to install full blown BIND.

---

### Post by dtech on 2010-09-16
If you experience further problems you could also try to let samba act as a WINS server.

---

