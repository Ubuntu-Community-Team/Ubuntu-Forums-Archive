---
title: "Gran Paradiso updating?"
date: 2007-12-27
forum: Ubuntuzilla
---

### Post by xeocub on 2007-12-27
Hello. Trying to update FF3 from the a08 I have now to the new beta. Doesn't seem to be working well with uzilla, Here's what happens:

> ubuntuzilla.py -a checkforupdatetext -p firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1051, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 244, in start
    self.checkforupdateText()
  File "/usr/local/bin/ubuntuzilla.py", line 539, in checkforupdateText
    self.getLatestVersion()
  File "/usr/local/bin/ubuntuzilla.py", line 652, in getLatestVersion
    self.releaseVersion = self.util.getSystemOutput(executionstring="wget -c --tries=20 --read-timeout=60 --waitretry=10 -q -O - [http://www.mozilla.com](http://www.mozilla.com) |grep 'product=' -m 1 |sed -e 's/.*<li>.*firefox-//' -e 's/&amp.*//'", numlines=1, errormessage="Failed to retrieve the latest version of "+ self.options.package.capitalize())
  File "/usr/local/bin/ubuntuzilla.py", line 124, in getSystemOutput
    return result[0]
IndexError: list index out of range


This happens no matter which of the commands I run... Any help?

---

### Post by nanotube on 2008-01-08
> **xeocub said:**
> Hello. Trying to update FF3 from the a08 I have now to the new beta. Doesn't seem to be working well with uzilla, Here's what happens:

This happens no matter which of the commands I run... Any help?

hm, that shouldn't really have anything to do with what firefox you have installed... it just fetches the version from the mozilla website.
i just tried and it works... maybe there were some access problems with mozilla.com site at the time you were trying it? try again now and see what happens...

---

