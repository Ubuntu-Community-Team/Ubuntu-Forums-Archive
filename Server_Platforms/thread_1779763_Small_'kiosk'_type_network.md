---
title: "Small 'kiosk' type network"
date: 2011-06-10
forum: Server Platforms
---

### Post by nickwood7 on 2011-06-10
Hey everyone, Im currently trying to get up a small kiosk type network involving 2 client laptops and 1 server. the purpose of the network hopefully will be to enable SSO log-ons for approx 50 users onto the clients to just browse the web through the server with a web blocker on so that only 'decent' sites can be accessed. No other functionality of the clients is really needed IE media playing etc.

Does anyone have any idea's on what would be the best angle to do this? All 3 computers have linux on them.

I currently have ubuntu 11.04 server + desktop CD's

Cheers for any help

---

### Post by jamesrw on 2011-06-17
this sounds interesting.

there is a long running LDAP/DC thread: 
[here]("http://ubuntuforums.org/showthread.php?t=640760")

and an outdated thin client howto:
[here]("https://help.ubuntu.com/community/ThinClientHowto")

---

### Post by crispy_420 on 2011-06-18
Doesn't edubuntu have thin client support through LTSP ([http://ltsp.sourceforge.net/](http://ltsp.sourceforge.net/)) and content filter in a single source? Install the server side and get clients that can boot from network.

If you have the hardware a gateway server with content filtering would be good too.

---

