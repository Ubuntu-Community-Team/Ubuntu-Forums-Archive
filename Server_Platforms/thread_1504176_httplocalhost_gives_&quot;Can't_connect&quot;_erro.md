---
title: "http://localhost gives &quot;Can't connect&quot; error in browser, http://192.168.0.100 works"
date: 2010-06-07
forum: Server Platforms
---

### Post by kayjaygee_13 on 2010-06-07
I have Ubuntu 10.04 32-bit server edition installed in a VirtualBox VM with the LAMP, DNS and SSH packages. VirtualBox is running on Vista Home Premium 64-bit host OS. The hostname during the installation has been set as "ubuntu-server". Now when I point my browser to [http://localhost/](http://localhost/) in Firefox, I get an error message saying that it can't connect, but if I put in the actual IP (assigned to eth0 in ifconfig) [http://192.168.0.100/](http://192.168.0.100/) in the address bar, I get the default Apache message saying that it's working.

Also, if I browse to [http://ubuntu-server/](http://ubuntu-server/), I get the Apache default message. Can anybody please help me figure this out. I'm sure it is something trivial, but this is my first experience with Ubuntu (and Linux, Unix, etc.). Thank you in advance.

---

### Post by Ryan Dwyer on 2010-06-07
Localhost always refers to the same machine. When you browse to it from your desktop/host it's not trying to connect to ubuntu-server.

---

### Post by kayjaygee_13 on 2010-06-07
Ryan, thank you for clearing that up. I did some more reading and found that by using the NAT network interface in the VirtualBox VM along with port-forwarding, I was able to view the site by typing [http://localhost](http://localhost) in a browser window in the host OS.

---

### Post by stefanadelbert on 2010-06-07
[FONT="Courier New"]localhost[/FONT] can actually resolve to any hostname you like, but usually (should always really) refers to the loopback IP address 127.0.0.1. It's like saying "localhost"=me. This is so that a machine can refer to itself using the network alias [FONT="Courier New"]localhost[/FONT]. This is defined in the mapping file /etc/hosts in Ubuntu, but may be different on other distros.

It's possible to add other hosts to this mapping file, e.g. you could add the following to /etc/hosts on a new line:

```
192.168.0.100 myfileserver printserver
```

and then both [FONT="Courier New"]http://myfileserver[/FONT] and [FONT="Courier New"]http://printserver[/FONT] would resolve to [FONT="Courier New"]http://192.168.0.100[/FONT], but just on the machine that has the modifed [FONT="Courier New"]/etc/hosts[/FONT].

---

### Post by kayjaygee_13 on 2010-06-08
stefanadelbert, thank you for teaching me something new. :-D

---

