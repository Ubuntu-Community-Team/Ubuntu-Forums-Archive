---
title: "GUTSY apache userdir permitions and some .conf questions"
date: 2008-02-20
forum: Server Platforms
---

### Post by pedrotuga on 2008-02-20
I want to enable apache userdirs.
I installed the lampstack using taskel on gutsy fresh installation.
I had some mermory that userdirs came enable by default, But aparently they are not...

Which permitions should my /home/user directory have? What about /home/user/public_html ?

whats the apache configuration file...

'whereis apache2.conf' returned like 5 or 6 results.

---

### Post by pedrotuga on 2008-02-20
I looked around a bit better and i found the answer.

There is a proper way to install apache modules on debian and keep things tidy.

man a2enmod

cheers

---

