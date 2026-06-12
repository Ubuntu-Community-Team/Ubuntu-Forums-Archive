---
title: "clearlooks engine backport"
date: 2005-12-07
forum: Ubuntu Backports
---

### Post by shidai.liu on 2005-12-07
Hi guys,

clearlooks in dapper has some new features. I'd like to see them available to breezy. Thanks for backporting.

---

### Post by dexae on 2005-12-07
[http://ubuntuforums.org/showthread.php?t=89056&page=3](http://ubuntuforums.org/showthread.php?t=89056&page=3) Here you have a .deb with the new clearlooks

---

### Post by shidai.liu on 2005-12-08
not my point.

---

### Post by MetalMusicAddict on 2005-12-08
You should have added your point to the above post.

---

### Post by arpunk on 2005-12-08
Well, i think he wants the new clearlooks in the backports repository, am i wrong? :O

---

### Post by fosk on 2005-12-13
[QUOTE=arpunk]Well, i think he wants the new clearlooks in the backports repository, am i wrong? :O[/QUOTE]
Yes, at least i also understood that...

Is it posible to backport the new clearlooks engine??
or has it a lot of dependencies that make it difficult to backport??

Thanks a lot guys!

PS: I prefer to update from backports repositories too. But i guess that i can also try to install the .deb from the other forum thread!!!

---

### Post by Kuolio on 2005-12-13
Yes please, do backport new clearlooks engine if possible.

---

### Post by Confuse on 2005-12-13
[QUOTE=shidai.liu]Hi guys,

clearlooks in dapper has some new features. I'd like to see them available to breezy. Thanks for backporting.[/QUOTE]

Whats new?

---

### Post by Jengu on 2005-12-14
The new clearlooks has some really nice animations :)

---

### Post by Confuse on 2005-12-15
Any slowdowns? And how do we revert back to it if we have any problems?

---

### Post by pecanov on 2005-12-16
If it is (and I think it is) clearlooks-cairo, it's actually faster than the current one in breezy.
I've been using it from CVS from quite some time.

Off course, it is still unfinnished. The borders around text boxes are missing, and until recently, it had a big problem with displaying Evolution calendar component. This has been fixed in CVS but I am not sure about Dapper.

---

### Post by shidai.liu on 2005-12-23
Seems that they consider clearlooks engine a lib and by the rule shouldn't be backported. If you want to use the engine, you need to compile yourself.

---

