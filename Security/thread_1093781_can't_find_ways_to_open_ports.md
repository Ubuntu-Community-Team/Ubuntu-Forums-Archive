---
title: "can't find ways to open ports"
date: 2009-03-11
forum: Security
---

### Post by imparja2 on 2009-03-11
I've installed firestarter and added rules to allow service to several of these ports but for some reason when I run tests to check if they're open they say they're all closed. Is there something wrong with the test or is firestarter to cause of blocking ports I want to open? please How can I determine and fix it step by step?

---

### Post by madverb on 2009-03-11
paste the output of
```
sudo iptables -L
```
here.

---

### Post by cdenley on 2009-03-12
> **imparja2 said:**
> I've installed firestarter and added rules to allow service to several of these ports but for some reason when I run tests to check if they're open they say they're all closed. Is there something wrong with the test or is firestarter to cause of blocking ports I want to open? please How can I determine and fix it step by step?

How are you testing your ports? Are you using a router? What are you trying to accomplish with a firewall? Also, posting the output for this command in addition to the one mentioned may be helpful:
```

netstat -tln

```

---

### Post by Neo_The_User on 2009-03-12
My dad uses Firestarter (used to use the SELinux GUI in Fedora) to secure out LAN. Might wanna try those out.

---

### Post by The Cog on 2009-03-12
If the the test is saying that the ports are closed then the firewall is probably allowing the packets through. If a firewall is blocking packets to a port, then you would normally get no reply when you try to talk to the port. My guess is that the operating system is replying to your connection request and saying the port is closed because there is no application listening for incoming calls on the port.

Use netstat to see if there is in fact an application listening on the port in question.

---

### Post by imparja2 on 2009-03-15
so for example if I'm downloading from p2p connections the closed ports will then open since I'm running this application. So how do I get the ports listening what commands should I use. If they're listening will that mean the test at grc shieldsup will confirm they're open?. Is this the type of test I should be doing?

---

### Post by bodhi.zazen on 2009-03-15
Not exactly.

Take a look at the tcp protocol. new packets are rejected, so your ports are closed.

related and established packets are accepted, but even though these packets are accepted your ports are still closed.

"grc shieldsup" is not really considered to be the best source of information.

[http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Connection_establishment](http://en.wikipedia.org/wiki/Transmission_Control_Protocol#Connection_establishment)

Then you will need to look at how iptables works.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

