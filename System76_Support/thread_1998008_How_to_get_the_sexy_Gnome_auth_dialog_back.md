---
title: "How to get the sexy Gnome auth dialog back?"
date: 2012-06-06
forum: System76 Support
---

### Post by CaptSaltyJack on 2012-06-06
I'm running Gnome Shell. After performing the System 76 "restore," now the default Gnome 3 auth dialog is gone, replaced by a rather ugly auth window.

How do I get the Gnome auth dialog back?

---

### Post by CaptSaltyJack on 2012-06-06
Never mind, figured it out.

[LIST=1]
[*]Open a terminal.
[*]Type "sudo pam-auth-update". Deselect the fingerprint reader option and choose OK.
[*]cd into /etc/xdg/autostart
[*]Find the fingerprint daemon (I forget the exact name at the moment, just type "ls *finger*".
[*]Edit that file, and just comment out the "Exec" line by putting a # before it. I chose this rather than outright deleting the file, just in case I want it later.
[*]Reboot.
[/LIST]

---

