---
title: "Nessus security question - PUT method"
date: 2005-07-13
forum: Server Platforms
---

### Post by ibanez88 on 2005-07-13
I originally posted this on the Desktop Help forum, but it seems more appropriate here.

I issued a Nessus scan using localhost as the host. I received an NG report saying that I should remove the PUT method capability from my server.. (edit: I'm not running a server, just a desktop workstation with Firefox, Evolution, OpenOffice, XMMS,  etc.)

I have the default Ubuntu settings with the exception of scanning for LAN printers (enabled in System > Administration > Printing). Could this be the cause for the warning in Nessus?

And how would I correct this supposed vulnerability? SHOULD I even consider it or will it disable some needed functionality?

Thanks in advance.

---

### Post by safecracker on 2005-07-14
It's making a reference to the CUPS server. I currently donno of a vulnerability using the PUT method to do with CUPS and I'm sure your not allowing that port to the net. I wouldn't worry about it.

---

