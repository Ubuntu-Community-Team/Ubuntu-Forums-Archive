---
title: "How to setup Local Test Server"
date: 2008-04-03
forum: Server Platforms
---

### Post by kl545 on 2008-04-03
Hello,

This has probably been answered numerous times, but I would feel better if I got a custom response to my question.

Basically I would like to follow this tutorial:
[http://www.howtoforge.com/perfect_server_ubuntu7.10_p3](http://www.howtoforge.com/perfect_server_ubuntu7.10_p3)

But instead I would like to set it up for local access only, invisible to the outer world.  

In my setup I would like to have two computers.  One computer would be used for checking out projects for work, and the other computer would act as the repository and staging server. 

How would I go about setting up the following files for what I described above?
/etc/network/interfaces  
/etc/hosts

Is there anything else I should know?

In addition, how would I be sure that my test server is not visible to the big bad world?

Thanks in advance.

---

### Post by uncannybuzzard on 2008-04-03
Hosts file (replace IP, fully qualified domain name, and hostname in second line):

```
127.0.0.1       localhost
IP address FQDN  hostname
```

as far as the interfaces file, are you using a static IP or dhcp? for static, which is most likely for a server, it will look something like this:

```
iface eth1 inet static
        address xxx.xxx.xxx.xxx
        netmask 255.255.255.xxx
        network 216.234.xxx.xxx
        broadcast 216.234.xx.xxx
        gateway 216.234.xxx.xxx
```

---

