---
title: "dapper to hardy - amavis in civicrm problems"
date: 2008-07-30
forum: Server Platforms
---

### Post by rick23 on 2008-07-30
I just upgraded from dapper to hardy.  The upgrade went fairly well, but now I am unable to run mail because the amavis config file for the civicrm program is unable to recognize the global symbols (e.g. Starting amavisd: Error in config file "/etc/amavis/conf.d/40-civimail": Global symbol "$civicrm_soap_proxy" requires explicit package name at /etc/amavis/conf.d/40-civimail line 5.).  The same error follows for the global symbol $civicrm_soap_login and $civicrm_soap_pass.

Does anyone have any experience with civicrm on dapper, and php5 upgrade problems from dapper to hardy?  Thanks in advance.
Rick

---

