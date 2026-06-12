---
title: "Questions ubuntu 10.04"
date: 2010-07-29
forum: Server Platforms
---

### Post by kendel on 2010-07-29
I have been searching the net for a while and after reading a few chapters into DNS & BIND I structed this design.
[[IMG]http://img168.imageshack.us/img168/9311/serversetup.th.jpg[/IMG]]("http://img168.imageshack.us/i/serversetup.jpg/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
The ones off to the side haven't been connected yet. Not till I get this working.
 
I have some confusion however and I hope someone can point me in the right direction.
I decided to go with Linux virtual server for load balancing (LVS) with ldirector and hearthbeat.
Let me explain my design first.
Each server has two (2) nic cards.
The load balancers are connected to the switch utilizing the router. The second nic is on a seperated subnet on a seperate switch.
 
1) Is having the Database server separate really better of redundant? If I leave it on the first switch will it be trouble. I planned to use it as account information storage.
2) BIND DNS server lookup, what is the better option for it. Is it run from the load balancers or is it better to simply put a server it for that purpose?
3) I was planning to use webmin for administration control and user control, etc. Is that installed on every box or do I pick a box and specify all the other boxes? (Which box to pick?)
 
I decided what I will do is use one box for my personal server and the other 2 web servers will host multiple websites (load balanced)

---

### Post by kendel on 2010-08-01
So I installedu ubuntu on load balaner 01 for testing and i figured I needed the light GUI for webmin.. but here is my new topology I still have a few questions if anyone can answer them.
[[IMG]http://img135.imageshack.us/img135/6319/serverconfig.th.jpg[/IMG]]("http://img135.imageshack.us/i/serverconfig.jpg/")
Uploaded with [ImageShack.us]("http://imageshack.us")
 
Does a virus software get installed on all servers or only on front end?

---

