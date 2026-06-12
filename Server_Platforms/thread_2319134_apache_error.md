---
title: "apache error"
date: 2016-04-01
forum: Server Platforms
---

### Post by midhun4 on 2016-04-01
When starting apache in ubuntu 12.04LTS i get this error message,can somebody tel me whats wrong?



"apache2: Syntax error on line 237 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/nagios.conf: No such file or directory"

---

### Post by slickymaster on 2016-04-01
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by midhun4 on 2016-04-01
Syntax error on line 14 of /etc/apache2/sites-enabled/nagios.conf:
Invalid command '<IfVersion', perhaps misspelled or defined by a module not included in the server configuration
Action 'start' failed.


I s it anything with nagios conf?

---

### Post by SeijiSensei on 2016-04-01
Include the contents of nagios.conf inside [noparse]```

```[/noparse] tags.  Otherwise we'll all be shooting in the dark.

---

