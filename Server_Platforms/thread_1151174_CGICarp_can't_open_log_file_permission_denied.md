---
title: "CGI::Carp can't open log file permission denied"
date: 2009-05-06
forum: Server Platforms
---

### Post by rocheteau on 2009-05-06
Hi, 

I am running the Ubuntu LAMP server (uname -a --> 
2.6.20-15-server i686 GNU/Linux) and am in the process of learning to use CGI scripts. All was going well until I tried to use the following .cgi script to test out CGI::Carp logging to an error log file:


```
#!/usr/bin/perl
BEGIN {
        use CGI::Carp qw(carpout);
        open LOG, '>>', '/var/log/apache2/carperror.log' or die "Cannot open file: $!\n";
        carpout(LOG);
}
use CGI qw/:standard/;
print "Content-type: text/html\n\n";
$dbi->connect();
print "hi";
```

the "$dbi->connect();" line is there to create an error but I get no output to the carperror.log file. carperror.log has the same permissions and ownership as the other error logfiles in /var/log/apache2. The following is the output in the apache error.log file:

```
[Wed May 06 14:39:33 2009] [error] [client 10.116.18.74] Cannot open file: Permission denied
[Wed May 06 14:39:33 2009] [error] [client 10.116.18.74] BEGIN failed--compilation aborted at /var/www/CgiBin/PerlCgiBook/Chap01/Listing1_15.cgi line 6.
[Wed May 06 14:39:33 2009] [error] [client 10.116.18.74] Premature end of script headers: Listing1_15.cgi
```

I would appreciate any help I can get and thank you all in advance, 
R.

---

