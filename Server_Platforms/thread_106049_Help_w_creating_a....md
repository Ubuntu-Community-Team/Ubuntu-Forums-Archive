---
title: "Help w/ creating a..."
date: 2005-12-19
forum: Server Platforms
---

### Post by echo $USER on 2005-12-19
proxy server.  Just point me in the write direction;  I have already drilled through Google.  I also tried using firestarter to no avail.  I need it to run on any port except 80 because I have my website running on it.  I need to access it from work;  they have almost everything locked down.  I use to be able to get to where I wanted by using the ip address, but that no longer works.  Thanks!

---

### Post by btdown on 2005-12-19
I use Squid to proxy my IM traffic and Shoutcast radio stations (that dont stream on port 80) through my home machine.
 
I use port 443 (which seems to be open on my companies firewall).
 
I would install Squid, uninstall firestarter, and forward the chosen ports on your router to your machine. The Squid.conf file can be hairy to edit, but its pretty self explanatory.
 
BT

---

### Post by echo $USER on 2005-12-19
Thanks for the help.  The squid.conf is the largest conf file I have ever seen.  Anyway I managed to get it up and running.  I had a friend check it out from outside my lan and it worked.  But, I will have to wait until tomorrow to see if it works at my office.  Thanks again.

---

### Post by btdown on 2005-12-20
If you got squid.conf to work on the first go, then you're the freakin man. Took me days to get it to work just right.....

---

