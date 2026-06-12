---
title: "Cant get pear smtp mail to work"
date: 2008-10-30
forum: Server Platforms
---

### Post by madsporkmurderer on 2008-10-30
It seems that using the php mail function gets caught in spam filters for a lot of people. My plan B is to create a gmail account and send them all through there.

I've tried following [this]("http://email.about.com/od/emailprogrammingtips/qt/et073006.htm") guide but using the path of the pear mail.php installed via aptitude install php-mail (/usr/share/php/Mail/mail.php) but just get Fatal error: Class 'Mail' not found in /usr/share/php/Mail/sendmail.php on line 25

It seems that the mail.php installed by php-mail might not work, or maybe I need to include something else

Anyone got any ideas?

Thanks,
Mike

---

### Post by kepardue on 2009-01-08
So this is way after your original post, but I was having the same problem and found that it was as easy to solve as installing the package "php-net-smtp" along with the php-mail package.

---

