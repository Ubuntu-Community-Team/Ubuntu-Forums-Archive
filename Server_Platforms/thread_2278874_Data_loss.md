---
title: "Data loss"
date: 2015-05-19
forum: Server Platforms
---

### Post by eric72 on 2015-05-19
Hello All,

I'm new on here. 

I have a question on my server issue. My server had data roughly 30G but only shows 5G data. It was fine until one hour ago and suddenly most old data is gone and shows partial data that saved recently. Please help me what is going on my server.

---

### Post by QIII on 2015-05-19
Moved to Server Platforms.

Hello!

Which release are you using?  Did you recently update your software?  What were you doing immediately prior to the loss?  Had you issued any commands in the terminal?

---

### Post by tgalati4 on 2015-05-19
If you have a failing hard disk, then you won't have much time for recovery.  Pull off as many important files as you can.  Some suggest imaging (making a bit-by-bit copy) the disk and then working on the copy.  That allows you a new drive (with better mechanical condition) to perform data recovery.

Some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by TheFu on 2015-05-22
It could just be a lose cable and the partition could be unmounted.  Please post some data like
df, and sudo parted -l.
Does everything look correct? Any missing partitions?

Oh - and I hope you've been making backups. Nothing replaces having a good backups BEFORE you need them.

---

