---
title: "Setup Nagios with Qmail?"
date: 2011-04-28
forum: Server Platforms
---

### Post by sentinelace on 2011-04-28
I have nagios up and running.  My problem is it is running on a server that uses qmail not postfix.  I cannot seem to get any emails to the qmail log at all.  Here is my commands.cfg file:
 
```
usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /var/qmail/bin/sendmail -s "** $NOTIFICATIONTYPE$ Host Alert: $HOSTNAME$ is $HOSTSTATE$ **" $CONTACTEMAIL$->/usr/bin/printf "%b" "***** Nagios *****\n\nNotification Type: [COLOR=#777777]$NOTIFICATIONTYPE$[/COLOR]\nHost: [COLOR=#777777]$HOSTNAME$[/COLOR]\nState: [COLOR=#777777]$HOSTSTATE$[/COLOR]\nAddress: [COLOR=#777777]$HOSTADDRESS$[/COLOR]\nInfo: [COLOR=#777777]$HOSTOUTPUT$[/COLOR]\n\nDate/Time: [COLOR=#777777]$LONGDATETIME$[/COLOR]\n" | /var/qmail/bin/sendmail -s "** [COLOR=#777777]$NOTIFICATIONTYPE$[/COLOR] Host Alert: [COLOR=#777777]$HOSTNAME$[/COLOR] is [COLOR=#777777]$HOSTSTATE$[/COLOR] **" [COLOR=#777777]$CONTACTEMAIL$[/COLOR]
```
 
This is not working at all.  How do I configure nagios with qmail?

---

