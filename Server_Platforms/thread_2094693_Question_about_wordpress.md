---
title: "Question about wordpress"
date: 2012-12-14
forum: Server Platforms
---

### Post by jstarner on 2012-12-14
Hello,

ok i have ubuntu 12.04 server up and running,

i also add cms - wordpress to it.  two questions i have

#1 how to i get my site to goto my wordpress and not striaght to index,html 

#2 i have tried to put some imbeded string in my word press to goto a flash game lie through goodgames but when i put the embeded links onto the page all you see is the code?

Do i need to install flash or something on my server to get it to load up? 
sorry this is the first time on my own server

i have googled and have found nothing.

thanks
j

---

### Post by nothingspecial on 2012-12-14
Changed title to reflect the question.

---

### Post by SeijiSensei on 2012-12-14
1)  Make the DocumentRoot in Apache point to the wordpress directory.  For instance, if the site resides in /var/www and you have WP installed in /wordpress/ below that, then the DocumentRoot should be "/var/www/wordpress" rather than just "/var/www".

2)  You would need to have the actual .flv file to embed a Flash object into a WP site.  Since the game is offsite, just include a link that points to the URL.  Check the box in the Add/Update URL dialog to have it open in a separate window.

---

