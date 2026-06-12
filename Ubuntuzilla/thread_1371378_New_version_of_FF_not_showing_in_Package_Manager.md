---
title: "New version of FF not showing in Package Manager"
date: 2010-01-03
forum: Ubuntuzilla
---

### Post by LeeU on 2010-01-03
I already have a copy of Firefox 3.0.4 on my system but after adding the Ubuntuzilla repository, FF 3.5 does not sure in the Synaptic Package Manager. How do I make the upgrade?

[LIST]
[*]When I am able to obtain FF 3.5+, will it be an upgrade to the one I have now and include everything for the current user? (Sorry if I missed it, I didn't find this info anyway.)
[*]FF 2.0 still shows up in the Package Manager as being installed.
[/LIST]

---

### Post by nanotube on 2010-01-03
> **LeeU said:**
> I already have a copy of Firefox 3.0.4 on my system but after adding the Ubuntuzilla repository, FF 3.5 does not sure in the Synaptic Package Manager. How do I make the upgrade?

[LIST]
[*]When I am able to obtain FF 3.5+, will it be an upgrade to the one I have now and include everything for the current user? (Sorry if I missed it, I didn't find this info anyway.)
[*]FF 2.0 still shows up in the Package Manager as being installed.
[/LIST]

Hi
as per the instructions on the ubuntuzilla website, the package you should be looking for is called "firefox-mozilla-build". that's the package you should install. 

also yes, your profile will be picked up automatically by the new firefox.

please follow instructions precisely, on [http://ubuntuzilla.sourceforge.net](http://ubuntuzilla.sourceforge.net)

Let know if you have any other questions.

---

### Post by LeeU on 2010-01-03
Sorry about that. I didn't really pay attention to the name of the package. I did find it but I have run into some problems trying to install it. When attempting to install using the Synaptic Package Manager, I get the following error message:

```

E: /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 2

```

When I checked the properties, it shows it as being installed but it doesn't list any installed files. I tried doing a complete removal but got the following error message:

```

E: firefox-mozilla-build: Package is in a very bad inconsistent state - you should reinstall it before attempting a removal

```

It actually stops after the "- you should" but it once displayed the rest. When I try to reinstall it, I get the following error message:

```

E: /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb: trying to overwrite `/usr/bin/firefox', which is also in package firefox-3.0

```

I then changed it to just "Mark for Removal" and was able to remove it. I have tried doing this a few times, but it's the same each time.

I then tried doing it through a terminal and got the following error code:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 239437 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb) ...
dpkg-divert: 'diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build' clashes with 'local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg-divert: mismatch on package
  when removing 'diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
  found 'local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I then had to go through the same procedures to remove it. Any ideas what is wrong?

---

### Post by nanotube on 2010-01-03
> **LeeU said:**
> Sorry about that. I didn't really pay attention to the name of the package. I did find it but I have run into some problems trying to install it. When attempting to install using the Synaptic Package Manager, I get the following error message:

```

E: /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb: subprocess pre-installation script returned error exit status 2

```

When I checked the properties, it shows it as being installed but it doesn't list any installed files. I tried doing a complete removal but got the following error message:

```

E: firefox-mozilla-build: Package is in a very bad inconsistent state - you should reinstall it before attempting a removal

```

It actually stops after the "- you should" but it once displayed the rest. When I try to reinstall it, I get the following error message:

```

E: /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb: trying to overwrite `/usr/bin/firefox', which is also in package firefox-3.0

```

I then changed it to just "Mark for Removal" and was able to remove it. I have tried doing this a few times, but it's the same each time.

I then tried doing it through a terminal and got the following error code:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  firefox-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.5MB of archives.
After this operation, 0B of additional disk space will be used.
Selecting previously deselected package firefox-mozilla-build.
(Reading database ... 239437 files and directories currently installed.)
Unpacking firefox-mozilla-build (from .../firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb) ...
dpkg-divert: 'diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build' clashes with 'local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg-divert: mismatch on package
  when removing 'diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build'
  found 'local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/firefox-mozilla-build_3.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I then had to go through the same procedures to remove it. Any ideas what is wrong?

Hi,

yes, i know exactly what's wrong - you have a local diversion of /usr/bin/firefox, which was created by the old ubuntuzilla script.

as the instructions on the website say (see the red-background inset box at the top of the 'installation' section), if you have used the old ubuntuzilla script to install, first, use the old ubuntuzilla script to remove, to clean up the system, and only /then/ install the package from the new repository. 

please give that a go.

---

### Post by LeeU on 2010-01-03
I didn't realize that I had used Ubuntuzilla before that's why I didn't pay attention to it. I'll give it a go. Thanks.

---

### Post by LeeU on 2010-01-03
Okay, I entered the command "ubuntuzilla.py -a remove -p firefox-mozilla-build" and got:

```

bash: /usr/local/bin/ubuntuzilla.py: Permission denied

```

I added "sudo" and got:

```

sudo: ubuntuzilla.py: command not found

```

Not sure what to do now ...

---

### Post by nanotube on 2010-01-03
err, well... something's messed up in your ubuntuzilla.py permissions...
suggest you grab the latest ubuntuzilla installer script from ubuntuzilla website ( [http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/) , in the 'ubuntuzilla' directory), install the script, then run the script with the 'remove' action on firefox, then try the repository installation again.

(also note that your ubuntuzilla command should be 'ubuntuzilla.py -a remove -p firefox' (not firefox-mozilla-build) )

---

### Post by yannn on 2010-03-01
Great, I didn't read that it was necessary to run 'ubuntuzilla.py -a remove -p firefox' before removing ubuntuzilla and installing firefox-mozilla-build. I removed ubuntuzilla, installed firefox-mozilla-build and now I'm really stuck:

1) I don't have ubuntuzilla installed anymore to run 'ubuntuzilla.py -a remove -p firefox'

2) I can't install firefox-mozilla-build anymore because it tells me:

```
$ sudo apt-get install firefox-mozilla-build
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Lese Status-Informationen ein... Fertig
firefox-mozilla-build ist schon die neueste Version.
Probieren Sie »apt-get -f install«, um dies zu korrigieren:
Die folgenden Pakete haben nicht erfüllte Abhängigkeiten:
  ubuntuzilla: Hängt ab: libnotify-bin soll aber nicht installiert werden
               Hängt ab: gdebi soll aber nicht installiert werden
E: Nicht erfüllte Abhängigkeiten. Versuchen Sie »apt-get -f install« ohne jegliche Pakete (oder geben Sie eine Lösung an).
```

3) I cannot install firefox-mozilla-build correctly neither:

```
$ sudo apt-get install firefox-mozilla-build
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Lese Status-Informationen ein... Fertig
firefox-mozilla-build ist schon die neueste Version.
Probieren Sie »apt-get -f install«, um dies zu korrigieren:
Die folgenden Pakete haben nicht erfüllte Abhängigkeiten:
  ubuntuzilla: Hängt ab: libnotify-bin soll aber nicht installiert werden
               Hängt ab: gdebi soll aber nicht installiert werden
E: Nicht erfüllte Abhängigkeiten. Versuchen Sie »apt-get -f install« ohne jegliche Pakete (oder geben Sie eine Lösung an).
```

4) Running 'apt-get -f install' doesn't work neither:

```
$ sudo apt-get -f install
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Lese Status-Informationen ein... Fertig
Abhängigkeiten werden korrigiert... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  gdebi gnome-icon-theme libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnomevfs2-extra libnotify-bin libvte-common libvte9 python-vte
Die folgenden Pakete werden ENTFERNT:
  firefox-mozilla-build
Die folgenden NEUEN Pakete werden installiert:
  gdebi gnome-icon-theme libgnome2-canvas-perl libgnome2-perl libgnome2-vfs-perl libgnomevfs2-extra libnotify-bin libvte-common libvte9 python-vte
0 aktualisiert, 10 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
2 nicht vollständig installiert oder entfernt.
Es müssen noch 0B von 5.071kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 27,1MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]?
(Lese Datenbank ... 331074 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne firefox-mozilla-build ...
dpkg-divert: Keine Übereinstimmung mit Paket
  beim Entfernen von »diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu by firefox-mozilla-build«
  »local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu« gefunden
dpkg: Fehler beim Bearbeiten von firefox-mozilla-build (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 2 zurück
Fehler traten auf beim Bearbeiten von:
 firefox-mozilla-build
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

5) I can't re-install ubuntuzilla because it tries to remove firefox-mozilla-build first, which leads to 2).


I tried downloading the .py file from [http://sourceforge.net/projects/ubuntuzilla/files/ubuntuzilla/4.1.1/ubuntuzilla_4.1.1.py/download](http://sourceforge.net/projects/ubuntuzilla/files/ubuntuzilla/4.1.1/ubuntuzilla_4.1.1.py/download)
But when I run it nothing happens and I get the following:

```
$ sudo ./ubuntuzilla_4.1.1.py -a remove -p firefox
from: can't read /var/mail/optparse
```


Can anybody please help me?

---

### Post by yannn on 2010-03-01
I don't know why, but now running 'ubuntuzilla.py -a remove -p firefox' worked..

---

### Post by nanotube on 2010-03-01
> **yannn said:**
> I don't know why, but now running 'ubuntuzilla.py -a remove -p firefox' worked..

so everything's good now, problem solved?

---

