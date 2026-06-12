---
title: "package problems, apt-get upgrade fails"
date: 2012-01-21
forum: Server Platforms
---

### Post by Keyno on 2012-01-21
Hello, I have a problem  right here.

If i do apt-get update and then apt-get upgrade with root, I get this thing as output:
```
root@v2201201112187210:/usr/src/ghost/ghost# apt-get update
Ign http://de.archive.ubuntu.com oneiric InRelease
OK   http://de.archive.ubuntu.com oneiric Release.gpg
OK   http://de.archive.ubuntu.com oneiric Release
OK   http://de.archive.ubuntu.com oneiric/main Sources
OK   http://de.archive.ubuntu.com oneiric/restricted Sources
OK   http://de.archive.ubuntu.com oneiric/universe Sources
OK   http://de.archive.ubuntu.com oneiric/multiverse Sources
OK   http://de.archive.ubuntu.com oneiric/main amd64 Packages
OK   http://de.archive.ubuntu.com oneiric/restricted amd64 Packages
OK   http://de.archive.ubuntu.com oneiric/universe amd64 Packages
OK   http://de.archive.ubuntu.com oneiric/multiverse amd64 Packages
OK   http://de.archive.ubuntu.com oneiric/main i386 Packages
OK   http://de.archive.ubuntu.com oneiric/restricted i386 Packages
OK   http://de.archive.ubuntu.com oneiric/universe i386 Packages
OK   http://de.archive.ubuntu.com oneiric/multiverse i386 Packages
OK   http://de.archive.ubuntu.com oneiric/main TranslationIndex
OK   http://de.archive.ubuntu.com oneiric/multiverse TranslationIndex
OK   http://de.archive.ubuntu.com oneiric/restricted TranslationIndex
OK   http://de.archive.ubuntu.com oneiric/universe TranslationIndex
OK   http://de.archive.ubuntu.com oneiric/main Translation-de
OK   http://de.archive.ubuntu.com oneiric/main Translation-en
OK   http://de.archive.ubuntu.com oneiric/multiverse Translation-de
OK   http://de.archive.ubuntu.com oneiric/multiverse Translation-en
OK   http://de.archive.ubuntu.com oneiric/restricted Translation-de
OK   http://de.archive.ubuntu.com oneiric/restricted Translation-en
OK   http://de.archive.ubuntu.com oneiric/universe Translation-de
OK   http://de.archive.ubuntu.com oneiric/universe Translation-en
Paketlisten werden gelesen... Fertig
root@v2201201112187210:/usr/src/ghost/ghost# apt-get upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Statusinformationen werden eingelesen... Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
15 nicht vollständig installiert oder entfernt.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
initscripts (2.88dsf-13.10ubuntu8) wird eingerichtet ...
mount: keine Berechtigung
dpkg: Fehler beim Bearbeiten von initscripts (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von netbase:
 netbase hängt ab von initscripts; aber:
  Paket initscripts ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von netbase (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
                                                                                   Es wurde kein Apport-Bericht verfasst, da                                  das Limit MaxReports bereits erreicht ist
                                          Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht is                                 t
 Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
                                                                                    Es wurde kein Apport-Bericht verfasst, d                                 a das Limit MaxReports bereits erreicht ist
                                           dpkg: Abhängigkeitsprobleme verhindern Konfiguration von ntpdate:
 ntpdate hängt ab von netbase; aber:
  Paket netbase ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von ntpdate (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von ifupdown:
 ifupdown hängt ab von initscripts (>= 2.88dsf-13.3); aber:
  Paket initscripts ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von ifupdown (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von procps:
 procps hängt ab von initscripts; aber:
  Paket initscripts ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von procps (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von rsyslog:
 rsyslog hängt ab von initscripts (>= 2.88dsf-13.3); aber:
  Paket initscripts ist noch nicht konfiguriert.
dpkg: Fehler beim BearbeiEs wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
                                                                                                            Es wurde kein Ap                                 port-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
                                                                   Es wurde kein Apport-Bericht verfasst, da das Limit MaxRe                                 ports bereits erreicht ist
                          Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
                                                                                                             Es wurde kein A                                 pport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
                                                                    Es wurde kein Apport-Bericht verfasst, da das Limit MaxR                                 eports bereits erreicht ist
                           ten von rsyslog (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von udev:
 udev hängt ab von procps; aber:
  Paket procps ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von udev (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von apache2.2-common:
 apache2.2-common hängt ab von procps; aber:
  Paket procps ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von apache2.2-common (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von apache2-mpm-prefork:
 apache2-mpm-prefork hängt ab von apache2.2-common (= 2.2.21-3ubuntu2); aber:
  Paket apache2.2-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von apache2-mpm-prefork (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von apache2:Es wurde kein Apport-Bericht verfasst, da das Limit MaxRepo                                 rts bereits erreicht ist
                        Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist
                                                                                                           Es wurde kein App                                 ort-Bericht verfasst, da das Limit MaxReports bereits erreicht ist

 apache2 hängt ab von apache2-mpm-worker (= 2.2.21-3ubuntu2) | apache2-mpm-prefork (= 2.2.21-3ubuntu2) | apache2-mpm-event (                                 = 2.2.21-3ubuntu2) | apache2-mpm-itk (= 2.2.21-3ubuntu2); aber:
  Paket apache2-mpm-worker ist nicht installiert.
  Paket apache2-mpm-prefork ist noch nicht konfiguriert.
  Paket apache2-mpm-event ist nicht installiert.
  Paket apache2-mpm-itk ist nicht installiert.
 apache2 hängt ab von apache2.2-common (= 2.2.21-3ubuntu2); aber:
  Paket apache2.2-common ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von apache2 (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von libapache2-mod-php5:
 libapache2-mod-php5 hängt ab von apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; aber:
  Paket apache2-mpm-prefork ist noch nicht konfiguriert.
  Paket apache2-mpm-itk ist nicht installiert.
 libapache2-mod-php5 hängt ab von apache2.2-common; aber:
Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist

                                                                                   dpkg: Fehler beim Bearbeiten von libapach                                 e2-mod-php5 (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von openssh-server:
 openssh-server hängt ab von procps; aber:
  Paket procps ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von openssh-server (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von ubuntu-minimal:
 ubuntu-minimal hängt ab von ifupdown; aber:
  Paket ifupdown ist noch nicht konfiguriert.
 ubuntu-minimal hängt ab von netbase; aber:
  Paket netbase ist noch nicht konfiguriert.
 ubuntu-minimal hängt ab von ntpdate; aber:
  Paket ntpdate ist noch nicht konfiguriert.
 ubuntu-minimal hängt ab von procps; aber:
  Paket procps ist noch nicht konfiguriert.
 ubuntu-minimal hängt ab von rsyslog; aber:
  Paket rsyslog ist noch nicht konfiguriert.
 ubuntu-minimal hängt ab von udev; aber:
  Paket udev ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von ubuntu-minimal (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von phpmyadmin:
 phpmyadmin hängt ab von libapache2-mod-php5 | libapache2-mod-php5filter | php5-cgi | php5-fpm | php5; aber:
  Paket libapache2-mod-php5 ist noch nicht konfiguriert.
  Paket libapache2-mod-php5filter ist nicht installiert.
  Paket php5-cgi ist nicht installiert.
  Paket php5-fpm ist nicht installiert.
  Paket php5 ist nicht installiert.
dpkg: Fehler beim Bearbeiten von phpmyadmin (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von ssh:
 ssh hängt ab von openssh-server; aber:
  Paket openssh-server ist noch nicht konfiguriert.
dpkg: Fehler beim Bearbeiten von ssh (--configure):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 initscripts
 netbase
 ntpdate
 ifupdown
 procps
 rsyslog
 udev
 apache2.2-common
 apache2-mpm-prefork
 apache2
 libapache2-mod-php5
 openssh-server
 ubuntu-minimal
 phpmyadmin
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Maybe it's caused by my sources.list, which I changed to this:
```
deb http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb http://de.archive.ubuntu.com/ubuntu/ precise main universe
```

from this:
```
deb http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
```

So, yes, I'm running 11.10

Any ideas how to solve this?

thx, Keyno

---

