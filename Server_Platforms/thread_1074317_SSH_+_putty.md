---
title: "SSH + putty"
date: 2009-02-19
forum: Server Platforms
---

### Post by P8ntBal1551 on 2009-02-19
I want to only be able to access my server )with ssh installed on it) from my computer, i found [this]("http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html") tutorial and i appended
> -: ALL EXCEPT root darren busa asp:192.168.1.102
to the end of /etc/security/access.conf

and
> account required pam_access.so
to the end of /etc/pam.d/sshd

but I can still sign in on other computers on the network

-my subnet ip is 192.168.1.102
-darren, busa and asp are the 3 users i want to be able to sign in as
-i can't try from out of my home network because my isp blocks all ports

---

### Post by windependence on 2009-02-19
I seriously doubt your ISP blocks 22.

Have you thought about limiting the computers that can sign on via MAC address?

The place to do this would be at the firewall, only allowing port 22 access to a certain MAC address (yours).

-Tim

---

### Post by bigbearomaha on 2009-02-19
This may be of some help

[http://www.debian-administration.org/articles/87](http://www.debian-administration.org/articles/87)


Have fun, learn lots

Big Bear

---

### Post by Nicador on 2009-02-19
If you are connecting to your server using your External IP Address or (sub)domain maybe you have to forward the SSH designated(usually 22) port to the server's LAN IP address.
That is if you are behind a router or firewall.
Or if the ISP closed the 22 port (i serious doubt it) you can change the SSH port...

```
vi /etc/ssh/sshd_config
```

Cheers!
Adrian

---

### Post by P8ntBal1551 on 2009-02-19
> **bigbearomaha said:**
> This may be of some help

[http://www.debian-administration.org/articles/87](http://www.debian-administration.org/articles/87)


Have fun, learn lots

Big Bear

I did that tutorial and i changed /etc/hosts.allow to have all the ip addresses on my network
and /etc/hosts.deny to just be set to all
then i couldn't sign into it from my computer on my network so i wen to the server and deleted all the rules i set, but now i can get to the logon prompt and type in the user name but it then says that the server unexpectedly closed the network connection.
...help?

---

### Post by P8ntBal1551 on 2009-02-19
Bump?

---

