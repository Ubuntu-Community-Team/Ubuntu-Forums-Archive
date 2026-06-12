---
title: "Adobe Flash Player"
date: 2014-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by DennisMesa on 2014-04-30
Just installed Ubuntu 14.04 LTS. I'm told by Amazon Prime to install Adobe Flash Player.
Adobe wants to know what program to associate the player with. I don't have a clue.
Also tried to install Flash Player on the command line. No luck. Any ideas??

---

### Post by kc1di on 2014-04-30
Hi DennisMesa,

to install the flash plugins install the following packages ```
ubuntu-restricted-extras and ubuntu-restricted-addons
``` you can do that in a terminal this way.
```
sudo apt-get update 
sudo apt-get install ubuntu-restricted-extras ubuntu-restricted-addons
```

---

### Post by monkeybrain20122 on 2014-04-30
Never watched Amazon videos but I think Linux flash doesn't work because of drm. You may need hal in addition to flash.
[https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal)

---

### Post by DennisMesa on 2014-05-06
> **kc1di said:**
> Hi DennisMesa,

to install the flash plugins install the following packages ```
ubuntu-restricted-extras and ubuntu-restricted-addons
``` you can do that in a terminal this way.
```
sudo apt-get update 
sudo apt-get install ubuntu-restricted-extras ubuntu-restricted-addons
```

I tried this, did not help. Thanks anyway.

---

### Post by DennisMesa on 2014-05-06
> **monkeybrain20122 said:**
> Never watched Amazon videos but I think Linux flash doesn't work because of drm. You may need hal in addition to flash.
[https://launchpad.net/~mjblenner/+archive/ppa-hal](https://launchpad.net/~mjblenner/+archive/ppa-hal)

Tried this, did not help. Thanks anyway.

---

### Post by monkeybrain20122 on 2014-05-06
Well then you may need pipelight-flash
[http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html)
See section 2.3

The switching alternatives can be simplified

Need to run this long command only once
```
sudo update-alternatives --install "/usr/lib/mozilla/plugins/flashplugin-alternative.so" "mozilla-flashplugin" /usr/lib/pipelight/libpipelight-flash.so 1
```
Whenever you want to switch default flash, just run
```
sudo update-alternatives --config mozilla-flashplugin
```
to choose the flash you want, then restart Firefox.

When both pipelight and system flash work (most of the time) system flash usually works better, so I don't recommend using it all the time.

---

