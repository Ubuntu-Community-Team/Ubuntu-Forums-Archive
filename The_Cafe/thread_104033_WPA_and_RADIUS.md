---
title: "WPA and RADIUS"
date: 2005-12-15
forum: The Cafe
---

### Post by prizrak on 2005-12-15
I'm getting a new router that is WPA enabled and has a RADIUS server. I was wondering where I could find some guides on how to setup/administer the thing. Another question is of local nature does my wi-fi card have to support WPA (it uses madwifi drivers it's an Atheros chipset) or is it all software and I just need the WPA thing for Ubuntu (which is another question, wth is it called?) Any networking administration/setup guides would be helpful as well since with a hack I'm supposed to be able to do packet shaping as well.

---

### Post by prizrak on 2005-12-15
Bump it like it's hot :)

---

### Post by Mr. Electric Wizard on 2005-12-15
Search in the forum for wpa_supplicant.
I have never set it up, but it seems like this is the only one that works.
WifiRadar in the repositories also has some kind of WPA tools.
Definately post your findings if you get either one working, as I would like to do this also...

---

### Post by Lambert on 2005-12-15
See if you can find some answers here.

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

> Supported WPA/IEEE 802.11i features:
WPA-PSK ("WPA-Personal")
WPA with EAP (e.g., with RADIUS authentication server)

---

### Post by prizrak on 2005-12-15
Thanks I'll post what develops when I get the router (it's in the mail right now) :)

---

### Post by Mr. Electric Wizard on 2005-12-15
Cool which one did you end up getting?

---

### Post by prizrak on 2005-12-15
[QUOTE=Mr. Electric Wizard]Cool which one did you end up getting?[/QUOTE]
WRT54G I heard that one was Linux based and someone released a firmware version that allows you to do many cool things that the base one can't do. Although now I hear that V5 is not Linux based or rather SOME of them are, so I'll see what's up when I get it here. :)

---

### Post by prizrak on 2005-12-19
The router hath cometh, it is unfortunately v5 so I cannot put 3rd party firmware on it. I'm gonna have to see how it holds up stability wise and then decide if I want to keep it. So far I got WPA set up (it supports WPA2 but my WNIC doesn't) I used this guide [http://ubuntuforums.org/archive/index.php/t-90450.html](http://ubuntuforums.org/archive/index.php/t-90450.html) to set it up. And I used a program found here keepass.berlios.de to generate and keep my WPA key.

---

