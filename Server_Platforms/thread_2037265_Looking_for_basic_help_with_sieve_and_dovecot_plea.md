---
title: "Looking for basic help with sieve and dovecot please"
date: 2012-08-04
forum: Server Platforms
---

### Post by jimwillsher on 2012-08-04
Hello

I've always used procmail to file spam emails, but on Wednesday I built a new server with 12.04 and would like to use sieve as it seems to be the preferred direction. I must be missing something incredibly basic as I can't get it to work.

I have installed dovecot-postfix and spamassassin, and they are working fine. Emails can come and go, and spam messages have the X-Spam-Status and X-Spam-Flag set correctly. But what I cannot achieve is to get spam emails to go into the spam folder (which I am viewing through squirrelmail). Emails always arrive in the inbox.

I've done pretty much no configuration (tried lots, but always reverted back) so there must be a config setting I am missing. The only configuration I have done for this is:

in /etc/dovecot/conf.d/01-mail-stack-delivery.conf:

```
# Plugins configuration
plugin {
        sieve=~/.dovecot.sieve
        sieve_dir=~/sieve

        # JRW
        sieve_global_path = /var/lib/dovecot/sieve/default.sieve
}
```

(added the JRW line)

Created a file /var/lib/dovecot/sieve/default.sieve:

```
require ["fileinto"];
# Move spam to spam folder
if header :contains "X-Spam-Flag" ["YES"] {
  fileinto "spam";
  stop;
}
```

and run 

```
sievec /var/lib/dovecot/sieve/default.sieve
```

These steps might be completely wrong, but this is me clutching at straws.

I just want basic sieve filtering for spam mail, for all suers. Nothing more.

Many thanks in advance.



Jim

SOLVED: permission problem on the /var/lib/dovecot/sieve/default.sieve directory. Needs to be owned by dovecot and with +x

---

