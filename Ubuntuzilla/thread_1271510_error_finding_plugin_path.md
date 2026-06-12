---
title: "error finding plugin path"
date: 2009-09-20
forum: Ubuntuzilla
---

### Post by TimeGoneBomb on 2009-09-20
I'm running jaunty. Thought I would give ubuntuzilla a try. However, it doesn't work for me. Here is what I get:

> Extracting archive

Trying to determine firefox plugin path...
find /usr/lib -name 'libunixprintplugin.so'
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["find: `/usr/lib/oss/modules.noregparm': Permission denied\n", "find: `/usr/lib/oss/modules.regparm': Permission denied\n", "find: `/usr/lib/oss/save': Permission denied\n", "find: `/usr/lib/oss/objects.noregparm': Permission denied\n", "find: `/usr/lib/oss/objects.regparm': Permission denied\n", '/usr/lib/xulrunner-addons/plugins/libunixprintplugin.so\n']
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 343, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 753, in install
    self.linkPlugins()
  File "/usr/local/bin/ubuntuzilla.py", line 648, in linkPlugins
    result = self.util.getSystemOutput(executionstring="find /usr/lib -name 'libunixprintplugin.so'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 121, in getSystemOutput
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

Anyone ever see this? Or anyone know how to fix it?

---

### Post by nanotube on 2009-09-21
Hi
what is this /usr/lib/oss thing?

as to how to fix it - change in line 648 to use 'sudo' for the find command.

---

### Post by TimeGoneBomb on 2009-09-21
That fixed it. Thank you very much.

The oss in there is probably open sound system; the only major change I have made to jaunty is to remove alsa and pulseaudio, and install oss 4.2 in their place. I had a sound issue because of my hardware, and it is resolved by using oss instead of alsa.

---

