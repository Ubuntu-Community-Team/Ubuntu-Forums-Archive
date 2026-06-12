---
title: "(gedit:8292): Gtk-WARNING **: cannot open display:"
date: 2008-12-03
forum: Server Platforms
---

### Post by carlosmiguel on 2008-12-03
Hello everybody,

I´m new is this world of UNIX-UBUNTU SERVER, and i trying to install the MAGENTO ICOMMERCE so when i executed the following command:
sudo gedit /etc/apache2/sites-available/default

this is the error that i received

(gedit:8292): Gtk-WARNING **: cannot open display:

Pls i really apreciate if somebody can help me ASAP

Best Regards,

Carlos

---

### Post by pennacook on 2008-12-03
Is your DISPLAY variable set? Are you running this without X running? Run ```
set
``` and look for DISPLAY= If not you'll need to set it - usually localhost:0.0 is sufficient if you are running X locally.

---

