---
title: "Which LTS should I install?"
date: 2008-03-25
forum: Server Platforms
---

### Post by pioni on 2008-03-25
I'm about to install Ubuntu on a server that broke down recently, but can't decide whether I should install Ubuntu 6.06 LTS or the latest 8.04 LTS beta. If I choose to latter one, can it be updated to release level without problems or should I install the 6.06 LTS (or the latest non-LTS) and upgrade it in a month, when 8.04 LTS is released? 

The server had CentOS 4.6 before, so for me the easiest solution would be installing CentOS 5.1 and restoring the backup. However, I heard that CentOS doesn't support other filesystems than ext3 officially and the last ext3 installation was totally trashed after a power failure and that's why I'm considering Reiserfs3 next time.

---

### Post by Oldsoldier2003 on 2008-03-25
> **pioni said:**
> I'm about to install Ubuntu on a server that broke down recently, but can't decide whether I should install Ubuntu 6.06 LTS or the latest 8.04 LTS beta. If I choose to latter one, can it be updated to release level without problems or should I install the 6.06 LTS (or the latest non-LTS) and upgrade it in a month, when 8.04 LTS is released? 

The server had CentOS 4.6 before, so for me the easiest solution would be installing CentOS 5.1 and restoring the backup. However, I heard that CentOS doesn't support other filesystems than ext3 officially and the last ext3 installation was totally trashed after a power failure and that's why I'm considering Reiserfs3 next time.

6.06 for production machines. never run beta on a production machine...

---

### Post by r0biwan on 2008-03-25
I actually just moved a small home office server from CentOS to Ubuntu Server. I decided against the using the beta, only because I've had issues in the past (with other products however) upgraded from a beta release to final. I decided to install 7.10 and will upgrade to 8.04 when it's released

I figure LTS doesn't concern me since 7.10 will only be installed for a month or so...

---

### Post by pioni on 2008-04-04
I installed the server version of 7.10 and I'm so glad that I did, because it's so much faster and better than CentOS so far. Now I wonder how well will the update go after a couple of weeks. :)

---

