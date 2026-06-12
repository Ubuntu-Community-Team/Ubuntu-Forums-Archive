---
title: "updating clamav signatures"
date: 2009-08-25
forum: Security
---

### Post by eltonw on 2009-08-25
I am using Ubuntu 9.04 NBR on an Asus 1000 PC. My concern and problem is that I cannot seem to get clamav to update the signatures. I have KlamAV 0.46 and clamtk 0.48 installed. As the only user, I do have root access. As regards installation / removal of software, my tool of preference is synaptic. 

(FWIW my usage or knowledge:confused: of command-line parameters in linux and / or console usage is extremely limited)

It does not seem that the virus sighatures have been refreshed by the update facility, though that is set to run automatically.

TIA for any pointers or assistance.

---

### Post by cariboo on 2009-08-25
Open an Applications-->Accessories-->Terminal, and type:

```
sudo freshclam
```

This will create a cron job that checks for virus signatures hourly.

---

