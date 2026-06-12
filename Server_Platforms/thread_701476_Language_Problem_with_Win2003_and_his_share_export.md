---
title: "Language Problem with Win2003 and his share exported to Ubuntu over NFS"
date: 2008-02-19
forum: Server Platforms
---

### Post by shadowmaster79 on 2008-02-19
Hi, 

i have one special problem....

I'm from czech, Windows in my country uses charset cp1250.
Linux NFS client uses UTF-8 for mounting.

People from Windows team have me exportet Directory over NFS  and i have succesfuly mounted it

Problem is now with this charset cp1250. Linux convert chars without special signs....

Now look my system so:

Windows2003 - cp1250 ->
Linux mount client - UTF-8 ->
system terminal - UTF-8

People from Rusia understand my :) 

Have everywhere any idea what now?

I have read any ideas with recompiling nfs client.... but that come me to hard....

It is posible to modify char table of UTF-8 for correct char?

Please help.....

---

### Post by shadowmaster79 on 2008-02-19
I need only view filenames with correct chars.....
nfs share is form me only in read state....

---

