---
title: "Install suPHP"
date: 2013-05-21
forum: Server Platforms
---

### Post by shaquille110 on 2013-05-21
Hi there.

I just installed LMAP using Tasksel than followed the instructions on this site [http://internetpartner.info/en/ubuntu/88-ubuntu-suphp-how-to-install.html](http://internetpartner.info/en/ubuntu/88-ubuntu-suphp-how-to-install.html) to install suPHP. I followed the instructions than at the end I realised that they arin't complete. After re-enabling suphp, I noticed that php doesn't work at all on my site, however it isn't a production site so not big of  loss.

What do I do now to completely setup suPHP?

I'm using Ubuntu Server 12.04.2 LTS 64BIT

---

### Post by DJ_Max on 2013-05-21
What do you mean by "doesn't work at all"?

What do your logs say?

---

### Post by shaquille110 on 2013-05-21
> **DJ_Max said:**
> What do you mean by "doesn't work at all"?

What do your logs say?

I'm getting Internal Server Error 500 when going to a .php document. The code is correct cause all I have is <?php phpinfo(); ?> in a file. If I go to access Wordpress same 500 error!

---

### Post by linuxtechguy on 2013-05-21
So look in the error log. Stop trying to guess what is wrong.

---

### Post by shaquille110 on 2013-05-21
The only error log I know of is Apache and its only showing when I last restart apache and installed! I made a deliberate error and it was saved to the log

---

