---
title: "[Ubuntuzilla] checkforupdategui failed"
date: 2009-08-10
forum: Ubuntuzilla
---

### Post by yel on 2009-08-10
Hi,

I installed Ubuntuzilla on Hardy to install Firefox 3.5.
The installation was correct, but the check for updates failed.

I tried this manual command:

```
/usr/local/bin/ubuntuzilla.py -p firefox -a checkforupdategui -d 2>&1 | logger -p user.notice -t "UBUNTUZILLA" --
```And I had the following logs in syslog:

```
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: Your commandline options:
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: {'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: Debug mode ON.
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: Latest release version of Firefox : 3.5.2
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: Currently installed version of Firefox : 3.5.1
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: ['9581b52338b7fd9d61b178604996a1cc-0']
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: # This file allows processes on the machine with id 9581b52338b7fd9d61b178604996a1cc using 
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: # display :0.0 to find the D-Bus session bus with the below address.
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: # If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: # be used rather than this file.
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: # See "man dbus-launch" for more details.
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: DBUS_SESSION_BUS_PID=6054
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: DBUS_SESSION_BUS_WINDOWID=65011713
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: 
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: Traceback (most recent call last):
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     bs.start()
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 300, in start
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     fi.start()
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 353, in start
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     self.checkforupdateGui()
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 777, in checkforupdateGui
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     self.updateActionsGui()
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 808, in updateActionsGui
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     notifier = Notifier()
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/usr/local/bin/ubuntuzilla.py", line 182, in __init__
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     bus      = dbus.SessionBus()
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     mainloop=mainloop)
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:   File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
Aug 10 20:26:50 user1-desktop UBUNTUZILLA:     bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
Aug 10 20:26:50 user1-desktop UBUNTUZILLA: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-IhAIrCB4B6: Connection refused
```

---

### Post by nanotube on 2009-08-10
can you run from terminal "notify-send bla" and see if a little message with "bla" shows up?

---

### Post by yel on 2009-08-10
Yes I see the message.

---

### Post by nanotube on 2009-08-10
> **yel said:**
> Yes I see the message.

hmm, now try 
```
ubuntuzilla.py -a checkforupdategui -p firefox -d
```
again

---

### Post by yel on 2009-08-11
> **nanotube said:**
> hmm, now try 
```
ubuntuzilla.py -a checkforupdategui -p firefox -d
```
again

I have exaclty the same error as in my first post:

```
Your commandline options:
{'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.2
Currently installed version of Firefox : 3.5.1
['9581b52338b7fd9d61b178604996a1cc-0']
# This file allows processes on the machine with id 9581b52338b7fd9d61b178604996a1cc using 
# display :0.0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
DBUS_SESSION_BUS_PID=6054
DBUS_SESSION_BUS_WINDOWID=65011713

unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 353, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 777, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 808, in updateActionsGui
    notifier = Notifier()
  File "/usr/local/bin/ubuntuzilla.py", line 182, in __init__
    bus      = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 217, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 106, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-IhAIrCB4B6: Connection refused
```

---

### Post by nanotube on 2009-08-11
hmm... strange, it works just fine for me (on intrepid).

let me try something - i'll post a modified ubuntuzilla.py here for you to try in a bit.

---

### Post by nanotube on 2009-08-11
Hi
here's a modified version of ubuntuzilla, that should be more robust as far as showing notifications.

just unzip it to wherewer, cd to that directory, and execute it with ```
python ubuntuzilla.py -a checkforupdategui -p firefox -d
```
and see if the notification shows up. 

if this works, i'll push it out as the next point release.

---

### Post by yel on 2009-08-11
I tried the new script, but it always fails with the following logs:

```
Your commandline options:
{'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.2
Currently installed version of Firefox : 3.5.1
['9581b52338b7fd9d61b178604996a1cc-0']
# This file allows processes on the machine with id 9581b52338b7fd9d61b178604996a1cc using 
# display :0.0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
DBUS_SESSION_BUS_PID=6054
DBUS_SESSION_BUS_WINDOWID=65011713

unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-IhAIrCB4B6: Connection refused
notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.5.1</b>. The new release available is <b>3.5.2</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Process returned code 1
ERROR showing GUI update notification.

```

I tried to reinstall the package libnotify-bin, but it changes nothing.

---

### Post by nanotube on 2009-08-11
well, what this seems to indicate to me is that there's something wrong with your dbus setup....

but i don't really know what to do to fix it. i don't suppose you have tried a reboot? :)

---

### Post by yel on 2009-08-11
> **nanotube said:**
> i don't suppose you have tried a reboot? :)

I reboot once a day.

On the other hand, I have just tested the scripts of test of the package *python-notify* and they work. They show a notification.

---

### Post by nanotube on 2009-08-13
Hi
well... here comes another try.
try this one, see if notification comes up. :)

---

### Post by yel on 2009-08-13
I still have the same errors:
```
Your commandline options:
{'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.2
Currently installed version of Firefox : 3.5.1
['9581b52338b7fd9d61b178604996a1cc-0']
# This file allows processes on the machine with id 9581b52338b7fd9d61b178604996a1cc using 
# display :0.0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
DBUS_SESSION_BUS_PID=6054
DBUS_SESSION_BUS_WINDOWID=65011713

unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-IhAIrCB4B6: Connection refused
notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.5.1</b>. The new release available is <b>3.5.2</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Process returned code 1
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-IhAIrCB4B6: Connexion refusée
ERROR showing GUI update notification.

```

As my tests with the package *python-notify* had been working, I took the liberty to change your script to do a test by implementing it. And it works, the notification shows up.
I attached the script if you want to have a look. My changes are between tags *# Start of test by yel* and *# End of test by yel*.

---

### Post by nanotube on 2009-08-13
Hi

the latest version that I posted for you a couple of posts ago already did use pynotify (the bit after line 843 in your modified version). It still didn't work for you?

could you open a fresh terminal, run command
```
env |grep DBUS
```
and then run command
```
more .dbus/session-bus/*
```
and check if the dbus_session_bus_address shown from the two is the same? (or just post complete output here)

also, for just in case... try ```
ls -al .dbus/session-bus/
```

as to your test code:

i see that in your test you have taken out the part that gets the dbus session bus address. this part is necessary in order for the notification to work from the cron job (since otherwise the cron job doesn't have information about the dbus session.

You say your modified script works for you when you run from a shell. Could I ask you to try your modified script by running it from a crontab? just add it to your crontab to run every minute, with the "-d" option to make sure the notification shows, and see if it shows anything.

also do the same for the last version that i posted and see if that works.

thanks for sticking with me through all this! :)

---

### Post by yel on 2009-08-14
Hi,

Here is the result of the first three commands. They shwo a different dbus_session_bus_address:
```
user1@user1-desktop:~$ env |grep DBUS
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-tKyFFCz2lo,guid=7c77c744fe9974119d6bfa514a851302
user1@user1-desktop:~$ more .dbus/session-bus/*
# This file allows processes on the machine with id 9581b52338b7fd9d61b178604996a1cc using 
# display :0.0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
DBUS_SESSION_BUS_PID=6054
DBUS_SESSION_BUS_WINDOWID=65011713
user1@user1-desktop:~$ ls -al .dbus/session-bus/
total 12
drwx------ 2 user1 user1 4096 2009-08-08 16:04 .
drwx------ 3 user1 user1 4096 2009-08-08 16:04 ..
-rw-r--r-- 1 user1 user1  466 2009-08-08 16:04 9581b52338b7fd9d61b178604996a1cc-0

```

You're right, it fails from cron.:(
Here is the result of my modified version:
```
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: /var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
Aug 14 10:00:02 user1-desktop UBUNTUZILLA:   warnings.warn(str(e), _gtk.Warning)
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: 
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: 
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.5.1</b>. The new release available is <b>3.5.2</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: Process returned code 1
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: 
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: ERROR showing GUI update notification.
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: Your commandline options:
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: {'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: Debug mode ON.
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: Latest release version of Firefox : 3.5.2
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: Currently installed version of Firefox : 3.5.1
Aug 14 10:00:02 user1-desktop UBUNTUZILLA: TEST python-notification : Failed to init
```

And your last one:
```
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: Your commandline options:
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: {'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: Debug mode ON.
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: Latest release version of Firefox : 3.5.2
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: Currently installed version of Firefox : 3.5.1
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: ['9581b52338b7fd9d61b178604996a1cc-0']
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: # This file allows processes on the machine with id 9581b52libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-IhAIrCB4B6: Connection refused
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.5.1</b>. The new release available is <b>3.5.2</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: Process returned code 1
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: /var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
Aug 14 10:04:02 user1-desktop UBUNTUZILLA:   warnings.warn(str(e), _gtk.Warning)
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-IhAIrCB4B6: Connection refused
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: ERROR showing GUI update notification.
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: 338b7fd9d61b178604996a1cc using 
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: # display :0.0 to find the D-Bus session bus with the below address.
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: # If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: # be used rather than this file.
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: # See "man dbus-launch" for more details.
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: DBUS_SESSION_BUS_PID=6054
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: DBUS_SESSION_BUS_WINDOWID=65011713
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: 
Aug 14 10:04:02 user1-desktop UBUNTUZILLA: unix:abstract=/tmp/dbus-IhAIrCB4B6,guid=2091f6f8ee85cdf69ecf249e4a7d85e2
```

---

### Post by nanotube on 2009-08-14
aha, ok, so the /root/ of the problem is that the dbus session that's sitting in your .dbus/session-bus is different from your "real" dbus-session. which, according to the docs, shouldn't be the case at all...

i notice that the date on the file is aug 8, even though you said you reboot every day... 

try deleting the file, then rebooting, and see if the contents of session-bus have synced up with the environment variable.

---

### Post by yel on 2009-08-14
After deleting the file in .dbus/session-bus and after rebooting, the file is not automatically recreated. All the scripts fail, either from cron or a shell, except mine which works from a shell.

I made additional tests from cron with the scripts of test of the package *python-notify* and I had this message:
```
libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
```

After some research I found this post: [http://ubuntuforums.org/showthread.php?t=615882]("http://ubuntuforums.org/showthread.php?t=615882")

So I did some tests from cron by adding *DISPLAY=:0.0* before the different versions of the scripts. Like this for example:
```
*/2 * * * * DISPLAY=:0.0 /usr/local/bin/ubuntuzilla.py -p firefox -a checkforupdategui -d 2>&1 | logger -p user.notice -t "UBUNTUZILLA" --
```

The first time, when the folder .dbus/session-bus is empty, only my version of the script works. A new file has been created in the folder. It is always out of sync compared to the variable DBUS_SESSION_BUS_ADDRESS. Then your two versions also work. There is apparently a problem of initializing the dbus session during boot which does not disturb my modified version of the script. And then, a new file of session dbus is created.

When I boot one more time, the file of session is always present in the folder .dbus/session-bus and it is always out of sync. The first time, only my version of the script works, then a new file of session is created, always out of sync. Then as the previous time, your two versions also work then.

---

### Post by nanotube on 2009-08-17
well, i have to say i'm stumped. i have no clue what's going on there... maybe there's a dbus bug in hardy or something? 

i see some stuff in launchpad on this topic... e.g. [https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/207157](https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/207157)

---

### Post by yel on 2009-08-18
Indeed, it seems to be that.

I add the following file as shown in the topic you've found:
```
# Place in /etc/X11/Xsession.d/75dbus_dbus-launch

## test for an existing bus daemon, just to be safe
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
    ## if not found, launch a new one
    eval `/usr/bin/dbus-launch --sh-syntax --exit-with-session`
fi
```I'm under GNOME, and even if they say there is not need this file, yet after a reboot it works with the script of your package. I found no problems yet. I still have the systems notification such as those of the update manager.

thanks

---

### Post by nanotube on 2009-08-18
Well, i must say this is excellent news :)
I was about ready to give up hope on getting this solved!

---

### Post by MatrixGIO on 2009-09-11
Hi nanotube,

I have the same problem.
the dbus version is the same (not differnt as yel had) and notification message works fine but i still getting refuse to connect to the server.
Any idea - ubuntuzilla version is 4.7.4

```

usr1@comp1:~$ env |grep DBUS
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-KuWC4nGpRX,guid=ca0b49693048782d03cd787e4aaac28d
usr1@comp1:~$ 
usr1@comp1:~$ 
usr1@comp1:~$ more .dbus/session-bus/*
::::::::::::::
.dbus/session-bus/494e8e1e3e56141480d9e2004648cc67-0
::::::::::::::
# This file allows processes on the machine with id 494e8e1e3e56141480d9e2004648cc67 using 
# display :0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-KuWC4nGpRX,guid=ca0b49693048782d03cd787e4aaac28d
DBUS_SESSION_BUS_PID=16790
DBUS_SESSION_BUS_WINDOWID=4194305
--More--(Next file: .dbus/session-bus/494e8e1e3e56141480d9e2004648cc67-0.before_restore_2009-03-21_03.25.08.015624)

```

```
usr1@comp1:~$ ubuntuzilla.py -a checkforupdategui -p firefox -d
Your commandline options:
{'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.3
Currently installed version of Firefox : 3.5.3
['494e8e1e3e56141480d9e2004648cc67-0.before_restore_2009-03-24_01.07.19.563863', '494e8e1e3e56141480d9e2004648cc67-1', '494e8e1e3e56141480d9e2004648cc67-0.before_restore_2009-03-21_03.25.08.015624', '494e8e1e3e56141480d9e2004648cc67-0']
# This file allows processes on the machine with id 494e8e1e3e56141480d9e2004648cc67 using 
# display :0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-QAHfPWZA0f,guid=b80da232724cbc41b56c9d6149c810cb
DBUS_SESSION_BUS_PID=11351
DBUS_SESSION_BUS_WINDOWID=6291457

unix:abstract=/tmp/dbus-QAHfPWZA0f,guid=b80da232724cbc41b56c9d6149c810cb
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 353, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 777, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 808, in updateActionsGui
    notifier = Notifier()
  File "/usr/local/bin/ubuntuzilla.py", line 182, in __init__
    bus      = dbus.SessionBus()
  File "/var/lib/python-support/python2.6/dbus/_dbus.py", line 219, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.6/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-QAHfPWZA0f: Connection refused
```

---

### Post by EnlistedSquire on 2009-10-28
+1 for this problem.

The fix from the Launchpad thread didn't work either.

---

### Post by nanotube on 2009-10-28
> **EnlistedSquire said:**
> +1 for this problem.

The fix from the Launchpad thread didn't work either.

hi
could you try the latest ubuntuzilla.py from project git repository? it includes some additional methods of notification for robustness purposes...

---

### Post by EnlistedSquire on 2009-10-28
Um, I know what Git is but that's as far as I can get with fulfilling your request. Sorry.

---

### Post by nanotube on 2009-10-28
> **EnlistedSquire said:**
> Um, I know what Git is but that's as far as I can get with fulfilling your request. Sorry.

no problem. in that case, try the .debs i have just created and attached to this thread:
[http://ubuntuforums.org/showthread.php?p=8183120#post8183120](http://ubuntuforums.org/showthread.php?p=8183120#post8183120)

---

### Post by EnlistedSquire on 2009-10-28
No joy:

```
darren@jaunty-desktop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : 3.5.3
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-pavnEpIjkd: Connection refused
notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.5.3</b>. The new release available is <b>3.5.4</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Process returned code 1
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-pavnEpIjkd: Connection refused
ERROR showing GUI update notification.
```

FYI, libnotify-bin is installed and up to date. All other applications that use notifications work fine.

---

### Post by nanotube on 2009-10-28
hmm, which version of ubuntu?

and does it work if you execute from a terminal:
```
notify-send 'test'
```

---

### Post by EnlistedSquire on 2009-10-28
I'm running Ubuntu 9.04, standard kernel with Gnome.

notify-send works fine as do other apps that use notifications.

I'm pretty sure Ubuntuzilla notifications used to work too but I can't say when they stopped working or why.

---

### Post by nanotube on 2009-10-28
hmm well i'm kind of at a loss here...
let me look around and i'll tell you if i find anything.

---

### Post by nanotube on 2009-10-28
maybe try this?:
[http://ubuntuforums.org/showpost.php?p=3918366&postcount=8](http://ubuntuforums.org/showpost.php?p=3918366&postcount=8)

---

### Post by EnlistedSquire on 2009-10-28
> **nanotube said:**
> maybe try this?:
[http://ubuntuforums.org/showpost.php?p=3918366&postcount=8](http://ubuntuforums.org/showpost.php?p=3918366&postcount=8)

Same error as before :(

Thanks for trying though.

---

### Post by shane2peru on 2009-10-29
Seems odd, I'm on Juanty and have this same problem.  Doesn't notify me of updates.  I didn't realize it, I didn't even know FF3.5.4 was out.  Ran the update thing and get this error:

```

ubuntuzilla.py -a checkforupdategui -p firefox -d
Your commandline options:
{'mirrors': ['mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/', 'www.gtlib.gatech.edu/pub/mozilla.org/', 'releases.mozilla.org/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'checkforupdategui', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : 3.5.3
['8c3f405fb51727b7c44d6fde49e4a871-0', '20f310683606ae568d78cc8c49e497d0-0', '25ec8ed1818a83e2a733793b49e0f036-0', '96bd3e481013d348084ff58b49f80d05-0', 'a3bb140275062724b0882dc349e9b20d-0']
# This file allows processes on the machine with id 8c3f405fb51727b7c44d6fde49e4a871 using 
# display :0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-OiFcCWkCtI,guid=7448cb936ba8bff6512e779449e9be6d
DBUS_SESSION_BUS_PID=5474
DBUS_SESSION_BUS_WINDOWID=4194305

unix:abstract=/tmp/dbus-OiFcCWkCtI,guid=7448cb936ba8bff6512e779449e9be6d
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 353, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 777, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 808, in updateActionsGui
    notifier = Notifier()
  File "/usr/local/bin/ubuntuzilla.py", line 182, in __init__
    bus      = dbus.SessionBus()
  File "/var/lib/python-support/python2.6/dbus/_dbus.py", line 219, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.6/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.6/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-OiFcCWkCtI: Connection refused

```

Not a big deal to me, since I know this is a problem, I will just update, and keep my eye out for new updates.  But did want to post here to let you know.

Shane

---

### Post by nanotube on 2009-10-29
hey thanks guys
i really don't know what's up with that at this point
i'll keep looking around
if anyone figures it out, please be sure to post your solution :)

---

### Post by 2LSS on 2009-10-31
Sorry if this doesn't relate. I'm not trying to hijack this thread, but I have a similar problem on hardy with ff version 3.5.3 

I run ubuntuzilla.py -a checkforupdategui -p firefox and get an error>
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : awk: warning: escape sequence `\.' treated as plain `.'
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1312, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 304, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 357, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 787, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 803, in updateActionsGui
    dbusfilelist = os.listdir(os.path.join(homedir, '.dbus/session-bus'))
OSError: [Errno 13] Permission denied: '/home/frank/.dbus/session-bus'

```
Do I need to run as root? Or is this part of the mystery?

---

### Post by shane2peru on 2009-10-31
> **2LSS said:**
> Sorry if this doesn't relate. I'm not trying to hijack this thread, but I have a similar problem on hardy with ff version 3.5.3 

I run ubuntuzilla.py -a checkforupdategui -p firefox and get an error>
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : awk: warning: escape sequence `\.' treated as plain `.'
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1312, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 304, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 357, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 787, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 803, in updateActionsGui
    dbusfilelist = os.listdir(os.path.join(homedir, '.dbus/session-bus'))
OSError: [Errno 13] Permission denied: '/home/frank/.dbus/session-bus'

```
Do I need to run as root? Or is this part of the mystery?

No, don't run ubuntuzilla as root, it will mess up some permission files see: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)  under installation the pink note on the right side. 

Shane

---

### Post by nanotube on 2009-10-31
> **2LSS said:**
> Sorry if this doesn't relate. I'm not trying to hijack this thread, but I have a similar problem on hardy with ff version 3.5.3 

I run ubuntuzilla.py -a checkforupdategui -p firefox and get an error>
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : awk: warning: escape sequence `\.' treated as plain `.'
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1312, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 304, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 357, in start
    self.checkforupdateGui()
  File "/usr/local/bin/ubuntuzilla.py", line 787, in checkforupdateGui
    self.updateActionsGui()
  File "/usr/local/bin/ubuntuzilla.py", line 803, in updateActionsGui
    dbusfilelist = os.listdir(os.path.join(homedir, '.dbus/session-bus'))
OSError: [Errno 13] Permission denied: '/home/frank/.dbus/session-bus'

```
Do I need to run as root? Or is this part of the mystery?

what are your permissions on ~/.dbus directory? your user needs to have rwx perms on it.

---

### Post by shane2peru on 2009-10-31
Here are mine:
```

drwx------   3 shane shane       4096 2009-04-11 14:32 .dbus

```
and inside:
```

drwx------ 2 shane shane 4096 2009-04-29 03:17 session-bus

```
and inside that:
```

ls -l
total 20
-rw-r--r-- 1 shane shane 466 2009-04-14 09:24 20f310683606ae568d78cc8c49e497d0-0
-rw-r--r-- 1 shane shane 466 2009-04-14 08:03 25ec8ed1818a83e2a733793b49e0f036-0
-rw-r--r-- 1 shane shane 463 2009-04-18 06:50 8c3f405fb51727b7c44d6fde49e4a871-0
-rw-r--r-- 1 shane shane 463 2009-10-31 18:26 96bd3e481013d348084ff58b49f80d05-0
-rw-r--r-- 1 shane shane 466 2009-04-29 07:12 a3bb140275062724b0882dc349e9b20d-0

```

Not sure if that will help. 

Shane

---

### Post by nanotube on 2009-11-01
> **shane2peru said:**
> 

Not sure if that will help. 

Shane

Hey Shane,

That question was to 2lss, who had the permission denied error. if you are not getting that error (which you shouldn't, looking at your permissions), then don't worry about it. But it'll serve as an example for 2lss of what the permissions should be :).

---

### Post by shane2peru on 2009-11-01
> **nanotube said:**
> Hey Shane,

That question was to 2lss, who had the permission denied error. if you are not getting that error (which you shouldn't, looking at your permissions), then don't worry about it. But it'll serve as an example for 2lss of what the permissions should be :).

Ohh, I see, the errors are different. :o oops   I guess I didn't read it close enough. :D

Shane

---

### Post by 2LSS on 2009-11-01
Here is mine:
```
cd ~
ls -a -l
drwx------   3 root  root       4096 2009-04-02 19:44 .dbus
```

```
sudo -i
cd .dbus
ls -l
drwx------ 2 root root 4096 2008-04-28 17:36 session-bus

```

```
cd session-bus
ls -l
-rw-r--r-- 1 root root 467 2009-10-27 00:19 025711e9d1dc2f87e2620d0047d5ae98-0

```

It looks like my permissions are the same. Am I missing files in /.dbus/session-bus?

---

### Post by nanotube on 2009-11-01
> **2LSS said:**
> Here is mine:
```
cd ~
ls -a -l
drwx------   3 root  root       4096 2009-04-02 19:44 .dbus
```

```
sudo -i
cd .dbus
ls -l
drwx------ 2 root root 4096 2008-04-28 17:36 session-bus

```

```
cd session-bus
ls -l
-rw-r--r-- 1 root root 467 2009-10-27 00:19 025711e9d1dc2f87e2620d0047d5ae98-0

```

It looks like my permissions are the same. Am I missing files in /.dbus/session-bus?

no, yours aren't the same - they are owned by root, but should be owned by your user. to fix this, run the following command:
```
sudo chown -R frank:frank ~/.dbus
```
that ought to fix you up. :)

---

### Post by shane2peru on 2009-11-01
> **2LSS said:**
> Here is mine:
```
cd ~
ls -a -l
drwx------   3 [COLOR="Blue"]root  root[/COLOR]       4096 2009-04-02 19:44 .dbus
```

```
sudo -i
cd .dbus
ls -l
drwx------ 2 [COLOR="Blue"]root root[/COLOR] 4096 2008-04-28 17:36 session-bus

```

```
cd session-bus
ls -l
-rw-r--r-- 1 [COLOR="Blue"]root root[/COLOR] 467 2009-10-27 00:19 025711e9d1dc2f87e2620d0047d5ae98-0

```

It looks like my permissions are the same. Am I missing files in /.dbus/session-bus?
Well, the permissions are the same, however the owner is different.  See how it says root, after the permissions (marked in blue).  You need to run:
```

sudo chown [COLOR="Red"]username[/COLOR]:[COLOR="Red"]username[/COLOR] -Rv .dbus

```

You need to run that in your user's home folder, and change the username to your username.  Then you should be all fixed up.

Shane

---

### Post by nanotube on 2009-11-01
> **shane2peru said:**
> 
```

ls -l
total 20
-rw-r--r-- 1 shane shane 466 2009-04-14 09:24 20f310683606ae568d78cc8c49e497d0-0
-rw-r--r-- 1 shane shane 466 2009-04-14 08:03 25ec8ed1818a83e2a733793b49e0f036-0
-rw-r--r-- 1 shane shane 463 2009-04-18 06:50 8c3f405fb51727b7c44d6fde49e4a871-0
-rw-r--r-- 1 shane shane 463 2009-10-31 18:26 96bd3e481013d348084ff58b49f80d05-0
-rw-r--r-- 1 shane shane 466 2009-04-29 07:12 a3bb140275062724b0882dc349e9b20d-0

```

Shane

hey shane
actually... one reason your notification's don't work could be the multiple files in the session-bus directory. 

right now the code just takes the first file - i'll try to grab the latest-created one, and post a test .deb here for you to try. hope this will solve your notification problems...

---

### Post by nanotube on 2009-11-01
hey shane

attaching some .debs for you to test.

first, run your current ubuntuzilla.py as
```
ubuntuzilla.py -a checkforupdategui -p firefox -d
```
and confirm that you get your error and no notification shows up.

then, install a .deb attached to this post, and run that again.

che code is now grabbing the most recent file in .dbus/session-bus dir. maybe that'll help. :)

---

### Post by 2LSS on 2009-11-01
> Well, the permissions are the same, however the owner is different. See how it says root, after the permissions (marked in blue). You need to run:
Code:

sudo chown username:username -Rv .dbus

You need to run that in your user's home folder, and change the username to your username. Then you should be all fixed up.

Shane 

Thanks, that got me past that problem but unfortunately it now looks like I'm running into the same problem as everyone else.
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : awk: warning: escape sequence `\.' treated as plain `.'
/bin/sh: Syntax error: EOF in backquote substitution
notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>awk: warning: escape sequence `\.' treated as plain `.'</b>. The new release available is <b>3.5.4</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Process returned code 2
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-JG4bAYzFIP: Connection refused
ERROR showing GUI update notification.
```

libnotify-bin is installed and notify-send 'test' works

---

### Post by nanotube on 2009-11-01
> **2LSS said:**
> Thanks, that got me past that problem but unfortunately it now looks like I'm running into the same problem as everyone else.
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : awk: warning: escape sequence `\.' treated as plain `.'
/bin/sh: Syntax error: EOF in backquote substitution
notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>awk: warning: escape sequence `\.' treated as plain `.'</b>. The new release available is <b>3.5.4</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Process returned code 2
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-JG4bAYzFIP: Connection refused
ERROR showing GUI update notification.
```

libnotify-bin is installed and notify-send 'test' works

could you try the 4.7.8 .debs that i attached to the post just above?

---

### Post by shane2peru on 2009-11-01
> **nanotube said:**
> hey shane

attaching some .debs for you to test.

first, run your current ubuntuzilla.py as
```
ubuntuzilla.py -a checkforupdategui -p firefox -d
```
and confirm that you get your error and no notification shows up.

then, install a .deb attached to this post, and run that again.

che code is now grabbing the most recent file in .dbus/session-bus dir. maybe that'll help. :)

That works!!!  Nice job, you hid the nail on the head.  I won't pretend I understand that .dbus stuff, cause I really don't, but apparently you have it figured out.

Shane

---

### Post by nanotube on 2009-11-01
> **shane2peru said:**
> That works!!!  Nice job, you hid the nail on the head.  I won't pretend I understand that .dbus stuff, cause I really don't, but apparently you have it figured out.

Shane

excellent! :) i'll push out the release then. :)

and, to be honest, i don't understand the dbus stuff either. :D :)

---

### Post by 2LSS on 2009-11-01
> could you try the 4.7.8 .debs that i attached to the post just above? 

I installed the .deb and tried again
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : 3.5.4
```

No more errors!

Unfortunately I already manually updated to 3.5.4 but I will report back when 3.5.5 comes out ;)
Thanks for all the help!

---

### Post by nanotube on 2009-11-02
> **2LSS said:**
> I installed the .deb and tried again
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.4
Currently installed version of Firefox : 3.5.4
```

No more errors!

Unfortunately I already manually updated to 3.5.4 but I will report back when 3.5.5 comes out ;)
Thanks for all the help!

good news :)

---

### Post by EnlistedSquire on 2009-11-02
All working here too. I didn't update from the posted debs though so my Ubuntuzilla.py must have auto-updated.

Nice work Nanotube - thanks!

Although you've solved the problem already, FYI I have three session files in my ~/.dbus/session-bus folder. What causes that to happen?

(@anyone who already has FF 3.5.4 installed, you can test this by looking for an update for either Seamonkey or Thunderbird, you don't even need to have them installed).

Cheers.

---

### Post by nanotube on 2009-11-02
> **EnlistedSquire said:**
> All working here too. I didn't update from the posted debs though so my Ubuntuzilla.py must have auto-updated.


indeed, i pushed out the release, and ubuntuzilla automatically checks for updates to itself.

> 
Nice work Nanotube - thanks!


you're welcome - and thanks for your feedback :)

> 
Although you've solved the problem already, FYI I have three session files in my ~/.dbus/session-bus folder. What causes that to happen?

I really have no clue... I'm kind of just poking in the dark at this dbus stuff. :)

> 
(@anyone who already has FF 3.5.4 installed, you can test this by looking for an update for either Seamonkey or Thunderbird, you don't even need to have them installed).

good point. :)

---

### Post by 2LSS on 2009-11-11
I'm sorry I have to bring this back up but....my dilemma has returned. Here's the story.
After I installed your new deb everything was working fine so I was just waiting for the new ff release to test it.
Then, because of a completely unrelated problem I ended up removing ubuntuzilla.
Today I reinstalled your deb (ubuntuzilla-4.7.8-0ubuntu1-i386.deb) and ran ```
ubuntuzilla.py -a removeupdater -p thunderbird
```
then 
```
ubuntuzilla.py -a checkforupdategui -p firefox
```
but the dreaded error has returned:
```
frank@frank-laptop:~$ ubuntuzilla.py -a checkforupdategui -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Latest release version of Firefox : 3.5.5
Currently installed version of Firefox : 3.5.4
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-JG4bAYzFIP: Connection refused
notify-send -i '/opt/firefox/icons/mozicon50.xpm' -t 14400000 'Ubuntuzilla: Firefox Update Available.' 'A Firefox Update is Available. The version you are running is <b>3.5.4</b>. The new release available is <b>3.5.5</b>. Please refer to the <a href="http://ubuntuzilla.sourceforge.net/#Update_Official_Mozilla_Build_of_Firefox">detailed update instructions</a> on the Ubuntuzilla website.'
Failed to execute 'notify-send'. Please make sure that package 'libnotify-bin' is installed.
Process returned code 1
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-JG4bAYzFIP: Connection refused
ERROR showing GUI update notification.
```

I didn't change anything related to dbus so I'm confused as to why I'm getting the error. I have libnotify-bin installed and notify-send 'test' still works.
```
frank@frank-laptop:~$ env |grep DBUS
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-dIvffPpE3z,guid=06c7323501e2d8c31008b7094afb7509
```
```
frank@frank-laptop:~$ more .dbus/session-bus/*
# This file allows processes on the machine with id 025711e9d1dc2f87e2620d0047d5ae98 using 
# display :0.0 to find the D-Bus session bus with the below address.
# If the DBUS_SESSION_BUS_ADDRESS environment variable is set, it will
# be used rather than this file.
# See "man dbus-launch" for more details.
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-JG4bAYzFIP,guid=cfa1312dc0664d1e4c5e54ce4ace3926
DBUS_SESSION_BUS_PID=32752
DBUS_SESSION_BUS_WINDOWID=46137345
```
```
frank@frank-laptop:~$ ls -al .dbus/session-bus/
total 12
drwx------ 2 frank frank 4096 2009-04-02 19:44 .
drwx------ 3 frank frank 4096 2009-04-02 19:44 ..
-rw-r--r-- 1 frank frank  467 2009-10-08 15:10 025711e9d1dc2f87e2620d0047d5ae98-0
```
Does anything look out of the ordinary? I find this dbus stuff to be very confusing!

---

### Post by nanotube on 2009-11-11
> **2LSS said:**
> 
Does anything look out of the ordinary? I find this dbus stuff to be very confusing!

you are not alone! :) 

no, everything looks ok.... but since you say  you are on hardy, maybe try the following fix for a hardy dbus bug:

[http://ubuntuforums.org/showpost.php?p=7805847&postcount=18](http://ubuntuforums.org/showpost.php?p=7805847&postcount=18)

(taken from this launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/207157](https://bugs.launchpad.net/ubuntu/+source/beagle/+bug/207157) )

---

### Post by 2LSS on 2009-11-11
I must say thank you good sir, that worked like a charm.

Will that update message display automatically every time there is an update? At boot up? 

Do I still need to update my ff 3.0 from the ubuntu repos?

And just out of curiosity do you guys plan on adding flock compatibility to ubuntuzilla?

thanks again

---

### Post by nanotube on 2009-11-11
> **2LSS said:**
> I must say thank you good sir, that worked like a charm.

excellent news! :)

> 
Will that update message display automatically every time there is an update? At boot up? 

the update checker is set to run every 4 hours. so as soon as a new release is made, you'll know no later than 4 hours afterwards.

> 
Do I still need to update my ff 3.0 from the ubuntu repos?

if the updates from the repos are offered, there's no harm in installing them. if only to make them go away :)

> 
And just out of curiosity do you guys plan on adding flock compatibility to ubuntuzilla?

no, ubuntuzilla's stated goal is just mozilla official builds, to which set flock does not belong...

> 
thanks again
you're quite welcome! :)

while i have you here, i'll also point you toward the new apt repository for the ubuntuzilla project. here's the thread about it:
[http://ubuntuforums.org/showthread.php?t=1323239](http://ubuntuforums.org/showthread.php?t=1323239)

---

