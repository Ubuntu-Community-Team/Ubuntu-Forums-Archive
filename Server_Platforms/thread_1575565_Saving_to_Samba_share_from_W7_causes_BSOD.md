---
title: "Saving to Samba share from W7 causes BSOD"
date: 2010-09-15
forum: Server Platforms
---

### Post by andynz22 on 2010-09-15
My W7 PC has been going to BSOD numerous times over the last week.  Eventually narrowed down the fault to when I saved a file to a Samba 3.4.0 Ubuntu 8.04 server.  Worked fine on other 8.04 Servers with same Samba 3.4.0.

Eventually found the fault was in the "security" setting in smb.conf.  Changed it to the same as other Samba servers and recommended in the conf file setting and no more BSOD :)

Changed "security = share" on smb.conf to "security = user".

Reference:
[http://www.sevenforums.com/crashes-debugging/29959-bsod-when-connected-linux-samba-share-2.html](http://www.sevenforums.com/crashes-debugging/29959-bsod-when-connected-linux-samba-share-2.html)

Cheers
Andy

---

