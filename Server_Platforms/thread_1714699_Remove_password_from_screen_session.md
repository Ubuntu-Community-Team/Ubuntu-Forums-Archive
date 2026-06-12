---
title: "Remove password from screen session"
date: 2011-03-25
forum: Server Platforms
---

### Post by fela on 2011-03-25
I added a password to a GNU screen session running irssi (IRC client) on my server, however I would like to remove the password now (it was just a test). I'd rather not have to restart the session as it's running some pretty important IRC logging and other stuff. ;)

Cheers :)

---

### Post by obsidiandh on 2011-03-27
Reattach your screen with **screen -r** then press **Ctrl-a :** (note the colon) type **password none** and press **enter** it should say *Password checking disabled* then just press **enter** again

---

### Post by fela on 2011-03-27
Thanks very much, did the trick :D

---

