---
title: "File Permissions"
date: 2013-03-04
forum: Server Platforms
---

### Post by Timothy271 on 2013-03-04
Hi all,

I hope this is the correct section to post our problem, let's give you a quick intro:

We're trying to set up a bacula back-up environment. We have an openfiler server and an ubuntu server, a mysql server with a samba share, directed to the openfiler (due to the fact there can be only 1 connection to your openfiler)

The ubuntu server mounts the samba share and writes the back-ups in it.

Our problem:
The bacula service writes a job file in the samba share, afterwards that service tries to execute the file but it doesn't work due to the file permissions. If we chmod 777 the file, and re-execute the back-up job, it works.
So, when the file is created, it should be created with specific file permissions so we can execute it afterwards. This is the part where we fail to succeed.

Do any of you have the solution?


Thanks in advance!

Greets
Timothy

---

### Post by albandy on 2013-03-04
You can mount samba with execution permissions as default.
in the option parameter add exec,fmask=755

---

### Post by Timothy271 on 2013-03-04
Hi

Thanks for your reply
unfortunately it didn't solve our problem. It's actually the baculla service who should make sure that the file he is writing has the right permissions to execute it, by itself, later on...
Do you have any other ideas? 

Thanks

Timothy

---

### Post by chris112233 on 2013-03-04
Please have a look to the following options (names copied from swat)

create mask    
force create mode    
security mask    
force security mode    
directory mask    
force directory mode    
directory security mask    
force directory security mode

---

