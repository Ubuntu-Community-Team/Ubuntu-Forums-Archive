---
title: "spontaneous remote desktop connection(scrared)"
date: 2010-08-18
forum: Security
---

### Post by ram0042 on 2010-08-18
ok so right now 11:40ish PM, somebody accessed my laptop while i was looking at my college schedule. it lasted for like 10-15 seconds until i just switched the wireless off physically. i was using bittorrent on Wine and i was i demonoid.com talking to some angry people in the forums. i couldnt catch wat it said wen it happened (like the IP) but i had my settings with the first 2 checkboxes [**** my time changed!] are checked and they said allow anyone in your network to cennect, and allow user to have full control. so they are unchecked, but how did that person get to my machine. let me chack the log in my router, i dont think anybody in this neighborhood has linux anyway. how can i stop this from ever happening again?

sorry for the typos and the cursing. my time is now 11:16!

i looked into my router and everything seems fine in the output log. but i might do some searching for the incoming..

---

### Post by prshah on 2010-08-18
> **ram0042 said:**
> i couldnt catch wat it said wen it happened (like the IP)

Please check /var/log/auth.log for incoming authenticated connection entries.

You can post any suspicious entries here for confirmation; please sanitize the output (Eg, remove your IP address and/or network, username, etc details).

---

### Post by cdenley on 2010-08-18
> **prshah said:**
> Please check /var/log/auth.log for incoming authenticated connection entries.

Vino doesn't log connections or authentication attempts, unfortunately, and that is almost certainly how the connection came through. Vino (Remote Desktop) uses the VNC protocol, which is not exclusively used on Linux, as with most open-source software. There are many bots which search IP's at random for VNC servers with a weak or no password. You probably enabled "Remote Desktop", then someone connected. No surprise there.

Post this output (don't use sudo):
```

gconftool -a /desktop/gnome/remote_access

```

Then disable "Remote Desktop":
System>Preferences>Remote Desktop

---

