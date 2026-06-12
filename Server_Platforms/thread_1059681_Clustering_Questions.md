---
title: "Clustering Questions?"
date: 2009-02-04
forum: Server Platforms
---

### Post by ductiletoaster on 2009-02-04
I'm obviously new to the idea of Clustering. Basically i would like to run a server (web, email, etc...) and my question is how would clustering help me. I have two machines different specs and possibly may have each running either Ubuntu 8.10 or another version of Ubuntu.

So is Clustering a good idea for web servers..... Maybe for redundancy im not really worried with the improvement in computing because its a web server so the bottle neck will be at the network side.

---

### Post by Thirtysixway on 2009-02-04
Clustering can help if you have a lot of users and activity.  Forgive me if I'm wrong but it seems as though you'll be setting this up at home?  It really depends on what you plan to run from there, most home internet connections can't handle the traffic required to even need clustered servers.

For redundancy it would help, but just remember the single point of failure most likely to hit you is the network capasity.

You can try this thread on ubuntu clustering
[http://ubuntuforums.org/showthread.php?t=16508](http://ubuntuforums.org/showthread.php?t=16508)

---

### Post by ductiletoaster on 2009-02-04
Thanks for the link. Im not really doing this for some gain. I have two old machines that are just collecting dust and have been experimenting with Web servers for a long time and i felt the next step would be to run a cluster of some kind. Though it would be nice to have a reliable web server.

---

### Post by ductiletoaster on 2009-02-27
Also both computers are running inside my network so yes the bottleneck will be the connection. However my home connection is pretty fast. Now its not quit a business class connection but it is approx 1.9mb/s down. But agian im not really looking for the ability to host many many many users. I care more about reliability. I want redundancy

---

### Post by JeppeM on 2009-02-27
It's actually more your upload speed which is being used when you server users... The server is "uploading" to the users, not downloading from them :)

Just a quick note :)

---

