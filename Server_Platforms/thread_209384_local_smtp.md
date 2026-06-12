---
title: "local smtp?"
date: 2006-07-05
forum: Server Platforms
---

### Post by termite on 2006-07-05
I'm doing some travelling at the moment, so switching providers constantly.  I want to be able to send mail from thunderbird no matter where I am, so I thought I could set up a local SMTP server that will only be open to my local machine...

Any hints?  I really have no idea where to start....

---

### Post by scxtt on 2006-07-05
if you want to send mail directly from your box, check out mailx (in the repos) and if you can't select it in thunderbird as the smtp protocol - install sendmail (i just have mailx installed, and in evolution "Sendmail" is an smtp option) ... 

w/ mailx you can also send emails from the command line ... it's a great program :D

---

### Post by termite on 2006-07-05
perfect...works :)

---

### Post by scxtt on 2006-07-05
did you look in evolution, if it's installed? -- just curious ...

---

### Post by macca87 on 2006-07-26
would you say sendmail is too large and server minded to be used as a local smtp for a laptop user?

Also doesnt sendmail allow for external (internet) connections?, does postfix or mailx?

---

### Post by lamego on 2006-07-26
postfix does not use much resources, it is ok to be used on a laptop.
The default configuration does not allow it to be used to relay emails from the internet.
You can set the main configuration options with:
```
sudo dpkg-reconfigure postfix
```

---

