---
title: "Increasing maximum number of IMAP connections?"
date: 2009-11-16
forum: Server Platforms
---

### Post by theRick on 2009-11-16
We just put iredmail into use this morning and I was thrilled with the ease of installation.

Running into a problem though - we have three people accessing the same IMAP account with the Apple Mail client and they are randomly losing their connections.

I checked the dovecot log and found...

```
dovecot: Nov 16 19:13:55 Info: imap-login: Maximum number of connections from user+IP exceeded (mail_max_userip_connections): user=
```

I went into /etc/dovecot/dovecot.conf and found the section

```
# IMAP configuration
protocol imap {
    #mail_plugins = quota imap_quota zlib expire
    mail_plugins = quota imap_quota zlib

    # number of connections per-user per-IP
    #mail_max_userip_connections = 10
}
```

I am still learning my way around linux, but it appears mail_max_userip_connections is commented out so I'm guessing this limit is coming from somewhere else.

How can I increase the connection limit?

Thanks in advance!

---

### Post by Amedee on 2012-10-27
> **theRick said:**
> I am still learning my way around linux, but it appears mail_max_userip_connections is commented out so I'm guessing this limit is coming from somewhere else.

*The force is strong with you, Young Skywalker, but you are not a Jedi yet!* ;-)
Every configurable software has some (according to the developer) sane defaults that are compiled in. You can change the defaults with a configuration file.
For your convenience, most software comes with a configuration file with all these default values, commented out. They are just for your information. If you agree with the defaults, you don't have to touch the config file.

> **theRick said:**
> How can I increase the connection limit?
Well, you just uncomment that particular line and you change the default to whatever you want it to be.
Or even better: copy the line and keep the default in comment, as a future reference.

---

