---
title: "Php"
date: 2006-08-07
forum: Server Platforms
---

### Post by jordans on 2006-08-07
I am trying to have PHP send mail with a simple script but it won't work no matter what. Any ideas?

---

### Post by cantormath on 2006-08-07
> **jordans said:**
> I am trying to have PHP send mail with a simple script but it won't work no matter what. Any ideas?

whats the script, are you running a mail server? which one?

---

### Post by jordans on 2006-08-07
Do i have to have a mail server set up?

---

### Post by scxtt on 2006-08-07
[php]<?php
 $to = "recipient@example.com";
 $subject = "Hi!";
 $body = "Hi,\n\nHow are you?";
 if (mail($to, $subject, $body)) {
   echo("<p>Message successfully sent!</p>");
  } else {
   echo("<p>Message delivery failed...</p>");
  }
 ?>[/php][http://email.about.com/cs/phpemailtips/qt/et031202.htm](http://email.about.com/cs/phpemailtips/qt/et031202.htm)

and obviously you can get inputs from the user to be the $to, $subject, and $body ...

---

### Post by jordans on 2006-08-07
That script failed.

---

### Post by scxtt on 2006-08-07
you have to have a program that sends email installed, hence the (mail($to, $subject, $body)) part ...

---

### Post by jordans on 2006-08-07
And how might i go about doing that? Does it take a long time?

---

### Post by scxtt on 2006-08-07
i'm assuming it needs an equivalent of sendmail, try a **sudo apt-get install mailx** then try again ...

---

### Post by jordans on 2006-08-07
Just did what you said and stayed the same. Went into a thing about postfix and I told it no configuration.

---

### Post by scxtt on 2006-08-07
i use the "internet" config (which i think is highlighted by default, 2nd option) ... i just installed apache2 / php5, so i'm gonna see if that script works for me ...

EDIT: worked fine for me ...

---

### Post by jordans on 2006-08-07
K, tell me when you know.

---

### Post by scxtt on 2006-08-08
i just reinstalled Kubuntu about a day or 2 ago, just installed apache2 / php5 (mailx a few days ago) -- so if you've got all that and it still doesn't work - i'm not sure why, worked fine for me -- maybe reinstall mailx and select the internet option - but mail() is a builtin php function (don't know exactly what it relies on) ...

---

### Post by jordans on 2006-08-08
ha, thanks, it works now!

---

### Post by scxtt on 2006-08-08
was it just the "internet" choice in mailx?

---

### Post by jordans on 2006-08-08
I think it was. I just reconfigured postfix. Do you know how i could set up squirrelmail to work?

---

### Post by cantormath on 2006-08-08
> **cantormath said:**
> whats the script, are you running a mail server? which one?

that is what i ment by a mail server, something to mail stuff out for you.

I had not thought of mailx.....will keep that one in mind.

looking at that php function mail() I thought maybe php was magically doing it for you by you just giving it an out going smtp server or something.

---

### Post by jordans on 2006-08-08
IT is telling me mail is sent successfully but it isn't getting to me.

---

### Post by scxtt on 2006-08-08
some ISPs block the equivalent of jordans@localhost or jordans@$HOSTNAME, type **mailq** in a termainal and see if you see it sitting there ...

when i tested it, i sent it to my gmail account - worked fine ...

---

