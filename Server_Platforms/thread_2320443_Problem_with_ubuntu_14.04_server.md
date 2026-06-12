---
title: "Problem with ubuntu 14.04 server"
date: 2016-04-14
forum: Server Platforms
---

### Post by Ionut_Sandu on 2016-04-14
Hi, i have a problem with my server my mysql server shutdown and when i start it my memory ram si overhigh. Here is a printscreen with my htop. if you need any logs and more information please tel me and please help me beacause my website is down from 3 day ago. If i restart mysql server my website works aprox. 2 minutes and after i received the message "500 internal error".

[ATTACH=CONFIG]268382[/ATTACH]

Thanks.

---

### Post by Graham_Willis on 2016-04-14
Have you checked what is in the database? Tried to go with a database from backup? Error logs from MySQL service can say something. It seems that their location in Ubuntu is /var/log/mysql.err. Checking main MySQL logs, /var/log/mysql.log will also not do any harm. From what you're saying it's almost given that the problem is somehow caused by MySQL server but to check if you observe the same behaviour when only HTML files are in use will be a good idea. BTW, is your site everything what is working on this server?

---

### Post by QIII on 2016-04-14
Please to not cut and paste large images.  Many of our users have slow connections and/or data limitations.  Large images can take a long time to download or may actually cost some users extra money.

Please use the attachment functionality provided by the paperclip button in the menu above the text input box.

Thanks.

---

