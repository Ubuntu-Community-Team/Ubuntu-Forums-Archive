---
title: "What's better: Postfix or Postfix+Procmail?"
date: 2007-09-29
forum: Server Platforms
---

### Post by bss on 2007-09-29
What is better: Using postfix (maildir) or using combination of postfix with procmail (comfigured for maildir).

Can you use SpamAssasin and ClamAV with the first option or must the mail go throu procmail?

Please post your opinion...

---

### Post by HermanAB on 2007-09-29
The advantage of procmail is that it gives another place where you can filter stuff before deliverying it - that's all.

Probably the easiest way to use Spamassassin and clamav with postfix, is with the Amavisd-new script.  Amavisd will unpack compressed attachments and invoke the scanners.  

Amavis runs as a daemon listening on a high port (10024) waiting for postfix to send it something.  Postfix runs with an additional listener on a high port (10025) waiting for amavis to send something back.  Each message received by postfix is then forwarded to amavis, scanned and forwarded back to postfix for delivery.

See these: 
[http://www.postfix.org/docs.html](http://www.postfix.org/docs.html)
[http://www.flakshack.com/anti-spam/wiki/index.php](http://www.flakshack.com/anti-spam/wiki/index.php)

It works quite well, but it is better if you add greylisting and blacklisting as well.

Cheers,

H.

---

### Post by bss on 2007-09-29
Thank you..

I'll try it the first thing in the morning...

Can spamassasin also be configured in procmail?


regards

B. R.

---

### Post by HermanAB on 2007-09-29
Oh yes, Postfix has only two ways to deliver messages - mbox or maildir.  Using procmail, you can do anything under the sun.  

However, the procmail syntax is arcane.  It uses an older obsolete kind of regular expression syntax, so good luck with that.  You'll have to read many guides before you'll be comfortable with it.

Cheers,

H.

---

### Post by bss on 2007-09-30
Well.... I've managed to configure procmail that it delivers the mail to the right Maildir/, becouse i have some users in /home directory and other in its admin user's directory... For now works fine... 

Oh.. Would postfix configuration allow me to config. it that it would do the spam checking in postfix and for the delivery procmail would be used?



Cheers,:)

B. R.

---

