---
title: "NFS server ports keep changing"
date: 2006-05-22
forum: Server Platforms
---

### Post by juicybananahead on 2006-05-22
Hi there,

Whenever I reboot my server, the ports used by mountd and statd seem to change, always in the region of 860 and 980, respectively. I wouldn't mind, except that my server is firewalled and I have to mess with the server's iptables config if I want to mount an NFS share on a client! Can anybody tell me how to nail down the ports used by an NFS server?

Thanks,
// dave

---

### Post by joft on 2006-05-22
Hi,

you have to edit /etc/default/nfs-common (for statd) and /etc/default/nfs-kernel-server (vor mountd). In the first one search for the variable STATDOPTS and append -p <portnumber> (inside the "). In the second one you need to look for RPCMOUNTDOPTS and use the same thing: -p <anotherport> .

---

### Post by juicybananahead on 2006-05-22
Hi joft,

Thanks for the reply. One quick question though, when I do an "rpcinfo -p <se.rv.er.ip>" I get the following:

```


    100005    1   udp    862  mountd
    100005    1   tcp    865  mountd
    100005    2   udp    862  mountd
    100005    2   tcp    865  mountd
    100005    3   udp    862  mountd
    100005    3   tcp    865  mountd
    100024    1   udp    980  status
    100024    1   tcp    983  status

```

Which port should I be specifying in the nfs config files in /etc/default - udp or tcp?

Thanks,
// Dave

---

### Post by joft on 2006-05-22
Hi,

AFAIK you cannot specify (with the -p option) if it's a udp or a tcp port. mountd and statd will listen on both protocols (tcp and udp) on the port you specify.

---

### Post by juicybananahead on 2006-05-23
Thanks Joft, that worked a treat.

// Dave

---

