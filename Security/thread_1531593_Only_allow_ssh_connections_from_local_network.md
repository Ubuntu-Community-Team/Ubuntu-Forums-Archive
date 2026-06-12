---
title: "Only allow ssh connections from local network"
date: 2010-07-15
forum: Security
---

### Post by winxpuser on 2010-07-15
As the title suggest I would like to limit ssh connections to my ssh enabled server to only allow connections from my local network. Are there any decent guides to show me how I can do this. 

My Network setup: 

1 desktop running ubnutu 8.10 (client) with an internal ip of 192.168.2.2
1 laptop running ubuntu 8.10 (the ssh enabled server) with an internal ip of 192.168.2.3

Thx, 
Dave

---

### Post by iponeverything on 2010-07-15
If you do not have port forwarding setup on your Internet connected device -- cable modem, wifi router or whatever -- the 192.168.x.x addresses will not be reachable from the outside. Those address are not routeable on the Internet they in the RFC1918 private address space and will be dropped by the first serious router that sees them.

---

### Post by winxpuser on 2010-07-15
I understand that but what happens if someone discovers my extrenal IP address, will they be able to connect or is that what you are saying the port forwarding would allow them to do and so long as I do not enable it even if they did discover my external IP address they would not be able to connect since I did not forward port 22 in my router for 192.168.2.3. 

My apologies if this seems like a redundent question but I just want to make 100% sure I understand the process. 

Dave.

---

### Post by endotherm on 2010-07-15
yup. just don't forward the ssh port on the router, and no one should be able to get to your hosts port 22. 

if you do want to be extra sure though, you can install gufw if the server has a desktop. then create a rule with these attributes (use the "Advanced" tab on rule creation)
```

To: <your ssh server IP>
From: <your subnet in 192.168.X.0/24 notation>
Type: TCP
To Port: 22

```

so if you have the network 192.168.55.x and your ssh server is has 192.168.55.48 then it would be somthing like:
```

To: 192.168.55.48
From: 192.168.55.0/24
...

```

you can also look into failtoban and denyhosts for blocking folks that are trying to break in. 

of course, all this is just depth of defense. your router firewall is taking care of the issue for the most part, so if you trust it, then you are already done.

---

### Post by endotherm on 2010-07-15
> **winxpuser said:**
> I understand that but what happens if someone discovers my extrenal IP address, will they be able to connect or is that what you are saying the port forwarding would allow them to do and so long as I do not enable it even if they did discover my external IP address they would not be able to connect since I did not forward port 22 in my router for 192.168.2.3. 

My apologies if this seems like a redundent question but I just want to make 100% sure I understand the process. 

Dave.

in a standard statefull firewall configuration, all outbound connections are **allowed**, and all incoming connections are **blocked** unless:
1) they are part of an existing connection, initiated from inside the network or
2) the router "forwards" the TCP/22 port. 

port forwarding allows you to set a port that will allow incoming connections, and routes them to a specific address. if I wanted my ssh servers to be accessible to the outside world, I would have to forward port 22 so that external people can connect to it. otherwise TCP\22 will appear closed to them when they try to connect.

there are several services you can use to see what ports you have open on your router. one of the better ones is [SheildsUp]("https://www.grc.com/x/ne.dll?bh0bkyd2") at Gibson Research. another is [http://www.canyouseeme.org/](http://www.canyouseeme.org/) (good for testing just one port)

---

### Post by winxpuser on 2010-07-15
Thanks for the replies I will enable the firewall rules once I get remote desktop working which I have been unsuccessful in doing so far but I will open up another topic for that instead of going off topic here. 

Thanks Again,
Dave.

---

### Post by bodhi.zazen on 2010-07-15
You can do this via at least 3 methods.

1. Firewall.

ufw - sudo ufw allow proto tcp from 192.168.2.0/24 to server_ip port 22
iptables - sudo iptables -A INPUT -p tcp --dport 22 -s 192.168.2.0/24 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 22 -j DROP

2. sshd_config - see allow rules (AllowUsers - allow user@ .... )


3. tcpwrappers

[http://linuxhelp.blogspot.com/2005/10/using-tcp-wrappers-to-secure-linux.html](http://linuxhelp.blogspot.com/2005/10/using-tcp-wrappers-to-secure-linux.html)


IMO you are best off using keys and disabling password authentication altogether.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by anomie on 2010-07-15
To the already good suggestions I'd add: 

If you are really concerned about someone cracking your router and accessing ssh on your private subnet, here's a very quick measure -- add the following to **/etc/hosts.deny**. 

```
sshd : 192.168.0.1
```

(Replace the address with your router/NAT device internal network IP.) 

The same thing can be accomplished with sshd_config USER@PATTERN directives, iptables, and pam_access (if Ubuntu includes it). I wouldn't worry about it too much, though. Just turn off port forwarding on your router/NAT device and check for firmware updates from time to time.

---

