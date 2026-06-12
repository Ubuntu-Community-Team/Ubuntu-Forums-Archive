---
title: "I have a domain name but can't view out of internal network"
date: 2006-09-19
forum: Server Platforms
---

### Post by scannerdarkly on 2006-09-19
Ok so pretty much I'm not sure why i can't view my site when i'm out of my internal network.  anybody have any suggestions?

---

### Post by Iowan on 2006-09-19
Is the router port-forwarding to the server?
IS there a router (and/or firewall)?

---

### Post by scannerdarkly on 2006-09-19
yea i have the port routed as far as the firewall i'm gonna have to check it out

---

### Post by gmclachl on 2006-09-19
If your router is running NAT then you will have problems viewing an internal site using an external address. 

 I kind of got round it by adding the external domain to the hosts file on my other local machines. 

George

---

### Post by scannerdarkly on 2006-09-19
well i've done a little configurating, but can't tell if that fixed the problem if you guys could try [http://razorbladex401.homelinux.com](http://razorbladex401.homelinux.com)  tell me if you see anything.  if not then i got a little bit of work to do.

---

### Post by The_Apprentice on 2006-09-19
Surely this is an external DNS error.

Sorry if this is a "suck eggs" answer.....

In order to reach your site from outside your nextwork you need to resolve your domain name to an IP address.

So, in a jutshell if you go to [http://ubuntuforums.org](http://ubuntuforums.org) your browser checks with the computer for what DNS servers it is supposed to be using.
It then sends a request to thr Primary DNS server requesting the IP address for [http://ubuntuforums.org](http://ubuntuforums.org).
The DNS server should return 82.211.81.186

The HTTP request will then be sent to that IP address, where the web server should pick it up and return the page(s).

There are two solutions......
1.  Ensure that the DNS record for you domain points to the external IP address of your server (probably the IP address you get from your ISP on your router)
2.  Create an entry in the host file of the external pc to resolve the IP address for you.

---

### Post by scannerdarkly on 2006-09-19
alright well i just tried something else could somebody check it out.  sorry i'm gonna be doing some configurations so i might ask a bit for people to check it out.  thanks for you guy's help

[http://razorbladex401.homelinux.com](http://razorbladex401.homelinux.com)

---

### Post by The_Apprentice on 2006-09-19
I am getting "Connection Refused"

The IP address for razorbladex401.homelinux.com is resolving to 68.100.16.25
Is that the correct IP address?

---

### Post by peanut butter on 2006-09-19
try putting you apache on port 81. I dont have Cox so I dont know but they might block port 80.

EDIT: you could use a web proxy such as blockmenot.com to check if it works from the outside.

---

### Post by scannerdarkly on 2006-09-19
> **peanut butter said:**
> try putting you apache on port 81. I dont have Cox so I dont know but they might block port 80.

EDIT: you could use a web proxy such as blockmenot.com to check if it works from the outside.

i used blockmenot.com like you suggested and at first i got a connection failed, now after i changed a few things i'm getting a connection timed out.

---

### Post by scannerdarkly on 2006-09-19
> **The_Apprentice said:**
> I am getting "Connection Refused"

The IP address for razorbladex401.homelinux.com is resolving to 68.100.16.25
Is that the correct IP address?

i was trying that ip just to see if that one would work.  now i changed it to the real ip so now it should be a "connection timed out" instead.

---

### Post by The_Apprentice on 2006-09-20
It is now resolving to 68.98.149.237 which is not responding.

I guess you have switched the PC off?

---

### Post by scannerdarkly on 2006-09-20
> **The_Apprentice said:**
> It is now resolving to 68.98.149.237 which is not responding.

I guess you have switched the PC off?

the PC is on, i'm trying to see if maybe i might have to change from port 80 to port 8080

---

### Post by scannerdarkly on 2006-09-20
i'm using [http://www.blockmenot.com](http://www.blockmenot.com) like someone suggested i use to see if my site is reachable and i just get "connection timed out"

---

### Post by scannerdarkly on 2006-09-21
here's a question.....now the way i'm set up and i'm sure alot of people are set up this way is i have my router connected to my cable modem.  so if i make changes on my router do i not only have to reset the router but the modem as well for the changes to take effect?


I'm at work right now so i can't check it.

---

