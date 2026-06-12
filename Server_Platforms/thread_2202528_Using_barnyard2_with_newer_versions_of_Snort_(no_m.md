---
title: "Using barnyard2 with newer versions of Snort (no mysql)"
date: 2014-01-29
forum: Server Platforms
---

### Post by jason54 on 2014-01-29
ok so the newer versions of snort do not compile with MySQL support because the preferred method is now unified2 output which is then parsed by barnyard2 to log to a MySQL database for BASE or Snorby to view.


Now the problem is that when I try to run barnyard2 it complains that my version of snort does not have MySQL support and it halts. Does anybody actually run barnyard2 these days with the newer version of snort? and how if so?


Do people actually have to use old MySQL versions of snort to operate barnyard these days? and if so why on earth do you need MySQL support on snort when it is barnyard that is actually outputting to a database anyway and snort is merely logging in a flat unified format.


I'm not expecting many answers on this one to be honest but worth a try :)
p.s.  I tried compiling with and without the --with-mysql switch on barnyard2


```

Ubuntu Server 14.10 trusty tahr - all dependencies appear to be met


Snort version ( tried v2.9.5.3 - v2.9.6.0 ) *works (without mysql)
Pulledpork (v0.7.0) *works

```


```

Barnyard2 (2.1.13 build 327) error =


ERROR database: 'mysql' support is not compiled into this build of snort


ERROR: If this build of barnyard2 was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
'mysql' support.


If this build of barnyard2 was compiled by you, then re-run the
the ./configure script using the '--with-mysql' switch.
For non-standard installations of a database, the '--with-mysql=DIR'
syntax may need to be used to specify the base directory of the DB install.


See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..
Barnyard2 exiting



```

---

