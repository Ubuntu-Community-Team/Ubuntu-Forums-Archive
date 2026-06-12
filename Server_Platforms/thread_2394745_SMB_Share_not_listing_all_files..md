---
title: "SMB Share not listing all files."
date: 2018-06-20
forum: Server Platforms
---

### Post by seantnichols on 2018-06-20
Hi,

I am running an autofs (CIFS) share to a Mac server (High Sierra) on my Ubuntu 16.04 Server. The directories all mount without error but any directory with greater than 600 files won't list the rest, so I have a directory with around 900 files in it and only can see 600 from the server. What would cause this?

---

### Post by TheFu on 2018-06-20
2 unix systems ... er ... nfs?

---

### Post by cariboo on 2018-06-21
Moved here for better help.

---

### Post by Morbius1 on 2018-06-21
Have you tried adding [COLOR=#0000cd]**noserverino**[/COLOR] to your list of cifs mount options? Um ... actually you [COLOR=#0000cd]_*may*_[/COLOR] need to add [COLOR=#0000cd]**nounix**[/COLOR] to your list as well.

---

