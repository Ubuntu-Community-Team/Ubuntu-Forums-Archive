---
title: "Encrypted directory for Apache, inside /var/www/"
date: 2010-12-30
forum: Server Platforms
---

### Post by pmla on 2010-12-30
Have 1 crazy question.
As anyone tried to have an encrypted directory inside /var/www/mydomain(encrypted)/subdirectories(also encrypted) ?

So the idea would be to manually mount an encrypted directory (password protected inside /var/www/ to be used by Apache and associated with a domain. So that domain only runs if the directory is mounted.

Apache config /host files would have to be modified to reflect the base directory of the domain.

What would be the best way to achieve this? maybe truecrypt?
Would this affect in a great deal the R/w speed and therefore be slow for the users when they are visiting the website with their browsers?

Interesting stuff, maybe someone already tried... Comments please.

---

### Post by James78 on 2010-12-30
I found this guide here.
[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

---

### Post by pmla on 2010-12-30
Thanks for the link. Encrypting a directory is not hard.

My questions are regarding encryption and apache?!

---

### Post by James78 on 2010-12-31
Well, first you encrypt the directory with the link I gave you, then have it setup to automatically decrypt it upon system bootup or whatever. Simple enough right?

Anyways though, it's not really possible to do this the way you'd like. For example, there's no way to have a domain only run if the directory is mounted (unless you want to get into the domain of using complex shell scripts and programs to complete your task); and yes, the rw speed would most likely be at least a little slower, although how much remains to be determined.

It shouldn't be much of a problem if you have permissions setup correctly. I have my websites setup like, /home/user/public_html, and who has permissions to access /home/user is only user and the users group (drwxr-x---). Using this setup no one but the user himself, and root, can read their files. Now, how would Apache have read access to the directory then? Simple! Add www-data to your users group, which would fall in the drwx_**r**-**x**_--- block, thus read only access.

---

