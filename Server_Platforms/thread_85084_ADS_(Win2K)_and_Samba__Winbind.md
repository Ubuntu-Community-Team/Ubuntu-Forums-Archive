---
title: "ADS (Win2K) and Samba / Winbind"
date: 2005-11-01
forum: Server Platforms
---

### Post by Swad on 2005-11-01
I am completely stumped in trying to get Samba to use my Windows 2000 Active Directory to authenticate against.  I have read and re-read these pages to no end:

[http://www.ubuntuforums.org/showthread.php?t=5409](http://www.ubuntuforums.org/showthread.php?t=5409)
[https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28active%29](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28active%29)

Currently I am getting this when I try to join my computer to the domain:

$ net ads join
[2005/11/01 15:47:32, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb

I'm starting to think something is wrong with some of my packages.  I am using everything from Breezy and I have up through multiverse enabled in my repositories.  As of right now I can't find any log to show me more and I have no idea what is wrong with this thing.  What a hokey deal trying to make this work with ADS.

Please help!  :(

---

### Post by LordHunter317 on 2005-11-01
Post your smb.conf, for starters.

---

### Post by Swad on 2005-11-01
I'll get the info tomorrow when I get back to work.  I totally un-installed everything out of frustration so I can start from a clean slate again.  I'll have to get back to where I was.

---

