---
title: "remote login with putty and vnc howto???"
date: 2005-11-25
forum: Server Platforms
---

### Post by mboto on 2005-11-25
hi there,

i want to run a server with an erp system on it.
for this a need a gui (i choosed e16).

for doing some root works on the server from far away i would like to be able to do a remote login on the server. i already know vnc from winxp days so i think its a good solution for me - running a program who shows you the servers desktop in an extra window.

now i read that vnc is not that safe and so i came to putty and heard about that vnc could somehow be used with putty (something bout port forwarding (i never heard of that)).

so what i would like to know now is the following.
- would this be a good solution (or are there similar but better ones)?
- which vnc version do you recommend (fast and functional ;) )?
- as i am totally new with that and the tries i already made with putty and vnc always were not working - do you know any howto/what settings i have to make in these programms??

regards

---

### Post by Enki on 2005-11-26
You might want to check out freenx as an alternative to vnc. It runs over ssh so it should be (potentially) secure. I found it to be much faster than vnc on the same hardware. Not sure if it supports e16 though.

---

### Post by herrpoon on 2005-11-26
Try this: [http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

Haven't tried it myself, although I'll give it a go later today to see if it works with ubuntu.

---

