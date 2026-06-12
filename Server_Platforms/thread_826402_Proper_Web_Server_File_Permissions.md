---
title: "Proper Web Server File Permissions"
date: 2008-06-11
forum: Server Platforms
---

### Post by JameoPotato on 2008-06-11
Hi,
I beginning to build my site that I am hosting as well and I was wondering what the typical permissions set-up would be.

I have a php script that calls on the txt file that I DO NOT want to be viewable to public.

I have tried a variety of settings from setting www-data as the owner of the file to setting it as part of a group that edits the file, but it seems whenever I get the script permission, I get public permission.

Currently my set up is this:
Apache runs under user: www-data (nothing new)
It is part of a group: www-editors
The restricted file(and the folder it is in) is set to: 770, owner is jameo (my local user) and group is www-editors
My local user is also a part of this group. 

Currently I cannot browse to the file (good) and I get this PHP error when running the site:
```
Warning: fopen(*filename*) [function.fopen]: failed to open stream: Permission denied in *file running script* on line 5
```

So that was my best guess as to a secure set up but it still doesn't work.

Should the user "www-data" ever be given group or superior permissions?

---

### Post by molotov00 on 2008-06-11
Typically what people do is put the file outside of /var/www and make it readable by www-data.

---

### Post by JameoPotato on 2008-06-11
Wow... seems so simple now.
That works perfectly.

Thank-you

---

### Post by molotov00 on 2008-06-11
Glad I could help. ;)

---

