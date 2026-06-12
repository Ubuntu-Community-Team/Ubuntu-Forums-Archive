---
title: "Website became unusable after Ubuntu Upgrade."
date: 2020-05-10
forum: Server Platforms
---

### Post by Andreyshel on 2020-05-10
Hello.
After upgrade to 20.04 my test website suddenly stopped working.
**Problem:**
1. Visiting my site homepage gives me a message:
>  The website encountered an unexpected error. Please try again later[COLOR=#000000][FONT=&amp].
2. [/FONT][/COLOR]phpinfo() gives blank page although display_errors variable is set to On in /etc/php/7.4/apache2/php.ini file
[COLOR=#000000][FONT=&amp]
[B]What i have tried:
[/B][/FONT][/COLOR]
1. Upgrade process deleted my php installation. I had to  install php7.4 from repositories.
2. Run systemctl status command for apache2 and mysql(Both running)
3. Run  apachectl -M (php7_module is on the list)

Sounds like everything should work fine, but it is not the case.
Thanks for your ideas.

---

### Post by Andreyshel on 2020-05-10
Problem was that my CMS version wasn`t compatible with php version included in Ubuntu 20.04 repositories.
Update solved problem

---

