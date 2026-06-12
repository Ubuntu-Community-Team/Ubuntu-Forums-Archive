---
title: "Upgrading PHP 5.2 on Ubuntu Server 8.04 LTS x64"
date: 2011-02-11
forum: Server Platforms
---

### Post by filburt1 on 2011-02-11
At my office we have a server running Ubuntu 8.04 LTS x64 with PHP 5.2.4. Recently we've needed to upgrade PHP to 5.2.17 or later (ideally the latest release of PHP 5.2, but not PHP 5.3). The server acts as a web server for an office of about 15 people as well as other mission-critical services like Subversion.

The only options I can think of are:
[list]
[*]Upgrading the server to 10.04 LTS. Unfortunately, I think this will install PHP 5.3 and carries a large risk overall.
[*]Building PHP from source. However, phpinfo.php doesn't show the ./configure options ([https://bugs.launchpad.net/ubuntu/+source/php5/+bug/516061](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/516061)).
[*]Using a third-party PPA to upgrade PHP using Aptitude. I'm guessing this may be the safest way.
[/list]

What's the safest way to accomplish this?

---

### Post by sasdaman on 2011-09-06
Hi Filburt,

Did you ever manage to upgrade your PHP version to 5.2.17 on Ubuntu 8.04 LTS? If so could you please share your solution?

Many thanks, Sasdaman

---

