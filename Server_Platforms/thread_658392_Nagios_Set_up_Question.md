---
title: "Nagios Set up Question"
date: 2008-01-04
forum: Server Platforms
---

### Post by LookUpSeeBlu on 2008-01-04
I am brand new to nagios so forgive my "nagios virginity" but I am installing for the first time and am having a few troubles.  I am also relatively new to Ubuntu (about a month or so - I am used to Gentoo a little more) so please have patience.

After working through the Quick Install on Nagios.org, I am getting:

Whoops!

Error: Could not read host and service status information!


Nagios is running.  THe log file has the following repeatedly:

[1199422971] Error: Could not re-connect to database server on host '' for status data.  I'll keep trying every 60 seconds...
[1199423571] Error: Could not re-connect to database server on host '' for status data.  I'll keep trying every 60 seconds...
[1199424171] Error: Could not re-connect to database server on host '' for status data.  I'll keep trying every 60 seconds...
[1199424771] Error: Could not connect to MySQL database '' on host '' using username '' and password 'XXXXXX'.  Retention data will not be processed or saved!

I have tried looking in the nagios.cfg and cgi.cfg files to see if one is to DB and the other is trying to access txt files but I am not sure how to check this.

Thanks very much for any help.  I have heard that Nagios is great once you get it running and understand it and I am thankful for any support.

---

### Post by HermanAB on 2008-01-05
Uhmm, the only thing I can say is that setting up Zabbix is a heckavalot easier than Nagios...

I don't recommend using Nagios, though it can work - it is just a PITA.

Cheers,

Herman

---

