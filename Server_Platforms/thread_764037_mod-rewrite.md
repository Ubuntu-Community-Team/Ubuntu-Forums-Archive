---
title: "mod-rewrite"
date: 2008-04-23
forum: Server Platforms
---

### Post by leg on 2008-04-23
Do I have to do anything to turn on mod-rewrite for apache. I can't seem to find it in synaptic and I have a problem that suggests it may not be on. 

[edit]
Ok I have found the mod-enabled and available folder so the question becomes how do I turn rewrite on. I am assuming it is something similar to the a2ensite format of command but I do not know it.

---

### Post by bluefrog on 2008-04-23
sudo a2enmod rewrite

restart/reload apache

---

### Post by leg on 2008-04-23
Thankyou very much. By the way how many of these types of commands are there and where can I reference them. I am not used to admining apache this way as I have been doing it in a more manual way until fairly recently and I should learn the Ubuntu way now really.

---

### Post by bluefrog on 2008-04-23
man a2enmod   says it all, especially the FILES section

you may need to install non present modules with apt-get/synaptic

---

### Post by leg on 2008-04-23
yeah but what I meant was there is a2ensite, a2enmod and their disable counterparts are there any other commands of the a2en format.

---

### Post by leg on 2008-04-25
I am still having trouble getting this to work. I have run the a2enmod rewrite command and then restarted the server but I am still having the same problem. I have a drupal site that I am trying to enable clean urls for but the test for it does not pass. Any ideas?

---

### Post by leg on 2008-04-25
Sorted this out now and the information I needed is [here]("http://drupal.org/node/134439") just in case anyone else wants to know.

---

### Post by mattbytes on 2008-04-27
Wow...I went through a similar issue.  This document helps too:

[https://help.ubuntu.com/community/forum/server/apache2/SSL?highlight=%28ssl%29](https://help.ubuntu.com/community/forum/server/apache2/SSL?highlight=%28ssl%29)

---

