---
title: "Flash stopped working today."
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by janderson91z on 2012-04-06
After some updates today, flash has stopped working in all my browsers :(

Anyone else experiencing this? Have any idea what's going on?

---

### Post by sgage on 2012-04-06
> **janderson91z said:**
> After some updates today, flash has stopped working in all my browsers :(

Anyone else experiencing this? Have any idea what's going on?

Yes, I experienced it. No, no idea what's going on. But I just reinstalled flash-installer, and all was well.

---

### Post by janderson91z on 2012-04-06
Oops, maybe I should have done that before making a thread. Yeah, that solved the issue. But that does bring up another question, though not specifically related to Precise. People say that Chrome uses it's own bundled flash plugin...yet when I just re-installed the flash installer in the Software Center it fixed the issue in Chrome as well. Weird.

---

### Post by nico23 on 2012-04-07
kubuntu 12.04 it worked yesterday. stangly i had to setup firefox sync again today. bookmarks and other settings seem to be there. i remember a update on this package. now there is nothign shows in addon manager. and there should be a flash***.so in /usr/lib/firefox/plugins/ right? there is nothing.

```
sudo apt-get --reinstall install flashplugin-installer 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
0 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0 B von 8.334 B an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Vorkonfiguration der Pakete ...
(Lese Datenbank ... 103604 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von flashplugin-installer 11.2.202.228ubuntu3 (durch .../flashplugin-installer_11.2.202.228ubuntu3_amd64.deb) ...
Ersatz für flashplugin-installer wird entpackt ...
Trigger für update-notifier-common werden verarbeitet ...
http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.228.orig.tar.gz
Installing from local file /tmp/tmpZI7d3o.gz
Flash Plugin installed.
flashplugin-installer (11.2.202.228ubuntu3) wird eingerichtet ...
```

---

### Post by chrisccoulson on 2012-04-07
> **nico23 said:**
> kubuntu 12.04 it worked yesterday. stangly i had to setup firefox sync again today. bookmarks and other settings seem to be there. i remember a update on this package. now there is nothign shows in addon manager. and there should be a flash***.so in /usr/lib/firefox/plugins/ right? there is nothing.



No, there definitely should not be a flash plugin in /usr/lib/firefox/plugins

---

### Post by shuttleworthwannabe on 2012-04-07
There is a update on flash that seems to fix this issue--just updated a while ago.

---

