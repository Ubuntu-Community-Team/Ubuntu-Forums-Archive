---
title: "UFW not working?"
date: 2009-10-06
forum: Security
---

### Post by emnaki on 2009-10-06
I am trying to use GUFW. I set a test to deny all connections from and to 80, which is http right?

here is my ufw status:

```

laptop:~$ sudo ufw status
Status: active

To                         Action  From
--                         ------  ----
Anywhere                   DENY    80
80                         DENY    Anywhere


```

But I can still access the webpages? Which this message is proof. What am I doing wrong?

---

### Post by XCan on 2009-10-06
That's inbound traffic. I don't think GUFW can set output rules.

---

### Post by wojox on 2009-10-06
Try clearing the private data in your browser.

---

### Post by cdenley on 2009-10-06
> **XCan said:**
> That's inbound traffic. I don't think GUFW can set output rules.

I'm pretty sure it doesn't. UFW will not filter outbound traffic. It only filters inbound traffic unrelated to established connections.

---

### Post by lovinglinux on 2009-10-06
> **cdenley said:**
> I'm pretty sure it doesn't. UFW will not filter outbound traffic. It only filters inbound traffic unrelated to established connections.

Yes. UFW only blocks incoming unrequested connections.

---

### Post by emnaki on 2009-10-07
Thanks everyone for your replies. I have a really strange problem which I hope some of you could help with:

Here is the problem, per packet pings are really slow (nearly x2 slower), but overall connection speed is normal and very fast (ie download speed via bt). I was hoping turning on ufw will help but it did not. But what did help was very strange.
```
Status: active

To                         Action  From
--                         ------  ----
Anywhere                   DENY    80
```
(I had to restart my computer to make the above apply by the way). Now my pings and telnet are back to normal, but I can't browse webpages! All my request go from localhost to localhost (probably mean can't contact DNS). Which is kind of expected since I block src port 80. But I don't understand what the problem is with the slowdown and how to fix it?

---

### Post by Rob_H on 2009-10-07
What exactly are you trying to block with your UFW rule?

---

### Post by emnaki on 2009-10-07
I'm trying to make my telnet faster. Blocking 80 works, but I don't know why?

---

### Post by kevdog on 2009-10-08
Im not going to ask why you are using telnet when you should be using ssh.

If you want to block access to outbound connections that access port 80 remotely, then do the following:

sudo /sbin/iptables -A OUTPUT -p tcp --dport 80 -j DROP

---

### Post by scottuss on 2009-10-08
> **kevdog said:**
> Im not going to ask why you are using telnet when you should be using ssh.

If you want to block access to outbound connections that access port 80 remotely, then do the following:

sudo /sbin/iptables -A OUTPUT -p tcp --dport 80 -j DROP


We shouldn't really tell people what they shouldn't do (Ah, the irony!) however I feel that you have a valid point. The OP should be made aware that telnet communications are not encrypted, and as such anything done in a telnet session can potentially be seen by others on the Internet.

SSH solves this problem by encrypting all traffic, therefore making it near enough impossible to snoop on.

---

### Post by Rob_H on 2009-10-08
> **emnaki said:**
> I'm trying to make my telnet faster. Blocking 80 works, but I don't know why?

Firewall settings have nothing to do with network throughput unless you're exposing a service that's getting hammered with traffic. Are you intentionally exposing a service on that machine? If not, the proper UFW setup is to block everything:

```
sudo ufw default deny
sudo ufw enable
```

You don't need any other rules in this case. Outbound Telnet connections will still work. Although, as others have suggested, you might want to consider SSH instead of Telnet. But that's a different topic.

---

### Post by __p1n__ on 2009-10-08
> **Rob_H said:**
> Firewall settings have nothing to do with network throughput unless you're exposing a service that's getting hammered with traffic. 

That's not strictly true.  A badly-designed iptables configuration will slow down kernel packet processing at the various netfilter hooks.

---

### Post by sopadeajo on 2009-10-08
> **XCan said:**
> That's inbound traffic. I don't think GUFW can set output rules.

That is strange indeed because Firestarter (which is said to be just a GUI) can (i just tried, and blocked all outbound traffic).

---

### Post by lovinglinux on 2009-10-09
> **sopadeajo said:**
> That is strange indeed because Firestarter (which is said to be just a GUI) can (i just tried, and blocked all outbound traffic).

Yes Firestarter can do that. Blocking outgoing connections is available through iptables, so any firewall manager like Firestarter or UFW could potentially create such rules if they are designed to do so. UFW is not designed to create iptables blocking rules for outgoing connections, while Firestarter is.

---

### Post by emnaki on 2009-10-09
> **Rob_H said:**
> Firewall settings have nothing to do with network throughput unless you're exposing a service that's getting hammered with traffic. Are you intentionally exposing a service on that machine?

I really wish I knew. But I've been doing some testing after getting some ideas from this thread. I have three machines, two laptops and a desktop. The two laptops have jaunty installed. The desktop has intrepid. I installed wireshark on all three and then started detecting traffic on a clean startup. Lo and behold, my two jaunty machines are outputing a lot of packets (a lot of [SYN] packets from different ports which I suspect is spawned by http daemon or something), after blocking 80 the packets stop. while the intrepid machine is dead silent (apart from modem echos). Is there something wrong with Jaunty?

---

### Post by Rob_H on 2009-10-09
> **emnaki said:**
> I really wish I knew. But I've been doing some testing after getting some ideas from this thread. I have three machines, two laptops and a desktop. The two laptops have jaunty installed. The desktop has intrepid. I installed wireshark on all three and then started detecting traffic on a clean startup. Lo and behold, my two jaunty machines are outputing a lot of packets (a lot of [SYN] packets from different ports which I suspect is spawned by http daemon or something), after blocking 80 the packets stop. while the intrepid machine is dead silent (apart from modem echos). Is there something wrong with Jaunty?

If you're not knowingly running a server on the Jaunty boxes and you see a whole bunch of outbound SYN packets, it sounds like your Jaunty boxes have been hacked or have some kind of malware running on them. You can run this command to try to figure out what program is responsible for the traffic (first column):

```
sudo lsof -i
```

What IP addresses are the outbound packets going to? If you could post the output of that command here, that might be useful.

---

