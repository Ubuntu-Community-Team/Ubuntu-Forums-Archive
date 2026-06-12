---
title: "Problem with Barnyard on Ubuntu 9.10"
date: 2010-05-05
forum: Security
---

### Post by Fireblader9000 on 2010-05-05
Hallo zusammen,

ich bekomme folgende meldung wenn ich Barnyard starte:

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
database:           user = snort
database:  database name = snort
database:    sensor name = localhost:eth1
database:      sensor id = 1
database:  data encoding = hex
database:   detail level = full
database:     ignore_bpf = no
database: using the "alert" facility

        --== Initialization Complete ==--

  ______   -*> Barnyard2 <*-
 / ,,_  \  Version 2.1.8 (Build 251)
 |o"  )~|  By the SecurixLive.com Team: [http://www.securixlive.com/about.php](http://www.securixlive.com/about.php)
 + '''' +  (C) Copyright 2008-2010 SecurixLive.

           Snort by Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           (C) Copyright 1998-2007 Sourcefire Inc., et al.

WARNING: Ignoring corrupt/truncated waldofile '/var/log/snort/barnyard.waldo'
Opened spool file '/var/log/snort/snort.log.1273070088'
Closing spool file '/var/log/snort/snort.log.1273070088'. Read 0 records
Opened spool file '/var/log/snort/snort.log.1273075052'
Closing spool file '/var/log/snort/snort.log.1273075052'. Read 0 records
Opened spool file '/var/log/snort/snort.log.1273075686'
Closing spool file '/var/log/snort/snort.log.1273075686'. Read 0 records
Opened spool file '/var/log/snort/snort.log.1273082537'
Closing spool file '/var/log/snort/snort.log.1273082537'. Read 0 records
Opened spool file '/var/log/snort/snort.log.1273083233'
Closing spool file '/var/log/snort/snort.log.1273083233'. Read 0 records
Opened spool file '/var/log/snort/snort.log.1273083267'
Closing spool file '/var/log/snort/snort.log.1273083267'. Read 0 records
Opened spool file '/var/log/snort/snort.log.1273083348'
Waiting for new data


Eigentlich sollte ich nach dem starten von Barnyard doch events sehen können in Base oder ?

Vielen Dank

Michael

---

### Post by bodhi.zazen on 2010-05-05
See if this helps : [http://forums.skynet-solutions.net/viewtopic.php?f=14&t=18&start=10](http://forums.skynet-solutions.net/viewtopic.php?f=14&t=18&start=10)

---

