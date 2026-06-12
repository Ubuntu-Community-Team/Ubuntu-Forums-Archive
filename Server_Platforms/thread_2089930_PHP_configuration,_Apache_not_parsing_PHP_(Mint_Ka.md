---
title: "PHP configuration, Apache not parsing PHP (Mint Katya)"
date: 2012-11-30
forum: Server Platforms
---

### Post by ranser on 2012-11-30
Turns out it was just some mis-configuration with my browser.
But good thing out of it is I refreshened my memory. :)

Hi,

One year back I configured LAMP to try and learn some web design/programming. After install I had a problem with Apache not parsing PHP and after much fiddling found a solution with some configuration done. The problem is I forgot what was the logic behind it. Only remember it was something with Apache listening on the wrong port or something. My /etc/apache2/httpd.conf contains only these lines:
```
ServerName localhost
Listen 88
```

After some updates when trying anything PHP in the browser it offers to download the file and not parsing. 

I would greatly appreciate help in solving this and if possible links to some explanations as to how the whole mechanism works and where are the log files so I can troubleshoot it myself next time.
Sorry for long post.

---

