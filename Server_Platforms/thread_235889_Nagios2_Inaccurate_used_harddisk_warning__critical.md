---
title: "Nagios2: Inaccurate used harddisk warning / critical status reporting"
date: 2006-08-13
forum: Server Platforms
---

### Post by Akhran on 2006-08-13
Checkcommand.cfg
----------------

define command {
command_name check_nt_useddiskusage
command_line /usr/lib/nagios/plugins/check_nt -H $HOSTADDRESS$ -v USERDDISKSPACE -w $ARG1$ -c $ARG2$ -l C
}

hosts.cfg
---------

define service {
use generic-service
host_name testpc
service_description Check Used Disk Usage
check_command check_nt_useddiskusage!10.10.10.10!80!90
}

However, when Nagios run a check on the host, it reports Critical status even though the critical level is set at 90% in the hosts.cfg file (as shown below).


Current Status: CRITICAL 
Status Information: C:\ - total: 2.00 Gb - used: 1.73 Gb (86%) - free 0.27 Gb (14%)
Performance Data: 'C:\ Used Space'=1.73Gb;0.20;1.60;0.00;2.00


Any advice please?

Thanks.

---

