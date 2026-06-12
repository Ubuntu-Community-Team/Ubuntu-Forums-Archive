---
title: "No panel system icon"
date: 2012-09-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by stinkeye on 2012-09-20
When using a non-default icon theme my top right system icon disapeared.
_Solution:_
Copy the icons in **/usr/share/icons/ubuntu-mono-dark/status/22**
system-devices-panel-information.svg
system-devices-panel-alert.svg
system-devices-panel.svg

to your themes **/status/22** or **/22x22/status** folder.

[COLOR="Red"]Edit:[/COLOR] In a recent update the image-missing fallback icon is used  if the theme's missing the session menu icon.
So you get an icon but you probably still want to copy over the system-devices-panel icons.

---

