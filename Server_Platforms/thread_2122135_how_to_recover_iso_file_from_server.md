---
title: "how to recover iso file from server?"
date: 2013-03-04
forum: Server Platforms
---

### Post by asteriks on 2013-03-04
Hi, I am interested if I deleted downloaded **iso** files from USB, how to udelete it, to recover it? 

I think it is the same like when we use recovery of file at server, therefore I ask in this section + most of this recovery software are working in terminal. for example:

**scalpel** has no iso files in configuration,
I tried **foremost** but no success (sudo foremost -t iso -i /dev/sdb -o /home/ubuntu/Desktop/recovery).

I don't want to recover other files because it would take very long + I don't need them, I need only iso files.

any recommendation?
how would you recover deleted iso file from server?

---

### Post by thnewguy on 2013-03-04
The photorec program would probably recover an ISO. You can tell photorec which file types you want to recover so it doesn't grab additional files you don't want. It's part of the "testdisk" package in the Ubuntu repositories.

---

