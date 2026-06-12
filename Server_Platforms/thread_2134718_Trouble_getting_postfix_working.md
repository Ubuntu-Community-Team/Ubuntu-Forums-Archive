---
title: "Trouble getting postfix working"
date: 2013-04-12
forum: Server Platforms
---

### Post by JaySeeJC on 2013-04-12
Trying to get a mail server working. I keep getting the following error: 
```

Apr 12 08:25:22 myserver postfix/smtpd[6512]: NOQUEUE: reject: RCPT from mail-oa0-f54.google.com[209.85.219.54]: 554 5.7.1 <sender@gmail.com>: Sender address rejected: Access denied; from=<sender@gmail.com> to=<admin@myserver.com> proto=ESMTP helo=<mail-oa0-f54.google.com>

```

Followed this tutorial exactly, only changing where intructed.
[http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/](http://www.pixelinx.com/2010/10/creating-a-mail-server-on-ubuntu-using-postfix-courier-ssltls-spamassassin-clamav-and-amavis/)

Any idea?

---

### Post by lisati on 2013-04-12
The "Access denied" error message suggests to me that the smtd_recipient_restrictions line in your main.cf file is working, so it's possible that there is something that you could have missed. Are there any warnings in your mail log that might point us towards a typo or something that has been overlooked?

---

### Post by JaySeeJC on 2013-04-12
The log seems pretty barren... running the following and monitering the log

```


/etc/init.d/postfix stop;sleep 10;/etc/init.d/postfix start;sleep 30;/etc/init.d/postfix stop

Apr 12 16:09:30 mysite postfix/master[1270]: terminating on signal 15
Apr 12 16:09:40 mysite postfix/master[2678]: daemon started -- version 2.9.6, configuration /etc/postfix
Apr 12 16:10:10 mysite postfix/master[2678]: terminating on signal 15




```

---

### Post by lisati on 2013-04-12
My impression is that your Postfix setup is a bit different to mine. I'm a bit puzzled by the way the tutorial you linked to has set up the processing via amavis.

I used the tutorials at [http://help.ubuntu.com](http://help.ubuntu.com) - a good starting point might be [https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

---

