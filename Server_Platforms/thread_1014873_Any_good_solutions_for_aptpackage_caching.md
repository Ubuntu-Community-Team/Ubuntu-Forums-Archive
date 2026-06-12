---
title: "Any good solutions for apt/package caching?"
date: 2008-12-18
forum: Server Platforms
---

### Post by Chris on 2008-12-18
Years ago I ran apt-proxy then apt-cacher.  Both of which didn't work very well.  If I recall correctly the problems were mostly related to network connections stalling and such.

Eventually I started running apt-cacher-ng which seems to not have issues with the network stalling when getting packages (at least not as often).  However, very often when I do "apt-get update" on other machines it will fail to get many of the files (most often the .gpg files).  Usually if I restart the apt-cacher-ng daemon the next "apt-get update" will succeed but then it will fail again on subsequent requests.  Sometimes it works, sometimes it doesn't.

This is incredibly irritating.  A good proxy like Squid has no such problems at all.  

Looking at the HTTP transactions I see that the "apt-get update" itself doesn't seem to do the request correctly.  Often it seems to request multiple URL's from the proxy all at the same time.  Squid will only return the first request then kill the connection.  apt-cacher-ng tries to fulfill all the requests.  When apt-cacher-ng does this it seems to confuse the apt-get process because some requests like for .gpg files succeed but then others like the translations fail (and should be ignored).  apt-get seems to think the failure of the later requests overrides the previous ones so the .gpg will fail if the translation request is done afterwards on the same connection.

So it appears to me that both apt-get and apt-cacher are broken... or something.  Very frustrating.  Does anyone have a setup that works?  Squid would obviously work but since it doesn't know anything about Debian packages then it's going to expire stuff I don't want to expire (based on time rather than when the package is updated or whatever).

---

### Post by iponeverything on 2008-12-18
You can tell squid what to keep..

```
refresh_pattern -i \.(deb|msi|msp|iso|raw|rpm)$  14400 30% 86400  

```

---

### Post by Chris on 2008-12-18
Yeah but eventually the Squid cache is going to fill up and start deleting stuff I don't want deleted because it can't expire packages based on versions.

For the package cache I never want it to expire a package unless there is a newer version.  In that case it needs to expire the old version and keep the latest.  Squid isn't that smart I don't think.

---

