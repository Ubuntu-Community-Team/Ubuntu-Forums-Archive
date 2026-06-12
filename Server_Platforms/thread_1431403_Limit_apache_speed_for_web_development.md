---
title: "Limit apache speed for web development"
date: 2010-03-16
forum: Server Platforms
---

### Post by SoftwareExplorer on 2010-03-16
Is there a way to limit the speed that apache will send a page to a specific computer in my LAN? I would like to be able to test what my pages would be like if they loaded at 25KB/s for example. My Server is 192.168.0.2 and the other 'browser' computer is 192.168.0.4.

---

### Post by dudumomo on 2010-03-16
I've never tried, but you can may be try with Mod_bw
And add:
BandWidthModule On
ForceBandWidthModule On
BandWidth 192.168.0.4

Or may be:
BandWidthModule On
ForceBandWidthModule On
BandWidth 192.168.0.0/24 0

will be find.

Check the third point of this article: [http://www.freelydifferent.com/self-hosting/easy-tip/](http://www.freelydifferent.com/self-hosting/easy-tip/)

---

### Post by SoftwareExplorer on 2010-03-22
Thanks for the reply. I don't think I have the syntax figured out yet, but I'll get to it when I'm less busy.
Thanks again!

---

### Post by dudumomo on 2010-03-22
Okay, let us know!

---

