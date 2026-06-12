---
title: "MTA: telnet 25 blocked.. any other way?"
date: 2008-04-11
forum: Server Platforms
---

### Post by vsiege on 2008-04-11
I have just moved my server (7.10 running Postfix) to another location and now port 25 seems to be blocked. Before this used to return something:> telnet: connect to address 72.14.205.27: Operation timed out
telnet: Unable to connect to remote host
telnet> I used to relay off my last ISP because i didnt have a static IP addy. Now I only have a Dynamic IP and I was looking to do more of the same. Is there another way to get my MTA running if this port is blocked?

---

### Post by MJN on 2008-04-12
Unfortunately not - if the ISP is blocking outbound port 25 then you're stuffed.

Can you not relay via the new ISP's SMTP server as before? (they will allow outbound port 25 to that server)

Mathew

---

### Post by gbjazzman on 2008-04-12
Some smtp servers will allow out going over another port. I know exim does. You might want to check that.

---

### Post by MJN on 2008-04-12
That's not going to help as everyone else's MTAs will be listening on port 25...

Mathew

---

### Post by vsiege on 2008-04-14
> Can you not relay via the new ISP's SMTP server as before? (they will allow outbound port 25 to that server) 

> Can you not relay via the new ISP's SMTP server as before? (they will allow outbound port 25 to that server)I havent tried this. i had moved the server to a different geographic location and different ISP.

When I tunnel into my machine and open 

sudo vi /etc/postfix/main.cf 

all I should need to do is change the relay option right?

then to save this file remotely... what key command is it again? is it this ==>  :wq

---

### Post by MJN on 2008-04-15
That's right, but make sure you wrap the hostname in square brackets e.g. **relayhost = [smtp.theisp.com] **This makes Postfix perform an A record query, as opposed to an MX record query.
 
Regarding vi commands I don't know as I don't use it. There should be many guides on the Web though to assist.
 
Mathew

---

