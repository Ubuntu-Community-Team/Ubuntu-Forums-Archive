---
title: "(D)DoS-Deflate and Dapper?"
date: 2008-06-17
forum: Security
---

### Post by wickid on 2008-06-17
Hello everyone,

I'm a bit of a Linux newb, but I am really enjoying learning with Ubuntu.  I started hosting a website using Plesk and Ubuntu 7.10 (Sorry for the title error, actully Gutsy).  I installed APF on my machine which works well; however my site gets flooded with strange requests from the same IP address constantly.  I'll manually block it with APF and then later on I will get similar requests flooding my machine again from a different IP address.  I read the DDoS Deflate could work well in this instance since it will block conections that are listed in netstat over a certain amount.  The only problem is I can't seem to get DDoS-Deflate to work on my machine.  When I run the program I get the following error:

[: 85: ==: unexpected operator
DDoS-Deflate version 0.6
Copyright (C) 2005, Zaf <zaf@vsnl.com>

$CONF not found.

Unfortunately I am not a coder and I have scoured google looking for something similar to what I am receiving with no luck.  If anyone has any ideas please let me know.  Alternatively, if you are aware of any other solutions to block large amounts of connections from the same IP address I'd love to hear them.

---

### Post by milosz.galazka on 2008-06-24
Do you have a file */usr/local/ddos/ddos.conf* ?

Script should be installed in such way:
```
$ wget http://www.inetbase.com/scripts/ddos/install.sh
$ chmod 0700 install.sh
$ sudo ./install.sh

```

---

### Post by harry71194 on 2009-08-25
Know it is an old thread, but for OP if he never solved his problem: [http://ubuntuforums.org/showpost.php?p=7709243&postcount=7](http://ubuntuforums.org/showpost.php?p=7709243&postcount=7)

---

### Post by jonathanross on 2009-08-26
Add "#!/bin/bash" as the first line. Works for me.

---

