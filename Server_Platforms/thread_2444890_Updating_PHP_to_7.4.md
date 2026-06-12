---
title: "Updating PHP to 7.4"
date: 2020-06-05
forum: Server Platforms
---

### Post by mcarrara2 on 2020-06-05
I am running Ubuntu 18.04.  PHP 7.2.24 is installed.  When I try to install Drupal 9 i get the error that I need at least PHP 7.3.  When I use APT to install all that is available is 7.2.  How can I update my PHP to the latest version?

Mark

---

### Post by darkod on 2020-06-05
If you can't wait until July/August when 20.04.1 should be out, you can try upgrading the release to 20.04 now.

In the packages list it seems php7.4 is included with 20.04.

Another option would be to add your own php, not related to the repo packages, but then you would have to maintain it yourself. And I don't know if the switch from repo to your own would be smooth. So it might be something you want to avoid too.

---

### Post by SeijiSensei on 2020-06-05
If you must upgrade today, there is a version of 7.4 for 18.04 in this PPA repository: [https://launchpad.net/~ondrej/+archive/ubuntu/php](https://launchpad.net/~ondrej/+archive/ubuntu/php).

---

