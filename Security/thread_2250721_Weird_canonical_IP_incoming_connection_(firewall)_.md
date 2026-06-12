---
title: "Weird canonical IP incoming connection (firewall) and huge UFW log"
date: 2014-10-30
forum: Security
---

### Post by Totolanio on 2014-10-30
Oct 26 20:34:19 computer kernel: [  764.782738] [UFW AUDIT] IN=eth0 OUT= MAC=90:de:70:cc:1a:77:00:17:33:cf:77:4c:08:00 SRC=91.189.91.14 DST=192.168.1.82 LEN=1492 TOS=0x00 PREC=0x00 TTL=51 ID=50849 DF PROTO=TCP SPT=80 DPT=48293 WINDOW=248 RES=0x00 ACK URGP=0 

(I'm on Zorin 9, Ubuntu)

My UFW log is filled by these, like 4 every second I guess for only 26/10.
I found the log by accident and saw it was 3.4 GB ! (previous ones are 200 mb)

So I decided to check it out (can't even open the log, too heavy) and these lines are pretty concerning imo.
I checked what was this IP : SRC=91.189.91.14
And it's one from  "orobas.canonical.com - Canonical Ltd" so it looks like it's related to Ubuntu but the website shows nothing but apache default page.

1) So what is that IP ? Is it a concern ? 
2) Why is my log full of this stuff ? Can I delete it after you answered ? :p
3) And finally why is my IP = 192.168.1.82 and not the IP I use when surfing the web ? It should connect to this IP, no ?


Thank you if you can answer !

---

### Post by bashiergui on 2014-10-30
That is your computer checking for updates automatically in the background. That's a good thing.

Your IP is 192.168.x.x because you're behind a router. This is the flow of packets:

You send packets to your router using your internal 192.168.x.x IP 
-> your router gives the packet your external IP 
-> the website responds with a packet to your external IP 
-> your router receives it and gives the packet your internal (192.168.x.x) IP ad delivers it to your computer.

---

### Post by Totolanio on 2014-10-30
"That is your computer checking for updates automatically in the background. That's a good thing."

But why this log is so huge ? and why is it checking 4 times a second ! And why other logs are small xD

Ok thank you very much for the router explanation !

---

### Post by bashiergui on 2014-10-30
You must have set logging higher. Set it to low which is default and sufficient.
```
sudo ufw logging low
```

---

### Post by untrustytahr on 2014-10-31
> **Totolanio said:**
> But why this log is so huge ? and why is it checking 4 times a second ! And why other logs are small xD



You can also set the /etc/logrotate.d/ufw to rotate your log based on size rather than time (or both if desired).

As for checking 4 times a second, your firewall isn't checking anything per unit time... it examines the packets at whatever rate they come in at and in networking a packet being sent/resent at 4 times /sec isn't particularly fast at all.

---

### Post by Totolanio on 2014-11-03
But why it happened this time and not the other times ? (just by checking the log sizes it's obvious it only happened this time)
And thankyou :P

---

### Post by bashiergui on 2014-11-03
Could be a few things:

1. You changed the log level recently so you only captured this update event
2. You haven't updated in a while or you recently turned auto updating on
3. Old logs rotated so you don't see the previous event

---

### Post by Totolanio on 2014-11-04
> **bashiergui said:**
> Could be a few things:

1. You changed the log level recently so you only captured this update event
2. You haven't updated in a while or you recently turned auto updating on
3. Old logs rotated so you don't see the previous event


I guess it was number 2. (but still 200 mega to 3 giga o_0)
But about number 3, does it mean the old logs are being erased after a while ?

Is there a way to give you "points" for all your answers ? :p

---

### Post by bashiergui on 2014-11-04
> **Totolanio said:**
> But about number 3, does it mean the old logs are being erased after a while ?Yes. If the logs didn't eventually get deleted then you would fill up your disk with logs.

---

### Post by Totolanio on 2014-11-04
Thank you for all the answers ! I reduced ufw log setting

---

