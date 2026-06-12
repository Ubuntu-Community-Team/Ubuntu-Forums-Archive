---
title: "&quot;sudo nmap -sP 192.168.1.0/24&quot;"
date: 2010-02-08
forum: Security
---

### Post by miggerish on 2010-02-08
Hi, I am not experienced in networks at all.  I just wanted to scan my wireless to see how many other computers are connecting to the same wireless network as me.

I did this command:

```
sudo nmap -sP 192.168.1.0/24
```

And I got this result:

```
ubuntu@Ubuntu:~$ sudo nmap -sP 192.168.1.0/24

Starting Nmap 5.00 ( http://nmap.org ) at 2010-02-08 10:53 PST
Host serendip-a7ddea (192.168.1.66) is up.
Host daniel-PC (192.168.1.67) is up (0.016s latency).
MAC Address: 00:22:69:81:5F:30 (Hon Hai Precision Ind. Co.)
Nmap done: 256 IP addresses (2 hosts up) scanned in 4.28 seconds

```

My question is, I know who "daniel-PC" is, it is my roommate.  But I do not know who "serendip-a7ddea" is..  Is this a possible security risk?  What do you think I should do?

Also, what does it mean, "256 IP addresses (2 hosts up)"?  256 IP addresses seems like a lot for a small house network.  What does this represent?

Thanks.

I am using Ubuntu the latest distribution.

---

### Post by FuturePilot on 2010-02-08
I take it you're on wireless? Is it secured?

When you scan 192.168.1.0/24 you are scanning the entire range of 192.168.1.0 - 192.168.1.255. That's where the 256 IP addresses is coming from.

I would start with asking your roommate if they might have another device connected to the network.

---

### Post by miggerish on 2010-02-08
> **FuturePilot said:**
> I take it you're on wireless? Is it secured?

When you scan 192.168.1.0/24 you are scanning the entire range of 192.168.1.0 - 192.168.1.255. That's where the 256 IP addresses is coming from.

I would start with asking your roommate if they might have another device connected to the network.

Yes it is wireless network.  No, he does not want to secure it.  So it has no security.  Does 256 Ip addresses mean that 256 different IPs have connected to my wireless network?

And my roommate said he does not have any other devices.

Thanks.

---

### Post by FuturePilot on 2010-02-08
> **miggerish said:**
> Yes it is wireless network.  No, he does not want to secure it.  So it has no security.  Does 256 Ip addresses mean that 256 different IPs have connected to my wireless network?

And my roommate said he does not have any other devices.

Thanks.

Since it has no security then I would assume it's someone leeching off your internet. Security threat? Maybe. Depends on what they are doing. They could just be using it as free internet, or they could be sniffing your traffic, or they could be using your internet for illegal things which would lead a trail back to you instead of them. I would strongly suggest securing the wireless. Is there any reason why it needs to be completely open? At the very least add MAC address filtering. But that can be bypassed relatively easily and your packets are still flying through the air in plain text.

> Does 256 Ip addresses mean that 256 different IPs have connected to my wireless network?
No. Like I said before when you tell nmap to scan 192.168.1.0/24 you are telling it to scan the range of 192.168.1.0 - 192.168.1.255 which is a range of 256 possible IP address. 

[http://en.wikipedia.org/wiki/CIDR_notation]("http://en.wikipedia.org/wiki/CIDR_notation")
[http://en.wikipedia.org/wiki/Subnetwork]("http://en.wikipedia.org/wiki/Subnetwork")

---

### Post by CharlesA on 2010-02-08
> **miggerish said:**
> Yes it is wireless network.  No, he does not want to secure it.  So it has no security.  Does 256 Ip addresses mean that 256 different IPs have connected to my wireless network?

And my roommate said he does not have any other devices.

Thanks.
It means there are 256 possible addresses that can be used. Technically it's 254, since you cannot use 192.168.1.0 and 192.168.1.255.

It would definitely be a good idea to secure the wireless. Is there any reason why yer roommate doesn't want it to be secured?

EDIT: FuturePilot beat me to it.. that's what I get for getting distracted in the middle of a post.

---

### Post by miggerish on 2010-02-08
> **CharlesA said:**
> It means there are 256 possible addresses that can be used. Technically it's 254, since you cannot use 192.168.1.0 and 192.168.1.255.

It would definitely be a good idea to secure the wireless. Is there any reason why yer roommate doesn't want it to be secured?

EDIT: FuturePilot beat me to it.. that's what I get for getting distracted in the middle of a post.

Okay, I will ask him, and then I will do it myself. (he doesnt know how to).  Is there any way to add the security to the router/modem thing without connecting via ethernet cable? I don't have an ethernet cable to connect my computer physically to the router/modem object.  Can it be done wirelessly?  Thanks.

---

### Post by FuturePilot on 2010-02-08
> **miggerish said:**
> Okay, I will ask him, and then I will do it myself. (he doesnt know how to).  Is there any way to add the security to the router/modem thing without connecting via ethernet cable? I don't have an ethernet cable to connect my computer physically to the router/modem object.  Can it be done wirelessly?  Thanks.

It can be configured over wireless but it depends on how the router is configured. Sometimes managing the router over wireless is disabled by default.

---

### Post by CharlesA on 2010-02-08
> **FuturePilot said:**
> It can be configured over wireless but it depends on how the router is configured. Sometimes managing the router over wireless is disabled by default.

I've configured one of my wireless routers over wireless (running DD-WRT) but if you change the key, you will need the key to reconnect (but that's a given).

---

### Post by wirelessmonkey on 2010-02-08
```
Host serendip-a7ddea (192.168.1.66) is up
```


In order to scan this network, you had to be on it too.  Since you knew the other machine, and there are only 2 devices, the above address is *you*

---

### Post by smc18 on 2010-02-08
> **wirelessmonkey said:**
> ```
Host serendip-a7ddea (192.168.1.66) is up
```


In order to scan this network, you had to be on it too.  Since you knew the other machine, and there are only 2 devices, the above address is *you*

x2 That's true

---

### Post by FuturePilot on 2010-02-08
Wow, good catch. I guess I was assuming the OP had omitted their own computer. Never assume [-X

---

### Post by Sarmacid on 2010-02-09
In my experience there should be 3 IPs on that network, Router, your PC and your roomate's PC, not sure why you only get 2 though.

---

### Post by cariboo on 2010-02-09
When I run the command, my SMC access point rarely shows up in the scan, all the rest of the computers, including the router running dd-wrt do. The access point is an SMC 2804WBR router, it has a static ip address, and DHCP is turned off. I have no idea why it doesn't show up.

---

### Post by wirelessmonkey on 2010-02-10
Most relatively modern home routers won't respond to a default nmap scan from inside the network, unless features (firewall, upnp, etc..) have been configured or added/removed.

---

