---
title: "wget ftp problem"
date: 2018-05-11
forum: Server Platforms
---

### Post by secoonder on 2018-05-11
Hello
i can not get the data by wget ftp. i  have access to the remote server. i can get another file in the same folder.But i can not get the file that i want.
**Error is:**
> wget ftp://abcd:defg@192.168.x.x//bcdedfg/nbackup/abcd_$(date +%Y-%m-%d_%H)_[SAATLIK_B3].nbk.gz


Removed &#8216;.listing&#8217;.
**No matches on pattern &#8216;abcd_2018-05-11_17_[SAATLIK_B3].nbk.gz&#8217;.**


But This file is in the folder ! No permission problem. 
Remote Server:
> root@bbbb:~# ls -l
-rw-r--r-- 1 root root 710967296 Nis 16  2017 x
-rw-r--r-- 1 root root 776841171 Nis 16  2017 abcd_2018-05-11_17_[SAATLIK_B3].nbk.gz


i can get x file.But i can not get another file.
Can you help me ?
Thank you very much

---

### Post by darkod on 2018-05-11
Have you tried without the [] characters in the filename? Those are rather special chars, I would try avoiding using them in filenames.

---

### Post by secoonder on 2018-05-12
darkod Thank you.
But the problem is not solved.it is same error

---

### Post by darkod on 2018-05-12
Have you tried using the filename in wget instead of variable?

I have no other ideas right now, looks like it should work if you can get other files too.

---

### Post by The Cog on 2018-05-12
Try putting one or two backslashes in front of the [ character: 
wget ftp://abcd:defg@192.168.x.x//bcdedfg/nbackup/abcd_$(date +%Y-%m-%d_%H)_\[SAATLIK_B3].nbk.gz
or 
wget ftp://abcd:defg@192.168.x.x//bcdedfg/nbackup/abcd_$(date +%Y-%m-%d_%H)_\\[SAATLIK_B3].nbk.gz

The "No pattern matches ..." tells me there is some regex matching going on, and [ is a special character for regex pattern matching.

---

### Post by secoonder on 2018-05-13
**Darkod **and **The Cog**
Thank you very much for your answers

**The Cog **
i tried > [COLOR=#000000]wget ftp://abcd:defg@192.168.x.x//bcdedfg/nbackup/abcd_$(date +%Y-%m-%d_%H)_**\\**[SAATLIK_B3].nbk.gz

[/COLOR]
it is work.The problem is solved.

Thank you very much again.

---

