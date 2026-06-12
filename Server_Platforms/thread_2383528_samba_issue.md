---
title: "samba issue"
date: 2018-01-26
forum: Server Platforms
---

### Post by geohei on 2018-01-26
Hi.

ubuntu 14.04 server
(up-to-date)

I used to upload snapshots and videos from a video surveillance camera to an Ubuntu server.
ABUS TVIP41550, lastest firmware 1313w
I used SMB for that purpose.

I just right now noticed, that since beginning of July 2017, nothing was uploaded anymore.
Did something change within Samba around that time?
I didn't touch the configurations (/etc/samba/smb.conf or video camera).

The video camera sports a test feature. This one writes a test file to the target folder. This works (?!), but the saving the snapshots to the share doesn't work.

Any ideas?

---

### Post by wildmanne39 on 2018-01-26
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by LHammonds on 2018-01-26
Make sure your samba configuration wasn't overwritten by an update.  Sometimes updates happen and ask if you want to replace, ignore or compare the changes from the new config.

---

### Post by geohei on 2018-01-29
Sorry, forgot to mention that in my OP. smb.conf was not overwritten. All other shares still work.
Also ... the test feature of the camera (see above) writes to the share, meaning the problem must be on a different level.

---

### Post by LHammonds on 2018-01-29
I cannot imagine why the camera's test function can write to the share but the normal operations do not.  Are the normal operations configured to write to the correct location?  Did it lose the write path?  Is there a alpha case change in the path?

LHammonds

---

