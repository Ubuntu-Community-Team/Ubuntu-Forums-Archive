---
title: "LAMP and php mail function"
date: 2010-11-17
forum: Server Platforms
---

### Post by Preau on 2010-11-17
Hello,

Recently I've set up a LAMP on my Ubuntu 10.04

Now I'm trying to run a php page with a mail script but it's not sending anything.

```
<?php if(mail('bla@bla.com', 'Test', $bericht, 'From: noreply@bla.nl')) echo 'win';
else echo 'fail'; ?>
```

This is basically where it's going wrong, it echos fail for me. I've already checked that there's nothing wrong in $bericht.

I've tried using sendmail but that didn't work at all and messed my page up.

Now I'm trying to use exim but that doesn't seem to work either. How can I be able to send mails from my localhost?

Thank in advance,
Preau

EDIT: Well I'm not sure if this is the right forum to post this in, if not sorry for that.

---

### Post by ICEB3AR on 2010-11-17
Have you configured the php.ini correct? Check the section with mail.

Basically you simply have to install a Mailtransferagent like sendmail, postfix or something like that then check if php.ini is right configured and maybe a restart of the webserver to refresh the config and it should work.

---

### Post by SeijiSensei on 2010-11-17
I'd check /var/log/apache2/error.log as well.  Modern PHP versions sometimes balk at having a function within a if().  It will throw an error in error.log if it's unhappy.  If so, try this:

```

$didmailwork=mail(....);
if ($didmailwork) { blah; } else { blahblah; }

```

Usually a default installation of an MTA like sendmail or Postfix listening on the localhost interface is all you need.  If you use a "smart host" for outbound mail, you can specify that in /etc/php.ini instead.

---

