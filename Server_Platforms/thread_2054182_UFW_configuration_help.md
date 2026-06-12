---
title: "UFW configuration help"
date: 2012-09-06
forum: Server Platforms
---

### Post by goybar on 2012-09-06
I could use some help with configuring my UFW.  It has been anything but "uncomplicated" for me today.

I have two interfaces eth0 and eth1

I want eth0 to only except tcp ports 22/443

I want eth1 to only communicate with one ip and one port

<eth1-ip> dst tcp port xyz to <dst-ip 1.1.1.1>

and

<src-ip 1.1.1.1> src tcp port xyz to <eth1-ip>

This seems like it should be easy, but I have not been able to get it to work.

I want all other traffic denied.  

Regards,

Chris

---

### Post by goybar on 2012-09-06
Is this correct:

[INDENT]ufw allow in on eth0 to any port 443 proto tcp
ufw allow in on eth0 to any port 22 proto tcp

ufw allow in on eth1 to 1.1.1.1/32 port 35555 proto tcp
[/INDENT]

Regards,

Chris

---

