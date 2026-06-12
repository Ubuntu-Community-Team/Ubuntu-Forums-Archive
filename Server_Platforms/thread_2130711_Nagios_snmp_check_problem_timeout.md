---
title: "Nagios snmp_check problem timeout"
date: 2013-03-30
forum: Server Platforms
---

### Post by mancora on 2013-03-30
Hi,

I am configuring nagios for snmp monitoring and I havent go further after getting a timeout error from the monitoring console from Nagios.
As far as I can see everything is well configured. But this is my first nagios implementation and I am not sure as I am learning on the way.
I am making snmpgets from the command line which are succesfull but Nagios system gets a timeout. Any idea what is the problem.

details from behavior and configuration below.

Thanks!

Linux nagios01 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Packet nagios3

Package nagios3:
i   3.2.3-3ubuntu1
----------------------------------------------------------------------------------------------
Error from web interface

nagios02
    
    
CPU Load
    
    UNKNOWN     2013-03-29 16:18:43     0d 21h 28m 14s     4/4     External command error: Timeout: No Response from 192.168.1.250:161. 
    
CPU Stats
    
    UNKNOWN     2013-03-29 16:14:58     0d 22h 21m 36s     4/4     External command error: Timeout: No Response from 192.168.1.250:161. 

-----------------------------------------------------------------------------
Test from CLI


sudo /usr/lib/nagios/plugins/check_snmp -H 192.168.1.250 -C pedropicapiedra -o .1.3.6.1.4.1.2021.11.9.0,.1.3.6.1.4.1.2021.11.10.0,.1.3.6.1.4.1.2021.11.11.0 -l 'CPU usage (user system idle)' -u '%'

SNMP OK - CPU usage (user system idle) 0 % 0 99 | CPU usage (user system idle)=0 iso.3.6.1.4.1.2021.11.10.0=0 iso.3.6.1.4.1.2021.11.11.0=99 


 
sudo /usr/lib/nagios/plugins/check_snmp -H 192.168.1.250 -C pedropicapiedra -o .1.3.6.1.4.1.2021.10.1.5.1,.1.3.6.1.4.1.2021.10.1.5.2,.1.3.6.1.4.1.2021.10.1.5.3 -w :70,:70,:70 -c :90,:90,:90 -l load

SNMP OK - load 0 1 5 | load=0 iso.3.6.1.4.1.2021.10.1.5.2=1 iso.3.6.1.4.1.2021.10.1.5.3=5

-----------------------------------------------------------------------------

Service Definition

define service{
         use                             generic-service
         name                            CPU-stats
         check_command                   snmp_cpustats!supersecreto 
         service_description             CPU Stats
         host_name                       nagios02
         notification_interval           0
         notification_options            c,r
         notification_period             24x7
         register                        0
        }

define service{
         use                             generic-service
         name                            CPU Load
         check_command                   snmp_load!supersecreto!70!90
         service_description             CPU Load
         host_name                       nagios02
         notification_interval           0
         notification_options            c,r
         notification_period             24x7
         register                        0
        }

 
Host Definition

define host{

    use                generic-host

    host_name            nagios02

    alias                unix nagios 02

    address                192.168.1.250
}


command definition

nagios01:/etc/nagios-plugins/config$ pwd
/etc/nagios-plugins/config

snmp.cfg

#define service{
 #       use                             generic-service         ; Name of service template to use
  #      host_name                       nagios02
   #     service_description             CPU load
#        check_command               snmp_load -H $HOSTADDRESS$ -C supersecreto -o .1.3.6.1.4.1.2021.10.1.5.1,.1.3.6.1.4.1.2021.10.1.5.2,.1.3.6.1.4.1.2021.10.1.5.3 -w 70 -c 90 -l load
 #       }



#define service{
 #       use                             generic-service         ; Name of service template to use
#        host_name                       nagios02
#        service_description             CPU usage
#        check_command                  snmp_cpustats -H '$HOSTADDRESS$' -C supersecreto -o .1.3.6.1.4.1.2021.11.9.0,.1.3.6.1.4.1.2021.11.10.0,.1.3.6.1.4.1.2021.11.11.0 -l 'CPU usage (user system idle)' -u '%'
 #       }


nagios.cfg

# Debian also defaults to using the check commands defined by the debian
# nagios-plugins package
cfg_dir=/etc/nagios-plugins/config

All configuration files are located in the right directories and defined in the nagios.cfg

------------------------------------------------------------------------------------------------

[1364570324.120066] [016.0] [pid=6041] Attempting to run scheduled check of service 'CPU Load' on host 'nagios02': check options=0, latency=0.120000
[1364570324.120183] [016.0] [pid=6041] Checking service 'CPU Load' on host 'nagios02'...
[1364570324.120253] [2320.2] [pid=6041] Raw Command Input: /usr/lib/nagios/plugins/check_snmp -H '$HOSTADDRESS$' -C '$ARG1$' -o .1.3.6.1.4.1.2021.10.1.5.1,.1.3.6.1.4.1.2021.10.1.5.2,.1.3.6.1.4.1.2021.10.1.5.3 -w :'$ARG2$',:'$ARG3$',:'$ARG4$' -c :'$ARG5$',:'$ARG6$',:'$ARG7$' -l load
[1364570324.120274] [2320.2] [pid=6041] Expanded Command Output: /usr/lib/nagios/plugins/check_snmp -H '$HOSTADDRESS$' -C '$ARG1$' -o .1.3.6.1.4.1.2021.10.1.5.1,.1.3.6.1.4.1.2021.10.1.5.2,.1.3.6.1.4.1.2021.10.1.5.3 -w :'$ARG2$',:'$ARG3$',:'$ARG4$' -c :'$ARG5$',:'$ARG6$',:'$ARG7$' -l load
[1364570324.120482] [016.1] [pid=6041] Check result output will be written to '/var/lib/nagios3/spool/checkresults/checktCrCxt' (fd=6)
ss (pid=6134)
[1364570327.129385] [016.0] [pid=6041] Starting to reap check results.
[1364570327.129523] [016.1] [pid=6041] Starting to read check result queue '/var/lib/nagios3/spool/checkresults'...
[1364570327.129581] [016.0] [pid=6041] Finished reaping 0 check results
[1364570330.177343] [016.2] [pid=6135] Moving temp check result file '/var/lib/nagios3/spool/checkresults/checktCrCxt' to queue file '/var/lib/nagios3/spool/checkresults/ckXBAPo'...
[1364570337.138898] [016.0] [pid=6041] Starting to reap check results.
[1364570337.138976] [016.1] [pid=6041] Starting to read check result queue '/var/lib/nagios3/spool/checkresults'...
[1364570337.139037] [016.1] [pid=6041] Processing check result file: '/var/lib/nagios3/spool/checkresults/ckXBAPo'
[1364570337.139315] [016.2] [pid=6041] Found a check result (#1) to handle...
[1364570337.139336] [016.1] [pid=6041] Handling check result for service 'CPU Load' on host 'nagios02'...
[1364570337.139353] [016.0] [pid=6041] ** Handling check result for service 'CPU Load' on host 'nagios02'...
[1364570337.139369] [016.1] [pid=6041] HOST: nagios02, SERVICE: CPU Load, CHECK TYPE: Active, OPTIONS: 0, SCHEDULED: Yes, RESCHEDULE: Yes, EXITED OK: Yes, RETURN CODE: 3, OUTPUT: External command error: Timeout: No Response from 192.168.1.250:161.\n
[1364570337.139404] [016.2] [pid=6041] Parsing check output...
eout: No Response from 192.168.1.250:161.
[1364570337.139436] [016.2] [pid=6041] Long Output:  NULL
[1364570337.139452] [016.2] [pid=6041] Perf Data:    NULL
: 3
[1364570337.139485] [016.1] [pid=6041] Service is in a non-OK state!
s state to make sure...
[1364570337.139516] [016.1] [pid=6041] * Using last known host state: 0
[1364570337.139532] [016.1] [pid=6041] Current/Max Attempt(s): 4/4

---

### Post by mancora on 2013-04-11
SOLVED

First problem was the service definition were I added a register 0 definition. This is only used for macros.

Service Definition

define service{
         use                             generic-service
         name                            CPU-stats
         check_command                   snmp_cpustats!supersecreto 
         service_description             CPU Stats
         host_name                       nagios02
         notification_interval           0
         notification_options            c,r
         notification_period             24x7
         }

define service{
         use                             generic-service
         name                            CPU Load
         check_command                   snmp_load!supersecreto!70!90
         service_description             CPU Load
         host_name                       nagios02
         notification_interval           0
         notification_options            c,r
         notification_period             24x7
         }

And the second problem was that the in the command definition the -C community parameter is not been taken by the check_snmp command giving a time out

# 'snmp_load' command definition
define command{
        command_name    snmp_load
        command_line    /usr/lib/nagios/plugins/check_snmp -H '$HOSTADDRESS$' -C
 '$ARG1$' -o .1.3.6.1.4.1.2021.10.1.5.1,.1.3.6.1.4.1.2021.10.1.5.2,.1.3.6.1.4.1.
2021.10.1.5.3 -w :'$ARG2$',:'$ARG3$',:'$ARG4$' -c :'$ARG5$',:'$ARG6$',:'$ARG7$'
-l load
        }


# 'snmp_cpustats' command definition
define command{
        command_name    snmp_cpustats
        command_line    /usr/lib/nagios/plugins/check_snmp -H '$HOSTADDRESS$' -C
 '$ARG1$' -o .1.3.6.1.4.1.2021.11.9.0,.1.3.6.1.4.1.2021.11.10.0,.1.3.6.1.4.1.202
1.11.11.0 -l 'CPU usage (user system idle)' -u '%'
        }

After change this and harcode the community everything worked!!!

# 'snmp_load' command definition
define command{
        command_name    snmp_load
        command_line    /usr/lib/nagios/plugins/check_snmp -H '$HOSTADDRESS$' -C
 supersecreto -o .1.3.6.1.4.1.2021.10.1.5.1,.1.3.6.1.4.1.2021.10.1.5.2,.1.3.6.1.
4.1.2021.10.1.5.3 -w :'$ARG1$',:'$ARG2$',:'$ARG3$' -c :'$ARG4$',:'$ARG5$',:'$ARG
6$' -l load
        }


# 'snmp_cpustats' command definition
define command{
        command_name    snmp_cpustats
        command_line    /usr/lib/nagios/plugins/check_snmp -H '$HOSTADDRESS$' -C
 supersecreto -o .1.3.6.1.4.1.2021.11.9.0,.1.3.6.1.4.1.2021.11.10.0,.1.3.6.1.4.1
.2021.11.11.0 -l 'CPU usage (user system idle)' -u '%'
        }

---

