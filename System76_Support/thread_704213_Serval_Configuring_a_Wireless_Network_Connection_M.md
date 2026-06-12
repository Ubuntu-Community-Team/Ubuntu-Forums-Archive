---
title: "Serval: Configuring a Wireless Network Connection Manually"
date: 2008-02-22
forum: System76 Support
---

### Post by lightnb on 2008-02-22
How can I setup a connection "profile" for a specific network manually?

I have instructions from my IT department on how to set it up using Windows, but they don't know anything about linux, and thus, don't "support it".

Could someone translate into Kubuntu for me?

This is what it says:

I need to enter an SSID, use WPA, and TKIP. (I have the SSID I need)

Then change the EAP type to PEAP.

Check "authenticate as computer" and "authenticate as guest".

Uncheck "validate server certificate".

Check "enable fast reconnect".

---

### Post by thomasaaron on 2008-02-22
I'm not sure how to translate that into Kubuntu (or Ubuntu for that matter), but there should be a manual configuration option with whatever kubuntu's version of network manager is.

In Gnome, left-click the networking icon in the upper left of the screen and then select "Manual configuration."

I know that several of the options you listed are not there, but you should be able to at least enter the SSID, select WPA and enter the WPA authentication code. Try that and see if it will log on.

---

### Post by lightnb on 2008-02-22
I think that the problem is the lack of the WPA authentication code.

They don't have one. Instead, they claim I should be prompted for a username and password- which I have, but don't know where to put it?

---

### Post by thomasaaron on 2008-02-22
Hmmm.  Interesting.

Here is a guy that uses WPA Supplicant/WICD.
[http://ubuntuforums.org/showthread.php?p=4366247](http://ubuntuforums.org/showthread.php?p=4366247)

Any customers out there that have dealt with this?

---

### Post by Vadi on 2008-02-22
Yes, I used WICD on my old laptop since nm refused to cooperate. It's fine here so far though (connects at least, still no "refresh" button).

Give WICD a try here - [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/).

---

