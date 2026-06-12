---
title: "CUPS access from WWW"
date: 2011-06-06
forum: Server Platforms
---

### Post by manningit on 2011-06-06
I am running a headless server on Ubuntu 10.10. I have installed CUPS and can access it from the local network [http://192.168.1.108:631](http://192.168.1.108:631) but not from [http://servername.dyndns.com:631](http://servername.dyndns.com:631) . I have opened ports 80 and 631 on my router and I can see the server at [http://servername.dyndns.com](http://servername.dyndns.com) but not the CUPS control panel at [http://servername.dyndns.com:631](http://servername.dyndns.com:631) I keep getting a "page cannot be displayed" error. CUPS is set to _listen 631_ and _allow all_ everywhere I could find. I have run the various setup guides I could find but no joy yet. Any help appreciated.

---

### Post by jperelli on 2011-06-06
maybe this helps:

[http://ubuntuforums.org/showthread.php?t=1747374](http://ubuntuforums.org/showthread.php?t=1747374)

```

System> Administration > Printers  (in 'classic gnome mode')

Under the Server menu, settings, make sure the printer is published, and allow printing from the internet).

Seems the upgrade turned these settings back off (Bad package managers!!!:razz:)

```

---

