---
title: "FreeNX for remote desktop?"
date: 2008-06-11
forum: Security
---

### Post by Mets on 2008-06-11
I use FreeNX to remotely connect into my Ubuntu desktop (Hardy) from my work pc (Windows XP SP2).  My office uses MS ISA server, which blocks almost all traffic known to man, so I have to run FreeNX and openSSH on port 443.  I was wondering - is the connection from my work pc to my home pc encrypted?  I don't see how to setup the nxclient to go through a proxy, but I know it uses SSH already.  Can my connection to my home pc be seen by IT, or is it already encrypted because I'm using FreeNX?

In NX Session Administrator I have
server: mets-laptop
port: 1000 (which made me think traffic it wasn't encrypted)
Session ID: big long hex string
PID: 4060
Type: client

---

