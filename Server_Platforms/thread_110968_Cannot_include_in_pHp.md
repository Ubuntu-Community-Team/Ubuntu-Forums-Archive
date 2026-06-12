---
title: "Cannot include in pHp"
date: 2006-01-01
forum: Server Platforms
---

### Post by Master Magnus on 2006-01-01
**[COLOR="Red"]Solved![/COLOR]** - I didn't fix the permission in the subfolders :)

Hi people

I cannot include another file in pHp. I have just installed Apache, pHp4, MySQL and pHpMyAdmin. When I'm trying to include a file it gives me this message;
> **Warning**: main(style1/common.php): failed to open stream: Permission denied in **/var/www/index.php** on line **12**

**Warning**: main(): Failed opening 'style1/common.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in **/var/www/index.php** on line **12**
I have tried several paths in the inclusuion-code (like .:/var/www/style1/common.php, /var/www/style1/common.php, style1/common.php) but it doesn't work.

Answer? Thank you,
Magnus :)

Oh btw, the folder pear doesn't exist in share if that helps.

---

