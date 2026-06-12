---
title: "Is clam in repositry broken?"
date: 2010-04-10
forum: Security
---

### Post by TheropodWatcher on 2010-04-10
I've installed "Virus Scanner" (clam) from the repository using Applications>Add/Remove. That should be the best way to install something in Ubuntu, or at least one would think so. However when I run it from the menu tree, it always says "Virus definitions - None found". So, it can't really be doing anything, can it?

Anyone know whats's going on here, and what the real answer is for getting clamav installed and actually doing something - or is it and it just pretends not to know anything?

Very strange ...

Running Ubuntu 8.10  - the Intrepid Ibex.

Thanks in advance!
 Brad

---

### Post by cor2y on 2010-04-10
its been a while since i used it but the first thing to understand about clam, whether from the terminal or the gui frontend is that for updates and file repairs/viri deletion and during the first time its run , it must be run as super user to get updates and check its at the most recent version.
so via the terminal
```

sudo freshclam.
```
It will then check for updates etc.

---

### Post by nitstorm on 2010-04-10
the version in the repos is 0.95 last time i checked( i might be wrong) and the current version in 0.96 
  
for updating the virus definitions and all that```
sudo freshclam
```

for running the scan ```
 sudo clamscan 
```

you can also see man clamscan or man freshclam for more options and all that..

---

### Post by cariboo on 2010-04-10
You may want to edit the cron job that freshclam creates, as it checks for updates hourly. For more info have a look [here]("http://www.gossamer-threads.com/lists/clamav/users/30708").

Unless you are running a mail/ftp server, there really isn't a need for a virus scanner on Ubuntu, as there are no Linux viruses in the wild.

---

