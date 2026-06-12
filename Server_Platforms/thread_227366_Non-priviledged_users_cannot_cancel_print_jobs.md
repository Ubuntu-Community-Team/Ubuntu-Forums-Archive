---
title: "Non-priviledged users cannot cancel print jobs"
date: 2006-08-01
forum: Server Platforms
---

### Post by anindya_m on 2006-08-01
Hi,
    I have a slight problem with cups. On my machine most users are not in the lpadmin group and so cannot add/remove printers, but they can print fine using the lpr command. The problem is that they cannot remove jobs (only lpadmin group members can). lprm or cancel just asks for password on localhost and never succeedes.

Another related problem is that sometimes after I cancel a job some zombie processes are created. They are harmless as the printing works just fine but these zombies go only after I have restarted cupsys.

Any ideas?

regards,
Anindya

---

