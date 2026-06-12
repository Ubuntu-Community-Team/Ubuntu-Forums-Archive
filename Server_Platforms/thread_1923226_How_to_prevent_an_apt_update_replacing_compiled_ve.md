---
title: "How to prevent an apt update replacing compiled version of PHP as system default ?"
date: 2012-02-10
forum: Server Platforms
---

### Post by interzoneuk on 2012-02-10
Hi.

At present when I compile a version of PHP in Ubuntu I use update-alternatives to specify system PHP version - i.e :-


update-alternatives --install /usr/bin/php php /usr/local/php/bin/php 50
update-alternatives --install /usr/bin/php-cgi-bin php-cgi-bin /usr/local/php-cgi/bin/php 50 --force
update-alternatives --install /usr/bin/php5-cgi php5-cgi /usr/local/php-cgi/bin/php-cgi 50
update-alternatives --set php5-cgi-bin /usr/local/php-cgi/bin/php --force

This is fine until there is a system update...

Then the version of php5-cgi and the apache module is replace by the standard ubuntu version rather than my compiled one.

I.E it sets the default php-cgi version as the standard Ubuntu one after an update - I have to manually change it back.

Does anyone have any ideas how to prevent this occurring ?

Im running Ubuntu 10.04.

Any hints will be welcomed.

There are no update-alternatives for the apache PHP module (as far as i'm aware)

Regards

---

### Post by Cheesemill on 2012-02-10
You can instruct apt to hold specific packages at the current version (ie not update them), this may be what you're looking for.

[https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages](https://help.ubuntu.com/community/PinningHowto#Introduction_to_Holding_Packages)

---

