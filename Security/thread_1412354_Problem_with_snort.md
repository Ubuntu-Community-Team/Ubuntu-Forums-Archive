---
title: "Problem with snort"
date: 2010-02-21
forum: Security
---

### Post by Saif24 on 2010-02-21
Hi,i have install snort and ACID (base) and the necessary via package! but when i started snort with " snort -c /etc/snort/snort.conf " it show me this error:

ERROR: database: mysql_error: Access denied for user 'snort'@'localhost' (using password: NO)
Fatal Error, Quitting..

and i'm sure that i make the passwoed into snort.conf! also the foldar /var/www had just one file " index.html ".
please,someone help me!:(

---

### Post by bodhi.zazen on 2010-02-21
The problem is that snort is not connecting to mysql.

We need a lot more information to help you, how did you install snort ? How did you configure mysql ? either post or confirm that you configured snort in snort.conf.

---

### Post by Saif24 on 2010-02-22
Hi,
for the install of snort i use this guide [http://openmaniak.com/fr/snort_tutorial_snort.php](http://openmaniak.com/fr/snort_tutorial_snort.php) and that's all. So this is how i tested snort: 

ping [www.google.fr](www.google.fr)

and in the same time i run

root@saif-laptop:/home/saif# snort -v
Running in packet dump mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Verifying Preprocessor Configurations!
***
*** interface device lookup found: eth0
***

Initializing Network Interface eth0
OpenPcap() device eth0 network lookup: 
        eth0: no IPv4 address assigned
Decoding Ethernet on interface eth0

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.4.1 (Build 38)  
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/team.html](http://www.snort.org/team.html)
           Copyright (C) 1998-2009 Sourcefire, Inc., et al.
           Using PCRE version: 7.8 2008-09-05

Not Using PCAP_FRAMES



and no answer! :(

---

### Post by bodhi.zazen on 2010-02-22
From what you posted snort seems to run just fine. I see no error messages and the output, with the little ascii pig at the bottom, is perfectly normal.

You can not test snort with ping or port scanners.

---

### Post by Saif24 on 2010-02-23
Please can you told me a simple example betwen 2 pc with a null modem cable witch can i be sure that i get an alerts. Thanks

---

### Post by bodhi.zazen on 2010-02-23
If you want alerts, connect directly to the internet or forward ports from your router.

If you want to generate alerts, that starts to get into grey hat / black hat (cracking) very fast and it is a slippery slope.

Do a google search.

Explaining network protocols and interpreting packets is a long  discussion and again google is your friend here as well.

See this article, at the bottom, for hwo snort sniffs and logs packets.

[http://www.ibm.com/developerworks/web/library/wa-snort1/](http://www.ibm.com/developerworks/web/library/wa-snort1/)

If you start snort from the command line and see the ascii pig it is working.

>    ,,_     -*> Snort! <*-
  o"  )~  
   ''''   
You do not need any further "testing" beyond that, although you will need to learn and understand the snort rules.

---

