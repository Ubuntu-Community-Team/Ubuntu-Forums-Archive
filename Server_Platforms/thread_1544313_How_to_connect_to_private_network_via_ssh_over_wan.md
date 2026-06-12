---
title: "How to connect to private network via ssh over wan links"
date: 2010-08-02
forum: Server Platforms
---

### Post by Thyagaraj on 2010-08-02
Hai all!

Could any one tell me how to connect to local network(private ip) via SSH over wan connection.
I've a dynamic ip address with dhcp enabled on the modem in the network 192.168.1.0.
for eg: if 200.254.78.6 is my public ip and 192.168.1.11 is the private network assingned to my machine, I would like to connect to a particular system 192.168.1.11 from my home using ssh.

Thanks you!

---

### Post by cdenley on 2010-08-02
Do you already have access to a SSH server on your network? Is 192.168.1.11 the SSH server, or is it another computer on the same LAN as your SSH server? What service/port do you want to connect to on 192.168.1.11?

---

### Post by Thyagaraj on 2010-08-02
Hi denley! it's glad to hear from you again

Actually my office has dynamic ip address and dhcp is enabled in the modem and the systems are in the network 192.168.1.0. At home with internet access I want to remotely connect to my office machines via SSH.
I can easily check dynamically changing office public ip address by simply running nslookup to dyndns domain name.



Thank You!

---

### Post by CharlesA on 2010-08-02
You'd need to forward the port SSH uses then connect to the external IP of the work network.

You can create a tunnel to whatever service on 192.168.11.

---

### Post by cdenley on 2010-08-03
> **Thyagaraj said:**
> Actually my office has dynamic ip address and dhcp is enabled in the modem and the systems are in the network 192.168.1.0. At home with internet access I want to remotely connect to my office machines via SSH.
I can easily check dynamically changing office public ip address by simply running nslookup to dyndns domain name.


You didn't answer any of my three questions. You want to use "port forwarding" with your SSH client to connect to your LAN servers through a SSH connection. When you answer my questions, I can be more specific.

---

### Post by Thyagaraj on 2010-08-03
192.168.1.11 is desktop editon and  ssh, openssh-server and openssh-client is installed in it and I have access to this(on the modem it's enabled). From the cloud servers I would like to connect to 192.168.1.11 via SSH(like how we connect via ssh over wan links if we have static public ip address)

I'm not sure what to use, give me all the possible options

Thank you!

---

