---
title: "PHP-CLI on 8.04 Server?"
date: 2009-03-22
forum: Server Platforms
---

### Post by lopes_andre on 2009-03-22
Hi,

I have 8.04 server, and I need to use PHP-CLI, I don't know if PHP-CLI is installed. How can I see that? If it is installed, how can I activate PHP-CLI?

When I do apt-get install php5-cli I got this error:

```
 apt-get install php5-cli

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  php-pear
The following NEW packages will be installed:
  php5-cli
0 upgraded, 1 newly installed, 0 to remove and 77 not upgraded.
Need to get 2550kB of archives.
After this operation, 5640kB of additional disk space will be used.
Err http://pt.archive.ubuntu.com hardy-updates/main php5-cli 5.2.4-2ubuntu5.3
  404 Not Found
Err http://security.ubuntu.com hardy-security/main php5-cli 5.2.4-2ubuntu5.3
  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-cli_5.2.4-2ubuntu5.3_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

What can I do?

Best Regards, André.

---

### Post by das7002 on 2009-03-22
Looks like that mirror is missing files try using a different mirror as that may solve things

---

### Post by hyper_ch on 2009-03-23
did you run ```
sudo apt-get update
``` first?

---

