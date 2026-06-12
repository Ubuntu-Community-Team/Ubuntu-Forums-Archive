---
title: "sendmail relay to SMTP"
date: 2012-12-14
forum: Server Platforms
---

### Post by sandyd on 2012-12-14
Ive been having a problem with Redmine and AxiGen not playing nice with each other, so Ive decided to setup a sendmail relay to Axigen instead.

Anyone have any good guides on this?

---

### Post by SeijiSensei on 2012-12-14
If you really want to use sendmail, and not Postfix, then you just need to edit /etc/mail/sendmail.cf and add the hostname of the upstream relay you want to use immediately after "DS" like this:

```

# "Smart" relay host (may be null)
DSrelay.example.com

```

Note that there is no space between DS and the hostname.  If you want to use an IP address instead, you need to encase it in square brackets like this:

```

# "Smart" relay host (may be null)
DS[10.10.10.10]

```

Sendmail uses that square-bracket syntax for IP addresses in other files like /etc/mail/mailertable as well.  You'll need to restart sendmail to put this change into effect.

If you only want to send some traffic to the relay and deliver the rest using regular MX lookups, leave the DS field blank and use /etc/mail/mailertable instead. You'll need to add support for mailertable lookups by building your own sendmail.cf. Install the sendmail-cf package, then add this line to /etc/mail/sendmail.mc after the line that references access_db:
```
FEATURE(`mailertable', `hash -o /etc/mail/mailertable.db')dnl
```
Then rebuild sendmail.cf with:

```

cd /etc/mail
sudo m4 < sendmail.mc > sendmail.cf

```

I usually create a new cf file and keep a copy of the old one in case things go wrong.  Either name the new one sendmail.cf, or use a symlink with that name that points to the new version.  Restart sendmail to use the new .cf file.

Now create a text file called /etc/mail/mailertable with entries that look like this:

```

example.com      relay:[relay.example.com]
another.com      relay:[another.example.com]

```

Then build mailertable.db with
```

cd /etc/mail
sudo makemap hash mailertable < mailertable

```

The rerouting will take effect immediately without needing to restart sendmail.

---

