---
title: "PHP 5.3 with FastCgi on Cherokee server."
date: 2010-02-25
forum: Server Platforms
---

### Post by rich97 on 2010-02-25
The title describes the sort of setup I'm trying to achieve, I'm fairly technically minded but I'm not really an expert on server setups.

I have compiled PHP5.3 from source and installed the cherokee server from the Ubuntu repositories.

Now the big problem I'm facing is that cherokee requires php-fcgi, how would I add this on to my compiled php5.3 install?

---

### Post by rich97 on 2010-02-25
Bumpity bump. :popcorn:

---

### Post by CyberJack on 2010-02-26
I don't use php 5.3 yet but I imagine something like this:


Verify that you compiled php with cgi support.
[FONT="Courier New"]php-cgi -v[/FONT] or [FONT="Courier New"]php -v[/FONT]
If you see something like "(cgi-fcgi)" it's ok.

Then use the following guide (not installing php again) to finish the installation
[http://www.howtoforge.com/installing-cherokee-with-php5-and-mysql-support-on-ubuntu-9.10](http://www.howtoforge.com/installing-cherokee-with-php5-and-mysql-support-on-ubuntu-9.10)

Instead of compiling php yourself you can also use the repository from dotdeb. ([www.dotdeb.org](www.dotdeb.org)). It has php5.3.1 and php5.2.12 with all the packages your normal ubuntu install would have (like php5-cgi and php5-cli)

---

