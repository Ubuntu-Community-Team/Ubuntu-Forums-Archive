---
title: "Pacemaker GUI (crm_gui) on Ubuntu Server 14.04"
date: 2014-11-14
forum: Server Platforms
---

### Post by keithouellette on 2014-11-14
I attempting to build a pacemaker cluster on two Ubuntu 14.04 LTS nodes. 

 I used the apt-get command to get corosync, pacemaker, pacemaker-mgmt. I was having difficulty getting crm_gui to connect to the server. I gave hacluster a password and added a user to the haclient, group, but was unable to connect. I keep getting the "Can't connect to server 127.0.0.1" popup. I finally decided to use the LCMC gui, but that seems to be having stability issues and continually complains that it is loosing connection to the server, when it is running on the same server. I am assuming that may be a bug in LCMC, so I am back trying to make crm_gui work. What am I missing to get that functioning? 

 Thanks

---

### Post by coffeecat on 2014-11-15
Support question.

*Thread moved to **Server Platforms**.*

---

### Post by levrinc on 2014-11-17
LCMC is meant to be run from your desktop computer not from the server.

---

