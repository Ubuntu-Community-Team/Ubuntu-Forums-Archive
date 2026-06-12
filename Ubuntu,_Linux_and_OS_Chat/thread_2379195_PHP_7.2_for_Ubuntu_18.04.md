---
title: "PHP 7.2 for Ubuntu 18.04 ??"
date: 2017-12-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Gottier on 2017-12-02
When Ubuntu 16.04 was released, it seemed that many people wanted PHP 7.0 to be the version that was installed by default. PHP 7.2 was released today, and it got me wondering if it will be in Ubuntu 18.04. How does one find out about these things? When I look to see what PHP version is currently scheduled to be included, I see 7.1.X, but there is still lots of time for 7.2.

---

### Post by faraco2 on 2017-12-07
When a new version was released for particular program, I'll usually  will check if it will be supported (of if there was already) for my  Ubuntu release on Launchpad (where the Ubuntu main development project  is hosted).

For example, checking if PHP 7.2 will be supported in Ubuntu 18.04  repository however gave me a negatory result at the time of writing  this. [https://launchpad.net/ubuntu/bionic/+search?text=php7.2](https://launchpad.net/ubuntu/bionic/+search?text=php7.2)

---

### Post by mw-jko on 2018-01-24
Hey @faraco2 - thank your for your reply. Your query is now returning 7.2-hits (and "php7.1" as well)

But: if I try the 18.04-Beta using the docker-image I still get 7.1 (apt-get update && apt-get install php && php -v). Do you have any idea, if the launchpad searchresult is an indicator if 7.2 (or maybe even 7.1 **and** 7.2) will be shipped with 18.04?

(Reason for why I'm so curious is we plan to upgrade our servers to 18.04 LTS and need to know the php version to prepare for)

---

### Post by -NabLa- on 2018-01-31
It's on proposed (7.2.1) [https://launchpad.net/ubuntu/bionic/+package/php7.2-common](https://launchpad.net/ubuntu/bionic/+package/php7.2-common)

---

### Post by Gottier on 2018-02-10
It's been a while since I posted this, and the good news is that 7.2.1 is available and working nicely in Ubuntu 18.04. I downloaded the daily build, and have been successful in installing and using everything that I normally use for web development. I've even overcome some of the things I hate about Gnome, so I'm excited and waiting for the release of 18.04.

---

### Post by mw-jko on 2018-02-12
Yeah tried this as well. Didn't work before works now. 

On a side note: you have to install "php7.2" atm, "php" will still give you 7.1 (I like it to have options though)

---

