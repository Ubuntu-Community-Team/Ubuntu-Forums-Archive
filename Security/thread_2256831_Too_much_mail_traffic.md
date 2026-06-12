---
title: "Too much mail traffic"
date: 2014-12-15
forum: Security
---

### Post by Elmi77 on 2014-12-15
Hi,

my Ubuntu 12.04 LTS often shows me this in logwatch:

```

[COLOR=#000000][FONT=monospace] --------------------- Postfix Begin ------------------------ [/FONT][/COLOR]

[COLOR=#000000][FONT=monospace]        1   Miscellaneous warnings  [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    1.173M  Bytes accepted                           1,230,092[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    1.173M  Bytes sent via SMTP                      1,230,243[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]   26.932K  Bytes forwarded                             27,578[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] ========   ==================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]        4   Accepted                                   100.00%[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] --------   --------------------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]        4   Total                                      100.00%[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] ========   ==================================================[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace] [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]        5   Removed from queue      [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]        4   Sent via SMTP           [/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]        1   Forwarded 
[/FONT][/COLOR]
```

Since there is only one mail forwarded I think I don't have a spam-problem but the size of the mails transmitted is way too big. So the ones sent automatically do have a payload of a few hundred bytes only, means they never should have a total size of more than one MByte.

When I test my mail server using the antispam-/open-relay-tools aout htere, everything is fine. But the abount of data still seems to be way too big for me.

So...any idea what I could check to track down this problem?

Thanks!

---

### Post by TheFu on 2014-12-16
Perhaps MIME attachments?

The RFCs for email require 7-bit ASCII text for the message, but many client programs will convert that from more complex editors or word processors and still include those other versions in a MIME attachment.

---

