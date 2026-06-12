---
title: "can't install slapd on x86_64 Kubuntu 9.10"
date: 2009-11-24
forum: Server Platforms
---

### Post by Asterix99 on 2009-11-24
Hello,
I've read a lot of postings in this forum, but didn't found the answer.
I can't install openldap on my Kubuntu 9.10 (x86_64) system.
After a 
```
sudo apt-get install slapd
```I got the error (Sorry some outputs are in german, but the error is in english.)

```

Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Lese Status-Informationen ein... Fertig
Die folgenden NEUEN Pakete werden installiert:
  slapd
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 23 nicht aktualisiert.
Es müssen 1.628kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 4.289kB Plattenplatz zusätzlich benutzt.
Hole:1 http://de.archive.ubuntu.com karmic/main slapd 2.4.18-0ubuntu1 [1.628kB]
Es wurden 1.628kB in 2s geholt (794kB/s)
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket slapd.
(Lese Datenbank ... 153059 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke slapd (aus .../slapd_2.4.18-0ubuntu1_amd64.deb) ...
Verarbeite Trigger für man-db ...
Verarbeite Trigger für sreadahead ...
Richte slapd ein (2.4.18-0ubuntu1) ...
  Backing up /etc/ldap/slapd.d/ in /var/backups/slapd-2.4.15-1ubuntu3... done.
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldap:/// ldapi:///' -g openldap -u openldap -F /etc/ldap/slapd.d/
invoke-rc.d: initscript slapd, action "start" failed.
dpkg: Fehler beim Bearbeiten von slapd (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I've removed slapd again and tried a reinstallation. Next try was to delete /etc/ldap and reinstallation. But all tries with same error.

Any idea what I can do ?

---

### Post by Asterix99 on 2009-11-26
Hello,

can really nobody help me ?

---

### Post by stefanadelbert on 2009-11-26
Try starting from scratch again:

```
sudo apt-get purge slapd
```
This will make sure that you're starting from scratch.
```
sudo apt-get install slapd ldap-utils
```

I'm also having trouble with installing LDAP, but on 9.04. Seems that things have changed in 9.10.

You could also try after you're purged slapd

```
rm -rf /var/lib/ldap/*
```
which will clear out previous LDAP entries, although "purge" might already do this.

---

### Post by Asterix99 on 2009-11-26
Hi,

you are my champ. Purge is the winner.
Now I could install slapd and it is runnung.
I can start configuring ldap now.

Thanks a lot.

---

