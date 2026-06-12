---
title: "home folder encryption"
date: 2010-05-17
forum: Security
---

### Post by SoFl W on 2010-05-17
If I wanted to transfer a home folder that was encrypted to another ubuntu computer could I?

If I had a separate home partition that was encrypted, but I wanted to upgrade ubuntu to the latest version by doing a clean install is there an easy way so that I can still read the data encrypted with the old version?

---

### Post by SoFl W on 2010-05-18
question bump

---

### Post by bodhi.zazen on 2010-05-18
> **SoFl W said:**
> If I wanted to transfer a home folder that was encrypted to another ubuntu computer could I?

Of course. I assume you are wanting to decrypt it on the target computer ?

> If I had a separate home partition that was encrypted, but I wanted to upgrade ubuntu to the latest version by doing a clean install is there an easy way so that I can still read the data encrypted with the old version?

Define "easy".

What encryption are you using , the default encrypted $HOME is ecryptfs.

"Clean install" implies you re-formatted or installed over your old home, and this would make it hard to access, encrypted or not :lolflag:

To answer your question, the easy way is to log in to your system , decrypt home, and transfer the un encrypted data either you your second install or back up your data and restore it on your fresh install.

If you want to manage the encryption see :

[http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

### Post by SoFl W on 2010-05-18
> **bodhi.zazen said:**
> 
"Clean install" implies you re-formatted or installed over your old home, and this would make it hard to access, encrypted or not 

I have a separate home partition so I wouldn't loose the data.  I figured I would have to save/copy all the data elsewhere and then put it in the new home of a clean installs partition.   
I was hoping there would be a quicker way and have been so busy/tired lately I thought MAYBE I was over looking something.  That is why I asked.... but I guess I already knew the answer!

---

### Post by uRock on 2010-05-18
I use the encrypted private folder which works the same as an encrypted home. As long as you use the same computer and account names, you will be signed into your encrypted home when you log in.

---

### Post by SoFl W on 2010-05-19
I figured if I did a new install of a new version they keys would change and I would loose the ability to decrypt  the data. 

My answer is when upgrading, save the unencrypted data elsewhere, do a new install and then transfer the data back.

---

