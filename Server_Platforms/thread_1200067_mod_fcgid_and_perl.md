---
title: "mod_fcgid and perl"
date: 2009-06-29
forum: Server Platforms
---

### Post by SvenNissel on 2009-06-29
Hy,

I'm using mod_fcgid with PHP5. Everything fine.
Now I want to configure fcgid with Perl.

I have try something.

Aapche VHOST config: 
```
...
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
SuexecUserGroup "itjungs" "kunden"
AddHandler fcgid-script .php .pl
FCGIWrapper /var/www/virtual/domain.de/cgi-bin/php-fcgi-wrapper.bash .php
FCGIWrapper /var/www/virtual/domain.de/cgi-bin/perl-fcgi-wrapper.bash .pl

Alias /fcgi-bin/ /var/www/virtual/domain.de/cgi-bin/
<Location /fcgi-bin/>
        SetHandler fcgi-script
        Options +ExecCGI
</Location>
...
```

The Wrapper
```
#!/bin/sh
exec /usr/bin/perl
```

my testscript
```
#!/usr/bin/perl

use FCGI; # Imports the library; required line

# Initialization code

$cnt = 0;

# Response loop

while (FCGI::accept >= 0) {
  print "Content-type: text/html\r\n\r\n";
  print "<head>\n<title>FastCGI Demo Page (perl)</title>\n</head>\n";
  print  "<h1>FastCGI Demo Page (perl)</h1>\n";
  print "This is coming from a FastCGI server.\n<BR>\n";
  print "Running on <EM>$ENV{SERVER_NAME}</EM> to <EM>$ENV{REMOTE_HOST}</EM>\n<$
   $cnt++;
  print "This is connection number $cnt\n";
}
```

Now I get a 500 Internal Server Error when I start the script with the browser.

Error Log:
```
[Sat Jun 27 09:49:58 2009] [notice] mod_fcgid: call /var/www/virtual/domain.de/htdocs/test.pl with wrapper /var/www/virtual/domain.de/cgi-bin/php5-default/perl-fcgi-wrapper.bash
[Sat Jun 27 09:49:58 2009] [warn] (104)Connection reset by peer: mod_fcgid: read data from fastcgi server error.
[Sat Jun 27 09:49:58 2009] [error] [client 192.168.1.133] Premature end of script headers: test.pl
[Sat Jun 27 09:50:01 2009] [notice] mod_fcgid: process /var/www/virtual/domain.de/htdocs/test.pl(2307) exit(communication error), terminated by calling exit(), return code: 0
```

Suexec has no errors in log.


Can somebody help me?

[EDIT]I'm using Ubuntu 9.04[/EDIT]

---

