---
title: "Nginx, PHP MySQL APC - white screen with includes."
date: 2010-07-25
forum: Server Platforms
---

### Post by pearce on 2010-07-25
Okay I've spent the last two hours setting up a Ubuntu server, with Nginx (granted, I customized it's configuration file a little, between the three documents I read and what I thought was right), PHP-FPM for PHP to run, PHP and MySQL. I also threw APC in there.

So all was dandy, I created my virtual host, serves nicely. Everyones happy. Put WordPress into a directory called 'wordpress' - works fine. Didn't set it up. Moved the files into the root directory for the domain and BAM. White pages ahoy.

I looked into the error log and it says that the wordpress install at / is calling on files at /wordpress. - but there's nothing in the code to make it to do that, it's just running 

require_once(wp-app.php); 
or similar, which the server is reenterpreting.

I'm doing my best to troubleshoot it by myself but I was curious to see if anyone had run into similar experiences and could share a few words of wisdom. I can share the config files but it's mostly pretty standard - and its worth noting that a index.php in the root, with phpinfo() runs just fine.

Thanks guys!

---

