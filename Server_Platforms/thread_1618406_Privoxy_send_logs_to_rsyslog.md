---
title: "Privoxy send logs to rsyslog????"
date: 2010-11-10
forum: Server Platforms
---

### Post by rjt290 on 2010-11-10
Hi all, 

First of all I would like to say thanks to everyone just by browsing this forum and using google I have managed to get Ubuntu server up and running with rsyslog receiving logfiles from various sources, piping them to mysql and searchable/viewable thorugh phplogcon.

The box I am using to do this, also has my privoxy install on it, I was wondering how I could get my privoxy logs to show up in phplogcon. I made adjustments to the .conf and confirmed that logging is working for all visited urls, but I have no idea how to get rsyslog to identify the logfiles if I add a line to the rsyslog.conf telling it to look at /var/log/privoxy it says it cannot open the location 

if I add a line asking it to look @ /var/log/pirvoxy/logfile it does not give an error but nothing shows up in phplogcon. 

I also attempted to do the same thing with squid as I found a site that said to just add teh line 

access_log syslog squid 

then restart the squid service and it should start working but that just gave me some really strange behaviour 

So I am open ot using any proxy suggested so long as someone can assist me to get all web traffic outputted to phpsyslogcon. 

Any and all help would be appreciated

---

### Post by rjt290 on 2010-11-11
anyone have any ideas???

---

