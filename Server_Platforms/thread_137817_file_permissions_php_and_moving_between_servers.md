---
title: "file permissions php and moving between servers"
date: 2006-02-28
forum: Server Platforms
---

### Post by gmclachl on 2006-02-28
Hi,
       I have moved a directory containing sub directories and PHP files from my desktop (Ubuntu) to one of our servers. However When i try to view the site I get forbidden errors or errors saying couldn't open an include as permission was denied.

 Apache error logs show nothing, i have even tried chmoding the files to 755 to see if that fixed it but nope, nothing seems to work. Any suggestions.
 I should have added is to create the folder in /var/www/  i just sudo mkdir and then chown. 


 Thanks 
G

---

### Post by gmclachl on 2006-03-01
I have walked through everything and I think i have managed to track it down to a group of files. Now all the permissions look ok, but I notice that when i ssh into the box one of the files seems to highlighted with a bold font. A silly question but, does this mean anything?

 George

---

### Post by LordHunter317 on 2006-03-01
If you looked at ls -l, it would surely tell you why.

---

### Post by gmclachl on 2006-03-01
I solved it in the end. It wasn't a file permissions problem, but a PHP problem, and an annoying one at that. 

 George

---

