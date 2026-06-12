---
title: "Virtual Hosts, Multiple Domains"
date: 2010-12-13
forum: Server Platforms
---

### Post by d3fau1t on 2010-12-13
Hey everybody :D

I purchased several domain names, in the hopes of running multiple websites from the same pc. But then I discovered it was more difficult than I thought!

Is it possible to set up virtual hosts in Apache so that each domain points to a separate folder? For instance, "ubuntustuff.ca" points to "/home/me/ubuntustuff", "myblog.com" points to "/home/me/myblog", etc?

And if so... how??

---

### Post by SeijiSensei on 2010-12-13
[http://ubuntuforums.org/showthread.php?p=10016541](http://ubuntuforums.org/showthread.php?p=10016541)

---

### Post by chrislynch8 on 2010-12-13
As the above link describes you need to look at a VirtualHost of each domain. Then set the Server_Name and DocumentRoot for each of them. Should work a threat

---

### Post by d3fau1t on 2010-12-13
Thanks, guys. I'll give that a try, and let you know how it goes.

---

### Post by d3fau1t on 2010-12-14
I moved two folders to the /var/www/sites folder, each containing all the files for a website I'm trying to set up. So there's two folders, each containing its own website. 

I opened 000-default, deleted everything in the file. Then I copied and pasted the example from the link you sent me, and replaced all of the references to "hello" with the name of one of the website folders (above).I changed ServerRoot to the first domain, and DocumentRoot to the corresponding website folder. Then I did the exact same thing again for the other website, copying the text and replacing with the name of the second website folder in /var/www/sites etc. 

Typing the domain of either website in my web browser takes me to the original "It works!" page.

Am I missing something? :confused:

---

### Post by d3fau1t on 2010-12-14
... then I rebooted, changed the permissions of both website folders to www-data - should I have done that security-wise? - and both sites now work!

Thank you so much!

---

