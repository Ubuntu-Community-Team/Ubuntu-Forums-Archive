---
title: "Uninstall Sendmail"
date: 2008-05-22
forum: Server Platforms
---

### Post by Mech13 on 2008-05-22
How do i compleatly uninstall Sendmail from my system?

What should i use that is a bit easier to use for a n00b :)?

---

### Post by turinglabs on 2008-05-22
You don't say what release you are using, but Postfix is the default in 8.04. If you haven't done anything, you probably have it installed already. Just 'sudo apt-get install postfix', it will tell you if it's installed already, or install it for you. You can only have one mail server installed at any given time, so this will remove sendmail for you at the same time it installs Postfix. Exim is also available; personally I find Postfix easier to configure, but both work just fine. See these links for more info:

[https://help.ubuntu.com/8.04/serverguide/C/postfix.html]("https://help.ubuntu.com/8.04/serverguide/C/postfix.html")
[https://help.ubuntu.com/8.04/serverguide/C/exim4.html]("https://help.ubuntu.com/8.04/serverguide/C/exim4.html")

---

