---
title: "Apache 2 question + WebDAV"
date: 2009-01-03
forum: Server Platforms
---

### Post by freebeer on 2009-01-03
I've set up Apache2 on my 8.10 box.  So far everything appears to be working normally, however I noticed that /var/www is owned by root, as opposed to www-data like it was when I set up Apache2 on my 6.04 box.  Was this changed for some reason in later versions?  I note that I don't have a www-data user on the 8.10 box, and if I recall correctly, one was set up on my 6.04 box when I installed Apache2.  (both boxes are desktop versions if that matters any)

Second question.  I'm trying to set up WebDav on this 8.10 box.  I followed these instructions: [http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622](http://www.digital-arcanist.com/sanctum/article.php?story=20070427101250622)

I think everything I did went fine.  The only difference I did compared to the listed instructions was to ignore the commands to chown the files/folders to www-data (due to the aforementioned root ownership, I just left ownership as root).  Now I can access (from my LAN) the WebDav'ed folder, but I'm not getting challenged with a password.  Shouldn't I be?

Any light you can shed on the matter would be helpful.

Thanks!

---

### Post by freebeer on 2009-01-06
*bump*

Anyone?

---

### Post by eatberrys on 2009-01-06
i am always looking for things to do. If You would like tomaro i can try setting it up on 8.10 and see what happens.

---

