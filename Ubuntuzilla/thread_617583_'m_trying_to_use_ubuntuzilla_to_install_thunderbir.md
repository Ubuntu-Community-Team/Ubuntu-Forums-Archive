---
title: "'m trying to use ubuntuzilla to install thunderbird"
date: 2007-11-19
forum: Ubuntuzilla
---

### Post by watkinsted on 2007-11-19
I used ubuntuzilla to install firefox, and can't get firefox to recognize the plugins for java and flash.  Not only that, but it's giving me errors trying to install thunderbird.  Here's what i get


Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1045, in ?
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 207, in start
    ti.start()
  File "/usr/local/bin/ubuntuzilla.py", line 231, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 508, in install
    self.aptgetMeasures()
  File "/usr/local/bin/ubuntuzilla.py", line 356, in aptgetMeasures
    self.util.execSystemCommand(executionstring="sudo apt-get install " + self.aptPackage, errormessage="Package installation failed. Cannot proceed.")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
admin@admin-desktop:/opt/firefox/plugins/plugins$

---

### Post by nanotube on 2007-11-20
about plugins... are you by any chance running 64bit?

about tbird install... could you please post the complete output (not just the traceback), i want to see what the apt-get output said before this.

---

