---
title: "Nagios on 10.10 64 bit checking windows servers; possible bug?"
date: 2010-12-29
forum: Server Platforms
---

### Post by djroot2 on 2010-12-29
It seems the file /etc/nagios-plugins/config/nt.cfg has an extra -v in the arguments.

```
define command {
 command_name    check_nt
 command_line    /usr/lib/nagios/plugins/check_nt -H $HOSTADDRESS$ -p 12489 -v $ARG1$ **-v** $ARG2$
}

```

This causes check_nt to throw an error and outputs the expected syntax.  Removing the -v before $ARG2$ seems to have fixed it.

Has anyone else had this problem?

---

