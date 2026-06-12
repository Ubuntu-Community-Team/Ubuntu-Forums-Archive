---
title: "ubuntu + zimbra POSTFIX conditional CONTENT-TYPE value REPLACE/rewrite"
date: 2015-08-17
forum: Server Platforms
---

### Post by zlaci on 2015-08-17
Hello!

I am using Ubuntu 14.04 LTS with Zimbra 8.6 FOSS.
I have a mailbox which regularly receives .csv files.

However, in the source its content-type is: [B]Content-Type: application/x-zip-compressed

[/B]I would like to replace the Content-Type value form the above to **Content-Type: application/octet-stream; **so Zimbra and other mailer agents (e.g. Thunderbird) would open the attachment as a csv file not as a zip file.

As I googled this could be done with postfix body_checks filter REPLACE or mime_header_checks, however, I do not know and understand postfix config files and syntax. T
This rule should be conditional as well, i.e. applied on certain letters with a given sender (from field).

Do you guys have any hint or idea, where to start?

Thanks,

Laszlo

---

