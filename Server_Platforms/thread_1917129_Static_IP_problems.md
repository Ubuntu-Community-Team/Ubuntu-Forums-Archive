---
title: "Static IP problems"
date: 2012-01-29
forum: Server Platforms
---

### Post by Shindokaku on 2012-01-29
I'm trying to set up a static IP for my server running Ubuntu Server 10.04. I've tried many google searches but nothing seems to work.
When I try to vi /ect/network/interfaces it tells me that i cannot open file for editing or something like that.
When I try to cd to /ect/network it tells me no such file or directory.

Please note that I am new to the whole server thing so please try to keep answers/replies simple.

---

### Post by Cheesemill on 2012-01-29
Take a look here:
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

---

### Post by 2F4U on 2012-01-29
It should be /etc/network/interfaces and you should place sudo before the command, since this is a system file and you need to edit it with administrator privileges.

---

### Post by Shindokaku on 2012-01-29
> **Cheesemill said:**
> Take a look here:
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

That's one of the ones I was trying...

> **2F4U said:**
> It should be /etc/network/interfaces and you should place sudo before the command, since this is a system file and you need to edit it with administrator privileges.

Tried: ```
sudo vi /ect/network/interfaces
``` didn't work, "E212 Can't open file for writing"
I already tried editing this after I did the "sudo su" command, and the sudo command.

If there's any additional information I need to provide please ask...

---

### Post by shumifan50 on 2012-01-29
Watch out for reversed chars it is NOT /ect it IS /etc

---

### Post by Shindokaku on 2012-01-29
> **shumifan50 said:**
> Watch out for reversed chars it is NOT /ect it IS /etc

Thank you, i kept reading it as /ect

Before I make any changes could someone look and see if this looks ok:
```

address 192.168.1.103
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

---

### Post by shumifan50 on 2012-01-29
It looks OK but it will depend on the IPs you are using in your network. The settings you show will work where the IPs are 192.168.1.xxx

---

