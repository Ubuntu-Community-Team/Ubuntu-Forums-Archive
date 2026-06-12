---
title: "Easy Question: Acces Router can see password"
date: 2009-05-23
forum: Security
---

### Post by MadMax2 on 2009-05-23
I access my router type in "admin" p/w [blank] and see
network ID
Security WEP
Authentification Type Open /shared/ both (checked)
WEP encryption 128 bit
Key mode Hex
WEP Key 1 2e34dfdgd etc

Does this mean my neighbours can see my pw? I thought I was safe with a long encrypted(?) pw.

Hmmmm ofcourse you'd have to be on the network to access router config to see the encrypted pw........?

I have been checking internet usage against when I was on/off and it doesn't tally.
Thanks for your help


Date mb up mb down total
15-May-2009 15:35:36		1.03	4.54	5.57
Off 16:30						
15-May-2009 16:35:36		0.51	2.65	3.16
On 17:30/  Off 17:50						
15-May-2009 18:35:36		0.34	0.85	1.19
						
15-May-2009 19:35:36		2.33	36.36	38.69
On 19:40/ Off 19:51						
On 20:15						
15-May-2009 20:35:36		2.12	15.27	17.39
Off 20:45						
						
15-May-2009 21:35:36		1.36	0.06	1.42
On 22:00						
15-May-2009 22:35:36		2.82	28.16	30.98
Off 22:34

---

### Post by Kareeser on 2009-05-23
Wireless encryption (through WEP or WPA) is different from the access password used to gain entry to the web-interface of the router. If you feel as though your neighbours have guessed or cracked your wireless encryption, then yes, if they correctly guess the admin password (which is readily available on the internet), they can access your admin page, and change whatever settings they'd like.

Secure your router and wireless properly with WPA2 encryption and a better admin password, **NOW**!

---

### Post by MadMax2 on 2009-05-23
I didn't have an admin password set [admin + blank], originally someone set it up for me and I was impressed by the fact that it had a very long password. 

How does a neighbour access the router address if he isn't in the network?


I've followed this article
[http://www.informit.com/articles/article.aspx?p=461084](http://www.informit.com/articles/article.aspx?p=461084)

---

### Post by Kareeser on 2009-05-23
If your neighbour has not connected to your wireless network, then they won't be able to access the web interface of your router, unless you specifically set it to be accessible from outside the internal network.

---

### Post by MadMax2 on 2009-05-24
> **Kareeser said:**
> If your neighbour has not connected to your wireless network, then they won't be able to access the web interface of your router, unless you specifically set it to be accessible from outside the internal network.

You mean the 
Remote Management
Let administrator perform administration task from remote host

  	Enabled Disabled
IP Address 	0 0 0 ?

---

### Post by MartyBuntu on 2009-05-24
> **Kareeser said:**
> 

Secure your router and wireless properly with WPA2 encryption and a better admin password, **NOW**!


Agreed. This is fundamental. A strong password (long, mixed letters and numbers) is prefered.

---

### Post by MadMax2 on 2009-05-24
Last night the router log showed 10 pages of WLAN unallowed access from 3 different MAC addresses.

How might they snoop/ hack (next step up)?
I think I'll use an ethernet  cable.

I can't log in automatically now. I see my network name (although not broadcast) but I can't connect. I have to (re)make a new connection and enter WPA password. Then I have to have a couple of goes at getting firefox to connect (ie takes time +evolution)

---

