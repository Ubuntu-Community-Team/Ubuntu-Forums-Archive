---
title: "rotating LVM snapshots - possible?"
date: 2009-08-07
forum: Server Platforms
---

### Post by nerrud on 2009-08-07
Hello, 

Id like to set hourly/daily/weekly scheme for LVM snapshots for archiving and security purposes. Is this possible?

From what I've read, the most common usage of LVM snapshots is create-copy-discard when e.g. backing up an online database. What I'd like to do is to create/rotate and phase out snapshots on a regular basis (actual backing up to a different disk wil be another matter), e.g at any moment having 24 hourly snapshots, 7 daily, 4 weekly etc.

Have anyone tried enything like this? Any tips regarding setup/disk quotas etc?

Thanks for your help!

---

### Post by nerrud on 2009-08-08
One follow up question: 23 hourly + 6 daily LVM snapshots at any time - would it affect system performance adversely?

---

