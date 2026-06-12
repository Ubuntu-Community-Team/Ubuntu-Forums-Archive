---
title: "Local Repository error"
date: 2021-09-27
forum: Ubuntu Development Version
---

### Post by cookiecruncher on 2021-09-27
```
Ign:1 http://za.archive.ubuntu.com/ubuntu impish InReleaseIgn:2 http://za.archive.ubuntu.com/ubuntu impish-updates InRelease         
Hit:3 http://dl.google.com/linux/chrome/deb stable InRelease               
Ign:4 http://za.archive.ubuntu.com/ubuntu impish-backports InRelease
Err:5 http://za.archive.ubuntu.com/ubuntu impish Release
  404  Not Found [IP: 197.155.77.2 80]
Hit:6 http://security.ubuntu.com/ubuntu impish-security InRelease
Err:7 http://za.archive.ubuntu.com/ubuntu impish-updates Release
  404  Not Found [IP: 197.155.77.2 80]
Err:8 http://za.archive.ubuntu.com/ubuntu impish-backports Release
  404  Not Found [IP: 197.155.77.2 80]
Reading package lists... Done
E: The repository 'http://za.archive.ubuntu.com/ubuntu impish Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://za.archive.ubuntu.com/ubuntu impish-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://za.archive.ubuntu.com/ubuntu impish-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```



To resume updates I installed synaptic, changed source to 'Main Server' in 'Download from'.
I'll check local repos again tomorrow.

---

