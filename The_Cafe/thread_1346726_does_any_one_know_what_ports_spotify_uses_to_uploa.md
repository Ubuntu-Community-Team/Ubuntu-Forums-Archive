---
title: "does any one know what ports spotify uses to upload?"
date: 2009-12-05
forum: The Cafe
---

### Post by markp1989 on 2009-12-05
my sister uses spotify for music, when shes using it, it uploads music aswell as downloading like p2p.

when she is doing this it increases my ping time alot making my xbox lag.

im not inteding to block the ports, i just wanna set the qos in my router so that when spotify is uploading it doesnt hog all of my upload speed.

---

### Post by Eclipse. on 2009-12-05
Spotify uses port 4070 (TCP) to login and for streams.Also random ports between 14000 and 65000 are used for p2p connections.

---

### Post by Icehuck on 2009-12-05
Mark these ports for Xbox live at the highest priority, 
TCP 80
UDP 88
UDP 3074
TCP 3074
UDP 53
TCP 53

Set a general rule for the rest of traffic to her PC as the lowest priority.

---

