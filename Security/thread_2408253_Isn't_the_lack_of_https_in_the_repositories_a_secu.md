---
title: "Isn't the lack of https in the repositories a security risk?"
date: 2018-12-16
forum: Security
---

### Post by Paddy Landau on 2018-12-16
It struck me today how few of the repositories use https instead of http. Here is a selection of those still using http:
```
http://security.ubuntu.com/ubuntuhttp://gb.archive.ubuntu.com/ubuntu
http://download.virtualbox.org/virtualbox/debian
http://dl.google.com/linux/chrome/deb
http://deb.playonlinux.com
http://linux.teamviewer.com/deb
http://ppa.launchpad.net/libreoffice/ppa/ubuntu
```
Isn't this an important security risk?

---

### Post by SagaciousKJB on 2018-12-16
> **Paddy Landau said:**
> It struck me today how few of the repositories use https instead of http. Here is a selection of those still using http:
```
http://security.ubuntu.com/ubuntuhttp://gb.archive.ubuntu.com/ubuntu
http://download.virtualbox.org/virtualbox/debian
http://dl.google.com/linux/chrome/deb
http://deb.playonlinux.com
http://linux.teamviewer.com/deb
http://ppa.launchpad.net/libreoffice/ppa/ubuntu
```
Isn't this an important security risk?

No I wouldn't think so.  You're downloading publicly available software, so privacy/secrecy is of no concern.  The only other thing HTTPS would provide is protection against a MITM manipulation of the data, but that would be a little redundant since apt itself has verification measures.

Plus I don't think an attacker would ever have much motivation to try to insert malicious code into these packages by conducting a MITM attack on individual TCP connections.  That would mean a lot of work to infect individual users, or at best networks that a single system administrator may be configuring.  It would pale in comparison to how much they could spread their malicious software if they hijacked the repository and supplanted the file there.  That wouldn't be a MITM attack so HTTPS would be irrelevant, and it would really fall back on the verification measures of apt at that point.

What makes this EVEN MORE unlikely to ever be a factor is that when it comes to "poisoning the well" and infecting Linux repositories with malware ( particularly Ubuntu/Debian systems ), is that PPAs are a far more lucrative target than official repositories.  Since PPAs can be offered by any 3rd party, you can't really vet who is offering the software.  As a consequence there have been things like 3rd party Kodi repositories infected with malware that installs cryptomining malware.  It's far easier to target this type of software, especially since a big appeal of these 3rd party versions of Kodi was to circumvent copyright laws; that means you're dealing with a user base cut off from the official program branch, and more likely to overlook what would ordinarily be red flags ( like downloading it off a hacking forum).  Of course, more "obscure" distributions aren't immune to it, Gentoo just had their GitHub hacked last summer.

Anyway, long post...  tl;dr....   No because package managers already handle package verification, and double no because no hacker would waste their time trying to manipulate software with a MITM attack on TCP connections.

---

