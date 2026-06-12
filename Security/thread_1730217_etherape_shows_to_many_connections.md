---
title: "etherape shows to many connections"
date: 2011-04-15
forum: Security
---

### Post by dimel on 2011-04-15
hello i am running ubuntu for some months and i don't feel like to get to windows never again..unfortunately i have to do this ms flight simulator but anyway..glad to find u and i have let u know that this is my first thread ever...i never been interested in firewalls and internet security just because i learned in windows with this stupid program called windows firewall.i am firewall free and i ll make a firewall as soon as i learn exactly what's going on with the network protocols etc etc...anyway sorry if my english is a little be strange and i am glad to be here and "nice to meet u guys".
let me tell u about my issue...pls notice that i am firewall free but let me know what's going on in my pc till i configure one firewall...
i am running Ubuntu 11.04 beta.
when i run the etherappe(without any downloading file or browsing ,skype etc etc of course)i get soooo many connection and it's a little bit difficult for me to explain u what exactly is going on so i was thinking to show u just a picture and whoever know tell me what's normal(like ubuntu daemons or i don't know) and what is 99% just intruders or whatever u can tell me to learn from u...
any comment will be much appreciated...
(btw i did traceroute in some of those ips and there is a 15-20 connection tree)

(etherappe is running under root privileges)
(i don't know what else to mention if u need something from me to do just i said will be appreciated):D

[http://img835.imageshack.us/f/forumscreenshot.png/](http://img835.imageshack.us/f/forumscreenshot.png/)
[IMG]http://img835.imageshack.us/f/forumscreenshot.png/[/IMG]

---

### Post by The Cog on 2011-04-18
I can't tell from that picture. Are you connected via a router, or directly connected to the internet? If you're directly connected, then I would suspect that it's just a background noise of rubbish and port scanning. A wireshark trace would give a lot more detail, such as whether the connections are incoming or outgoing, and whether they are succesful. Even a tcpdump output for a while would add enlightenment.

---

### Post by dimel on 2011-04-19
sa

---

### Post by dimel on 2011-04-19
is it possible just to lockdown some specific *.akamaitechnologies.* or whatever annoying i can notice???with this way at least i will have only foreign ips comming for a cup of coffe in my pc :P

---

### Post by The Cog on 2011-04-19
I can just about see that there are lines in that screenshot, but I cannot tell what colour they are or which end is thicker.

Is your router performing address translation, or do you have a public address right on your PC? I ask because if the router is doing NAT, then I would not expect to see any incoming un-solicited packets. But if your PC has a public in-translated IP address, then I would expect to see lots of incoming packets and to see your PC sending connection refusals to them. 

How about if you run the command
**sudo tcpdump -n -i eth0**
for a few seconds and post the output here?

---

### Post by dimel on 2011-04-29
as

---

