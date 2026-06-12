---
title: "Chromium (snap) not using kdewallet for password storage"
date: 2020-02-23
forum: Ubuntu, Linux and OS Chat
---

### Post by maglin2 on 2020-02-23
Chromium Version 80.0.3987.116 (Official Build) snap (64-bit)
Kubuntu 19.10

Chromium (snap) is not by default using kdewallet for password storage - at least not for me. Don't know about the gnome keyring case.

The issue is discussed here [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1849160) and appears to rumble on.

Until now I'd thought I didn't *really* need full disc encryption on my netbook because no sensitive data was ever kept on it except some website login credentials saved in chromium, and these I thought were encrypted in kdewallet until I entered my kubuntu user login password. That's my (admittedly limited) understanding how chromium before the transition to snap worked. If the netbook was stolen, then I'd only lost a netbook.

It now apears I was wrong and all my login credentials were potentially extractable.

Running

```
snap connect chromium:password-manager-service
```

gets it working properly for newly saved passwords, but doesn't import and encrypt those already saved.

(Fortunately my netbook wasn't stolen before I discovered this!). 

To my mind this issue arising from snap transition seems serious enough to have merited some prominence - but perhaps it had it and I failed to notice.

---

