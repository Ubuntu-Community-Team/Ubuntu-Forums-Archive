---
title: "I Need To Know!"
date: 2008-11-09
forum: The Cafe
---

### Post by kevin11951 on 2008-11-09
Right now im using godaddy as a webhost, and when i set up both drupal, and wordpress on there, there were able to send emails, no smtp setup, nothing...

HOW! what does godaddy do!?

---

### Post by LookTJ on 2008-11-09
The ISPs they use don't block smtp like Comcast does. Or I could be wrong, also maybe a relay?

---

### Post by ad_267 on 2008-11-09
In php you can use the [mail]("http://nz2.php.net/function.mail") function to send email with smtp. Most hosts should allow this and you don't have to do any setup.

---

### Post by kevin11951 on 2008-11-10
> **ad_267 said:**
> In php you can use the [mail]("http://nz2.php.net/function.mail") function to send email with smtp. Most hosts should allow this and you don't have to do any setup.

i ask because we will soon be switching from godaddy to in-house servers, and i was wondering how to do that?

any good how-tos?

---

### Post by ad_267 on 2008-11-10
> **kevin11951 said:**
> i ask because we will soon be switching from godaddy to in-house servers, and i was wondering how to do that?

any good how-tos?

I've never had to set this up myself, but this looks like a good simple guide for configuring PHP if that's what you're using: [http://www.sitepoint.com/article/advanced-email-php/](http://www.sitepoint.com/article/advanced-email-php/). For configuring sendmail this one might help: [http://www.linuxjournal.com/article/5507](http://www.linuxjournal.com/article/5507)

---

### Post by LookTJ on 2008-11-10
> **kevin11951 said:**
> i ask because we will soon be switching from godaddy to in-house servers, and i was wondering how to do that?

any good how-tos?

I would look at this howto, as I relayed my smtp to my ISP's smtp servers.

[http://www.howtoforge.com/postfix_relaying_through_another_mailserver](http://www.howtoforge.com/postfix_relaying_through_another_mailserver)

---

