---
title: "Update Screwed PHP Up"
date: 2011-11-11
forum: Server Platforms
---

### Post by xiveira on 2011-11-11
Alright so I just updated Apache2 (and I have no idea where else to ask so I came here, sorry) and according to the Webmin logs it disabled PHP. I restarted the Apache server in hopes that it would pick up on the new PHP5 configuration but it appears to not have worked. I have a forum, a WordPress which for some unknown reason works fine, (wait no it doesn't), a Nova install and a web directory, and while they're pointing to the right location (thus it isn't a VirtualHost issue), they're not loading properly.

I.E. I click on a thread link and it downloads index.php.

So, what *exactly* is wrong, and how do I fix it? Walk me through this I'm kinda new with these things. Running Ubuntu 10.10. I did a search real quick first trying to find it and I didn't come up with anything helpful. :/ Thank you in advance. ... this won't happen every time I update it will it because if it will I'm tempted to never update it again. >>; Also this is a VPS not a server I'm sitting in front of, but I do have shell access.

---

### Post by Bizzaro on 2011-11-13
I also suffered from this update. Ubuntu 11.10. All php is downloaded instead of ran by the PHP interpreter.

---

### Post by SeijiSensei on 2011-11-14
Make sure you have the **libapache2-mod-php5** package installed.

---

### Post by Bizzaro on 2011-11-14
SeijiSensei, is correct. According to my log, libapache2-mod-php5 seems to have been removed by the update. I just installed it again using apt-get and restarted Apache to fix. Strange that it was removed.

---

### Post by SeijiSensei on 2011-11-14
First, see if this bug applies to you: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/330099](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/330099)

If not, perhaps you should [file a bug report at Launchpad]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect").  You'll need to create an account there if you haven't one already.  I'd file the bug, but I've not actually encountered the problem myself (my servers run CentOS).  I only know that a number of other people have reported this problem in the past few months, so I have to think that the erroneous removal of libapache2-mod-php5 is more systematic than the current bug report I cited above would suggest.

---

