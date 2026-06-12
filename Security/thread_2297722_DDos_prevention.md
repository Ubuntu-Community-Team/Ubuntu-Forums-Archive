---
title: "DDos prevention"
date: 2015-10-06
forum: Security
---

### Post by ELMIT on 2015-10-06
There is so many written on the Internet. Some seems to be as old as the Internet itself.

What is the best way to protect a server (not necessary a web server alone) including how to switch to another server, ....

E.g. I have a service running at a certain port, which is also reachable from the Internet. 
I have the service also running on another server.
A program needs to contact this service to get the data. If this port is under attack, I cannot reach it from my local program either. In that case I want to use the service on another (remote) site instead.

Basically if service localhost:xxxx is not available, then I want to use example.com:xxxx    (it is the same port)
I don't run a dns server, so it should be solvable with the host file (update or include info in host file).

---

### Post by slickymaster on 2015-10-06
*Moved to the ***Security*** sub-forum*

---

### Post by CharlesA on 2015-10-06
Short answer: Get DDoS filtering for that server.

Long answer: If you do not want to pay the amount of money they want, you could host your service with a VPS company that offers DDoS protection and pay extra each month to get a filtered IP. It wouldn't prevent all DDoS attacks, but it should help mitigate the majority.

The other option is to use a roundrobin style of DNS in the event one server is under attack, but what prevents the attackers from taking out the other server as well?

---

### Post by zhelev81 on 2015-10-25
Hi I found this Thread interesting because i am running 4 game servers on a ubuntu machine and i get flooded very often. The machine is used only for that game servers and one website is hosted on it. Can you please help me make a protection at some good level by blocking those attacks with some good scripts which are executed automatically every X seconds ?

Also if you know some paid software that can be installed let me know because i am tired of my servers being down ...

Waiting for some help here..


Thanks in advance

---

### Post by Lars Noodén on 2015-10-25
It's probably better to start a new thread for a new question, but what is the nature of the flooding?   There is no one-size-fits-all solution.  It all depends on where the bottlenecks are.

---

### Post by CharlesA on 2015-10-26
> **zhelev81 said:**
> Hi I found this Thread interesting because i am running 4 game servers on a ubuntu machine and i get flooded very often. The machine is used only for that game servers and one website is hosted on it. Can you please help me make a protection at some good level by blocking those attacks with some good scripts which are executed automatically every X seconds ?

Also if you know some paid software that can be installed let me know because i am tired of my servers being down ...

Waiting for some help here..


Thanks in advance

No software can mitigate a DDoS. You would need to sign up for a DoS filtering service such as Black Lotus but those can be expensive.

---

### Post by Habitual on 2015-10-27
check out cloudflare ;)

---

### Post by HermanAB on 2015-10-30
Minor attacks can be thwarted with iptables rate limiting.

---

