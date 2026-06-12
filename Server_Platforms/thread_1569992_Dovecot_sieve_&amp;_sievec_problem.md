---
title: "Dovecot sieve &amp; sievec problem"
date: 2010-09-07
forum: Server Platforms
---

### Post by Rynor on 2010-09-07
Hello all,

I'm having a problem getting sieve to work with dovecot on 10.04.

Even weirder, when I try to compile the following script with sievec

```

require ["setflag","fileinto"];
if header :contains "X-DSPAM-Result" "Spam" {
        setflag "\\Seen";
        fileinto "Junk";
        stop;
}

```

I get the following errors

```
sievec .dovecot.sieve
.dovecot: line 1: error: require command: unknown Sieve capability 'setflag'.
.dovecot: line 3: error: unknown command 'setflag' (only reported once at first occurence).
.dovecot: error: validation failed.
Error: failed to compile sieve script '.dovecot.sieve'

```

This is all using dovecot version 1:1.2.9-1ubuntu6

**edit: found the mistake, should've required imap4flags instead of setflag.**

---

### Post by Versusnja on 2010-11-19
Same here.
After upgrading from 8.10 to Lucid I started getting similar errors.

So I changed require "imapflags" to require "imap4flags" and it worked.

So mind **imap4flags**.

---

