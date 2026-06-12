---
title: "LTSP + Likewise + Local Apps Issue"
date: 2010-05-06
forum: Server Platforms
---

### Post by Kevin.Kolk on 2010-05-06
I'm working on setting up an LTSP server and so far it's been going fairly well.  I want it to be able to authenticate against our existing active directory environment so I've setup likewise-open and that's now working fine.  I also have pam_mount working for mounting the users documents off the network.

Everything was fine until I wanted to add firefox and flash as local applications on the thin clients.   I went though the guides in the Wiki and it is working for local users on the LTSP server.

But, my domain users don't get local-apps and after a bit of troubleshooting on the thin clients in syslog I found this:

```
ltsp4488 ltsp-localappsd: Unknown user: DOMAIN\\user
```Any ideas how I get Likewise authenticated users to be recognized on the thin client for localapps?   They work fine otherwise.

---

### Post by fang0654 on 2010-05-06
I haven't done this myself, but here's an idea:

likewise works through pam.  (Not sure which modules offhand, but looking in the config files in /etc/pam.d should show).  Does the LTSP local apps daemon have its own config in that folder?  Maybe it needs to be specifically configured to use the likewise module.

---

