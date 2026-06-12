---
title: "How to add a new server to PhpMyAdmin?"
date: 2012-02-17
forum: Server Platforms
---

### Post by pgf1234 on 2012-02-17
I'm not understanding how PhpMyAdmin is working on my system (Ubuntu 10.10). I have two database servers configured and I want to add a third one. The root directory is /usr/share/phpmyadmin, as expected. In there I find the config.inc.php file I expect, but it does not list either of my existing servers. There is also a file of the same name in /etc/phpmyadmin, but it does not list my servers either. In both files the $cfg[Servers] entries are empty. grep'ing for my server names in those directories does not get any hits. 

Where do configure my new server? For that matter (same question really) where is it getting the information to allow me to manage my existing servers?

---

### Post by pgf1234 on 2012-02-17
Figured it out. It is reading the file: /var/lib/phpmyadmin/config.inc.php

---

