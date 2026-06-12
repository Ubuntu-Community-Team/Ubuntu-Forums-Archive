---
title: "VPN and Public WiFi"
date: 2009-03-05
forum: Security
---

### Post by m i k e on 2009-03-05
I'm going away on vacation and will potentially be using quite a few public WiFi hotspots.  Naturally I'm a little worried about security.  My university has a VPN that they allow people to connect to.  They ask you to download a Cisco client so I'm assuming it is an L2TP over IPSec connection.  They advertise the VPN as a way to use online university resources while away the from campus but I'm assuming that this should also setup a secure tunnel so that I don't have to worry about entering sensitive information on public WiFi.  Am I correct?  Is there more I should know?

---

### Post by olivesandtrees on 2009-03-06
Cisco VPN clients use split tunneling when connecting remotely (i.e. off-campus).  Using a split tunnel means 2 things

1.  All Internet traffic that is bound for the University network (data from a network share, Intranet websites, and other campus network resources) will be routed through the VPN client and is secure.

2. All traffic not destined for your University (your personal email, online banking information, etc) will **not** be routed through the VPN, but directly to the connection provided by the WiFi WAP which is not secure in anyway!!!!

Hopes this answers your question.

---

### Post by olivesandtrees on 2009-03-06
I'd just like to make a note that this is the most common setup to reduce network overhead... your IT guys may not have setup the VPN in this way, in which case all your info would be encrypted.

It may be best to ask them which setup they are using.

---

### Post by m i k e on 2009-03-06
I did contact the IT department today and the guy said I should be fine as long as my public IP is the same as the VPN IP.  I checked on [http://ipchicken.com](http://ipchicken.com) and it is.  Does that sound right to you?

Thanks.

---

### Post by olivesandtrees on 2009-03-07
Being an IT support personnel for a large, unnamed *cough* university myself, I would say trust your own IT staff... we usually know the ins and outs of our own systems.  If they tell you it's OK, I would trust them.

...if by chance you do get compromised because of your own IT dept's advice I would say it's their *** not yours.

---

### Post by olivesandtrees on 2009-03-07
BTW: Go Big Red!

---

### Post by Dave_Connor on 2009-03-07
Set up a small public ssh server with key auth only and then ssh to your box and then set up a tunnel and use firefox to have all your http traffic go through your box encrypted to avoid alot of security risks.

---

### Post by curadebt on 2009-03-07
VPN is secure and you should use it. other public options can create problems for you data and information.

---

