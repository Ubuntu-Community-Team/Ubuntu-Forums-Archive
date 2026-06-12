---
title: "UTOPIC modem manager not remembering usb mobile broadband pin code and keyring"
date: 2014-07-12
forum: Ubuntu Development Version
---

### Post by Cliff_Simonds on 2014-07-12
Since I've installed 14.10 *every* time I boot, I've had to reenter my pin code in the sim pin unlock, the modem manager ask me to authenticate  saying "System policey prevents unlocking or controlling the mobile broadband device", and last but not least my default keyring password.
 I've been using ubuntu since 12.04 and usually only had to enter the keyring after the first initial setup. Is there a work around or is this because it' a dev version? Has anyone else had  or noticed this behaviour?
 Before posting I used the "Check if Already Posted" button and couldn't find any posting.  It's just that the repetitive extra steps to get on line, and the nagging popups are really starting to nerve and I wanted to know if UTOPIC's modem manager is going to stay that way.
Thanks ahead...

---

### Post by grahammechanical on 2014-07-12
What have you installed Utopic on? Please give some details about the hardware including the device/adapter that is used to connect to the internet. I have a standard desktop machine with the usual built-in ethernet and WiFi adapters connecting to a router. So, I do not experience what you are experiencing.
 
As regards things staying that way, well it all depends on whether the behaviour is part of the design blueprint or breaking the design blueprint. 

Regards.

---

### Post by Cliff_Simonds on 2014-07-12
> **grahammechanical said:**
> What have you installed Utopic on? Please give some details about the hardware including the device/adapter that is used to connect to the internet.
 I am using an ASUS X54C laptop and a vodafone K 3772-Z mobile broadband HSPA USB stick. 
  I've had this setup since 2011 and I have never had this problem before with any version since I started using ubuntu. I thought it could be while utopic is still an a alpha maybe there was a conflict with one of the other packages, being that different teams and people are in different stages of updating utopic. Kind of like: we can install conky and conky-std but conky-all isn't in the repositories for utopic yet. 
 The modem manager itself works good, maybe it's keyring that "forgets", but I couldn't find anything wrong in the seahorse password manager.

---

### Post by Cliff_Simonds on 2014-07-16
I found the problem. In GUFW Firewall I had my profile set to public  instead of home, so every time I booted and wanted to turn my mobile  broadband usb on,  the modem manager would ask me to authenticate saying  "System policey  prevents unlocking or controlling the mobile broadband device", on home  it only wants my keyring and my pin.

---

