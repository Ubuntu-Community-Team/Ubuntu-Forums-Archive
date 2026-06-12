---
title: "Problem with Barnyard2 on Ubuntu 12.04"
date: 2013-10-11
forum: Security
---

### Post by n8ywTDk on 2013-10-11
hello everybody!!
i have a problem with mine barnyard2 when I run command:
barnyard2 -c /etc/snort/barnyard2.conf

NOTE: I have installed snort with barnyard2 in Virtual Machine.

i get this error:

carlos@carlos-VirtualBox:~$ barnyard2 -c /etc/snort/barnyard2.conf
Running in Continuous mode

        --== Initializing Barnyard2 ==--
Initializing Input Plugins!
Initializing Output Plugins!
Parsing config file "/etc/snort/barnyard2.conf"
Log directory = /var/log/barnyard2
database: 'mysql' support is not compiled into this build of snort

ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
'mysql' support.

If this build of snort was compiled by you, then re-run the
the ./configure script using the '--with-mysql' switch.
For non-standard installations of a database, the '--with-mysql=DIR'
syntax may need to be used to specify the base directory of the DB install.

See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..

---

### Post by n8ywTDk on 2013-10-22
I found the error, the path mysql wasn't right, the correct was: ./configure --with-mysql-libraries=/usr/lib/i386-linux-gnu/ and make make install

I solved this problem but appeared other problem with waldo file

I run command:
carlos@carlos-VirtualBox:~$ barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/barnyard2/barnyard2.waldo
Running in Continuous mode

        --== Initializing Barnyard2 ==--
Initializing Input Plugins!
Initializing Output Plugins!
Parsing config file "/etc/snort/barnyard2.conf"
Log directory = /var/log/barnyard2
database: compiled support for (mysql)
database: configured to use mysql
database: schema version = 107
database:           host = localhost
database:           user = root
database:  database name = snort
database:    sensor name = snort:eth0
database:      sensor id = 3
database:     sensor cid = 1
database:  data encoding = hex
database:   detail level = full
database:     ignore_bpf = no
database: using the "log" facility

        --== Initialization Complete ==--

  ______   -*> Barnyard2 <*-
 / ,,_  \  Version 2.1.9 (Build 263)
 |o"  )~|  By the SecurixLive.com Team: [http://www.securixlive.com/about.php](http://www.securixlive.com/about.php)
 + '''' +  (C) Copyright 2008-2010 SecurixLive.

           Snort by Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           (C) Copyright 1998-2007 Sourcefire Inc., et al.

WARNING: Ignoring corrupt/truncated waldofile '/var/log/barnyard2/barnyard2.waldo'
Waiting for new spool file

snort conf >>> [http://pastebin.ca/2469866](http://pastebin.ca/2469866)

barnyard2.conf>>> [http://pastebin.ca/2469868](http://pastebin.ca/2469868)

---

### Post by n8ywTDk on 2013-10-23
I solved the problem first is need delete waldo file
after create output for snort.conf output unified2: filename snort.u2, limit 128
after I run command:


root@carlos-VirtualBox:~# barnyard2 -c /etc/snort/barnyard2.conf -d /var/log/snort -f snort.u2 -w /var/log/snort/barnyard2.waldo
Running in Continuous mode


        --== Initializing Barnyard2 ==--
Initializing Input Plugins!
Initializing Output Plugins!
Parsing config file "/etc/snort/barnyard2.conf"
Log directory = /var/log/barnyard2
database: compiled support for (mysql)
database: configured to use mysql
database: schema version = 107
database:           host = localhost
database:           user = root
database:  database name = snort
database:    sensor name = snort:eth0
database:      sensor id = 3
database:     sensor cid = 11
database:  data encoding = hex
database:   detail level = full
database:     ignore_bpf = no
database: using the "log" facility


        --== Initialization Complete ==--


  ______   -*> Barnyard2 <*-
 / ,,_  \  Version 2.1.9 (Build 263)
 |o"  )~|  By the SecurixLive.com Team: [http://www.securixlive.com/about.php](http://www.securixlive.com/about.php)
 + '''' +  (C) Copyright 2008-2010 SecurixLive.


           Snort by Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           (C) Copyright 1998-2007 Sourcefire Inc., et al.


Using waldo file '/var/log/snort/barnyard2.waldo':
    spool directory = /var/log/snort
    spool filebase  = snort.u2
    time_stamp      = 1382474203
    record_idx      = 20
Opened spool file '/var/log/snort/snort.u2.1382474203'
Closing spool file '/var/log/snort/snort.u2.1382474203'. Read 20 records
Opened spool file '/var/log/snort/snort.u2.1382479354'
Waiting for new data

---

