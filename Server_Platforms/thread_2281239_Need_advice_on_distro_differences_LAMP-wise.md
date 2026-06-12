---
title: "Need advice on distro differences LAMP-wise"
date: 2015-06-05
forum: Server Platforms
---

### Post by papakota on 2015-06-05
Hello!
I've got Ubuntu Desktop 14.04 and I plan to install LAMP on it. One of  my friends (he uses SUSE) has this nice video course here: LinuxCBT  SLES-10 Edition
My question is if I can borrow and follow along its lessons in regards  to configuring (NOT installing -- that I would do myself) Apache  directives, change Apache's config files etc.
That's the main thing that interests me, but in your answer you can also  touch other aspects that you see as relevant to my question.
Thx!

---

### Post by SeijiSensei on 2015-06-06
Apache's configuration files will have the same syntax regardless of the distribution you choose.  However the location of those files varies from distribution to distribution.  On Debian/Ubuntu they reside in /etc/apache2, while on RedHat/CentOS they are in /etc/httpd.  Moreover Debian has its own system for managing virtual hosts, the /etc/apache2/sites-available/ and /sites-enabled/ directories.  RH-flavored distributions have none of that.  Starting with 14.04 Ubuntu now uses /var/www/html as the location for the default site as RedHat has always done.  Before that the default site directory on Debian/Ubuntu was just /var/www.

I haven't looked at SuSE for a very long time now.  Last I saw it was closer to RedHat than Debian.

---

### Post by tgalati4 on 2015-06-06
You could install SUSE on a spare machine and follow the tutorials.  Then search for a LAMP tutorial for Ubuntu and follow that.  I like to use *tasksel* for installing LAMP, but there are several ways to do it.  If you want to run a web server on Ubuntu, then focus on Ubuntu tutorials, otherwise you will get hopelessly confused.  SeijiSensei gave some of the differences, but a big part of maintaining a website is maintaining the underlying server, and there are several differences between SUSE and Ubuntu.  So focus on what you want to learn and study RedHat/Centos or SUSE if you plan to run those operating systems.

---

### Post by papakota on 2015-06-06
Thank you all for trying to help! Okay, well I'll do my best not to lose my horizons with both Ubuntu and SLES. And what worries me a little is that they use Apache 2.2 in there and I'm  gonna use a current version which is 2.4 What do you think of that?

---

### Post by SeijiSensei on 2015-06-06
There are so many tutorials about installing and configuring LAMP that I wouldn't tie myself to a distribution just because you found a tutorial you liked.  Ubuntu's documentation is pretty good: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and [https://help.ubuntu.com/14.04/serverguide/](https://help.ubuntu.com/14.04/serverguide/).  Apache 2.4 is somewhat different from 2.2, and I wouldn't get invested in the older version.  

Linode has pretty solid documentation for a variety of Linux distributions: [https://www.linode.com/docs/websites](https://www.linode.com/docs/websites)

---

