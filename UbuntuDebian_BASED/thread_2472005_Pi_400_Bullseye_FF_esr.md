---
title: "Pi 400 Bullseye FF esr"
date: 2022-02-15
forum: Ubuntu/Debian BASED
---

### Post by WacoJohn on 2022-02-15
[https://wwww.mewe.com](https://wwww.mewe.com)


> Your browser is not supported.
We cannot provide a good experience to your browser.
To use this site, please upgrade to the latest version of [Chrome]("https://www.google.com/intl/en/chrome/"), [Firefox]("https://www.mozilla.org/en-US/firefox/"), [Safari]("https://www.apple.com/safari/"), [Edge]("https://www.microsoft.com/en-us/windows/microsoft-edge") or some other modern browser.




Raspberry Pi 400

$ cat /proc/version
Linux version 5.10.92-v8+ (dom@buildbot) (aarch64-linux-gnu-gcc-8 (Ubuntu/Linaro 8.4.0-3ubuntu1) 8.4.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #1514 SMP PREEMPT Mon Jan 17 17:39:38 GMT 2022

Firefox Version 91.6.0esr (64-bit)

Anything I can do besides install Chromium????

---

### Post by Frogs Hair on 2022-02-15
I use Firefox  esr on multiple operating systems. I don't see any message on the main page, but I have no account for that site. Does this message appear when setting up the account or logging in ?

---

### Post by WacoJohn on 2022-02-15
the instant FF connects to their server.  If I am on another domain's page and type in [www.mewe.com](www.mewe.com)    new window/tab opens with that notice.  No sign in.  Just hittin' that page.

---

### Post by Frogs Hair on 2022-02-15
Sorry but, I can't reproduce the error. Are you using any extension that may interfere such as a user agent switcher ?

---

### Post by guiverc on 2022-02-15
This is in an Ubuntu area of this site; but you appear to be using Debian??

If it's Ubuntu, standard `firefox` packages are available that work; as I use them, and use mewe too (*I don't browse from a pi though*) and I have no issues accessing mewe from Ubuntu (*or Debian that I use too, though I'm mostly accessing mewe from Ubuntu*)

---

### Post by howefield on 2022-02-15
Thread moved to the "*Ubuntu/Debian BASED*" forum.

FWIW, that website opens fine on this machine running Debians FF 91.6.0esr.

---

### Post by WacoJohn on 2022-02-16
> **Frogs Hair said:**
> Sorry but, I can't reproduce the error. Are you using any extension that may interfere such as a user agent switcher ?

Possibly.  I will try to confirm either way.

---

### Post by WacoJohn on 2022-02-16
> **guiverc said:**
> This is in an Ubuntu area of this site; but you appear to be using Debian??

If it's Ubuntu, standard `firefox` packages are available that work; as I use them, and use mewe too (*I don't browse from a pi though*) and I have no issues accessing mewe from Ubuntu (*or Debian that I use too, though I'm mostly accessing mewe from Ubuntu*)

As for what I am using, ... Pi400 and the 'new' 64-bit OS which is bundled/released with Ubuntu and Chromium.  I got FF esr from that default repository (and have already uninstalled Chromium) 

 Turns out, there are different ways to determine what OS one may have.

[https://linuxhandbook.com/check-linux-version/](https://linuxhandbook.com/check-linux-version/)

What i posted is the output for:
```
[COLOR=#000000]$ cat /proc/version[/COLOR]
```

Other commands return different data.

```
[FONT=var(--font-mono)]cat /etc/os-release or [/FONT][FONT=var(--font-mono)]hostnamectl[/FONT]
```

So I picked one and posted its output.

When I was running Bullseye 32-bit and FF esr, I did not have this issue.

I have a feeling .... reproducing the problem ain't gonna happen unless it's on a system 'exactly' like mine.  Just a feeling.

---

### Post by guiverc on 2022-02-16
I'd suggest using `apt-cache policy firefox` to see where it's from.

Ubuntu packages of `firefox` can be seen with [https://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=all&section=all)

ie. that's

> 
[LIST]
[*][bionic (18.04LTS)]("https://packages.ubuntu.com/bionic/firefox") (web):     Safe and easy web browser from Mozilla            
97.0+build2-0ubuntu0.18.04.1 [**security**]: amd64 i386            
59.0.2+build1-0ubuntu1 [**ports**]: arm64 armhf ppc64el 
[*][bionic-updates]("https://packages.ubuntu.com/bionic-updates/firefox") (web):     Safe and easy web browser from Mozilla            
97.0+build2-0ubuntu0.18.04.1: amd64 arm64 armhf i386 ppc64el s390x 
[*][focal (20.04LTS)]("https://packages.ubuntu.com/focal/firefox") (web):     Safe and easy web browser from Mozilla            
97.0+build2-0ubuntu0.20.04.1 [**security**]: amd64            
75.0+build3-0ubuntu1 [**ports**]: arm64 armhf ppc64el s390x 
[*][focal-updates]("https://packages.ubuntu.com/focal-updates/firefox") (web):     Safe and easy web browser from Mozilla            
97.0+build2-0ubuntu0.20.04.1: amd64 arm64 armhf ppc64el s390x 
[*][hirsute (21.04)]("https://packages.ubuntu.com/hirsute/firefox") (web):     Safe and easy web browser from Mozilla            
96.0+build2-0ubuntu0.21.04.1 [**security**]: amd64            
87.0+build3-0ubuntu4 [**ports**]: arm64 armhf ppc64el s390x 
[*][hirsute-updates]("https://packages.ubuntu.com/hirsute-updates/firefox") (web):     Safe and easy web browser from Mozilla            
96.0+build2-0ubuntu0.21.04.1: amd64 arm64 armhf ppc64el s390x 
[*][impish (21.10)]("https://packages.ubuntu.com/impish/firefox") (web):     Safe and easy web browser from Mozilla            
97.0+build2-0ubuntu0.21.10.1 [**security**]: amd64            
93.0+build1-0ubuntu3 [**ports**]: arm64 armhf ppc64el s390x 
[*][impish-updates]("https://packages.ubuntu.com/impish-updates/firefox") (web):     Safe and easy web browser from Mozilla            
97.0+build2-0ubuntu0.21.10.1: amd64 arm64 armhf ppc64el s390x 
[*][jammy]("https://packages.ubuntu.com/jammy/firefox") (web):     Safe and easy web browser from Mozilla            
97.0+build2-0ubuntu1: amd64 arm64 armhf ppc64el s390x 
[/LIST]


Where as your version fits [https://packages.debian.org/search?keywords=firefox&searchon=names&suite=all&section=all](https://packages.debian.org/search?keywords=firefox&searchon=names&suite=all&section=all)

Your kernel looks like a Debian (5.10) to me too, even if it was *compiled* (*created*) on a Ubuntu system, it's still Debian.

The most recent build of Ubuntu Desktop uses the 5.13 kernel  (this is what's included - [https://cdimage.ubuntu.com/releases/21.10/release/ubuntu-21.10-preinstalled-desktop-arm64+raspi.manifest](https://cdimage.ubuntu.com/releases/21.10/release/ubuntu-21.10-preinstalled-desktop-arm64+raspi.manifest) which does **not** include chromium)

I have little recent experience with r.pi's & Ubuntu but I do see available (via *snap*)

```

channels:
  latest/stable:    97.0-2      2022-02-14 (973) 162MB -
  latest/candidate: 97.0-2      2022-02-11 (973) 162MB -
  latest/beta:      98.0b5-1    2022-02-16 (993) 163MB -
  latest/edge:      99.0a1      2022-02-16 (994) 180MB -
  esr/stable:       91.6.0esr-1 2022-02-14 (988) 161MB -
  esr/candidate:    91.6.0esr-1 2022-02-14 (988) 161MB -
  esr/beta:         &#8593;                                  
  esr/edge:        

```

so if `apt-cache policy` doesn't show an answer; I'd suggest `snap list` to see what you're using.  If using Ubuntu, you could switch from one package format to the other (it's what I'd try, my *jammy* system is still using *deb* package but that's **not** because I changed it)

---

### Post by WacoJohn on 2022-02-16
Evidently it is an add-on issue.  Just tried mewe.com from private window and works perfectly.  I will work on which add-on it i today.  Thanks to everyone for the terrific support.

---

