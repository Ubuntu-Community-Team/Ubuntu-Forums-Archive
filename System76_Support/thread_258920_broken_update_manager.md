---
title: "broken update manager"
date: 2006-09-16
forum: System76 Support
---

### Post by ubarry on 2006-09-16
Update manager stopped working, just dying in the gui. It could have something to do with the my effort to obtain a printer description file for my Brother hln1270n. I got a debian package from brother, but it failed, trying to setup its files for lpd printing. 

After dpkg failed to install, update-manager kept reporting one broken package, so eventually I used dpkg to try to remove, but I got an error from the post remove script -- it cannot find lpd to restart.

At least that's my theory after reading the message below from running update-manager on the cmd line. Am I right? If so, how can I clean this up? If not, what do I do?

I have a nvidia serval; /proc/version says it's got Ubuntu 4.0.3-1ubuntu5. 

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 71, in ?
    app.main(options)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 749, in main
    self.fillstore()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 603, in fillstore
    self.list.update(self.cache)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 199, in update
    cache.saveDistUpgrade()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 93, in saveDistUpgrade
    assert self._depcache.BrokenCount == 0 and self._depcache.DelCount == 0
AssertionError

Also, the gui's package manager lists the packages in the marked for change list, but trying to remove it only runs dpkg (I think) and it fails.

update-notifier seems to be working -- it said 1 update the other day, and now 7. 

(of course, this failure kept me from putting in that problem kernel update!)

Tia, 

Barry

---

### Post by crichell on 2006-09-16
Synaptic usually does a good job with broken packages.

System > Administration > Synaptic
Edit > Fix Broken Packages

You can also attempt to run if Synaptic doesn't fix it:
```
sudo apt-get -f install
```

Also - it's safe to run the kernel update on the Serval.  The nvidia problem from fixed soon after it was found.

---

### Post by ubarry on 2006-09-16
Nope. 

'Fix broken packages' doesn't work. Attempting to remove or install **anything**  now only gets me a message that the broken package needs to be reinstalled, but it cannot be installed or removed because the postinstall(or rm) fails. The package apparently assumes you have lpd set up and running. (btw, apt-get tells me the archive cannot be found.)

I found a reference on the web that trying to install the Brother deb package may have corrupted my package db. This quote is from a 2004 freestandards list:

"Brother _does_ supply LPD drivers at [http://solutions.brother.com/linux/](http://solutions.brother.com/linux/) but they don't list the MFC-6800 under the CUPS section.  Be carefull installing the .deb package if you aren't running lpd or if you are running CUPS; you can corrupt your package database!"

I have a different printer, and got a different package, but the result was the same. I'm stuck. 
 
I tried to use Synaptic to install the lp daemon, thinking I could remove it later, but I cannot get past the fact that I must fix the Brother package first.

Barry

---

### Post by ubarry on 2006-09-16
The package db was apparently OK.

I had to fake out dpkg. To reinstall and then uninstall, I created a dummy script for postinstall to run: /etc/init.d/lpd

It gave me a message and exited. That was good enough for dpkg.

---

### Post by DFKQ on 2006-09-17
Hi, I'm having the exact same trouble you had.  I'm pretty much a complete Linux newbie so could you (or any other nice person out there) elaborate on how you created that dummy script and fixed this problem?

Thanks in advance

---

### Post by dishbert on 2006-09-18
I'm having similar problems:  Synaptic gives me a "You have 6 broken packages" when I flash it up, but "edit - fix broken packages" tells me that 1256 packages including "24 essensial packages" will be removed if I proceed.

How is this possible?  I may have tried to install 6 non-Ubuntu Debian packages, but not 1256.

How should I proceed?  I have yet to upgrade to Dapper, would that help?

---

### Post by ubarry on 2006-09-21
The script that I wrote just three lines was something like this:

#!/bin/bash
echo "fixing..."
exit 0

and named how dpkg was looking for it, in this /etc/init.d/lpd

The line in postinstall was trying to restart lpd, as it should; it's a sloppy script from Brother that causes the problem.

This is likely to be a rare case. The dpkg error messages spelled out what went wrong. Since we have, by default, cups printing, there were plenty of other warnings in trying find other lp set up stuff.

---

