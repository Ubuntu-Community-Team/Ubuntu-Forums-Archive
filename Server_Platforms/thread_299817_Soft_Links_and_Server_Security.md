---
title: "Soft Links and Server Security"
date: 2006-11-14
forum: Server Platforms
---

### Post by zds on 2006-11-14
Here's a quick question about soft links that I can't find already answered in any forum. Is a soft link a security concern?

Here's the scenario. I have a partition (actually a separate drive) that holds files shared over my local network (samba). I'd like to make one of those folders available remotely via https. 

My understanding of server security is that the best way to do this is to create a separate home directory for apache. In that directory I will place a soft link to the directory in question, with appropriate permissions set on the link and on the target files. The target directory will keep its current permissions.

Am I missing something or is this in line with best practices?

Thanks.

---

### Post by zds on 2006-11-15
Anyone?

---

### Post by zds on 2006-11-20
One final bump. Can anyone please help with some info?

---

