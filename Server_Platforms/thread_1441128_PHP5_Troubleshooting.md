---
title: "PHP5 Troubleshooting"
date: 2010-03-28
forum: Server Platforms
---

### Post by HollowSteps on 2010-03-28
After many a google, I haven't found anything reliable about my problem. I had installed apache2/subversion/ubuntu in order to set up a source control server for a project that a large group of people were going to work on. The subversion end is fine, but because of my single-minded focus, I did not do a LAMP install previously.

Now we're talking about needing a forum, which I could oh-so-graciously host :). I tried to do a straight LAMP install, hoping for the best, but whenever I try to reach the test.php file that I put on the server, I am asked to download it.

Besides subversion working correctly and the index.html file at the folder root, I'm quite sure apache is serving files from that directory correctly (I browsed to it through the ip). But I tried enabling the php5 module and troubleshooting documentation seems scarce. Can anyone help me figure out this issue?

EDIT: Despite having done the subversion install twice, I'd rather not purge apache if I can avoid it.

---

### Post by aklo on 2010-03-28
Have you tried following a step by step guide? 
I also had problems with my install but i'm not sure which guide i read...i simply followed it step by step from installing apache first then mysql and finally php5...

I'm not sure if there is a full package which takes care of everything with no configuration from your side...but for me i remembered editing the php config files...it was a pain considering i don't even know where they are kept...but somehow i got it working...

by default i think the place to store your .php files should be /var/www

Hope the below links can help you.

[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[https://help.ubuntu.com/8.10/serverguide/C/php5.html](https://help.ubuntu.com/8.10/serverguide/C/php5.html)

---

### Post by HollowSteps on 2010-03-28
Yeah, I got messages like '0 installed 0 updated (etc)' when I tried to install the libapache php mod file, and when I try to enable it using command line it says that it's already enabled! Very confusing.

---

### Post by HollowSteps on 2010-03-28
Uh, not sure what happened but I just refreshed the page a couple of minutes ago and it worked! I hadn't done anything in a while. Very strange!

---

