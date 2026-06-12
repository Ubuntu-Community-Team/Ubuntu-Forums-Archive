---
title: "ufw allow tcp port to udp port"
date: 2010-03-18
forum: Security
---

### Post by Goldline on 2010-03-18
Hello guys,
 
For my css gameserver i wanna allow
limited traffic to my webserver only thats needed so thats why
i wanna allow port 27005 udp to port 8080 tcp.
 
because if i dont then ppl will also be able to access my webserver through
the world wide web which costs performance.
 
Can this be achieved?

---

### Post by adam814 on 2010-03-18
I don't think you can magically make TCP traffic UDP traffic or vice versa (either it has the extra headers for TCP or it doesn't), but I know iptables can do redirection like that (i.e. "iptables -t nat -A PREROUTING -p tcp --destination-port 8080 -j REDIRECT --to-port 27005").

---

### Post by uRock on 2010-03-18
TCP and UDP are 2 very different things. TCP requires constant communication between server and client to verify the delivery of packets whereas a UDP server does not check that the client ever receives the data. Hence video and music streaming is usually UDP. Much less overhead.


Regards,
Ronnie

---

