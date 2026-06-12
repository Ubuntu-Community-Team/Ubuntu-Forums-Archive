---
title: "Permission problem"
date: 2010-02-19
forum: Server Platforms
---

### Post by VoodooLoveDog on 2010-02-19
I hope this is the home for this topic. I apologize if this belongs in somewhere else.

I'm having a little trouble getting some software to work and it looks like it's a result of permissions. 

I'm running arpwatch on my server and want to use the perl script arpwatch2html.pl. I dropped it in the cgi-bin directory, renamed it and gave it permissions to execute:

chmod a+x /usr/lib/cgi-bin/arpwatch2html.cgi

However, looking at the error logs for apache2 tells me that it can't read the /var/lib/arpwatch/arp.dat file. 

ERROR: could not open /var/lib/arpwatch/arp.dat for reading: Permission denied

Confused, because the permissions on the arp.dat file states that everyone can read it:

-rw-r--r--

root owns arpwatch2html.cgi and arpwatch owns arp.dat which I think has something to do with it, but I don't know how to allow the script access to that file.

Any help is much appreciated.

---

### Post by VoodooLoveDog on 2010-02-26
My assumption was that www-data needed rights to arp.dat so I dropped www-data into the arpwatch group. That has not solved my problem. Apache2 error.log still reports permission denied on that arp.dat file. 

A little help please?

---

