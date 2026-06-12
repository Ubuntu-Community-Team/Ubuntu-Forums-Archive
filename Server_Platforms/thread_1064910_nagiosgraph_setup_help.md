---
title: "nagiosgraph setup help"
date: 2009-02-09
forum: Server Platforms
---

### Post by geraldbrandt on 2009-02-09
Hi,

I've installed nagios3 and nagiosgrapher under intrepid, from the repos.  Nagios is working just fine, but I can't get nagiosgrapher to work at all.

All the wen sites I've hit say to use insert.pl or some other perl file that the installer didn't give me.

Does anyone have experience setting up nagiosgrapher from the repos that can lend me a hand?

Gerald

---

### Post by deadlines on 2009-02-12
Sadly, in my experience, the repos have always been woefully behind on the latest Nagios builds so I ended up compiling my installation.  To address your question, I would recommend considering perfparse as an alternative.  No matter how you slice it, setting up performance data gathering plugins for Nagios can be painful, but I've personally  always had the best luck with perfparse.

---

### Post by illsen on 2009-03-14
Hi,

I installed nagios3 on ubuntu intrepid system and added nagiosgrapher sucessfully. I had to change /etc/nagios3/ and add the following lines:

process_performance_data=1
service_perfdata_command=ngraph-process-service-perfdata-pipe

after 
/etc/init.d/nagios3 restart 
nagios sends performance data to nagiosgrapher. After some time the directory 

/etc/nagiosgrapher/nagios3/serviceext 

should fill up with files named <hostname>.cfg. This take some minutes (due to the nature of nagios3 and nagiosgrapher). But even if the files appear nagios3 does not know about them yet. Another 

/etc/init.d/nagios3 restart 

makes them available for nagios and you can see new links on the page "Service details".

Regards

---

### Post by smo0th on 2010-06-25
old post but useful!

thanks illsen!!

=D>=D>=D>

---

### Post by deadlines on 2010-06-27
> **smo0th said:**
> old post but useful!

thanks illsen!!

=D>=D>=D>

For what it's worth, [PNP4Nagios]("http://docs.pnp4nagios.org/start") is probably one of the best solutions out there these days, if you're looking into graphing nagios performance data.

---

### Post by dbenamy on 2010-08-04
Still useful on 10.04. Thanks! A small typo- the config file mentioned should say /etc/nagios3/nagios.cfg.

---

### Post by pipemartinm on 2010-08-04
Interesting, I might look into it. I've never been able to get nagiosgrapher to graph any services other than ping.

---

### Post by ziggan on 2011-02-23
> **dbenamy said:**
> Still useful on 10.04. Thanks! A small typo- the config file mentioned should say /etc/nagios3/nagios.cfg.
bump!
How did you get this to work? I'm using 10.10. I seem to be missing something.. adding those lines don't seem to do it for me. I installed both nagios and the grapher through "ubuntu software center" hoping that would solve my problems. Needless to say it didn't. Mind giving me some pointers?

/ziggan

---

### Post by mdacova on 2011-10-12
guys thanks helped me

---

