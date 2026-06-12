---
title: "jeos-10.04??"
date: 2010-05-04
forum: Virtualisation
---

### Post by kuda on 2010-05-04
Hi

we are using few virtual guests like jeos-8.04, this is lts so question is very simple: will cannonical release any kind of jeos-10.04 lts ...?? sorry for stupid question, I have tried google rather much and without success .... TIA k.

---

### Post by YQ002lc2 on 2010-05-07
I was wondering this, too. 
I googled it without success. 
I saw your post and knew that I wasn't alone. 
I went to ubuntu.com and searched jeos.
I came upon the following page:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

You will notice the lines that say: 
Tech Specs - v 8.10 and above:
- Now part of the standard server ISO image.

So I guess the answer is that it's now part of the standard server ISO image.

---

### Post by northwoodmfg on 2010-05-07
I think "Now part of the standard server ISO image" means that it IS part of the standard download. 

At the bottom of the page you referenced it says:

'Download the [server  ISO image]("http://www.ubuntu.com/getubuntu/download"), boot from it, press F4 on the first screen and select  "Install a minimal virtual machine"'

And indeed, I am looking at that F4 menu right now.

---

### Post by kuda on 2010-05-08
OK, thanx for answers, so the problem is kinda solved :-) ... so I hope that when one tries to do kind of version upgrade, it will "jump" to "minimal virtual machine 10.04" ....

---

### Post by stephanhughson on 2010-05-08
I've just upgraded to 10.04 on quite a few JeOS virtual machines (from 9.10).

My personal ones were installed using the vmbuilder script (about 4 of them).
The ones I use at work were installed using the CD as mentioned above (3 of them).

On all, the upgrade went fine. I don't think it actually says "JeOS" anywhere, either before or after the upgrade, but the disk space used is about the same. The upgrade didn't get loads of extra package and turn it into a full install, it's still JeOS as far as I can see.

Hope that helps.

---

