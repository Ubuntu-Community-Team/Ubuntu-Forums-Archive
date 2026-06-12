---
title: "Apache questions (ports)"
date: 2006-06-27
forum: Server Platforms
---

### Post by Ramses de Norre on 2006-06-27
I'm running a webserver with apache1.3 (apache2 didn't start and 1.3 works perfect for my purpose) and I've got a little question, if I want my site at the normal http port 80 I have got to forward this port through my router to my local ip, but will other pc's in the same local network be able to use port 80 for there webbrowsing like before? 
And if not, are their ports better for serving sites at as others? Apache is at 10024 now.
Any ideas are welcom ;)

---

### Post by Ctrl+Alt+Del on 2006-06-27
yes, they will still be able to browse the web, others in your network cannot have their webservers accessible (if there are any) from the outside on the same port. That's the only limitation they will have.

---

### Post by Ramses de Norre on 2006-06-27
Ok perfect, that's less typing then;)

---

### Post by MJN on 2006-06-27
Just to elaborate, the forwarding of port 80 on your router is concerned only with **incoming** traffic toport 80. All of your LAN clients are sending **outgoing **traffic to port 80 on the destination host. Of course, the clients will be expecting a reply however this will be to an *ephemeral port* (which won't be port 80)... Ephemeral port? That's your homework assignment... ;)

Mathew

---

### Post by Ramses de Norre on 2006-06-27
Ok, I think it's like this: when I connect to a website I send out a request containing my IP, the servers IP, and the port I want to connect to on the server (80 for webbrowsing). The server sends a reply back to me on an ephemeral port, a port between 32768 & 61000 on my system (man I did my homework), so I don't use my own port 80 for webbrowsing but I sent a request to port 80 of the server and I get a reply on a much higher port.

Thanks for making me learn something today ;)

---

### Post by MJN on 2006-06-28
Got it in one. Now take the rest of the day off. ;)
 
(Just to clarify - your outgoing request contains your ephemeral source port in addition to the source IP and desination IP/port)
 
Mathew

---

### Post by Ramses de Norre on 2006-06-28
I'm going to work on a festival here for the next five days, but that's even better as just taking off;)

---

