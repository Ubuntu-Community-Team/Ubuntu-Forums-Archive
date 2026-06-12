---
title: "server ltsp"
date: 2010-05-20
forum: Server Platforms
---

### Post by felixvah on 2010-05-20
I setup Ubuntu lstp 9.10 server a while ago.  I had everything work correctly after a recent update on the server and now when a thinclient boot it got into a black screen going no where.  Can someone help me here please?

Here's what I have on the server:

opt/ltsp/i386/etc/lts.conf

[default]
LDM_AUTOLOGIN = true

#test pc public
[00:24:81:83:34:36]
LDM_USERNAME = public
LDM_PASSWORD = password

XRANDR_DISABLE = True
X_MODE_0 = 1024x768
X_HORZSYNC = 30.0-100.0
X_VERTREFRESH = 55.0-60.0

the above lts.conf was working fine up until a recent update.  I did not update to 10.4 yet.

---

