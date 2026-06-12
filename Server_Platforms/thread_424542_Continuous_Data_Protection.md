---
title: "Continuous Data Protection"
date: 2007-04-26
forum: Server Platforms
---

### Post by PilotJLR on 2007-04-26
Hello,
I'm looking for an open source / free Continuous Data Protection program... does anyone know of any? I've come up with zilch on google so far.

What I'd ideally like to do is get a CDP service going for a small office with only 5 Windows users and 1 Ubuntu server.
The Tivoli CDP product is pretty much exactly it... just wondering if there is an open source way to do this.

Thanks!

---

### Post by thingy on 2007-04-27
A pure cdp would involve dedicated hardware and there are only about 4 near cdp products that I could find.
 
This url lists them: [http://forum.r1soft.com/showthread.php?p=454](http://forum.r1soft.com/showthread.php?p=454)
 
umm can I ask why you want something like near cdp for a mere 5 Windows desktops ?
 
You might be over engineering the problem you are trying to solve. :-)

---

### Post by PilotJLR on 2007-04-27
Good info there, thanks.

I'm not looking for replication or server CDP... just the lightweight type of workstations. Tivoli has this, it's about $35 per computer. This is not to be confused with the server versions from Tivoli, Symantec, etc.
[http://www-306.ibm.com/software/tivoli/products/continuous-data-protection/](http://www-306.ibm.com/software/tivoli/products/continuous-data-protection/)

Basically any workstation worthy of network backups (Retrospect, Veritas, whatever) is a candidate for CDP to me. At least over a LAN.

Plus these 5 users are mischievous, so I need as much protection as possible, cause they call me when they accidentally delete their own stuff.  :-)

Everything for Linux I've seen in CDP so far is for servers, which I agree is overkill for this. I'll probably just run reasonably frequent traditional backups from a cron job.

---

