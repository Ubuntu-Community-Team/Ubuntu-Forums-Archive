---
title: "Natty Upgrade - GPG hangs"
date: 2011-06-04
forum: Server Platforms
---

### Post by bmorgan on 2011-06-04
I have a home file server that I am trying to upgrade to natty 11.04. It was running 10.04 and was behind on updates due to lack of an internet connection for several months. I didn't have any problems applying all updates (sudo aptitude update; sudo aptitude full-upgrade) and then upgrading to 10.10 (sudo do-release-upgrade). I applied all updates to 10.10 (sudo aptitude update; sudo aptitude full-upgrade) without any problems. However I encountered problems trying to upgrade to 11.04.

Running: 
```
user@system:/$sudo do-release-upgrade 
Checking for a new ubuntu release
Get:1 Upgrade tool signature [198B]                                       
Get:2 Upgrade tool [1304kB]                                               
Fetched 1304kB in 0s (0B/s)                                               
extracting 'natty.tar.gz'
authenticate 'natty.tar.gz' against 'natty.tar.gz.gpg'
```
hangs indefinitely. I don't receive error messages, it just sits there. I have to escape from Screen and 'sudo screen -wipe' to try anything else.

I tried changing my repository list to point to a different mirror, but no change.

If I had error messages I would have more to go on, but at the moment I'm stuck. Any suggestions would be appreciated.

Thanks,
~B

---

### Post by bmorgan on 2011-06-27
Just thought I would update this:

I have since figured out the problem. There was no problem with the repos or with GPG. The problem was actually with GNU Screen. After downloading the upgrade defs and comparing the signature with GPG, the upgrade process launches screen for the actual upgrade. I assume this is for stability of upgrades during remote sessions, which makes sense. Anyway, upon other system work I discovered that screen wouldn't launch properly. After purging a lingering manual install of screen and reinstalling it from the repos screen functioned properly. Once screen was running correctly the install process was able to continue past the upgrade def signature verification and launch screen into the actual upgrade process.

Don't know if this will help anyone, but at least it is now resolved.

~B

---

