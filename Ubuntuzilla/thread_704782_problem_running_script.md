---
title: "problem running script"
date: 2008-02-22
forum: Ubuntuzilla
---

### Post by Maggie1 on 2008-02-22
I am trying to install Thunderbird with the Ubuntuzilla script. Placed the tar.gz in /tmp. I get the following error message when running the script:
maggie@maggie-desktop:~$ ubuntuzilla.py -a install -p thunderbird

Welcome to the Ubuntuzilla Thunderbird script version 4.4.5

This script installs the latest release of the official Mozilla build of Thunderbird on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Retrieving the version of the latest release of Thunderbird from the Mozilla website...
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1051, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 212, in start
    ti.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 509, in install
    self.getLatestVersion()
  File "/usr/local/bin/ubuntuzilla.py", line 724, in getLatestVersion
    self.releaseVersion = self.util.getSystemOutput(executionstring="wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - [http://www.mozilla.com/thunderbird/](http://www.mozilla.com/thunderbird/) |grep 'product=' -m 1 |sed -e 's/.*<li>.*thunderbird-//' -e 's/&amp.*//'", errormessage="Problem retrieving the latest release version. Exiting.")
  File "/usr/local/bin/ubuntuzilla.py", line 124, in getSystemOutput
    return result[0]
IndexError: list index out of range

Can someone help please?
Thanks in advance
M.

---

### Post by nanotube on 2008-02-23
seems to work just fine for me... try it again, and if it still throws the same error, please run this command in a terminal, and post the output:

```
wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - http://www.mozilla.com/thunderbird/ |grep 'product=' -m 1 |sed -e 's/.*<li>.*thunderbird-//' -e 's/&amp.*//'
```

(should produce the latest thunderbird version number...)

---

