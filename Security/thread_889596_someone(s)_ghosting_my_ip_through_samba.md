---
title: "someone(s) ghosting my ip through samba"
date: 2008-08-14
forum: Security
---

### Post by eival on 2008-08-14
i think i made a mistake by setting up a share though a windows pc on my network cause yesterday i checked my router traffic and noticed ALOT of "established" connections(meaning active, not old an waiting to time-out from the routers log) to my ubuntu IP, but i hadnt been browsing. my router is the D LINK DGL 8100

so i thenk checked Firestarter and under the active connections it showed a long list of blocked connections from Samba.

i had been using a static ip through dhcp ip reserve, so i revoked my current ip an set up a different one and also uninstalled samba, that seemed to work cause there was no more traffic through my old ip, but there was then 2 connections on my new ip

i never had this happen before i created the share and i keep track of my traffic on a regular basis. how can i stop my ip from being ghosted? 

reinstall ubuntu?

im using Ubuntu Hardy 8.04

---

### Post by cariboo on 2008-08-14
Are the ip addresses outside of the range of ip addresses in your net block?  Ubuntu can still connect to windows shares via smbclient.

Jim

---

### Post by eival on 2008-08-14
> **cariboo907 said:**
> Are the ip addresses outside of the range of ip addresses in your net block?  Ubuntu can still connect to windows shares via smbclient.

Jim

no, it was my ip address, i had the share going through NAT.
the activity was going through my IP address.

---

### Post by cariboo on 2008-08-14
Then it probably is just normal day to day activities. When you are connected to a share there is always some communication back and forth, and the update manager always checks for updates during a boot.

Jim

---

### Post by eival on 2008-08-15
i did a reinstalled of ubuntu and i unplugged my router an modem during the process(about 20 minutes) when i set everything back up it seems to be back to normal.

it was just wierd cause during the time i was getting attacked i can see the website ip in the active sessions log and they were all Google.com, Yahoo.com
nothing that would tell me someones trying to use my connection for browsing.
right now the only connection thats showing is port 5353, which i already found out that its a normal port and ip for everyone an theres no activity going through it, its just open

also i found a thread here that shows how to change the mac address of ubuntu, so if this ever happens again(assuming the attacker was cloning my mac) i can change that then block both the old ip an mac address.


do you guys think this also could be connected with the recent DNS flaw?

---

### Post by osjak on 2008-08-16
In order for someone from outside to connect to your PC's you need to set up a port forwarding in your router, i.e. you have to deliberately open your home network to the outside world. From what you are saying, you didn't do it. So the probable cause of all these connections is that Windows share. It uses four different ports for some reason if I remember correctly. And it polls those ports from time to time, so you will have open connections.

---

