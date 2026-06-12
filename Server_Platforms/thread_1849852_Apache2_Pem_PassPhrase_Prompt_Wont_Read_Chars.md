---
title: "Apache2 Pem PassPhrase Prompt Wont Read Chars"
date: 2011-09-25
forum: Server Platforms
---

### Post by HuckBerry on 2011-09-25
I'm having an issue where if I reboot my https web server when apache2 begins to load I'm presented with the pem pass phrase dialog. This would be fine except that none of the characters I enter seem to make it to apache. I'll enter the passphrase and hit enter and nothing will happen. I generally have to ALT+F2 into a new tty and kill apache2 then restart it. From the second tty the password prompt works fine.

The only keystroke that seems to work in the original (init) tty is CTRL+ALT+DEL, but of course this reboots the system, landing me back where I started.

---

