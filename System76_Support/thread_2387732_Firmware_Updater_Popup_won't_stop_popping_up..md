---
title: "Firmware Updater Popup won't stop popping up."
date: 2018-03-22
forum: System76 Support
---

### Post by helge59 on 2018-03-22
The Firmware Updater Popup (headphone jack) is popping up every day now.  This is in spite of that fact that I ran the updater last week on my recently acquired Serval.  
The updater ran to completion except that I never saw item 6 of the list, "Two small blue boxes..."
So I re-ran it but I got a message during boot:  "Error 451: the host CPU does not have write access to the target flash area...".
I don't think this message appeared the first time I ran the updater but I am not sure.

Ever since then I am seeing the same Updater pop-up every day.

Anybody know how I can stop the pop-up?

---

### Post by kerry_s on 2018-03-22
try running in terminal:
sudo apt update && sudo apt -y full-upgrade

---

### Post by helge59 on 2018-03-25
Thanks for the suggestion kerry_s.  I tried it and restarted the system but I continue to see the pop-up every afternoon around the same time.  I'll try system76 support during the week.

---

### Post by helge59 on 2018-04-03
With the help of s76 support the problem is resolved.  I needed to unplug my external monitor which I had neglected to do.  With the monitor disconnected the firmware update succeeded and the popups stopped.

---

