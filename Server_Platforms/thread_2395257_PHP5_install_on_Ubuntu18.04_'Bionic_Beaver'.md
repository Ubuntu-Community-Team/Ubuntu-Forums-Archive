---
title: "PHP5 install on Ubuntu18.04 'Bionic Beaver'"
date: 2018-06-29
forum: Server Platforms
---

### Post by ligustri on 2018-06-29
Hi,

I did try to install PHP5.5.12 on Ubuntu 18.04 from source package. It failed because of libphp5.so or libapache2-mod-php5 is missing. I tried to install libapache2-mod-php5, but it did not success. 

I'm not able to work with PHP7 because the web solution I'm going to improve is made with PHP5 and do not work with PHP7. Is it possible to make PHP5.x.x to work with Ubuntu 18.04 in the first place or should I use an older version of Ubuntu, for example Ubuntu 14 'Utopic Unicorn' ?

---

### Post by cariboo on 2018-06-29
Moved here for better help.

---

### Post by ligustri on 2018-06-29
Hi,

I did try to install PHP5.5.12 on Ubuntu 18.04 from source package. It failed because of libphp5.so or libapache2-mod-php5 is missing. I tried to install libapache2-mod-php5, but it did not success. 

I'm not able to work with PHP7 because the web solution I'm going to improve is made with PHP5 and do not work with PHP7. Is it possible to make PHP5.x.x to work with Ubuntu 18.04 in the first place or should I use an older version of Ubuntu, for example Ubuntu 14 'Utopic Unicorn' ?

---

### Post by Holger_Gehrke on 2018-06-29
The last supported Ubuntu which still has PHP5 is 14.04 LTS, support for which will end next year.

Your first order of business in improving your "web solution" -- in order to stop it from becoming a "web problem" -- should be to find out why it won't work with modern versions of PHP and fix that. Finding hosting that still offers php5.x is difficult; for in-house deployment you would in the long run end up having to compile PHP -- and possibly Apache -- from source, which is no fun (been there, done that, have the {mental} scars to prove it). Instructions for that can be found on php.net and httpd.apache.org 

Holger

---

### Post by ligustri on 2018-06-29
Thanks for answer! I thought something the same...

---

### Post by cariboo on 2018-06-29
Merged duplicate threads.

---

### Post by SeijiSensei on 2018-06-30
CentOS 6, which will receive security updates and critical bug-fix support until November, 2020, uses PHP 5.3.3.

I haven't compiled PHP with apache for a long time now. It wasn't that hard the third or fourth time around!

---

### Post by LHammonds on 2018-07-02
I have not installed PHP5 on Ubuntu Server 18.04 and nor do I have a need to do so.  But I did need PHP5 installed on Ubuntu Server 16.04 for a project management site.  I documented [how I configured the 16.04 server to run PHP5](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=222#p510) on my website and the same steps "might" work for 18.04.

**EDIT:** Added URL

LHammonds

---

