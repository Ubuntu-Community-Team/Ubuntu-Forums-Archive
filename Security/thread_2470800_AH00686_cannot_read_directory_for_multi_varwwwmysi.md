---
title: "AH00686: cannot read directory for multi: /var/www/mysite/web/"
date: 2022-01-12
forum: Security
---

### Post by konkoutr on 2022-01-12
I have a problem. I have ispconfig and i have a lot of sites. If i make from beginning the joomla installation, the site works fine. When i moved 6 sites from another server, the 3 of them works fine but the other 3 i get an empty page with the word error. I try to search the solution but i didnt find anything. Only that perhaps it must be from apache2/php.
I see the error log and the error that says there is:
[Mon Jan 10 14:38:08.064460 2022] [negotiation:error] [pid 3501998] (13)Permission denied: [client myiport] AH00686: cannot read directory for multi: /var/www/mysite/web/


I have done some changes to .htaccess and php.ini but neither worked. Also the permissions are the same at the folders that the sites are working and the sites that arent working.
Ubuntu version is 20.04.3.


Thank you in advance

---

