---
title: "Amavisd-new and DSPAM error"
date: 2007-05-24
forum: Server Platforms
---

### Post by tuaris on 2007-05-24
I installed amavisd-new and dspam on Ubuntu Server 7.04.  Postfix is setup properly, and everything appears to work ok, but I receive the follow error in the mail log:

May 24 15:22:34 dspam dspam[13745]: Unable to create directory: /var/spool/dspam/data/local: Permission denied
May 24 15:22:35 dspam dspam[13745]: Unable to open file for reading: /var/spool/dspam/data/local/amavis/amavis.lock: Permission denied
May 24 15:22:35 dspam dspam[13745]: Unable to attach DSPAM context
May 24 15:22:35 dspam dspam[13745]: process_message returned error -2.  delivering.


I've spent hours tying to  figure this out with no luck.

---

