---
title: "No prompt on exit when I use power button in ubuntu 13.10"
date: 2013-08-26
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-08-26
How do I set the system to prompt me when I hit the power button on exit in ubuntu 13.10.  Tried installing gnome-tweak-tool to do it, but it did not work.

Henry

---

### Post by mc4man on 2013-08-27
That & several other settings were handled in gnome-settings-daemon > plugins > power
Currently very little if anything in there works. (or works properly

Whether the plugin is no longer used or is just broken I don't now but there are certainly a host of possible issues, the one you've mentioned is just one
(ubuntu sets an override to make 'interactive' the default when pressing power button, obviously it's of little current value if the daemon isn't being used.

---

### Post by Hewjr100 on 2013-08-27
Oh well I just have to wait and see.

Henry

---

