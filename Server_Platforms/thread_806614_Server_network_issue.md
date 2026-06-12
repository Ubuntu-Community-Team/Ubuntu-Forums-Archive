---
title: "Server network issue"
date: 2008-05-25
forum: Server Platforms
---

### Post by deeq on 2008-05-25
I have ubuntu 8.04 server installed, when the server is idle for sometime (about 5min) i cant connect remotely anymore (SSH, Apache, FTP). Its like in "sleep mode".

When i login localy and connect somewhere with lynx, then server wakes up and i can connect again remotely.

Any ideas whats wrong?

P.S
Network is normal, not wireless.

---

### Post by hyper_ch on 2008-05-25
not really a clue... server shouldn't go sleeping at all...

---

### Post by deeq on 2008-05-25
> **hyper_ch said:**
> server shouldn't go sleeping at all...Agree!


Same problem with Debian etch server.

---

### Post by hyper_ch on 2008-05-25
might it be a setting in the bios that makes the computer sleep after a given time of "inactivity"?

---

### Post by deeq on 2008-05-25
Motherboard is Asus A7N8X

I suspect BIOS but don't see anything wrong. I switched hard drive and network card also.

---

### Post by hyper_ch on 2008-05-25
ubuntu/debian server shouldn't do that... at least they don't do it for me... hence my guess it's somehow bios related...

---

### Post by deeq on 2008-05-25
[Bios picture]("http://img176.imageshack.us/img176/9716/a7n8xlk2.jpg")

Something wrong?

---

### Post by hyper_ch on 2008-05-26
not that I can see :( I have no clue why it behaves like that.

---

### Post by deeq on 2008-05-26
Have somebody else any ideas? Help please.

---

### Post by volkswagner on 2008-05-26
Why is the alarm set?  Can that be disabled?

---

### Post by Gunman1982 on 2008-05-26
You connect remotely from where? From the internet? Do you have a dialup connection and use pppoe? It could be that the standardsetting for that is "on demand" meaning it just opens the connection to the internet if the server tries to access a non-lan ip (like with lynx) and shuts it down if it is idle for too long (5min).

---

### Post by deeq on 2008-05-26
> **volkswagner said:**
> Why is the alarm set?  Can that be disabled?

It is disabled.


> **Gunman1982 said:**
> You connect remotely from where? From the internet? Do you have a dialup connection and use pppoe? It could be that the standardsetting for that is "on demand" meaning it just opens the connection to the internet if the server tries to access a non-lan ip (like with lynx) and shuts it down if it is idle for too long (5min).

Yes internet and no i dont have dialup connection, just normal adsl.

---

### Post by Gunman1982 on 2008-05-26
> Yes internet and no i dont have dialup connection, just normal adsl.
Ok so adsl, but still with pppoe I presume?. So maybe you should check the configuration. It should be in /etc/pppoe/... .

---

### Post by deeq on 2008-05-26
/etc/pppoe does not exist

---

### Post by Gunman1982 on 2008-05-26
Does anything with ppp exist in /etc?

---

### Post by deeq on 2008-05-26
Yes /etc/ppp/ip-up.d/exim4

---

### Post by Gunman1982 on 2008-05-26
Uhhhm are you using a router between server and dsl-modem? If yes check if the router is set to disconnect if the internet connection is not used for some time.

---

### Post by deeq on 2008-05-26
I have TW-EA500 and its not set to disconnect. Server gets ip directly from isp (bridged).

---

### Post by Gunman1982 on 2008-05-26
Is something shown in the logs (i.e. /var/log/messages) about suspending the server?
What happens if the server keeps a connection alive to the internet (i.e. ping) does it go offline regardless or any connections?
Is it every time 5 minutes or does it differ?

---

### Post by deeq on 2008-05-27
Nothing /var/log/messages :(

---

