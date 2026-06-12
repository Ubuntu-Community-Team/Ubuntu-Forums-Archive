---
title: "No network connection, unless using recovery mode to root user with networking."
date: 2009-05-31
forum: Server Platforms
---

### Post by Invader Amoto on 2009-05-31
Ubuntu server edition 9.04
Everything started out perfectly. Install went great. Everything ran how it should. Then the server crashed and shut down.
Now it can't connect to my network when I start it up.
I found out that choosing the recovery mode in Grub and then choosing root use with networking gives me network connection, and eth0 even shows up again in ifconfig.
The only problem is that I'm not sure I should be running the server from root user, and that ssh no longer works. I need ssh because I don't normally have a monitor and keyboard hooked up to the server.
I hope I gave enough information for someone to help me.
Thanks in advance,
John

---

### Post by windependence on 2009-05-31
Logged in as a regular user and doing:

```
sudo ifconfig -a
```

produces what output?

-Tim

---

