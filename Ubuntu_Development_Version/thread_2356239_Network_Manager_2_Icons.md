---
title: "Network Manager 2 Icons"
date: 2017-03-21
forum: Ubuntu Development Version
---

### Post by kc1di on 2017-03-21
I've just installed 17.04 mate and I now have two Network manager Icons on the panel.  Network manager seems to be working ok. but don't need the two any way to get rid of one?
Thanks

---

### Post by vanadium on 2017-03-21
In Mate, you can add/remove items on the panel as you wish. Just remove the extraneous icon configuring the panel.

---

### Post by kc1di on 2017-03-21
Thank You vanadium,
But that does not work with icon in the system tray - you can only remove the tray completely not the Items within it. 
Other apps your right you can right click and add or remove them.

---

### Post by vanadium on 2017-03-21
Sorry, indeed, the tray icons appear in a single applet. Could be that the network manager is started twice. Here, for Mint, a user ([https://forums.linuxmint.com/viewtopic.php?t=159797#p826856](https://forums.linuxmint.com/viewtopic.php?t=159797#p826856)) reported it was loaded twice in the startup applications. Try disabling it in your autostart applications, even if you see only one entry. If after disabling it, there is no icon anymore, you can always turn it back on.

Elsewhere, I have seen that two icons appeared because also indicator-network was installed. On standard ubuntu (I do not know about Ubuntu Mate), this is not installed. The icon is provided by nm-applet, which comes with the network-manager package. If you have indicator-network installed, try removing it.

---

### Post by kc1di on 2017-03-21
Thanks again vanadium,

I do not have indicator-network installed.  unchecking in start up just removes both of them. Sure it's just something that will get straightened out eventually.
Thanks for the help though.

---

### Post by Frogs Hair on 2017-03-22
Try the following. ```
mate-panel --reset
```

[http://manpages.ubuntu.com/manpages/xenial/man1/mate-panel.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/mate-panel.1.html)

---

