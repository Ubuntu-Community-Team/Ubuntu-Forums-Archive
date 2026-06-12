---
title: "help!!! oracle sqlplus client disconnects upon login"
date: 2010-01-19
forum: Server Platforms
---

### Post by tianshuo on 2010-01-19
platform: ubuntu 9.10
using instant client, made using rpm version 11.2.0.1.0 production


test 1, perl
```
#!/usr/bin/perl
my $dbh=DBI->connect('dbi:Oracle:host=192.168.1.10;sid=db;port=1521','db','db') || die "Cannot open connection to oracle: $DBI::errstr\n";
die "byebye";
```

does not die, exits without any prompt, very strange

test 2, sql*plus /nolog

prompts
```
SQL*Plus: Release 11.2.0.1.0 Production on Tue Jan 19 19:48:52 2010

Copyright (c) 1982, 2009, Oracle.  All rights reserved.

SQL> 

```

type
```
connect db/db@192.168.1.10/db
```

directly exits without any warning

this is so frustrating

---

