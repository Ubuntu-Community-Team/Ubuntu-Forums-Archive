---
title: "Apache serving PHP files in plain text after upgrade (Hardy)"
date: 2011-09-13
forum: Server Platforms
---

### Post by Vunutus on 2011-09-13
I upgraded several apache/php related files yesterday through webmin so I assume that is what caused the problem. My apache installation only serves the local office intranet and isn't used constantly so I wasn't notified that something had gone wrong until this morning.

All PHP files requested from apache are just sent to the browser in plain text without being executed.

What steps should I take to see what the problem is here and fix it? I'm using more or less default options which means my only virtual host is the default one that serves /var/www

---

### Post by Vunutus on 2011-09-13
Fixed my own problem. It appears that webmin went skynet on me and removed php5 and libapache2-mod-php5 instead of upgrading them. The other apache-related packages it upgraded are fine, though...

---

