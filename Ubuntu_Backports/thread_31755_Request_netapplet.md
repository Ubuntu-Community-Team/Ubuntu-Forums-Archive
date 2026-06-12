---
title: "Request: netapplet"
date: 2005-05-04
forum: Ubuntu Backports
---

### Post by thully on 2005-05-04
The version of netapplet (0.99) currently in Hoary is buggy (it always crashes on GNOME logout, for instance) and the one in sid (1.00) works prefectly fine on Hoary.  Could somebody please look into getting this new version into Ubuntu Backports?

---

### Post by Technoviking on 2005-05-04
I have made an Ubuntu deb for netapplet, it works great, but it is not showing up with the other applets on the "Add to Panel" menu. It this normal for this applet?

Mike

---

### Post by thully on 2005-05-04
[QUOTE=Mike Basinger]I have made an Ubuntu deb for netapplet, it works great, but it is not showing up with the other applets on the "Add to Panel" menu. It this normal for this applet?

Mike[/QUOTE]
 The latest version requires you to start it by adding it to the startup programs in the "Sessions"
control panel applet - you can't add it using the panel anymore.

---

### Post by jdong on 2005-05-04
I'm currently building one from Sid. Let's see where that takes us.

---

### Post by jdong on 2005-05-04
It's uploaded into Backports Staging [rev. 150]

Please test.

---

### Post by poofyhairguy on 2005-05-06
[QUOTE=jdong]
Please test.[/QUOTE]

Works good for me. I can't scan though ( I never can its the card) so someone else needs to test that....

---

### Post by bdp on 2005-05-21
I tried the backported netapplet today on my IBM t42 (with an internal atheros a/b/g wireless care) running hoary.  Netapplet was working, but for some reason running it caused my wireless connection to be dropped repeatedly.  It would reconnect, but the cycle time was so quick that I might as well have had no connection.

Removing the package solved the problem, though of course I don't have the netapplet features (it would be nice to be able to easily switch among wireless networks and configurations).

---

### Post by emendelson on 2005-05-21
Does your message about the T42 mean that the backported version caused this problem of repeated disconnects? Or was that the earlier (non-backported) version?

---

