---
title: "Can not install curl"
date: 2018-11-06
forum: Ubuntu Development Version
---

### Post by ubername on 2018-11-06
Tried to install curl (command line and synaptic - I know they are pretty much the same but thought I would give it a whirl). I get:

```
sudo apt-get install curl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 curl : Depends: libcurl4 (= 7.61.0-1ubuntu2) but 7.61.0-1ubuntu2.2 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Any clues what to do mext? Thanks

---

### Post by mc4man on 2018-11-07
libcurl4 7.61.0-1ubuntu2.2  is from cosmic-security, disco hasn't gotten that version.
So either wait or remove libcurl4, update your sources, then curl and libcurl4  (7.61.0-1ubuntu2) can be installed

(- or download & install the cosmic-security curl source packages you need.

---

