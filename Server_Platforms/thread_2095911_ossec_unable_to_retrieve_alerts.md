---
title: "ossec: unable to retrieve alerts"
date: 2012-12-18
forum: Server Platforms
---

### Post by sowdust on 2012-12-18
Hello everyone,

I have recently installed ossec and its web-ui from the repositories.
I have configured its parameters, have added www-data to the /var/ossec folder, changed its permissions to 755 (although not necessary) ...
I did not touch php nor apache configuration.

Now whenever I try accessing the web gui I get this message:
> No integrity checking information available.
Nothing reported as changed.
Unable to retrieve alerts.

I noticed that log files in the folder /var/ossec/log are all empty.

If I try starting ossec ```
/var/ossec/bin/ossec-control start
``` nothing appears at console, but on the web ui I see the line > Name: ossec-server
  IP: 127.0.0.1
  Last keep alive: 2012 Dec 18 15:31:38

but the command ```
ps aux | grep ossec 
``` only returns the line for  "grep" having "ossec" as an argument.

I would infer ossec is not running but I honestly wouldn't know what to do with that... any ideas on this?


Thanks in advance!

---

