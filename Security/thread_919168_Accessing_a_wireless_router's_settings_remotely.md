---
title: "Accessing a wireless router's settings remotely?"
date: 2008-09-13
forum: Security
---

### Post by secondstage on 2008-09-13
When I put my IP address (the one that my ISP assigns) into Firefox, I can access all of the settings of my router as if I was behind the router. I have not tried this out from another computer yet. Would this be a potential security threat?

---

### Post by CarrotRevelation on 2008-09-13
> **secondstage said:**
> When I put my IP address (the one that my ISP assigns) into Firefox, I can access all of the settings of my router as if I was behind the router. I have not tried this out from another computer yet. Would this be a potential security threat?

Yes, any time you have a server accessible to people you don't trust it is a security vulnerability.

1. When you access it from a browser does the url(address bar) say http or https?

2. Do you use a user name and password to log into the webpage?

Depending on what type of router you have you probably need to disable remote management immediately.

---

### Post by cariboo on 2008-09-14
I agree with CarrotRevelation, you are leaving yourself wide open to anyone that wants to do what they want with your router. Access your router from it's internal ip  address and turn off remote access. You should still be able to access the router from your internal network with remote access turned off. As a precaution I would also change the Admin username and password using a strong password.

Jim

---

### Post by brian_p on 2008-09-14
> **secondstage said:**
> When I put my IP address (the one that my ISP assigns) into Firefox, I can access all of the settings of my router as if I was behind the router. I have not tried this out from another computer yet. Would this be a potential security threat?

A router has two IP addresses, an internal one which you choose and an external one assigned by your ISP. But it only has one MAC address.

So

```
user@laptop:~$ sudo arping -I eth2 -c 2 192.168.0.1
ARPING 192.168.0.1 from 192.168.0.15 eth2
Unicast reply from 192.168.0.1 [00:30:EB:C6:03:A6]  2.298ms
Unicast reply from 192.168.0.1 [00:30:EB:C6:03:A6]  4.268ms
Sent 2 probes (1 broadcast(s))
Received 2 response(s)
```

and

```
user@laptop:~$ sudo arping -I eth2 -c 2 80.xxx.xx.xxx
ARPING 80.xxx.xxx.xxx from 192.168.0.15 eth2
Unicast reply from 80.xxx.xxx.xxx [00:30:EB:C6:03:A6]  2.234ms
Unicast reply from 80.xxx.xxx.xxx [00:30:EB:C6:03:A6]  2.049ms
Sent 2 probes (1 broadcast(s))
Received 2 response(s)
```

I think what is happening is: the router receives a request to send a packet to port 80 at 80.xxx.xx.xxx. It uses ARP to determine the MAC address of the router to forward the packet to and gets itself.

The result is no different from connecting to the router on 192.168.0.1. There is no security threat, potential or otherwise, and the web server on the router remains completely safe from possible connection attempts from the internet. You can check the state of port 80 on your router from an external machine at [http://www.canyouseeme.org](http://www.canyouseeme.org) or [www.proxy.org](www.proxy.org).

---

### Post by secondstage on 2008-09-14
@CarrotRevelation: It says http://

@brain_p: canyouseeme.org said that port 80 was not accessable. 

If port 80 isn't open externally, then it's safe, right? Just in case it isn't,  I'll check if remote access can be turned off. Thanks.

---

### Post by brian_p on 2008-09-14
> **secondstage said:**
> @CarrotRevelation: It says http://

@brain_p: canyouseeme.org said that port 80 was not accessable.

Fingers! Its 'brian'. 

> If port 80 isn't open externally, then it's safe, right?

Perfectly correct.

> Just in case it isn't,  I'll check if remote access can be turned off. Thanks.

There is no 'Just in case'. What you observed is normal and is the way routers work when contacted on the internal interface. But there is no harm in checking with other sites similar to canyouseeme and becoming familiar with your router's settings.

By the way, if your router has a remote access and you wanted to enable it (which you probabaly don't) there is nothing foolhardy about that. There are a number of ways to secure access, foremost being a good strong password.

---

### Post by secondstage on 2008-09-14
> 
Quote:
Originally Posted by secondstage View Post
@CarrotRevelation: It says http://

@brain_p: canyouseeme.org said that port 80 was not accessable.
Fingers! Its 'brian'. 

My bad.

Looked at the settings and turned off remote access. One step closer to "security".

---

