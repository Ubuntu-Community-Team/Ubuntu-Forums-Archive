---
title: "Could not install the upgrades"
date: 2012-09-06
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by theanswriz42 on 2012-09-06
I'm trying do-release-upgrade -d and am getting the following error:

```


Could not install the upgrades 

The upgrade has aborted. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

dpkg: error: parsing file '/var/lib/dpkg/status' near line 54770 package 'libqt4-scripttools:i386':
 mixed non-coinstallable and coinstallable package instances present
dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 54770 package 'libqt4-scripttools:i386':
 mixed non-coinstallable and coinstallable package instances present

Upgrade complete 

The upgrade has completed but there were errors during the upgrade 
process. 

```

I also notice this output when I try running it, which is the same from the GUI installer (update-manager -d):

```

start: Job is already running: apport

```

Any thoughts?

---

### Post by theanswriz42 on 2012-09-07
ttt

---

### Post by Epodx64 on 2012-09-07
You could try "sudo apt-get -f upgrade" that will attempt to fix it

---

### Post by theanswriz42 on 2012-09-07
> **Epodx64 said:**
> You could try "sudo apt-get -f upgrade" that will attempt to fix it

Yeah, it couldn't resolve everything, either could aptitude safe-upgrade. Totally bizarre.

---

### Post by cariboo on 2012-09-07
I'd suggest making a backup copy of /var/lib/dpkg/status, then deleting the file to see if that solves your problem.

---

### Post by paul_in_london on 2012-09-07
Try this:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
sudo aptitude safe-upgrade
```

or if you're using apt-get:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
sudo apt-get upgrade
```

Eventually you should be able to do:

```
sudo aptitude full-upgrade
``` or

```
sudo apt-get dist-upgrade
```

If that doesn't work, try using **/var/backups/dpkg.status.0** instead of **/var/lib/dpkg/status-old**.

Note also that in **/var/backups** there are other backups of the status file (dpkg.status.1.gz, dpkg.status.2.gz etc). If things are really screwed up, try unzipping one or more of those and replacing your corrupted status file with an even older one. It just means you'll end up applying more updates.

EDIT: Just make sure that if you revert to a status file which precedes your **do-release-upgrade -d** command you update and upgrade before repeating the **do-release-upgrade -d**.

---

