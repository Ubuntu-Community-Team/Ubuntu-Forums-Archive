---
title: "PHP 7 in server release of 16.04?"
date: 2016-01-08
forum: Ubuntu Development Version
---

### Post by cincibluer6 on 2016-01-08
Saw an article about this. Is there any official word on PHP7?
I have a prod server being used for a wiki and don't really wish to upgrade to 7 so soon after initial release but would like the LTS backing of 16.04.
Just wondering what I should prepare for. I suppose I can always snap the machine but I like to be prepared all the same.
Thanks

---

### Post by dino99 on 2016-01-08
request & dev answer : [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/1522422](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/1522422)

Looks like it cant be done till 18 Feb (too much transition work)

---

### Post by cincibluer6 on 2016-01-08
Thanks for the link. I'll keep looking at it just so I know what to expect.

Cheers mate.

---

### Post by anca-emanuel on 2016-01-08
Read this [https://www.reddit.com/r/PHP/comments/3zvlso/we_need_your_help_to_get_php_7_in_ubuntu_1604/cyq6k54](https://www.reddit.com/r/PHP/comments/3zvlso/we_need_your_help_to_get_php_7_in_ubuntu_1604/cyq6k54)
First, there must be an transition tracker on Debian: [https://release.debian.org/transitions](https://release.debian.org/transitions)
And for php there is none.
There is an ppa to try at your own risk: [https://launchpad.net/~ondrej/+archive/ubuntu/php-7.0](https://launchpad.net/~ondrej/+archive/ubuntu/php-7.0)

For comparation, perl transition for an minor version: [https://release.debian.org/transitions/html/perl.html](https://release.debian.org/transitions/html/perl.html)
Read [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=796345](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=796345) to see how much effort was needed, and is not 100% solved yet.

---

### Post by nacc3 on 2016-04-08
Just an FYI, PHP7.0 is officially in main in 16.04 for a few weeks now, and php5 has been removed (as of this week).

---

### Post by cincibluer6 on 2016-04-09
Yep. I saw that when I put 16.04 in a VM to test something. Thanks for updating the thread mate. I would've forgotten to.

---

