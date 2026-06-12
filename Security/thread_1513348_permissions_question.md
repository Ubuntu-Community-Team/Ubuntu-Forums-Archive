---
title: "permissions question"
date: 2010-06-19
forum: Security
---

### Post by methodtwo on 2010-06-19
Hi
This is something i noticed on my mac.However i is not a mac question but a permissions question.I didn't get any responses at the mac forums.So the example comes from the mac but i asked the question incase anyone could tell me if i've got anything to worry about.
I have the files twpol.txt and twcfg.txt, in the root owned directory tripwire, i have permissions thus:
-rw-r----- 2 root admin 563 26 Apr 19:09 twcfg.txt
-rw-r----- 2 root admin 15148 9 May 19:09 twpol.txt
The permissions for /opt/local/etc/tripwire are:
drwxr-x--- 9 root admin 306 9 May 19:42 
The permissions of the parent directory(/opt/local/etc), however, are:
drwxr-xr-x 5 root admin 170 26 Apr 19:09 .
The permissions for /opt/local and /opt are the same as for /opt/local/etc(which is the last output from ls -l that i pasted in)
I'm worried because i was able to open twpol.txt and twcfg.txt with nano as a normal user.Is this because of the permissions of the parent directories?
Also i couldn't execute tripwire as a normal user but it had an execute bit on in the long file listing.Is this because i didn't have permission to read the database file?.I suppose it was.I just need to be clear about BSD permissions rules and couldn't find anything on this when i googled it!.

---

### Post by rookcifer on 2010-06-19
It's because the directories and files are all owned by the "admin" group of which your user is a member of.  You can change the group using the "chgrp" command.  Remember, the UNIX file permissions are UGO (user, group, other).  If a user is a member of the group that is listed as the "group" owner, that user will have access. 

In any case, if Tripwire set the permissions that way, I wouldn't mess with them unless you have a good reason to.

---

### Post by methodtwo on 2010-06-19
Well i looked in /etc/group on the mac and there was no normal username next to the admin group. Here is the relevant output of cat /etc/group:

```
admin:*:80:root
```

So my normal user isn't in that group.I forgot to mention this in the original post, sorry
Thank you for your time
regards methodtwo

---

### Post by methodtwo on 2010-06-19
Oh i've just done:
```
$groups
```
and it said i am in admin.The worry arose in the first place because i looked in /etc/group and wasn't listed under admin.No more worries though as the groups command said i'm in admin.Thank you for your time...regards methodtwo

---

