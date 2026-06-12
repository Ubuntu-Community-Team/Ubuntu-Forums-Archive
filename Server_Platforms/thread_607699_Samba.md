---
title: "Samba"
date: 2007-11-09
forum: Server Platforms
---

### Post by il.Boni on 2007-11-09
I got this problem with a samba shared filesystem. 
I mount it without problem and using an xterm I navigate trough the folder, making folder, saving files ecc. 
But for some reason it has strange behaviour. 
For example with vi editor I can create and save a file, move it ecc,, but if I try to do the same with gedit for example I got an error of permissions. The same file created with the vi and xterm! But if I try to edit the same file with eclipse IT WORKS!

and more. 
I use svn. I can't use the svn command or a svn client ( rapidSVN ) because I got the same problem of permissions, but If I mount the same samba filesystem under Windows ( sorry :-) ) and I try to do the same with a svn client ( tortoise ),  again IT WORKS!

I can't understand...

someone has an idea?

thank's

---

### Post by il.Boni on 2007-11-09
Another strange behaviour 
 I can  create a new file with gedit and it is correctly saved with the samba mapped user. But if I try to continue the editing and try to save again I don't have the permission to do it and a new file called .gedit-xxxx is created but with a "olduser" named use owner.

?????

---

### Post by HermanAB on 2007-11-09
Hmm, what version of Samba are you using?  Maybe you need to upgrade, since there has been some regression at some point.

---

