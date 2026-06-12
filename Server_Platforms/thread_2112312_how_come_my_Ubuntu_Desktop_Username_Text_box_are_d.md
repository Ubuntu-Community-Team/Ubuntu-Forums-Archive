---
title: "how come my Ubuntu Desktop Username Text box are disable?"
date: 2013-02-04
forum: Server Platforms
---

### Post by chinye2020 on 2013-02-04
[IMG]http://img16.imageshack.us/img16/5597/61963113.jpg[/IMG][IMG]http://imageshack.us/photo/my-images/16/61963113.jpg/[/IMG]

how come my Ubuntu Desktop Username Text box are disable?
i m using Root account to login,but the username text box are not available?
but still can use SSH puty to login.

---

### Post by chinye2020 on 2013-02-04
Last time i able to enter the username,where is the username text box?

---

### Post by chinye2020 on 2013-02-05
problem solved,

just hit the command
sudo sh -c 'echo "greeter-show-manual-login=true" >> /etc/lightdm/lightdm.conf'

---

