---
title: "also stuck when &quot;Retreiving list of available . . .&quot;"
date: 2009-09-20
forum: Ubuntuzilla
---

### Post by jimwhitend on 2009-09-20
My problem seems different that the other thread with a similar name, but I am a newbie, so who knows?
The latest version of the script keeps trying different mirrors, so I interrupted it with ^C and get this the information below. I don't use a proxy server but it does go through a router, which shouldn't be blocking anything. What to do? Thanks.
-JimW

Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
^CTraceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1294, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 300, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 343, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 739, in install
    self.getLocalizationList()
  File "/usr/local/bin/ubuntuzilla.py", line 416, in getLocalizationList
    self.locList = self.util.getSystemOutput(executionstring="w3m -dump ftp://" + mirror + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 107, in getSystemOutput
    returncode = p.wait()
  File "/usr/lib/python2.6/subprocess.py", line 1123, in wait
    pid, sts = os.waitpid(self.pid, 0)
KeyboardInterrupt

---

### Post by nanotube on 2009-09-20
Hi,

first: just let it keep trying, and see if it finds one that works. I just tried it myself for test, and the mozilla.isc.org mirror was down, but it succeeded on the subsequent mirror.

second: if it still fails, post the complete session without canceling it, so that i know the version of ubuntuzilla you're using, and so that i can see which mirrors have been tried.

---

### Post by jimwhitend on 2009-09-21
Here is what happens. Thanks!


[INDENT]Welcome to the Ubuntuzilla Firefox script version 4.7.4

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.5.3. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
w3m -dump [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.ussg.indiana.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://ftp.osuosl.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.cs.utah.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://mozubuntuzilla.py](ftp://mozubuntuzilla.py) -a install -p firefoxilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://mozilla.mirrors.tds.net/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://ftp.scarlet.be/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://ftp.uni-erlangen.de/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://sunsite.rediris.es/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://www.gtlib.gatech.edu/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
w3m -dump [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/) |grep '\. \. \.' |grep -v 'xpi'
w3m: Can't load [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).
Previous command has failed to complete successfully. Exiting.
Process returned code 1
["w3m: Can't load ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/.\n"]
Download error. Trying again, hoping for a different mirror.
Failed to retrieve list of localizations. This may be due to transient network problems, so try again later. If the problem persists, please seek help on our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
jim@jim-ubuntu:~$ [/INDENT]

---

### Post by nanotube on 2009-09-21
Hi
well, that is rather strange - i suspect something weird in your network config as far as w3m can see...

can you go to [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/)  with your regular browser?

how about running the following from the terminal:
```

w3m -dump ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/

```

---

### Post by jimwhitend on 2009-09-22
Just so--a network configuration problem. I can't browse to the ftp site with either firefox or opera. Here is what the other command yielded:

~$ w3m -dump [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/)
w3m: Can't load [ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/](ftp://mozilla.isc.org/pub/mozilla.org/firefox/releases/3.5.3/linux-i686/).

Thanks for helping!
-JimW

---

### Post by nanotube on 2009-09-22
So look through the various firewall rules you may have to check that you are allowing outdoing connections to port21 (default ftp port), both on your local comp, and on your router. 

i don't know what your setup is, and what exactly you did as far as fiddling with your firewall rules... the default on routers, and on ubuntu, is to allow anything out, so clearly you (or someone else) changed these defaults to be more restrictive... 

so just poke around and see what's going on. :)

---

