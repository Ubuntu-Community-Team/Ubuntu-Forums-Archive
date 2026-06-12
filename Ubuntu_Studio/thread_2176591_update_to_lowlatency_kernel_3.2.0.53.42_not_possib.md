---
title: "update to lowlatency kernel 3.2.0.53.42 not possible (dependency problem in 12.04)"
date: 2013-09-25
forum: Ubuntu Studio
---

### Post by Alexander_Keller on 2013-09-25
Hi folks,

Hope this is the right place for the posting as the lowlatency kernel is of particular interest in UbuntuStudio.

Using UbuntuStudio 12.04 LTS (German localisation) I've got a problem updating via apt-get/aptitude/synaptic (the package managment program does not matter) the lowlatency kernel. There is obviously a dependency problem with the kernel-headers and I'd like to know how to avoid it, or rather see it solved on the repository side.

Here is aptitude's output after ```
sudo aptitude update
``` and ```
sudo aptitude full-upgrade
```

> Die folgenden Pakete werden aktualisiert:       
  linux-lowlatency 
1 Pakete aktualisiert, 0 zusätzlich installiert, 0 werden entfernt und 0 nicht aktualisiert.
0 B/1.726 B an Archiven müssen heruntergeladen werden. Nach dem Entpacken werden 0 B zusätzlich belegt sein.
Möchten Sie fortsetzen? [Y/n/?] y
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-lowlatency:
 linux-lowlatency hängt ab von linux-image-lowlatency (= 3.2.0.52.41); aber:
  Version von linux-image-lowlatency auf dem System ist 3.2.0.53.42.
 linux-lowlatency hängt ab von linux-headers-lowlatency (= 3.2.0.52.41); aber:
  Version von linux-headers-lowlatency auf dem System ist 3.2.0.53.42.
dpkg: Fehler beim Bearbeiten von linux-lowlatency (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Es wurde kein Apport-Bericht verfasst, da die Fehlermeldung darauf hindeutet, dass dies lediglich ein Folgefehler eines vorherigen Problems ist.
                        Fehler traten auf beim Bearbeiten von:
 linux-lowlatency
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ein Paket konnte nicht installiert werden. Versuch, dies zu lösen:
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von linux-lowlatency:
 linux-lowlatency hängt ab von linux-image-lowlatency (= 3.2.0.52.41); aber:
  Version von linux-image-lowlatency auf dem System ist 3.2.0.53.42.
 linux-lowlatency hängt ab von linux-headers-lowlatency (= 3.2.0.52.41); aber:
  Version von linux-headers-lowlatency auf dem System ist 3.2.0.53.42.
dpkg: Fehler beim Bearbeiten von linux-lowlatency (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 linux-lowlatency

Greatful for any help
cheers
Alexander

---

### Post by ibjsb4 on 2013-09-25
```
The following packages will be upgraded:
linux-lowlatency
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
B/1.726 0 B of archives must be downloaded. After unpacking 0 B will be additionally used.
Would you like to continue? [Y / n /?] Y
dpkg: dependency problems prevent configuration of linux-lowlatency:
linux-lowlatency depends on linux-image-lowlatency (= 3.2.0.52.41), but:
Version of linux-image-lowlatency on the system is 3.2.0.53.42.
linux-lowlatency depends on linux-headers-lowlatency (= 3.2.0.52.41), but:
Version of linux-headers-lowlatency on the system is 3.2.0.53.42.
dpkg: error processing linux-lowlatency (- configure):
Dependency problems - leaving unconfigured
There was no apport report written because the error message indicates that this is merely a result of a previous error problem.
Errors were encountered while processing:
linux-lowlatency
E: Sub-process / usr / bin / dpkg returned an error code (1)
A package failed to install. Attempt to solve this:
dpkg: dependency problems prevent configuration of linux-lowlatency:
linux-lowlatency depends on linux-image-lowlatency (= 3.2.0.52.41), but:
Version of linux-image-lowlatency on the system is 3.2.0.53.42.
linux-lowlatency depends on linux-headers-lowlatency (= 3.2.0.52.41), but:
Version of linux-headers-lowlatency on the system is 3.2.0.53.42.
dpkg: error processing linux-lowlatency (- configure):
Dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-lowlatency
```

3.2.0.52.41, is this the currently running kernel or can you remove it?

---

### Post by Alexander_Keller on 2013-09-25
Hi ibjsb4

currently I've switched to the 3.20.53-generic kernel as standard boot option. The lowlatency kernel (.53) can't boot as it's not configured.

The thing is: After years of customization I prefer having as much on standard update settings as possible, including the lowlatency-kernel. And that is what I would like to have. For the time being the latest lowlatency version is just not booted (customization again). The previous version does still work when I need lowlatency for recording. But I don't think that's the way it should be.

Anybody who knows whom to ask to set the kernel-headers correctly that dpkg will implement the latest lowlatency kernel?

If I had known whom to ask, I'd have asked the person directly - unfortuntately I didn't and still don't.

cu
alexander

---

