---
title: "how to change default apache root directory"
date: 2009-07-08
forum: Server Platforms
---

### Post by firsttimeuser on 2009-07-08
i want to change the default server home dir to /array/html, but it appears that apache2 won't take it after I change the serverroot in apache2.conf and reloaded.

#ServerRoot "/etc/apache2"
ServerRoot "/array/html"

Can anyone tell me beside this argument, what else should I change?

i remember in apache1.3 changing this will do the trick.

---

### Post by credobyte on 2009-07-08
If I'm not wrong, you should be able to change your default www directory in [COLOR=Blue]/etc/apache2/sites-available/default[/COLOR] !

---

### Post by firsttimeuser on 2009-07-08
thanks a lot man! it works!

Now i can deal with the real task, no need to mess around apache anymore.

---

