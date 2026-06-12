---
title: "Files owned by &quot;nobody&quot; dangerous?"
date: 2011-05-21
forum: Security
---

### Post by Dave_L on 2011-05-21
From [this article](http://www.net-security.org/article.php?id=92):

> The other issue are files which don't belong to anyone, or don't belong to a group. These are also dangerous, as they provide more ways to manipulate with your system. Also, an unowned file may be a signal indicating an intruder on your system. Let's find them:

find / -nouser -o -nogroup

Nothing? Heh, that's exactly what we expect! And if you find any, feel free to change the ownership of the file to any user you want, or to delete it. If you want to change the ownership you might want to check out the command 'chown', of course by typing 'man'chown'.

How do these files "provide more ways to manipulate your system"?

---

### Post by sanderd17 on 2011-05-21
files owned by nobody can be edited by anyone (like all files in Windows :-D) so that's a problem.

Since anyone can edit it, if you find those files, if should not be a problem to delete it.

I don't know those files, but maybe they are changed by accident. In that case, you may not remove them.

---

### Post by Morbius1 on 2011-05-21
Files owned by "nobody" can be edited by no one locally except root.

"nobody" is a legitimate user on your system:
```
id nobody
```The question is how did it get there ?

Do you have a samba share on your system that accepts guest access? When  the remote user adds a file it will save as owner : group = nobody :  nogroup. No one else on your local system can edit the file since it also saves with permissions = 644.

---

