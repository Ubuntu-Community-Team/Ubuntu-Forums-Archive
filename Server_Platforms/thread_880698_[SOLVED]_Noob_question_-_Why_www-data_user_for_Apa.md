---
title: "[SOLVED] Noob question - Why www-data user for Apache's public folder?"
date: 2008-08-05
forum: Server Platforms
---

### Post by Kolipoki on 2008-08-05
Please excuse my partial lack of knowledge on the matter, but I've been reading in some topics in this forum that the /var/www should be chown(ed) to www-data:www-data, because that's the user that Apache has for that purpose. But still it's not quite clear why this change of ownership should be done, other than not being owned by root account.

At the moment I don't have the /var/www chowned to www-data and has been working fine with another user I created just to avoid using root. Should I change ownership for security (or any other) reasons? 

I'm also curious as why the "user:user" format/syntax in this case (with the 2 usernames divided by the colon), because I haven't seen it in any other user examples.

Thanks for your time, most appreciated.

---

### Post by ilrudie on 2008-08-05
read man chown but basically it works like ```
chown <user>:<group>
```Using a seperate user and group is just so that apache doesn't need root privileges to get at the website's code.  It's for security reasons.  I'm not an apache expert but www-data is probably just used by convention to make it easier to share/understand different apache configurations.

---

### Post by StickyStyle on 2008-08-05
> **Kolipoki said:**
> Please excuse my partial lack of knowledge on the matter, but I've been reading in some topics in this forum that the /var/www should be chown(ed) to www-data:www-data, because that's the user that Apache has for that purpose. But still it's not quite clear why this change of ownership should be done, other than not being owned by root account.

At the moment I don't have the /var/www chowned to www-data and has been working fine with another user I created just to avoid using root. Should I change ownership for security (or any other) reasons? 

/var/www should NOT be owned by www-data, it should be owned by root.  If it is owned by www-data and www-data has +rwx on the directory and one of your web applications get compromised there is now the potential for the attacker to take over all of your other sites, or even setup new ones depending on how you have apache configured.

> **Kolipoki said:**
> 
I'm also curious as why the "user:user" format/syntax in this case (with the 2 usernames divided by the colon), because I haven't seen it in any other user examples.


its actually user:group, its just that there is also a group called www-data which is the primary group for the **user** www-data.  It's a shorthand method so you dont have to do a chown then a chgrp.

---

### Post by Kolipoki on 2008-08-05
> **StickyStyle said:**
> /var/www should NOT be owned by www-data, it should be owned by root.  If it is owned by www-data and www-data has +rwx on the directory and one of your web applications get compromised there is now the potential for the attacker to take over all of your other sites, or even setup new ones depending on how you have apache configured.


its actually user:group, its just that there is also a group called www-data which is the primary group for the **user** www-data.  It's a shorthand method so you dont have to do a chown then a chgrp.

Mighty thx guys, Sticky. BTW... be sure I'm doing my homework, got over 250 bookmarks (including the server guide) on the subject of the server edition, in the last month alone, but coming from the Windz environment makes all this like learning to read and write again. K.

---

### Post by Kolipoki on 2008-08-05
I think I should clarify something out of my first line up here in this post. The topics I mentioned in which I saw recomendations to chown www-data:www-data, were actually to /var/www/another_folder, not to /var/www. So that should make a difference on this issue, I guess.

---

### Post by StickyStyle on 2008-08-05
> **Kolipoki said:**
> I think I should clarify something out of my first line up here in this post. The topics I mentioned in which I saw recomendations to chown www-data:www-data, were actually to /var/www/another_folder, not to /var/www. So that should make a difference on this issue, I guess.

That makes a bit of difference ;)

Although personally I have all my web files owned by root and only give www-data write access via the www-data group where it is specifically needed.  Always start off with the most restrictive, then start loosing things up till it works.

---

