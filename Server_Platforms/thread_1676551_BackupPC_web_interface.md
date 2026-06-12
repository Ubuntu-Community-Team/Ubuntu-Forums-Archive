---
title: "BackupPC web interface"
date: 2011-01-27
forum: Server Platforms
---

### Post by humberty on 2011-01-27
Hi 

I have ubuntu 10.04 with all lamp perl apache sql all update and upgrade are installed.

I did install backuppc with the "perl configure.pl" file after extracting the backuppc 3.2.0 tar.

The service is starting and I'm convinced it is installed but I can't get the webpage [http://ip/backuppc](http://ip/backuppc)  it says 404 Not Found.
Obviously if I do [http://ip](http://ip) i get It Works!


Can anyone help?

Thanks
humberty
:popcorn:

---

### Post by amra.sonntag on 2011-01-27
My guess would be, that you aren't pointing your browser to the right directory or need to allow acces to the directory of backuppc in your Apache2 Virtual Host Site.

Or you block your connection with your own firewall?

---

