---
title: "help with my steam installation (Kali Linux x64 2017.1)"
date: 2017-11-29
forum: Ubuntu/Debian BASED
---

### Post by facundo1558 on 2017-11-29
When I Execute The Command sudo apt-get install steam. 
this error occurs
```
root@facundo:~# sudo apt-get install steam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libglade2.0-cil : Depends: libglade2-0 (>= 1:2.6.4-2~) but it is not going to be installed
 libgtk2.0-cil : Depends: libmono-system-drawing4.0-cil (>= 4.6.1.3) but it is not going to be installed
 libmono-system-web-services4.0-cil : Depends: libmono-system-design4.0-cil (>= 1.0) but it is not going to be installed
 libmono-system-web4.0-cil : Depends: libmono-system-drawing4.0-cil (>= 4.6.1.3) but it is not going to be installed
                             Depends: libgdiplus but it is not going to be installed
 libwebkit1.1-cil : Depends: libmono-corlib4.0-cil (>= 2.10.1) but it is not going to be installed
 libwebkitgtk-1.0-0 : Depends: libjavascriptcoregtk-1.0-0 (= 2.4.11-3) but it is not going to be installed
                      Depends: libenchant1c2a (>= 1.6.0) but it is not going to be installed
                      Depends: libgl1-mesa-glx but it is not going to be installed or
                               libgl1
                      Depends: libgstreamer-plugins-base1.0-0 (>= 1.2.0) but it is not going to be installed
                      Depends: libgstreamer1.0-0 (>= 1.4.0) but it is not going to be installed
                      Depends: libharfbuzz-icu0 (>= 0.9.18) but it is not going to be installed
                      Depends: libsecret-1-0 (>= 0.7) but it is not going to be installed
                      Depends: libwebp6 (>= 0.5.1) but it is not going to be installed
                      Depends: libxslt1.1 (>= 1.1.25) but it is not going to be installed
                      Depends: libxt6 but it is not going to be installed
                      Recommends: gstreamer1.0-plugins-base (>= 1.0.3) but it is not going to be installed
                      Recommends: gstreamer1.0-plugins-good but it is not going to be installed
                      Recommends: geoclue-2.0 but it is not going to be installed
 mono-devel : Depends: libmono-system-drawing4.0-cil (>= 4.6.1.3) but it is not going to be installed
              Depends: libmono-system-runtime4.0-cil (>= 2.10.1) but it is not going to be installed
              Depends: libmono-system-servicemodel4.0a-cil (>= 4.6.1.3) but it is not going to be installed
              Depends: libmono-system-serviceprocess4.0-cil (>= 3.0.6) but it is not going to be installed
              Depends: mono-mcs (= 4.6.2.7+dfsg-1) but it is not going to be installed
              Depends: mono-xbuild (= 4.6.2.7+dfsg-1) but it is not going to be installed
              Depends: libmono-cil-dev (= 4.6.2.7+dfsg-1) but it is not going to be installed
              Recommends: mono-csharp-shell but it is not going to be installed
 steam:i386 : Depends: libc6:i386 (>= 2.15) but it is not going to be installed
              Depends: libstdc++6:i386 (>= 4.3) but it is not going to be installed
              Depends: libx11-6:i386 but it is not going to be installed
              Depends: libudev1:i386 but it is not going to be installed
              Depends: libxinerama1:i386 but it is not going to be installed
              Depends: libtxc-dxtn0:i386
              Depends: libgl1-mesa-dri:i386 but it is not going to be installed
              Depends: libgl1-mesa-glx:i386 but it is not going to be installed
              Recommends: zenity:i386
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
Solutions?

---

### Post by howefield on 2017-11-29
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldos2er on 2017-11-29
Why on earth are you trying to install/run steam on Kali? It's not a desktop distro, From  [https://docs.kali.org/introduction/should-i-use-kali-linux](https://docs.kali.org/introduction/should-i-use-kali-linux)

As the distribution&#8217;s developers, you might expect us to recommend that  everyone should be using Kali Linux. The fact of the matter is, however,  that Kali is a Linux distribution specifically geared towards  professional penetration testers and security specialists, and given its  unique nature, it is **NOT** a recommended distribution if  you&#8217;re unfamiliar with Linux or are looking for a general-purpose Linux  desktop distribution for development, web design, gaming, etc.

---

### Post by uRock on 2017-11-29
> **oldos2er said:**
> Why on earth are you trying to install/run steam on Kali?

That was the first thing that came to mind when I saw the title. Second thought was, why not 2017.3?

---

