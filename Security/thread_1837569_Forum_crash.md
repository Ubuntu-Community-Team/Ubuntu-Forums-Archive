---
title: "Forum crash"
date: 2011-09-02
forum: Security
---

### Post by loekanle on 2011-09-02
FORUM CRASHING, I need help my ClamTk virus scanner has no menu options like file, view , option and etc

and the antivirus engine and GUI version has a stop sign instead of a check mark 

Help!!!!!!!!!!

---

### Post by lisati on 2011-09-02
Moved to own thread. Please do not hijack other people's thread or post the same request multiple times.

---

### Post by nastynate1219 on 2011-09-05
solved

the menu is at the top of the panel near the ubuntu sign just move it around in the top left panel and you should see options

these are some command codes to update antivirus engine enter them separately 

sudo add-apt-repository ppa:ubuntu-clamav/ppa; sudo apt-get update; sudo apt-get -y upgrade; sudo freshclam

Will give later defs and engine.

courtesy of actionparsnip (andrew-woodhead666) of launchpad 

that will only update the antivirus engine

to Update GUI version in clamTK you need
To download the newest GUI, go here:

[http://clamtk.sf.net](http://clamtk.sf.net) and follow the downloads links. Double-click the .deb you download.

Also, see here:

Why is the GUI telling me the GUI is outdated?
[http://clamtk.sourceforge.net/faq.html#outdated_gui](http://clamtk.sourceforge.net/faq.html#outdated_gui)

credit due to Dave M (dave-nerd)

---

