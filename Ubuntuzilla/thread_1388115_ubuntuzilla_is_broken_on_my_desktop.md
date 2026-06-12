---
title: "ubuntuzilla is broken on my desktop"
date: 2010-01-22
forum: Ubuntuzilla
---

### Post by jlh68 on 2010-01-22
This is the output from an attempted running of the script to update.  I have not been able to update on this computer.  What is wrong with the script?

> When adding, default is --local and --divert <original>.distrib.
When removing, --package or --local and --divert must match if specified.
Package preinst/postrm scripts should always specify --package and --divert.
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Previous command has failed to complete successfully. Exiting.
Process returned code 2
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1331, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 311, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 354, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 781, in install
    self.linkLauncher()
  File "/usr/local/bin/ubuntuzilla.py", line 984, in linkLauncher
    self.util.execSystemCommand(executionstring="sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox")
  File "/usr/local/bin/ubuntuzilla.py", line 154, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)


---

### Post by kansasnoob on 2010-01-23
Are you using 64 bit Ubuntu?

If unsure run:

```
uname -m
```

64 bit users would see x86_64, 32 bit users would see i686. 

I'm asking because there is now an Ubuntuzilla PPA for 32 bit users:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

If you are using 32 bit Ubuntu and you want to change from the old Ubuntuzilla script to the new PPA be sure to run the appropriate commands to remove the old "script versions":

```
ubuntuzilla.py -a remove -p firefox

ubuntuzilla.py -a remove -p thunderbird

ubuntuzilla.py -a remove -p seamonkey

```

Before installing the PPA and the new packages.

If it's 64 bit I'm clueless because I've never used it.

---

### Post by nanotube on 2010-01-23
to the original poster:

it looks like you're trying to use the script, even though you already have the ppa installed. that's why your dpkg-divert is failing from the script, because a diversion is already present due to the ppa.

choose one or the other (if you're on 32bit, use the ppa).

---

