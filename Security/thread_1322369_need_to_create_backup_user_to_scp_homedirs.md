---
title: "need to create backup user to scp homedirs"
date: 2009-11-10
forum: Security
---

### Post by jeffk on 2009-11-10
I need to run a copy and subsequently sync all user homedirs from Ubuntu 9.04 to Windows 2003.

I planned to use WinSCP for the initial copy, then unison to sync nightly.

Getting sudo working with WinSCP is proving a bit difficult. I would like to create a user 'backupuser' who has read access to all files.

What is the most practical way to do configure this user? i.e. what groups, etc. to be used with useradd and groupadd?

Or should I just enable root with a password?

Thanks.

---

