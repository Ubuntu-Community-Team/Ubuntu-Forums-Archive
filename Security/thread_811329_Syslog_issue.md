---
title: "Syslog issue"
date: 2008-05-29
forum: Security
---

### Post by adimenia on 2008-05-29
Hello 

im trying to use syslog to relay messages from network devices such as juniper ssg and fortinet firewall and im having this odd problem
when writing the logs locally everything get written both local events and device events (juniper fortinet) now when im configuring the syslog server to relay the messages to a seim system 
(*.debug               @ipaddress ) where the ip address is my seim system i only receive the local Linux events of the syslog server all the events from my juniper and fortinet are gone nothing from those devices gets relayed i used tcpdump (my syslog machine has only one NIC) and i cant see the events coming to my syslog server 
if i change back the configuration of the syslog server to write the logs locally (*.debug         /var/log/all.log) everything gets written to the log file including the events from my juniper and fortinet i dont know what to do if anyone has ANY idea ill be most thankful:)

---

### Post by HalPomeranz on 2008-05-29
From the syslogd manual page:

```

       -h     By  default  syslogd  will not forward messages it receives from
              remote hosts.  Specifying this switch on the command  line  will
              cause  the log daemon to forward any remote messages it receives
              to forwarding hosts which have been  defined.   This  can  cause
              syslog  loops  that fill up hard disks quite fast and thus needs
              to be used with caution.

```

So edit /etc/default/syslogd and add the "-h" option to the SYSLOGD variable.  The configuration on your box will probably end up looking something like:

```

SYSLOGD="-r -h"

```

Is there a reason why you don't have the Juniper and Fortinet devices log directly to your SEIM server?  It seems weird to relay the events through your Linux box.

Also, you might want to check out Syslog-NG ([http://www.balabit.com/network-security/syslog-ng/](http://www.balabit.com/network-security/syslog-ng/)).  If you're looking at turning a Linux box into a central syslog server for your network, Syslog-NG is definitely the right way to go.

---

