---
title: "FTP app with interactive bandwith limiting features?"
date: 2006-01-01
forum: Server Platforms
---

### Post by jimbodot on 2006-01-01
I'm looking for an ftp program that would allow me to change the bandwith consumtion on demand, without restarting the server. I need to log on, see how much data is transfered (graphicly if possible) then slow it down or increase it. I've done that with FTP-U in windows, I dunno why I couldnt do that in LINUX.

Would it be possible that inetd is responsable for that? I mean, maybe this fonction is available inside the protocol or whatever it is, but inside linux instead of the app? Kind of making the app believe the connection is simply slower.

---

### Post by peanut butter on 2006-01-02
i know you can do thatwith pureftpd and pureadmin. but this ftp server dosent have a very good web access configuration and is very confussinng. but if you have a monitor on theserver it is a good choice otherwise i would use proftpd which i dont know if it does the bandwith but i know you can do that with pureftpd in the graphical frontend pureadmin

---

