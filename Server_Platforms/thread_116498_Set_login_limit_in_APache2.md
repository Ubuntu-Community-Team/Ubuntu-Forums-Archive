---
title: "Set login limit in APache2 ?"
date: 2006-01-12
forum: Server Platforms
---

### Post by duffydack on 2006-01-12
all i can find is the Maxclient variable to play with in apache2.conf but i have to set it to like 3 (and threadsperchild needs adjusting accordingly) to be able to view my site properly, but really i`d just like it to allow 1 login (has user/pass login enabled on site also) to the site and any more login attempts to be denied 
any way to do this?  must be

---

### Post by LordHunter317 on 2006-01-12
No, there's no way I know of to do waht you want.

And MaxClients doesn't control what you think it does.  Don't play with that.

---

### Post by duffydack on 2006-01-13
shame.  its only a musicindex page that i dont want anymore than 1 using, since it doesnt stream at different bitrates to original file (some of mine are 320 and my upload isnt much better).... nevermind.....  no i dont wanna use ice/shoutcast either, like the musicindex layout better :)

---

