---
title: "Apache Server"
date: 2009-01-24
forum: Server Platforms
---

### Post by Mauler5858 on 2009-01-24
OK here is my situation:

My equipment/software:

I have my domain name set up to point to my static ip address, which i will refer to as mydomain.com.

I have a wrt54g router(stock OS).

I have Ubuntu 8.04 Server Edition running as LAMP.  Apache is listening on port 8080.

My problem:

When i go to [www.mydomain.com](www.mydomain.com) the server will not respond.
When i go to [www.mydomain.com:8080](www.mydomain.com:8080) i can hit my server.

i need to get rid of the :8080.

I cannot figure out where the problem is.

---

### Post by albinootje on 2009-01-24
> **Mauler5858 said:**
> 
I have Ubuntu 8.04 Server Edition running as LAMP.  Apache is listening on port 8080.
-- cut --
When i go to [www.mydomain.com](www.mydomain.com) the server will not respond.
When i go to [www.mydomain.com:8080](www.mydomain.com:8080) i can hit my server.


Don't you want to have apache listening to port 80 ?
Where is port 80 on your router port_forwarding to ? To port 80 or 8080 ?

---

### Post by Mauler5858 on 2009-01-24
ive tried listening on 80 and forwarding 80 to 80.
Ive also tried listening on 8080 and triggering 80 to go to 8080.

---

### Post by albinootje on 2009-01-24
> **Mauler5858 said:**
> ive tried listening on 80 and forwarding 80 to 80.
Ive also tried listening on 8080 and triggering 80 to go to 8080.
Okay, I assume you are testing all this from outside your LAN at home, no ? Or let someone else test it from the outside.

What happens when you or someone else would do a :
```

telnet mydomain.com 80

```
from the outside, when you have apache running on port 80, and your router configured to port-forward port 80 to port 80 on your webserver.

---

### Post by Mauler5858 on 2009-01-24
> **albinootje said:**
> Okay, I assume you are testing all this from outside your LAN at home, no ? Or let someone else test it from the outside.

What happens when you or someone else would do a :
```

telnet mydomain.com 80

```
from the outside, when you have apache running on port 80, and your router configured to port-forward port 80 to port 80 on your webserver.

When i try that internally i can connect fine.
When a friend tries it from outside my LAN it fails.

---

### Post by jimv on 2009-01-24
If I had to guess, I'd say that your ISP is block port 80.

---

### Post by Mauler5858 on 2009-01-24
Yea thats something i was kinda starting to suspect.  As when i tried the telnet thing on another port,  it worked.

---

