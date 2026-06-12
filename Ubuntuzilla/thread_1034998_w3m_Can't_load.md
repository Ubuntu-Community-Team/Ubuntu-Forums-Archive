---
title: "w3m: Can't load"
date: 2009-01-09
forum: Ubuntuzilla
---

### Post by vitality1987 on 2009-01-09
Hello, 

I got this message when traing to install Firefox with Ubuntuzilla. What I can do?


```
Welcome to the Ubuntuzilla Firefox script version 4.6.0

Ubuntuzilla is built only for Ubuntu Linux and other distributions derived from Ubuntu (such as Linux Mint, e.g.)

This script will now install the latest release of the official Mozilla build of Firefox on your Linux system. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at http://ubuntuzilla.sourceforge.net/

Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0.5. Please make sure this is correct before proceeding. (You can confirm by going to http://www.mozilla.org/)
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]?
Please enter 'y' or 'n': y
Retrieving list of available localizations for Firefox ...
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1146, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 597, in install
    self.getLocalizationList()
  File "/usr/local/bin/ubuntuzilla.py", line 309, in getLocalizationList
    self.locList = self.util.getSystemOutput(executionstring="w3m -dump ftp://" + mirror + self.options.package + "/releases/" + self.releaseVersion + "/linux-i686/ |grep '\. \. \.' |grep -v 'xpi'", numlines=0)
  File "/usr/local/bin/ubuntuzilla.py", line 110, in getSystemOutput
    if re.match("w3m: Can't load", result[0]):
IndexError: list index out of range
```

thx
vitality1987

---

### Post by nanotube on 2009-01-09
hi
hmm... could you try again? could have been a transient network error...

---

### Post by nanotube on 2009-01-09
regardless of whether it was a transient network error or not, i realized that the script should handle the possibility of empty w3m output, so i released an update that properly takes that possibility into account. so, go to the project homepage and download the latest release, v 4.6.1, and give it a shot. 

thanks for your feedback :)

---

