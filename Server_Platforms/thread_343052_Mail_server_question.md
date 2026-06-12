---
title: "Mail server question"
date: 2007-01-20
forum: Server Platforms
---

### Post by llamakc on 2007-01-20
My Debian box recently had a hardware failure and I have decided to migrate my home vanity servers to my Ubuntu box.

I just installed courier-imap, squirrelmail, apache2 and the *php modules. Squirrelmail's login page comes up just fine, however any login produces a failure in:

[B] ERROR: Connection dropped by IMAP server.

[/B]Additionally, there is nothing inside of /var/mail

Last: when I tail /var/log/syslog I see this:

```

Jan 20 20:39:14 nola imapd: Connection, ip=[::ffff:127.0.0.1]
Jan 20 20:39:14 nola authdaemond: PAM unable to dlopen(/lib/security/pam_foreground.so)
Jan 20 20:39:14 nola authdaemond: PAM [dlerror: /lib/security/pam_foreground.so: undefined symbol: pam_set_data]
Jan 20 20:39:14 nola authdaemond: PAM adding faulty module: /lib/security/pam_foreground.so
Jan 20 20:39:14 nola imapd: chdir Maildir: No such file or directory

```My router's already pointing to this particular machine as apache2 is serving pages just fine.

My question is this: I haven't installed a mail server in years. What do I need to do?

Oh, btw I DID install the exim4-daemon-heavy package (with which I have experience) and it is running and is configured as 'internet':

```

110       4311  0.0  0.1  11260  1584 ?        Ss   20:38   0:00 /usr/sbin/exim4 -bd -q30m

```

---

### Post by llamakc on 2007-01-20
Okay, so mail is delivering locally to the interface but IMAP is not delivering via Squirrelmail.

I can successfully telnet to the imap port on localhost just fine. I have squirrelmail configured to use courier, which I am using.

Ideas?

---

### Post by llamakc on 2007-01-21
I switched to PostFix and it worked out of the box.

SOLVED.

---

