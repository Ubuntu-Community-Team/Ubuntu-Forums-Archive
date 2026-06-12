---
title: "Apache Restarting Every Week?"
date: 2007-03-11
forum: Server Platforms
---

### Post by rocktorrentz on 2007-03-11
I am running an up-to-date installation of Edgy server i386 with a LAMP installation with torrentflux. However I have noticed that my torrents appear to be dieing every sunday morning and this coincides with this in my apache error.log and error.log.1:
```
[Sun Mar 11 06:25:49 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
```

and this from last week
```
[Sun Mar 04 06:25:49 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
```

Although the only problem this causes is me having to start my torrents when I get up on sunday I would still quite like to know what is going on. Does anyone know why apache restarts and if it is unnecessary how to stop it?

Thanks
rocktorrentz

---

### Post by conjur3r on 2007-03-11
Looks like your apache logs are being rotated weekly.  Take a look in /etc/logrotate.d/apache2

Change that restart to reload.  This will tell apache to gracefully reload its configuration changes (in this case, so it knows the logs just got rotated).  This should fix it up.

---

### Post by rocktorrentz on 2007-03-11
Thanks for the quick reply. I'll post next sunday to say if it has worked.

---

### Post by conjur3r on 2007-03-13
The alternative is to not rotate your logs.  It depends on how you want the logs to look (one big large one or multiple files at regular intervals).  To not rotate them, either comment out the whole file or remove it from that directory.

---

### Post by Daniel15 on 2007-03-13
> **conjur3r said:**
> The alternative is to not rotate your logs.  It depends on how you want the logs to look (one big large one or multiple files at regular intervals)
As far as I know, Apache doesn't work correctly if the log file grows larger than 2 GB.
Supposedly, a tool called "chronolog" is an alternative to logrotate, but I've never tried it before.

---

### Post by MJN on 2007-03-13
> **rocktorrentz said:**
> Although the only problem this causes is me having to start my torrents when I get up on sunday I would still quite like to know what is going on. Does anyone know why apache restarts and if it is unnecessary how to stop it?
 
I think you're barking up the wrong tree....
 
The Apache rotate function in Logrotate was defined by the Apache project team i.e. they've said they want Apache restarted when the logs are rotated (this is a requirement for most services that log to file).
 
Hence, Apache restarting is by design and thus should not be causing you any problems. The fact that it does, and that these problems are solely with Torrentflux suggests to me that's where you should be looking.
 
Unfortunately I'm not familiar with Torrentflux hence cannot advise specifically however you can't be only user having these problems so have a hunt round.
 
If you have no joy then raise it as a bug against the Torrentflux project.
 
Mathew

---

