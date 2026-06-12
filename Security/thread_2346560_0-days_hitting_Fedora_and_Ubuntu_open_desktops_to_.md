---
title: "0-days hitting Fedora and Ubuntu open desktops to a world of hurt"
date: 2016-12-16
forum: Security
---

### Post by Daveski17 on 2016-12-16
[http://arstechnica.com/security/2016/12/fedora-and-ubuntu-0days-show-that-hacking-desktop-linux-is-now-a-thing/](http://arstechnica.com/security/2016/12/fedora-and-ubuntu-0days-show-that-hacking-desktop-linux-is-now-a-thing/)

'If you run a mainstream distribution of Linux on a desktop computer, there's a good chance security researcher Chris Evans can hijack it when you do nothing more than open or even browse a specially crafted music file. And in the event you're running Chrome on the just-released Fedora 25, his code-execution attack works as a classic drive-by.'

~ Ars Technica

---

### Post by vasa1 on 2016-12-16
Chris Evans is a pretty active security expert over at Google:> All discoveries were ethically reported. Some of these discoveries were sponsored by my employer, Google. We're always hiring for security.from [https://security.appspot.com/security/index.html](https://security.appspot.com/security/index.html). He blogs at [http://scarybeastsecurity.blogspot.com](http://scarybeastsecurity.blogspot.com) 

I hope his concerns are taken on board!

---

### Post by Daveski17 on 2016-12-16
Yes, I hope his concerns are taken seriously too.

---

### Post by mc4man on 2016-12-16
Already patched in supported Ubuntu releases.

---

### Post by vasa1 on 2016-12-16
> **mc4man said:**
> Already patched in supported Ubuntu releases.

Would these be the ones?```
08:56 PM ~ $ grep stream /var/log/dpkg.log.1 | grep "status installed"
2016-11-17 14:58:13 status installed libgstreamer-plugins-bad1.0-0:amd64 1.8.2-1ubuntu0.2
2016-11-17 14:58:13 status installed gstreamer1.0-plugins-bad-videoparsers:amd64 1.8.2-1ubuntu0.2
2016-11-17 14:58:13 status installed gstreamer1.0-plugins-bad-faad:amd64 1.8.2-1ubuntu0.2
2016-11-17 14:58:13 status installed gstreamer1.0-plugins-bad:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:50 status installed gstreamer0.10-plugins-good:amd64 0.10.31-3+nmu4ubuntu2.16.04.1
2016-11-23 07:55:50 status installed libgstreamer-plugins-base1.0-0:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:50 status installed gstreamer1.0-plugins-base:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:51 status installed libgstreamer-plugins-good1.0-0:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:51 status installed gstreamer1.0-plugins-good:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:52 status installed gstreamer1.0-x:amd64 1.8.2-1ubuntu0.2
2016-11-29 15:03:13 status installed gstreamer0.10-plugins-good:amd64 0.10.31-3+nmu4ubuntu2.16.04.2
2016-11-29 15:03:14 status installed libgstreamer-plugins-good1.0-0:amd64 1.8.2-1ubuntu0.3
2016-11-29 15:03:14 status installed gstreamer1.0-plugins-good:amd64 1.8.2-1ubuntu0.3
08:56 PM ~ $ 

```

---

### Post by mc4man on 2016-12-16
> **vasa1 said:**
> Would these be the ones?```
08:56 PM ~ $ grep stream /var/log/dpkg.log.1 | grep "status installed"
2016-11-17 14:58:13 status installed libgstreamer-plugins-bad1.0-0:amd64 1.8.2-1ubuntu0.2
2016-11-17 14:58:13 status installed gstreamer1.0-plugins-bad-videoparsers:amd64 1.8.2-1ubuntu0.2
2016-11-17 14:58:13 status installed gstreamer1.0-plugins-bad-faad:amd64 1.8.2-1ubuntu0.2
2016-11-17 14:58:13 status installed gstreamer1.0-plugins-bad:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:50 status installed gstreamer0.10-plugins-good:amd64 0.10.31-3+nmu4ubuntu2.16.04.1
2016-11-23 07:55:50 status installed libgstreamer-plugins-base1.0-0:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:50 status installed gstreamer1.0-plugins-base:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:51 status installed libgstreamer-plugins-good1.0-0:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:51 status installed gstreamer1.0-plugins-good:amd64 1.8.2-1ubuntu0.2
2016-11-23 07:55:52 status installed gstreamer1.0-x:amd64 1.8.2-1ubuntu0.2
2016-11-29 15:03:13 status installed gstreamer0.10-plugins-good:amd64 0.10.31-3+nmu4ubuntu2.16.04.2
2016-11-29 15:03:14 status installed libgstreamer-plugins-good1.0-0:amd64 1.8.2-1ubuntu0.3
2016-11-29 15:03:14 status installed gstreamer1.0-plugins-good:amd64 1.8.2-1ubuntu0.3
08:56 PM ~ $ 

```
I'd think - 
```
game-music-emu (0.6.0-3ubuntu0.16.04.1) xenial-security; urgency=medium

  * SECURITY UPDATE: code execution via missing register value clamps
    - debian/patches/missing_register_value_clamp.patch: clamp values to
      uint8_t in gme/Spc_Cpu.h.
    - No CVE number

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Tue, 13 Dec 2016 11:37:51 -0500



```
(- i.e. libgme0

---

### Post by vasa1 on 2016-12-16
I got```
07:55 AM ~ $ apt-cache policy libgme0
libgme0:
  Installed: 0.6.0-3ubuntu0.16.04.1
  Candidate: 0.6.0-3ubuntu0.16.04.1
  Version table:
 *** 0.6.0-3ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.6.0-3 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
07:58 AM ~ $ 

```So people who have updated systems are fine. (I got the update on 2016-12-14.) Regarding the test, if unpatched, which particular calculator would run? For example, Lubuntu users won't have *gnome-calculator* by default. They, and perhaps ubuntu-mate users, may have *galculator*.

---

### Post by mc4man on 2016-12-16
> **vasa1 said:**
> I got```
07:55 AM ~ $ apt-cache policy libgme0
libgme0:
  Installed: 0.6.0-3ubuntu0.16.04.1
  Candidate: 0.6.0-3ubuntu0.16.04.1
  Version table:
 *** 0.6.0-3ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.6.0-3 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
07:58 AM ~ $ 

```So people who have updated systems are fine. (I got the update on 2016-12-14.) Regarding the test, if unpatched, which particular calculator would run? For example, Lubuntu users won't have *gnome-calculator* by default. They, and perhaps ubuntu-mate users, may have *galculator*.

not sure & while seeing on an ubuntu session with older libgme actually don't get calc opening, just totem crashing & not being able to open again until some ./files are removed. 
(- so removed file from prior post, it came from researchers site so assume it did work on some 16.04 installs somewhere to demonstrate vulnerability

---

### Post by Daveski17 on 2016-12-19
Well, as long as Trusty Tahr LTS has been patched I'll be OK then.

---

### Post by maglin2 on 2016-12-23
I get:

```
~$ apt-cache policy libgme0
libgme0:
  Installed: (none)
  Candidate: 0.6.0-3ubuntu0.16.04.1
```

this is on 16.04 without the ubuntu restricted extras or add-ons packages, so I'm not sure if the exploit would actually have worked on a truly default 16.04 install.

---

