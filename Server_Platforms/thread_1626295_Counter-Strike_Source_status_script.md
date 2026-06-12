---
title: "Counter-Strike: Source status script"
date: 2010-11-20
forum: Server Platforms
---

### Post by Strega on 2010-11-20
Hello,

I have 2 Counter-Strike: Source server running on my Ubuntu server. To start, stop and restart the servers I have a script which I have to use like this```
./public.sh restart
```That's easy right? I also have these cronjobs to restart both the server every night with the exact same command, this works fine too, but...since I don't need that second server that much I put it offline. When I check the next day on the status of the servers in my server list they are both online again instaid of only 1, this is normal, because the servers restart ( actually stop and start ) every night. Now I want to have a script that checks the server status when the cronjob has been excecuted. It should restart the server if it is online, but leave the offline server offline.
Is there a way to do this?

Regards,
Strega

---

### Post by Strega on 2010-11-22
Is there a way to check the status of the gameserver port? The server is running in screen, can the server status be checked by looking at the screen?

---

