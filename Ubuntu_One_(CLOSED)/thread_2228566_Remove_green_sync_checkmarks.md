---
title: "Remove green sync checkmarks"
date: 2014-06-08
forum: Ubuntu One (CLOSED)
---

### Post by Sleepy-zz-John on 2014-06-08
Hi,   Having uninstalled Ubuntu One following the closure of their service,  I'm still seeing green checkmarks on my folders indicating they are still sync'd.  

Right click -> Ubuntu One -> Stop Synchrorising This Folder  doesn't have any effect.    

How can I remove these green checkmarks?

---

### Post by TheFu on 2014-06-08
What about purging UbuntuOne packages from the system? Seems that would solve this.

---

### Post by Sleepy-zz-John on 2014-06-08
Thanks TheFu,    I did my uninstallation through Ubuntu Software Center and that told me it was also removing some associated files,  but evidently not the ones responsible for these green checkmarks.  

So now,   with UbuntuOne and some associated files already removed,  how would I identify what UbuntuOne packages are still remaining and purge them?  Seems like Software Center only did half the job it ought to have done?

---

### Post by TheFu on 2014-06-08
Open a terminal.[B]
dpkg -l | grep {something}[/B]  Sorry, I don't know the package names - don't run stock Ubuntu desktop here.

Or install **synaptic** and search inside there for "ubuntu one"?

---

### Post by Sleepy-zz-John on 2014-06-08
> **TheFu said:**
> Open a terminal.[B]
dpkg -l | grep {something}[/B]  Sorry, I don't know the package names - don't run stock Ubuntu desktop here.  OK thanks,  but since I didn't know what to enter in place of that **"something"**,  I couldn't try that.  :icon_frown:  >  Or install **synaptic** and search inside there for "ubuntu one"? Ah yes!   Good  :D    Done that, found 10 packages,   and it's worked  :biggrin:   Synaptic looks like a useful tool for the future,  tool.

But I'm a little puzzled as to why uninstalling Ubuntu One in Ubuntu Software Center didn't find those extra 10 associated packages and uninstall them in the first place.  :?:  I'd have expected everything that was associated with Ubuntu One when I originally installed it,  to be uninstalled when I removed it,  but that clearly didn't happen.   If every programme I installed and then subsequently uninstalled left clutter around on my system like this, surely everything would slowly get clogged up,  wouldn't it?  

Or could it be something to do with my 12.04.3 coming with Ubuntu One partly pre-installed ?  

Anyway,  many thanks.   It's worked  :-)

---

### Post by bapoumba on 2014-06-09
As others also have experienced this issue, would you by any chance have kept the list of packages you uninstalled Sleepy-zz-John ?

If not, you may find them in /var/log/apt/history.log, not sure about term.log, as synaptic may not be logging there.

---

### Post by Sleepy-zz-John on 2014-06-09
> **bapoumba said:**
> As others also have experienced this issue, would you by any chance have kept the list of packages you uninstalled Sleepy-zz-John ?

If not, you may find them in /var/log/apt/history.log, not sure about term.log, as synaptic may not be logging there.I didn't keep a list at the time,  but found these in my today's  /var/log/apt/history.log:  

Remove: gir1.2-ubuntuoneui-3.0:amd64 (3.0.1-0ubuntu1), 
python-ubuntuone-client:amd64 (3.0.2-0ubuntu2.2), 
ubuntuone-client:amd64 (3.0.2-0ubuntu2.2), 
ubuntuone-couch:amd64 (0.3.0-0ubuntu4), 
python-ubuntuone-storageprotocol:amd64 (3.0.2-0ubuntu1), 
ubuntuone-control-panel:amd64 (3.0.1-0ubuntu1), 
libsyncdaemon-1.0-1:amd64 (3.0.2-0ubuntu2.2), 
libubuntuoneui-3.0-1:amd64 (3.0.1-0ubuntu1), 
python-ubuntuone-control-panel:amd64 (3.0.1-0ubuntu1), 
ubuntuone-client-gnome:amd64 (3.0.1-0ubuntu1) 

A possible word of caution though:   Although deleting these has eliminated the green sync checkmarks and the repetitive U1 closure reminder at log-in, not sure but it could be that synaptic knew what it was doing better than I did when it didn't remove them itself.   See my concern at [http://ubuntuforums.org/showthread.php?t=2215788&page=4](http://ubuntuforums.org/showthread.php?t=2215788&page=4) post #40

---

### Post by TheFu on 2014-06-09
So - it appears that 
**sudo aptitude purge gir1.2-ubuntuoneui* ubuntuone*** should do it.  The smarter dependency resolution of aptitude should clean up those extra dependencies.  In theory. ;)

Synaptic is closer to the old-school package manager which can be confusing for people new-to-Ubuntu, hence why software-center is the default.  They all read/write to the APT DB (probably using the APT library), so switching package manager isn't really an issue.  Use each when they are best used and be happy with APT (which rocks!).

---

### Post by bapoumba on 2014-06-09
Thanks Sleepy-zz-John & TheFu :)
As I fresh installed, going through the package list website was a little tedious.. If others come around with the same issue, we know which package they should remove.

---

