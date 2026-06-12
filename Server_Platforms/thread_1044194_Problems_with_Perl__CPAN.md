---
title: "Problems with Perl / CPAN"
date: 2009-01-19
forum: Server Platforms
---

### Post by Peque on 2009-01-19
Hey Guys. 

I'm running into a problem on my mailserver constantly about this little problem. 
I have tried to update the different Perl packages etc and everything is uptodate. But in my mail.log I'm getting this error: 
```
Jan  9 06:57:18 sif postfix/smtp[4775]: BA82A150571: to=<rita@xxxxxx.xxx>, relay=127.0.0.1[127.0.0.1]:10024, conn_use=3, delay=145226, delays=145171/53/0/2.
1, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=04801-01-3, quar+notif FAILED: temporarily unable to quarant
ine: 451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/w/spam-wF3wbVF51GVY.gz failed: Can't call method "value" on an undefined value at /usr/share/p
erl5/IO/Compress/RawDeflate.pm line 98., id=04801-01-3 at /usr/sbin/amavisd-new line 10371. (in reply to end of DATA command))
Jan  9 06:57:19 sif amavis[4791]: (04791-01-5) (!)451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/f/spam-fmQs5XfFlx+6.gz failed: Can't call method 
"value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line 98.
Jan  9 06:57:19 sif amavis[4791]: (04791-01-5) (!!)TROUBLE in check_mail: quar+notif FAILED: temporarily unable to quarantine: 451 4.5.0 Local delivery(1) to
 /var/lib/amavis/virusmails/f/spam-fmQs5XfFlx+6.gz failed: Can't call method "value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line
 98., id=04791-01-5 at /usr/sbin/amavisd-new line 10371.
```


And when trying to install/update CPAN I'm getting this error - so how can I make this rigth again????? 
```
j# cpan
Terminal does not support AddHistory.

cpan shell -- CPAN exploration and modules installation (v1.7602)
ReadLine support available (try 'install Bundle::CPAN')

cpan> install Bundle::CPAN
CPAN: Storable loaded ok
Going to read /root/.cpan/Metadata
  Database was generated on Tue, 25 Nov 2008 04:26:52 GMT
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  ftp://mirrors.dotsrc.org/cpan/authors/01mailrc.txt.gz
Going to read /root/.cpan/sources/authors/01mailrc.txt.gz
CPAN: Compress::Zlib loaded ok
Can't call method "value" on an undefined value at /usr/share/perl5/IO/Uncompress/RawInflate.pm line 64.

cpan> install IO::Compresws::Rawdeflate
Going to read /root/.cpan/sources/authors/01mailrc.txt.gz
Can't call method "value" on an undefined value at /usr/share/perl5/IO/Uncompress/RawInflate.pm line 64.

cpan> quit
Terminal does not support GetHistory.
Lockfile removed.

```

So how do I fix this little problem, when even CPAN not can read it's own configuratiopn and files ????? 

Tia
Per

---

