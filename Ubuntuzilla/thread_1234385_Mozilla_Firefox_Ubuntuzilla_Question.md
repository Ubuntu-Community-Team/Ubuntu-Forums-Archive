---
title: "Mozilla Firefox Ubuntuzilla Question"
date: 2009-08-07
forum: Ubuntuzilla
---

### Post by sports fan Matt on 2009-08-07
Since my FF "Check for updates is greyed out and im running ubuntuzilla 4.73..is there anything that needs to be done for the greyed updates to be shown..Below Is what I ran to fix the issue..any ideas?

I ran ffice@office-desktop:~$ notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.0.8</b>. The new release available is <b>3.0.9</b>. Please refer to these <a href="http://ubuntuzilla.sourceforge.net/#updatefirefox">detailed update instructions</a>.'
office@office-desktop:~$ ubuntuzilla.py -p firefox -a checkforupdategui -d
Your commandline options:
{'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.2
Currently installed version of Firefox : /bin/sh: firefox: not found
['7d7579913e06aefd06eee3c04a745366-0']
# This file allows processes on the machine with id 7d7579913e06aefd06eee3c04a745366 using 
# display :0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-LcUe7MqFTo,guid=26086e8947c7368ac4e428334a7c8fd8
DBUS_SESSION_BUS_PID=3093
DBUS_SESSION_BUS_WINDOWID=4194305

unix:abstract=/tmp/dbus-LcUe7MqFTo,guid=26086e8947c7368ac4e428334a7c8fd8

---

### Post by sports fan Matt on 2009-08-08
Im gonna give a bump since its been nearly 24 hrs

---

### Post by nanotube on 2009-08-08
hi

assuming you already installed the mozilla build with ubuntuzilla:

to get the "check for updates" functionality available, just run firefox with 'gksudo'.

see these detailed update instructions on the ubuntuzilla website:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Update_Official_Mozilla_Build_of_Firefox](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Update_Official_Mozilla_Build_of_Firefox)

if you haven't yet installed the mozilla build, then just run ubuntuzilla with the "install" action, to install the latest version.

---

