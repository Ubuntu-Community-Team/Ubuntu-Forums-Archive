---
title: "PHP FastCGI segfaults"
date: 2011-05-18
forum: Server Platforms
---

### Post by sapphirecat on 2011-05-18
I recently migrated my server from Slicehost to Linode and now I get seemingly random FCGI segfaults like this:

```
kernel: php-cgi[27359]: segfault at 4c ip PTR sp PTR error 6 in php5-cgi[40000
0+OFFSET]
```

[COLOR="Red"]EDIT: backtrace has been removed.[/COLOR]

Initially there was some suhosin stuff in the backtrace, so I removed php5-suhosin from the system, but it still crashes.  At this point I don't really know where to look next, since the stack seems 99% bogus: especially the apparent call to main(SHORT_MAX, NULL).

Both old and new machines were/are 64-bit Lucid installs, up-to-date, using the standard debs (lucid-security & lucid-updates enabled).  However, I already canceled the old server, unaware of this issue, so I can't double-check its logs.

It's configured as: the internet -> lighttpd,mod_fastcgi -> php5-cgi = PHP 5.3.2-1ubuntu4.9 with Suhosin-Patch (cgi-fcgi) (built: May  3 2011 00:45:34).

uname -a gives me: ```
2.6.38-x86_64-linode17 #1 SMP Thu Apr 28 22:18:47 UTC 2011 x86_64
```

I tried searching the web, but all I've found so far are similar questions, without answers.

Any help on where to go next, or how to track down what file it's trying to compile? :confused:

---

### Post by sapphirecat on 2011-05-18
I found gdb-doc, printed a few values, and found the immediate cause of the crash.  I'm still tracking down why garbage gets in there, but I think I'm doing okay for the moment.

---

### Post by sapphirecat on 2011-05-19
It looks like php-apc was either causing the problem or allowing another bug to manifest.  The immediate cause of the crash was a corrupt op_array bringing down the executor.  Removing APC makes these op_arrays much shorter-lived; either the corruption was caused by APC, or without APC persisting them, they don't live long enough to manifest the crash.

I've decided to leave the backtrace out of this, on the off chance it points to some exploitable flaw.  I don't think it's likely, but I'm no security researcher.

I've gotten about 13 hours of trouble-free operation so far with Suhosin restored and APC not loaded, compared to at most 5 hours before.

php-apc-3.1.3p1-2, for the record.

---

