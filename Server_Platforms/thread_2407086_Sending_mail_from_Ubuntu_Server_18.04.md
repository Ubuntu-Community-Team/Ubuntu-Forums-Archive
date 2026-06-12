---
title: "Sending mail from Ubuntu Server 18.04"
date: 2018-11-29
forum: Server Platforms
---

### Post by juanferaviles on 2018-11-29
Good afternoon, I decided to use Ubuntu Server 18.04 to install xampp and put a website.
That site handles a password reminder with php with which mail is sent to reset it. In Xampp with Windows I have it configured with sendmail that comes integrated, but xampp for Ubuntu is very different this part in specific.
I would like to know, based on your experience, how to best manage this post office, thank you.

---

### Post by QIII on 2018-11-29
Moved from LoCo sub-forum to ***Server Platforms*** for greater visibility and a better fit.

---

### Post by juanferaviles on 2018-11-29
Tks, im new on forum and makes me crazzy so different links for posting.

---

### Post by mastablasta on 2018-11-30
you need to configure sendmail:
[https://help.ubuntu.com/lts/serverguide/email-services.html.en](https://help.ubuntu.com/lts/serverguide/email-services.html.en)
[https://gist.github.com/adamstac/7462202](https://gist.github.com/adamstac/7462202)

14.04:  [https://www.abeautifulsite.net/configuring-sendmail-on-ubuntu-1404](https://www.abeautifulsite.net/configuring-sendmail-on-ubuntu-1404)

if you need to just send email then sSMTP is also a good option:

[https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

---

### Post by SeijiSensei on 2018-11-30
> **mastablasta said:**
> if you need to just send email then sSMTP is also a good option:

[https://wiki.debian.org/sSMTP](https://wiki.debian.org/sSMTP)

Just the other day here I was trying to help someone here using ssmtp, and we discovered it doesn't support /etc/aliases.  That made what would have been a simple solution to the problem of redirecting root's mail to another account much more difficult.

If you're used to sendmail and can manuever your way around sendmail.mc and sendmail.cf, I'd stick with what you know.

---

### Post by juanferaviles on 2018-11-30
Thanks a lot i think i´ll be testing this, i´ve tryed pearphp, msmtp, phpmailer, postfix, and doesnt work!

---

### Post by LHammonds on 2018-12-02
> **SeijiSensei said:**
> Just the other day here I was trying to help someone here using ssmtp, and we discovered it doesn't support /etc/aliases.  That made what would have been a simple solution to the problem of redirecting root's mail to another account much more difficult.

If you're used to sendmail and can manuever your way around sendmail.mc and sendmail.cf, I'd stick with what you know.

I use ssmtp.  It has it's own configuration files in /etc/ssmtp/ if I recall correctly.  I remap root to the webmaster mail account in the "from" address so that any replies go to the right place (server is outbound notification mail only).

Here is the info page: [EmailAlerts](https://help.ubuntu.com/community/EmailAlerts)

LHammonds

---

### Post by juanferaviles on 2018-12-03
Tks, that was very helpfull!<br>

---

