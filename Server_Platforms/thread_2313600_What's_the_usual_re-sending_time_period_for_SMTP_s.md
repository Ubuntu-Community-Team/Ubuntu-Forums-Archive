---
title: "What's the usual re-sending time period for SMTP servers?"
date: 2016-02-14
forum: Server Platforms
---

### Post by Grigoriy on 2016-02-14
Hello!

My Postfix SMTP server is off most of the time (because the computer is  not always on). I know it's not the way it should be in a production  environment, but anyhow...

Since, obviously, I don't wanna miss any mail I get curious. I was  trying to send e-mails to myself from different web mail accounts that I  have (like Yahoo, GMail etc.). What happened is that after my SMTP  server had gone online, it actually received the e-mails that I sent.

Sometimes it wasn't instantaneously, but nevertheless within an hour, if not less. But that's web mail SMTP servers.

What I want to ask is about regular SMTP servers, say, which operate at  different IT companies (hosting SMTP servers, corporate SMTP servers  etc.) I know that every server can be configured differently, but maybe  there's an unwritten standard in the industry or at least just let me  know what kind of configuration you personally installed or know about.

---

### Post by SeijiSensei on 2016-02-14
Traditionally sendmail was configured to retry messages every fifteen minutes for up to five days.  According to [this](http://www.linuxtopia.org/online_books/mail_systems/postfix_documentation/TUNING_README_008.html), Postfix also holds queued mail for up to five days and retries undeliverable messages every 1000 seconds, or a bit longer than fifteen minutes.

If you had a backup MX server so that your mail queues up while your primary server is offline, you would likely get your mail faster than relying on the various originating servers to resend it.  It's also possible to trigger a despooling using the ESMTP "[ETRN]("https://en.wikipedia.org/wiki/Extended_SMTP#ETRN")" command.

---

### Post by Grigoriy on 2016-02-14
Thanks for your reply!

It's very interesting, but if  I had a secondary SMTP server that is more reliable, then I wouldn't be  using the primary one. I can pay probably for some 3rd party service or  just use hosting for everything, but I want to do everything in house,  so to speak and also save an extra expense.

Is there a way to query a  mail server to find out its delivery attempts schedule (set up)? Or the  only way is to explicitly ask its sysadmin about it?

---

### Post by Grigoriy on 2016-02-14
**queue_run_delay (default: 300s)** prior to Postfix 2.4 the default value was 1000s. 
[http://www.postfix.org/postconf.5.html#queue_run_delay](http://www.postfix.org/postconf.5.html#queue_run_delay)
So it's 5 minutes now.

---

### Post by SeijiSensei on 2016-02-14
Five minutes is way too short if you have a busy server. Your mail logs will be full of failed retry attempts. Most of my queued mail consists of notices to bogus spam senders that keep getting refused.

---

### Post by Grigoriy on 2016-02-14
Correction. It's the FIRST ATTEMPT is after 5 minutes. After that it's doubled each time for up to about an hour (66,66 minutes approx.) 
That's if I understood default Postfix behavior right...

---

