---
title: "Missing Contacts in shared DB"
date: 2010-11-12
forum: Ubuntu One (CLOSED)
---

### Post by brianw0667 on 2010-11-12
Hope this is the correct place for this.  

Under 10.04 We were using Evolution to share contacts between several users on our computer with the System-wide CouchDB.  We did not sync with Ubuntu One and therefore did not have ubuntu one accounts.  After I upgraded to 10.10 all the contacts that we were sharing are gone.

Is there any way to get them back?  All we want to do is share contacts without having to sync with an outside server.

---

### Post by duanedesign on 2010-11-19
If the contacts are not showing up in Evolution this is likely because desktopcouch is not running, but it might be due to other causes. First lets try to restart desktopcouch.

Run this command in a Terminal (Applications > Accessories > Terminal)
```
killall beam.smp
```
this will kill any existing desktopcouch processes. (Note: do not do this with sudo!) If this says beam.smp: no process found, then do this command instead 
```
killall beam
```


Now remove the desktopcouch configuration file, which will then be re-generated. (This will not lose any data stored in desktopcouch, do not worry.)
```
rm ~/.config/desktop-couch/desktop-couchdb.ini
```

Restart desktopcouch. You can ignore messages printed by this command.
```
dbus-send --session --dest=org.desktopcouch.CouchDB --print-reply --type=method_call / org.desktopcouch.CouchDB.getPort
```


open the bookmark file, which should then correctly take you to your desktopcouch web interface (Futon). This step is not really necessary. But it will allow you to confirm desktopcouch is running. Also while Futon is open look for yoru Contacts database to insure it is still on the machine.
```
xdg-open file:///home/YOURUSERNAME/.local/share/desktop-couch/couchdb.html
```

let us know how it goes,
duanedesign

---

