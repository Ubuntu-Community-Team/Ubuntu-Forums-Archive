---
title: "Setting up samba"
date: 2006-09-19
forum: Server Platforms
---

### Post by Steve Smith on 2006-09-19
While setting up samba I got the following errors:

---
Generating /etc/default/samba...
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0
 * Starting Samba daemons...                                             [ ok ]
---

I can't log in on the windows machine, and I guess that's why.  I'd be grateful if someone could explain what the errors are about, and what I should do

Thanks!
Steve

---

### Post by Iowan on 2006-09-19
[http://www.ubuntuforums.org/showthread.php?t=245681]("http://www.ubuntuforums.org/showthread.php?t=245681")
A similar problem - dunno if their advice will help you or not...

---

### Post by Steve Smith on 2006-09-19
Thanks, that thread's helped me learn more.  Googling, it seems the errors I pasted aren't a problem, and the next time samba loads it'll be fine.

I don't think I really want a smbusers file from what I can work out - I want  to be able to enter any of my ubuntu usernames and passwords into the windows machine, rather than a separate set listed in smbusers.  How can I do that?

---

