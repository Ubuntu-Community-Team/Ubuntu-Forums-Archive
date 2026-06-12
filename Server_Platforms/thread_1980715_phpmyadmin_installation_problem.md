---
title: "phpmyadmin installation problem"
date: 2012-05-15
forum: Server Platforms
---

### Post by trundlenut on 2012-05-15
Just installed phpmyadmin on a fresh install of 12.04 server.  However when I tried to go to the web interface I just got a 404 error.

After a bit of ferreting around I realised that the .conf file (/etc/phpmyadmin/apache.conf) had not been copied to /etc/apache2/conf.d/phpmyadmin.conf.  I did this manually, restarted apache and it all worked as anticipated.

Not sure if this is a bug in the installation package or what and so I'm not sure where I should file a bug report.  Any help on this would be appreciated.

---

### Post by Headfirst on 2012-05-17
Holy smokes am I glad that you made this thread! I was going through configuring my newest frankenstein server w/ a fresh install of 12.04 went through your standard LAMP installation process and when I tried pulling up localhost/phpmyadmin in firefox I was getting a 404 error too. I checked and I also was missing the phpmyadmin.conf file I copied it manually and restarted apache. Everything is running smooth now!

Cheers

---

### Post by trundlenut on 2012-05-17
I have reprodced this in another fresh installation on a separate server (using the same ISO image though).

I wonder if a step/line has been omitted when the installation package was created for 12.04.

Found a bug report for this [here]("https://bugs.launchpad.net/ubuntu/+source/phpmyadmin/+bug/892487?comments=all").

---

