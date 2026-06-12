---
title: "Start a extra server if the first one fails.."
date: 2012-01-10
forum: Server Platforms
---

### Post by seven01 on 2012-01-10
Hi

Im trying to find a answer to this. Lets say that im using ubuntu server 24/7 and like to have a extra server that automatically starts if the first one fails. 

How can this be done, or can it be done?

---

### Post by a2j on 2012-01-10
what kind of server? run both at the same time?

---

### Post by seven01 on 2012-01-10
> **a2j said:**
> what kind of server? run both at the same time?

Ubuntu server 10.4 that runs MySQL. No just one, if the first one fails (shuts down or the hdd brakes down) i like to get the other one to start up and take over...
Must be some way to get this to work...like wake on lan or something....

---

### Post by seven01 on 2012-01-14
I have understood that i have to have a separate server that automaticly ping the main server to see if its up or not. And if there is a package loss it sends a ping to start the extra server that uses "wake on lan". The "ping-server" should also send a e-mail so i know if the main server is down.

This is how far i have come in this matter. Im trying to find some info about how to accomplish this, but is not easy if you not exactly know what you suppose to look for.

start script to ping a host
and if package fails send a ping to another host
send mail if package loss

Any help?

---

### Post by Dangertux on 2012-01-14
> **seven01 said:**
> I have understood that i have to have a separate server that automaticly ping the main server to see if its up or not. And if there is a package loss it sends a ping to start the extra server that uses "wake on lan". The "ping-server" should also send a e-mail so i know if the main server is down.

This is how far i have come in this matter. Im trying to find some info about how to accomplish this, but is not easy if you not exactly know what you suppose to look for.

start script to ping a host
and if package fails send a ping to another host
send mail if package loss

Any help?

You might want to look into something like HA-heartbeat. Essentially what happens is you can rsync (or clone between the two servers as you see fit). They will share a vIP if one fails the other automatically takes over. 

This would seem to meet your needs perfectly. Minus the fact that they both need to be running simultaneously.

---

### Post by seven01 on 2012-01-14
> **Dangertux said:**
> You might want to look into something like HA-heartbeat. Essentially what happens is you can rsync (or clone between the two servers as you see fit). They will share a vIP if one fails the other automatically takes over. 

This would seem to meet your needs perfectly. Minus the fact that they both need to be running simultaneously.

This is not what i looking for...

My main server (server1) i want to be up and my extra server (server2) i like to be to sleep and only wake up if server 1 fails. The "ping-server" (server3) i like to manage the checks (send pings) to server 1, if it fails i like it to ping server2 to wake it up and at the same time send a mail so i know what happend. 

Maybe sounds a bit weird but thats what i like to do...when and how i dont know yet..#-o

So server1 and server2 do the same things but i dont want them up and running at the same time....

---

