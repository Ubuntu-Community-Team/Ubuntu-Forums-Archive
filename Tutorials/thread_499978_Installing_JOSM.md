---
title: "Installing JOSM"
date: 2007-07-13
forum: Tutorials
---

### Post by spd106 on 2007-07-13
[COLOR="Red"]Please see the Ubuntu help wiki page on JOSM at [https://help.ubuntu.com/community/JOSM](https://help.ubuntu.com/community/JOSM)[/COLOR]

This is an installation guide for the Java Open Street Map editor on Ubuntu 7.04 (Feisty Fawn). It has not yet been tested on any previous version of Ubuntu, though it will most likely work without problem.

The Open Street Map project has been around for several years now and the best currently developed editor (JOSM) has not yet been packaged for Debian or Ubuntu. There are several sticking points, but while they are being resolved I have put this installation guide together to allow you to use the project's main development jar file directly. Once JOSM has been cleared for Debian inclusion this guide could be used to install the latest daily release.
Be advised that some potential licensing problems have been raised and are not yet fully resolved.
[SIZE="3"]
Step 0 - Install Java[/SIZE]
Unfortunately GNU's GCJ is not compatible yet, so you will have install Sun Java JRE of at least v1.5. This is best done through Synaptic or the following command. Requires universe repository.
i) ```
sudo aptitude install sun-java6-jre
```
ii) Ensure the Java path is set to the latest Java version.
```
sudo update-alternatives --config java
```
[SIZE="3"]
Step 1 - Install JOSM[/SIZE]
i) Download JOSM
```
wget http://josm.openstreetmap.de/download/josm-latest.jar
```
Also maybe take a look at the recent changes.
[http://josm.openstreetmap.de/log/?verbose=on](http://josm.openstreetmap.de/log/?verbose=on)
ii) Copy the jarfile into a system directory.
```
sudo mv -v josm-latest.jar /usr/share/java/
```

iii) Now it should start with the following command.
```
java -jar /usr/share/java/josm-latest.jar
```
[SIZE="3"]
Step 3 - GNOME integration[/SIZE]
For better integration into the gnome desktop I used these steps
i) Download the menu icon and place it in the /usr/share/pixmaps/ directory.
```
wget http://josm.openstreetmap.de/browser/trunk/images/logo.png
```
```
sudo mv -v logo.png /usr/share/pixmaps/josm.png
```
ii) Use the following code to create a josm.desktop file place it in the /usr/share/applications/ directory. I only speak English so I am unable to add any translations at this time.
```
[Desktop Entry]
Encoding=UTF-8
Name=JOSM
Comment=Import GPX files and upload Open Street Map data
Exec=java -jar /usr/share/java/josm-latest.jar
Icon=josm.png
Terminal=false
Type=Application
StartupNotify=true
Categories=Application;GTK;Java;Utility;Viewer;
MimeType=application/x-GPS-Exchange-Format
```

Now you should have an entry for JOSM in your Applications -> Accessories menu. You only have to repeat step 1 to update JOSM to the latest daily build.

---

### Post by klap-in on 2008-01-01
josm.eigenheimstrasse.de has changeover to: 
[http://josm.openstreetmap.de/wiki/]("http://josm.openstreetmap.de/wiki/")

So at this moment the new locations are: 
[http://josm.openstreetmap.de/download/josm-latest.jar](http://josm.openstreetmap.de/download/josm-latest.jar)
[http://josm.openstreetmap.de/browser/trunk/images/logo.png](http://josm.openstreetmap.de/browser/trunk/images/logo.png)

---

### Post by RussNelson on 2008-01-26
For the desktop file, I would have this in the code block, to be consistent with the previous two code blocks:
```

sudo cat > /usr/share/applications/josm.desktop <<EOF
[Desktop Entry]
Encoding=UTF-8
Name=JOSM
Comment=Import GPX files and upload Open Street Map data
Exec=java -jar /usr/share/java/josm-latest.jar
Icon=josm.png
Terminal=false
Type=Application
StartupNotify=true
Categories=Application;GTK;Java;Utility;Viewer;
MimeType=application/x-GPS-Exchange-Format
EOF

```

---

### Post by spd106 on 2008-01-26
Thanks for the recommendation RussNelson.

I've created a page in the help wiki for JOSM. This will make it easier if anyone has anything further to add or any changes they would like to make.

I'm not trying compete with the OSM wiki, this should be for Ubuntu specific information only.

[https://help.ubuntu.com/community/JOSM](https://help.ubuntu.com/community/JOSM)

---

### Post by achadwick on 2008-02-23
Thanks for the useful info, spd103 and everyone in this thread too! :KS Is there anyone working on packaging this for Debian/Ubuntu in the form of a normal .deb?

---

### Post by spd106 on 2008-02-23
There has been a bug open on launchpad for a good while now, see [https://bugs.launchpad.net/ubuntu/+bug/94009](https://bugs.launchpad.net/ubuntu/+bug/94009)

Upstream in Debian I think the main concern has been resolved and there is a sponsor attached. Now we just need someone with the time and skills to put a package together.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=385371](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=385371)

---

### Post by pobice on 2009-04-22
I've uploaded the Debian package to the Openstreetmap Launchpad PPA:

[https://launchpad.net/~openstreetmap/+archive/ppa](https://launchpad.net/~openstreetmap/+archive/ppa)

---

### Post by azitizz on 2012-06-27
Hi There, I'm wondering why the plug-ins list in JOSM has only a few of them showing up, (only 10 of them) even after updating the plugin list it doesnt increase the list. 

Any clues?
Thanks.

---

### Post by gordintoronto on 2012-06-28
You're looking at a thread which is three years old.

---

