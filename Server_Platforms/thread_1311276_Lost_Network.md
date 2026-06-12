---
title: "Lost Network"
date: 2009-11-02
forum: Server Platforms
---

### Post by yabbies on 2009-11-02
I updated my server over ssh connection and rebooted remotely
I have now lost all networking:
SSH
VSFTP
Samba
nothing works

I was able to ping from windows to the server at first but now have lost the ability to ping to the IP.

Anyone have any ideas where to start the troubleshooting?

I didn't pay attention to the packages updated, big mistake.

---

### Post by yabbies on 2009-11-02
just checked the server
I can ping outside IP and DNS
I can ping internal network station IP and DNS
ping localhost
and ping the router

It's not accepting requests from windows workstations

---

### Post by yabbies on 2009-11-02
I have upgraded the server to karmic
Server can ping client 
client can ping server
still can't connect through SSH, FTP or Samba

doesn't make sense.

---

### Post by will81 on 2009-11-02
I, too, upgraded mine to Karmic remotely, and watched and waited.  It came back up but disappeared again a few minutes later - no www, ssh or ping.  I wasn't on site at the time so had it power cycled and it seems to be fine now.  I don't know what caused the problem but, touch wood, no problems since then.

-Will.

---

