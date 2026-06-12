---
title: "two apache servers, how to manage failover"
date: 2009-01-14
forum: Server Platforms
---

### Post by mshenoy4573 on 2009-01-14
Well, This being my first post here at ubuntuforums, I assume I am posting at the right place. Please correct me If I am wrong. 

I need a lot of help here as I am not quiet sure if this is even remotely possible. 

1. Firstly, I have a domain registered with yahoo suppose (a.com) 

2. I have 2 web server's (Apache), one running on my laptop and the other at my friends place (different domains). 

3. We are using dyndns for dynamic IPs and hence using their hostnames. 

4. So there are 2 hostnames using dyndns (b.com) and  (c.com)  that point to our web servers running locally .. 

What I aim to do is host the same content on both the web servers (b.com and c.com). Now using the yahoo domain (a.com) is that possible that when i type (a.com) if there happens to be a way to check if (b.com or c.com) which ever one is online and then redirect accordingly. there need not be any content on a.com. It is jus there, I am not sure If I need to use it or not. 

I have read about this and I believe its a totally related to DNS. I believe round robin dns is a way. But what that does is randomly redirects, in that there is no check done to see if the web server (host) is online and then redirect . Like some kind of failover mechanism that can run on (a.com). since these are local apache servers I plan to see how it reacts if one is down and the other is up and running and vice the versa. 

I hope my question is clear please let me know if you need any more details and any which way if this is even possible. I hope I am going in the right direction.

---

### Post by cariboo on 2009-01-14
You may want to give heartbeat a try.  It is available in  the repositories.

Jim

---

### Post by dmizer on 2009-01-14
Moved this to the servers section.

---

### Post by mshenoy4573 on 2009-01-14
Jim thanks for the reply 

and dmizer thanks for moving the post.... 

well i did find and install hibernate ..... and read about a few of the config files..... it is necessary that both the computers be on the same LAN ? or like do they need to be connected via a cable or something as one of the similar tutorials i happen to read.... 

can anyone shed more light on this ...

---

