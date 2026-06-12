---
title: "Clamd dies without warning"
date: 2007-06-05
forum: Server Platforms
---

### Post by hashbrowncipher on 2007-06-05
I am using Clamd with amavisd-new to filter viruses out of email.  Recently, clamav has been spontaneously dying (or so I can deduce, there is no direct evidence of that) leaving amavis without a virus scanner and causing a major backlog until I notice that it has died.  While I could create a cronjob to periodically restart clamd, I would like to address the root of the problem.  Clamd dies spontaneously, without logging any information that even references impending death.  This is from /var/log/clamav/clamav.log :

```

Mon Jun  4 22:39:07 2007 -> /var/lib/amavis/tmp/amavis-20070604T223858-21685/parts/p001: HTML.Phishing.Bank-1092 FOUND
Mon Jun  4 22:47:07 2007 -> SelfCheck: Database status OK.
Mon Jun  4 23:22:16 2007 -> /var/lib/amavis/tmp/amavis-20070604T232133-08617/parts/p001: HTML.Phishing.Pay-35 FOUND
Mon Jun  4 23:39:02 2007 -> Reading databases from /var/lib/clamav
Tue Jun  5 00:01:48 2007 -> +++ Started at Tue Jun  5 00:01:48 2007
Tue Jun  5 00:01:48 2007 -> clamd daemon 0.90.2 (OS: linux-gnu, ARCH: i386, CPU: i486)

```

Notice the twenty minute gap.  Because there is no virus scanner, Amavis has a fit and prints this to /var/log/mail.err:

```

Jun  5 00:01:59 <hostname redacted> amavis[19580]: (19580-01-5) (!!) ClamAV-clamd av-scanner FAILED: Too many retries to talk to /var/run/cl
amav/clamd.ctl (Can't connect to UNIX socket /var/run/clamav/clamd.ctl: Connection refused) at (eval 44) line 268.
Jun  5 00:01:59 <hostname redacted> amavis[19580]: (19580-01-5) (!!) WARN: all primary virus scanners failed, considering backups

```

While clamd is running, Amavis is happy and email is routed.


Information that may or may not be pertinent:
Postfix relays emails to amavis and amavis also uses spamassassin to check for spam.  Clamav is in the amavis group.

---

### Post by turinglabs on 2007-06-05
While it will not fix the underlying problem, you should configure amavis to use clamscan as a secondary virus scanner. As it is command-line based, it should work for you all the time (although it is more resource-intensive). There should be a block that you can un-comment in your amavisd.conf that looks something like this:

```

@av_scanners_backup = (

  ### http://www.clamav.net/
  ['Clam Antivirus - clamscan', 'clamscan',
    "--stdout --no-summary -r --tempdir=$TEMPBASE {}", [0], [1],
    qr/^.*?: (?!Infected Archive)(.*) FOUND$/ ],

);

```

For the problem of clamd dying, take a look at the various Log* options in clamd.conf(5), for example turning verbose logging on to a dedicated file.

---

### Post by hashbrowncipher on 2007-06-05
Thank you, I have done both of those, now all that needs to happen is that clamav needs to fail so that I can figure out how.

---

### Post by hashbrowncipher on 2007-06-06
Clamd has died, and logverbose is true, but nothing is logged?  I assume this is a bug in clamd.

---

### Post by turinglabs on 2007-06-06
Sounds like a bug. You could attach to the daemon with strace (1), and watch the output to see what system cal it was in when it died. That might show you what file it was last scanning, for example. 'strace -p PID' will do the trick, interrupt it with ctrl-c.

---

