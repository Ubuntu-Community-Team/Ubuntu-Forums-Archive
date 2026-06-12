---
title: "Apache respond to additional IP"
date: 2008-10-12
forum: Server Platforms
---

### Post by wgregori on 2008-10-12
Can someone briefly explain how I get Apache to bind to a different IP address.  Here's what I need to do:

1) Add an additional IP address to my existing NIC

2) Steps necessary to bind Apache to that new IP

Thanks,
Wayne

---

### Post by wgregori on 2008-10-12
Trying to bind Apache to a different IP.

Apache will not start and gives me this error:
(98)Address already in use: make_sock: could not bind to address 192.168.2.99:80

I think I correctly setup my NIC with the additional IP here's what my interfaces file looks like:

iface eth0 inet static
        address 192.168.2.3
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1


iface eth0:0 inet static
        address 192.168.2.99
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

Any ideas?
Thanks,
Wayne

---

### Post by cariboo on 2008-10-13
Have a look at /etc/apache2/ports.conf, from what i understand you can set it up this way:

```
Listen 80:192.168.2.3
Listen 80:192.168.2.99
<ifModule mod_ssl.c>
   Listen 443:192.1168.2.2
   Listen 443:192.168.2.99
</IfModule>
```


Jim

---

### Post by brian77095 on 2008-10-13
cariboo907,

The port you gave SSH is the default port right?  For tighter security you should assign some thing out of the ordinary right?  Is there a range you should choose form?  Also if he was to make that change in the /portsconf were else does he need to make that change?  Router?  SSH set up?

Thanks for the info!!

wgregori hope you find these questions useful too I did not mean to take your thread over...

B

---

### Post by wgregori on 2008-10-13
Figured it out... my NIC and Apache configuration was correct... my mail server (surgemail) was sitting on all ports.  I have to limit the surgemail installation to binding to a single IP.

Thanks,
Wayne

---

