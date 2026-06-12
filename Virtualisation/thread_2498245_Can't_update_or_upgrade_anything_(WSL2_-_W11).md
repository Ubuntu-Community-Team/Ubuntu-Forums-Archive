---
title: "Can't update or upgrade anything (WSL2 - W11)"
date: 2024-06-06
forum: Virtualisation
---

### Post by carpi06 on 2024-06-06
Hi, I have a problem with the updates and upgrades. I am running Ubuntu on a WSL on Windows 11 //I'm new in the forum, so tell me if I do something wrong.//
The problem is this: When I try to do an update or an upgrade, the "Working" percentage remains at 0% and does not continue. 
This is the error:
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:3 [https://http.kali.org/kali](https://http.kali.org/kali) kali-rolling InRelease
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Ign:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Ign:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease](http://archive.ubuntu.com/ubuntu/dists/jammy/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  Temporary failure resolving 'archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'

---

### Post by carpi06 on 2024-06-06
I have solved it with what is in this ask [ubuntu link]("https://askubuntu.com/questions/91543/apt-get-update-fails-to-fetch-files-temporary-failure-resolving-error")
Hope it helps to others with the same problem (&#12484;)

---

