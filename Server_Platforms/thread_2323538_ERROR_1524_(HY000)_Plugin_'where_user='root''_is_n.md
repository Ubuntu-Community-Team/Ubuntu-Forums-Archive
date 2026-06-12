---
title: "ERROR 1524 (HY000): Plugin 'where user='root'' is not loaded"
date: 2016-05-06
forum: Server Platforms
---

### Post by cesar23 on 2016-05-06
Hi,

I was following these instructions to be able to log in to mysql...

[COLOR=#000000]shell$ sudo mysql -u root[/COLOR]

[COLOR=#000000][mysql] use mysql;[/COLOR]
[COLOR=#000000][mysql] update user set plugin='' where User='root';[/COLOR]
[COLOR=#000000][mysql] flush privileges;[/COLOR]
[COLOR=#000000][mysql] \q
[/COLOR]
But I entered the second command incorrectly, typing

update user set plugin=" whee user='root' ";

So now I get the error

ERROR 1524 (HY000): Plugin 'where user='root'' is not loaded

when I try to log in to mysql in any way. Stupid mistake (darn dyslexia).

Could someone help me out to fix this?

Thanks!

---

### Post by cesar23 on 2016-05-06
I decided to completely uninstall and reinstall mysql, so issue is solved now.

---

