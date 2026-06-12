---
title: "ssh doesn't work from internet"
date: 2010-05-02
forum: Server Platforms
---

### Post by velden on 2010-05-02
I can't connect to my ssh-server (on ubuntu 10.04) from any external address. The error in putty is "connection timed out". From my internal network, everything works fine, even if I select my external IP address and port in putty as the destination.

This is what I have done so far:


[LIST=1]
[*]installed open ssh with the ubuntu server 10.04 cd
[*]set up port forwarding (11041) in my router (seems to work ok, port is open according to "shields up")
[*]configured ssh to use port 11041 in /etc/ssh/sshd_config
[*]changed tcp and udp ssh port in /etc/services to 11041
[*]enabled UFW and did sudo ufw allow ssh
[/LIST]
UFW status yields:
```
sjoerd@ubuntu:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
11041                      ALLOW IN    Anywhere
```I searched through the internet but I was unable to find a solution. Does someone have an idea?

---

### Post by hictio on 2010-05-02
You have restarted the sshd daemon on your Ubuntu Server box after editing the /etc/ssh/sshd_config file, right?
Or at least, did a:

```

sudo /etc/init.d/sshd reload ENTER

```

---

### Post by velden on 2010-05-02
> **hictio said:**
> You have restarted the sshd daemon

Yep, restartet the server more than once.

---

### Post by hictio on 2010-05-02
That's right, besides. I've noticed after posting that it is working A OK within the confines of your LAN, that is somehow good, since it leaves out an sshd misconfiguration as well as an iptables firewall glitch as well.
I would double or triple check the port forwading settings, make sure it accepts connections on the alternative port, and also that it forwards to that same port to the internal IP address of the Ubuntu Server box in your LAN; another thing to look out might be to check that the destination it is set to the correct IP address of the Ubuntu Server inside the LAN.

---

### Post by velden on 2010-05-06
Thanks for your help: I solved the problem. The router (sweex R0003) was simply not working properly. It forwarded www  (port 80) correctly but for an unknown reason to me forwarding port 11041 was not working. Now I installed another router and everything works fine.

---

