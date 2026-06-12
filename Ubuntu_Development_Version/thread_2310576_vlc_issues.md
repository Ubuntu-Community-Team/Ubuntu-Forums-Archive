---
title: "vlc issues"
date: 2016-01-20
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-01-20
This first one could be specific to an ubuntu session. The Tools > Preferences windows opens way too wide so are unusable.
A workaround for starting vlc from it's .desktop is in comment  #2
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1531516](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1531516)

The 2nd is specific to optimus machines (most laptops with nvidia gpu), when using the Intel gpu only.
 The default option for hwdec is automatic & at least here it always chooses vdpau which is wrong. Changing in Tools > Preferences > Input / Codecs > the hwdec dropdown fixes playback issues.
(- though one would need to be able to open & use Preferences to change.
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1536010](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1536010)

---

### Post by QDR06VV9 on 2016-01-20
Thanks mc4man! Good find..I have been using Kodi lately so i would have missed this one.
Regards

---

### Post by mc4man on 2016-01-20
In regards to both bugs - vlc's nasty head dev considers them not vlc's issue. So for vlc users, (I'm no longer one nor have been for a while), - 
good luck

---

