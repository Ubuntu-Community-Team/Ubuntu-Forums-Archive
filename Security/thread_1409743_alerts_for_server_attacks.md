---
title: "alerts for server attacks"
date: 2010-02-17
forum: Security
---

### Post by foxxxau on 2010-02-17
Hi there,

We're been getting a few attacks on our server / website recently, we have a high traffic site on a dedicated server with ubuntu 9.

Is there any apps out there we can install that will monitor network traffic real-time and alert us if there's 1 ip smashing our server with requests?

At the moment we are alerted by higher than average CPU / MySQL usage, check the logs, see an ip and block it with IPTABLES... hardly ideal...

If there's an app that can monitor attacks like this and block the user for X minutes it would be great.

Does anyone know any?

Thanks

---

### Post by bodhi.zazen on 2010-02-18
You have several options.

Snort is one option, but it will not necessarily log excessive "normal" activity.

iptables is a second option, you can limit the rate if incoming connections. This works best for things like ping.

mod_evasive is a third option.

What kind of traffic is it ?

---

### Post by foxxxau on 2010-02-18
We've had 2-3 people run Acunetix on the site to try an find holes - a full acunetix scan runs for 4-6 hours with 2-3 requests a second non stop. 60k+ requests.

XSS attacks, SQL injections and things like that. not just 1 injection but typically an application that will do a few thousand tries of something at a time.

Apps like that alone generate 40-80 sql requests a second per person trying it.

---

### Post by bodhi.zazen on 2010-02-18
I would install snort, which will detect the mysql (and other) attacks, and OSSEC, with will block the IP address. 

See : [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

2 scans / sec is rather trivial, but if multiplied by thousands of ip is a DDOS. Again you can either look at mod_evasive or rate limit your ports.

More likely then not once you have OSSEC installed they will go away.

---

### Post by foxxxau on 2010-02-18
looks like something that could do the trick

thanks for that :D 
appreciate it

---

