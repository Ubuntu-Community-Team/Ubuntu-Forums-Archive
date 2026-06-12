---
title: "Issue with Apache after upgradr to 11.10"
date: 2011-11-11
forum: Server Platforms
---

### Post by Xeneth on 2011-11-11
I have Transmission-daemon running with web access.  For security, I am reverse proxying through Apache for ssl.

After the upgrade from 11.04 to 11.10, Apache seemed to throw fits.  I  fixed most of the issues, but the reverse Proxy is still causing issues.

When I go to my server "https://10.0.0.100" it connects, asks for password, but then my Transmission webUI is wacky.  At first, the reverse proxy was sending the webUI over normal http.  This seemed to be fixed but now it seems the webUI is not updating properly.  Not only am I seeing inconstancy in the feedback, but some options are not having an affect until I refresh.

EDIT: upon further investigating, I believe this issue is the webUI

---

