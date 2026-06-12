---
title: "redirecting ports for running two web servers"
date: 2010-09-05
forum: Server Platforms
---

### Post by cliffordsnow on 2010-09-05
I am running apache2 and tornado web servers on the same server with one ip address.  The apache2 listens on port 80.  Tornado listens on port 8888.  I want to redirect requests from a specific ip port 80 to port 8888.  I don't have the ability to change the port request on the device. It wants is looking for a web server on port 80.  

Any other web server request should go to the apache.  

I tried adding the following to /etc/ufw/before.rules
*nat
-A PREROUTING -p tcp -s 192.168.0.9 --dport 80 -j REDIRECT --to-ports 8888

When I run iptables -L it doesn't appear.  I have disabled and enabled ufw with no help.

Any suggestions

---

### Post by BkkBonanza on 2010-09-05
You are changing the nat table so the list command needs to also list the nat table.

sudo iptables -t nat -L

to see if it's there.

I tested this on my machine and it took hold,

sudo iptables -t nat -A PREROUTING -s 192.168.0.9 -p tcp --dport 80 -j REDIRECT --to 8888

---

### Post by cliffordsnow on 2010-09-05
Thanks that worked, or at least it showed that the iptables were working as I wanted.  However, I still didn't see traffic redirected to port 8888.  I suspected that the problem was that apache was listening on port 80 and was grabbing the traffic before it was to be redirected. 

To solve the problem, I moved the apache to port 8000 and now I can redirect port 80 to 8888 with no problem.

---

### Post by BkkBonanza on 2010-09-05
Except that isn't how it works.
The rule is in PRERROUTING so it's long before Apache gets it.
iptables would be useless if programs got data before it did.
Something else is happening in your rules...

---

