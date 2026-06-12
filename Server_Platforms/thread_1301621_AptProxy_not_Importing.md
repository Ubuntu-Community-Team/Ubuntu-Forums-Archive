---
title: "AptProxy not Importing"
date: 2009-10-26
forum: Server Platforms
---

### Post by kmuzheri on 2009-10-26
Hello Guys.
I have recently installed AptProxy on my machine. I used the ```
sudo apt-get install apt-proxy
``` command.
The AptProxy installed successfully but the sticky point in importing the libraries. For this I am using the following command:```
 sudo apt-proxy-import -r /var/cache/apt/archives
```

I then receive an error of failing to import packages (error snippet shown below). I have checked the known bug on this and possible work arounds. The question is: What are the implications of this problem?. Will I be able to install the updates on the server to a client machine, while the other updates from the backends may not be seen? Will I not be able to install anything through this proxy (AptProxy) until I am able import the libraries? Could someone explain the dynamics of this proxy in relation to this bug.

BELOW IS THE ERROR SNIPPET:
```
2009-10-26 15:03:19+0200 [-] [import] Importing packages from directory tree: /var/cache/apt/archives
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for debian backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for debian backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu backend
2009-10-26 15:03:20+0200 [-] [import] libdc1394-22_2.0.2-1_i386.deb skipped - no suitable backend found
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for debian backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu-security backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for debian backend
2009-10-26 15:03:20+0200 [-] [apt_pkg] No Packages files available for ubuntu backend

```

---

