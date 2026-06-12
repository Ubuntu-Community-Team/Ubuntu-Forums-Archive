---
title: "SSH Woes..."
date: 2005-03-15
forum: Server Platforms
---

### Post by FX on 2005-03-15
Having trouble with ssh. I have a server (running warty) running and I can ssh from my laptop to that just fine. I can log into the server with vnc and ssh from there to the laptop (running hoary) just fine. When I try to ssh from either the laptop or the server to the kids machine I get "no route to host". Or another errror like this....  Permission denied (publickey,keyboard-interactive). I get rid of one error and then I get another. All the pc's are on a local lan here in my home.

I am running Hoary.

---

### Post by FX on 2005-03-16
Hmmmm...... No takers?

Good thing I posted over at mandrakeusers.org. There I got an answer within about 5 to 6 hrs. I've had this posted here the last 24.

---

### Post by alastair on 2005-03-16
We're all a bit thick over here obviously.

So, the solution's a secret?

---

### Post by FX on 2005-03-16
The reply over there was to make sure I didn't have a firewall blocking the port. That isn't the problem cause sometimes it will work and sometimes it won't. It just happens to be not working at this point.

I thought maybe a Hoary update on it might have had something to do with it, but I have Hoary on this laptop also and I can ssh from the server to here just fine.

---

### Post by alastair on 2005-03-16
OK - you gave the impression it was fixed.

An error "no route to host" is a plain networking problem i.e. you cannot even reach the remote computer at all. You do not want this error - so I assume you fixed your network/routes.

An error "Permission denied (publickey,keyboard-interactive)" means that you are using public key authentication - and it is failing. So, the first question is - do you want public key auth? If so, did you copy your public key to the remote system?

If you do not want to use public key auth - the remote system can be set to use "password" auth.

Is this still the error?

Remember you can use "ssh -v" (and -vvv) to be more verbose in a login.

The server sshd can also be set to verbose debug.

---

### Post by az on 2005-03-16
[QUOTE=FX]Hmmmm...... No takers?

Good thing I posted over at mandrakeusers.org. There I got an answer within about 5 to 6 hrs. I've had this posted here the last 24.[/QUOTE]

Last night, I had the answer typed half in when my baby started to cry.  I closed the window.  this was something like five minutes after you originally posted.  Seriously, this is true. 

(I think this is the sixth thread in a row that Alastair shows up with the same thinking as mine.  You rock, dude!)

I was going to ask you if your local ip address is always the same or it changes depending on what order your boxes boot.  That would make so that the keys do not match or that the host is not there,


Anyway.  I am sorry my one-year-old made your life inconvenient.

---

### Post by FX on 2005-03-16
Well I played around with the kids computer some. I uninstalled anything to do with ssh. Then reinstalled. Came to the laptop here and was able to ssh into it. I thought cool. So I logged out and then vnc'ed into the server (still in the same home and lan) and tried to ssh into the kids pc and I get "no route to host" deal again. I'm thinking, wth. So I closed out of vnc and tried again from here and no go with the same error. I started to think that the router wasn't releasing the port so I tried ssh'ing from here to the server and it was find. Then from the server to here and it was fine. So I tried again to the kids machine and still "no route to host"  Ugh....

So I thought maybe it might be the wireless card in the kids pc, but the server has one too and that works fine. Only thing that I could possibly come up with is they are the same brand cards (netgear) but one (server) takes the madwifi drivers and the other (kids machine) takes the ndiswrapper driver.

I'm at a lost.  :(

---

### Post by alastair on 2005-03-17
What's the "kids" machine running?

If you get a "no route to host" - forget ssh and try a plain "ping <host>". It might be a plain networking issue.

Same error on laptop -> kids? i.e. "no route to host"? try a ping.

Maybe the wireless connection isn't stable? It happens with wireless sometimes. Check the logs on the kids machine as well and make sure nothing's going on with networking i.e.

/var/log/syslog

---

### Post by FX on 2005-03-18
Sorry didn't mean to sound so pissy. I was just crabbly with life and took it out on the wrong people.

But I think I'v narrowed down my problem to the wireless nic card. I have to investigate some more, but pretty sure thats the problem. Probably with the nidswrapper driver. I'm not having a problem on here with Hoary and the madwifi drivers.

---

