---
title: "Unix user - Samba user sync using Webmin"
date: 2006-10-12
forum: Server Platforms
---

### Post by magicgeorge on 2006-10-12
I'm using Webmin trying to administer Samba and cannot get Unix users to convert to Samba users.  The error reported follows:

Failed to convert user: /usr/bin/pdbedit failed: 

tdb_update_sam: Failing to store a SAM_ACCOUNT for [melKinney] without a primary group RID

The reference to primary group RID has me stumped. I haven't found anything in the documentation about that or where the SAM_ACCOUNT gets stored. (for what it's worth, this user has a primary group of Unix users.) ](*,)

---

