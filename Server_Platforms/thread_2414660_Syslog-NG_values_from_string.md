---
title: "Syslog-NG values from string"
date: 2019-03-13
forum: Server Platforms
---

### Post by dspit on 2019-03-13
Hello guys,

I have a big problem, I need to extract some values from the field $MESSAGE and to assign them to a different variables.
 
The string is as follows:

```
[COLOR=#0000E9][FONT=Times]_[[NotificationHandler] NMS error: ERROR Net: NET Station: STATION serial-num: ]("http://212.43.102.124:8080/index.php#")01234_[/FONT][/COLOR]

```

and I need to export to MySQL Database the following data:

**Columns     Data**
Error           ERROR
Net             NET
Station        STATION
Serial          01234

Please, note that the length of values is not always the same (like: LAN, TLC, STDWN, etc), also for the Nets.
It would be ok also if I can extract only SERIAL value (always 5 digit).

Thank you for your help.

---

### Post by fekete77-robert on 2019-03-14
Hi, 
syslog-ng has several parsers that can help you, see the documentation for a complete list:  [http://support.oneidentity.com/technical-documents/syslog-ng-open-source-edition/administration-guide/parser-parse-and-segment-structured-messages](http://support.oneidentity.com/technical-documents/syslog-ng-open-source-edition/administration-guide/parser-parse-and-segment-structured-messages)
Unfortunately, the log message you are trying to parse is not well-structured, there are no separators between the pairs, so you can't just use the csv-parser or the key-value parser. I think your best bet is to use either the db-parser ([http://support.oneidentity.com/technical-documents/syslog-ng-open-source-edition/administration-guide/db-parser-process-message-content-with-a-pattern-database-patterndb](http://support.oneidentity.com/technical-documents/syslog-ng-open-source-edition/administration-guide/db-parser-process-message-content-with-a-pattern-database-patterndb)) or the Python parser ([http://support.oneidentity.com/technical-documents/syslog-ng-open-source-edition/administration-guide/parser-parse-and-segment-structured-messages/the-python-parser](http://support.oneidentity.com/technical-documents/syslog-ng-open-source-edition/administration-guide/parser-parse-and-segment-structured-messages/the-python-parser)). 
The db-parser is available in older syslog-ng versions as well, for the Python parser you need at least version 3.10. Using the Python parser is probably easier, as the db-parser can be a bit difficult to set up. You can find an introductory blogpost about the Python parser here: [https://www.syslog-ng.com/community/b/blog/posts/parsing-log-messages-with-the-syslog-ng-python-parser](https://www.syslog-ng.com/community/b/blog/posts/parsing-log-messages-with-the-syslog-ng-python-parser)
HTH

---

