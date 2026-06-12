---
title: "Text/CSV/Simple.pm not found"
date: 2011-08-12
forum: Server Platforms
---

### Post by PhonicLynx on 2011-08-12
I've just tried to run a script which is using perl with these modules:
```
use strict;
use LWP::Simple;
use Text::CSV::Simple;
use Proc::Simple;
use Proc::Killall;
use Time::localtime;
```
When I try and run the scrip I get this error message:
```
Can't locate Text/CSV/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at ./addblock.pl line 5.
```

I have tried looking for the installer for these in ubuntu 11.04 but can't seem to get it to run or figure out how its supposed to find the file.

---

