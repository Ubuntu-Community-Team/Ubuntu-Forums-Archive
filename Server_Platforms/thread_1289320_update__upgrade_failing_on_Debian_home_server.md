---
title: "update / upgrade failing on Debian home server"
date: 2009-10-12
forum: Server Platforms
---

### Post by quixote on 2009-10-12
apt-get tells me it cannot resolve, for instance, ftp.us.debian.org, but I can ping it.  Since apt-get can't find any packages, I can't upgrade my system.  And I'm too ignorant too know how to fix it! :(  Please help!

This is an HP Mediavault on which I installed Debian Lenny and which I'm running as a headless server with ssh access, so I can get at files when I'm not at home.  All that seems to be working okay.  I hadn't actually used it in about a month, and when I logged in again, apt couldn't update or upgrade.

Is apt somehow corrupted on my system?  ??  What can I do best to fix it?

Here are the actual error messages I'm getting:
```

debserv:/# apt-get update
Err http://security.debian.org lenny/updates Release.gpg                
  Could not resolve 'security.debian.org'
Err http://ftp.us.debian.org lenny Release.gpg                          
  Could not resolve 'ftp.us.debian.org'
W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```
The last message is particularly frustrating, since you see the initial command....

I realize this is a Debian, not Ubuntu, question, but I don't know my way around the Debian community.  If there's a Debian forum you know about where I should be asking this, please let me know.

Thanks!

---

