---
title: "Can't pull my backup"
date: 2009-05-25
forum: Server Platforms
---

### Post by Spiny Norman on 2009-05-25
Hi I have been using 8.04 Lamp servers in several locations. My routine for backup is to pull a file using cron from my backup server. I establish this by scp ing my public key into root on the remote machine, I then ssh in and accept the key into my known hosts file. This all worked fine until I installed 8.04.2. Suddenly this fails and requires a password. I know this because when I run my shell scrip from the CLI I get that request. Main difference in my root file is the presence of a folder ".gnupg" I quickly rebuilt the offending machine with an old 8.04.1 iso I had and now I am disturbed to notice that after the usual update upgrade this .gnupg folder is present in the root again. Is this my problem?
I have used apt-get remove "gnupg" to try to get rid of this.
Has anyone run into this before?
My other Lamps continue to run and back up faultlessly so I dare not upgrade them until I have a way forward.

---

### Post by Spiny Norman on 2009-07-22
This was a corrupt server build. No recurrence using a better iso. OOPs!:oops:

---

