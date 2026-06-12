---
title: "Monitoring windows hosts on Nagios3 (ubuntu server 9.10)"
date: 2010-02-21
forum: Server Platforms
---

### Post by mysteriousspammer on 2010-02-21
Hey guys,

I just installed Nagios3 on ubuntu server 9.10 and successfully got my localhost to be monitored by using the instructions contained in ([https://help.ubuntu.com/9.10/serverguide/C/nagios.html](https://help.ubuntu.com/9.10/serverguide/C/nagios.html)). 

I'm abit confused as to how to monitor Windows hosts, can anybody explain. I've created a new server cfg and put in the following:

```

define service{
    use            generic-service
    host_name        winserver
    service_description    NSClient++ Version
    check_command        check_nt!CLIENTVERSION
    }



# Create a service for monitoring the uptime of the server
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    Uptime
    check_command        check_nt!UPTIME
    }



# Create a service for monitoring CPU load
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    CPU Load
    check_command        check_nt!CPULOAD!-l 5,80,90
    }



# Create a service for monitoring memory usage
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    Memory Usage
    check_command        check_nt!MEMUSE!-w 80 -c 90
    }



# Create a service for monitoring C:\ disk usage
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    C:\ Drive Space
    check_command        check_nt!USEDDISKSPACE!-l c -w 80 -c 90
    }



# Create a service for monitoring the W3SVC service
# Change the host_name to match the name of the host you defined above

define service{
    use            generic-service
    host_name        winserver
    service_description    W3SVC
    check_command        check_nt!SERVICESTATE!-d SHOWALL -l W3SVC
    }
```All i'am getting are errors such as missing -l parameter. Can anybody share a sample of their nagios config or explain how i should go about this?

Thanks in advanced

---

### Post by koenn on 2010-02-21
[http://nagiosplugins.org/man/check_nt](http://nagiosplugins.org/man/check_nt)
> Notes:
 - The NSClient service should be running on the server to get any information
   ([http://nsclient.ready2run.nl](http://nsclient.ready2run.nl)).

do you have that (on winserver, presumably) ?

---

### Post by mysteriousspammer on 2010-02-21
Hey,

Yeah i've got nsclient running on the windows host, but no lucky still

the exact errors im getting:
C drive - missing -l parameter
CPU load -  missing -l parameter
memory usage - refused connection
nsclient++ version - refused connection
uptime - refused connection 
explorer - no services/processes specified

---

### Post by koenn on 2010-02-21
not sure about this but the "missing parameter" error might be because nagios doesn't see it because  there's no space between the command and the '-l'

the 'connection refused" suggests the service in winserver is not running, not configured corectly, or there's a problem with authentication or privileges.
Here(s a nice writeup that you can use as a checklist to see what's missing :
[http://www.thegeekstuff.com/2008/07/how-to-monitor-remote-windows-machine-using-nagios-on-linux/](http://www.thegeekstuff.com/2008/07/how-to-monitor-remote-windows-machine-using-nagios-on-linux/)

---

### Post by mysteriousspammer on 2010-02-22
Hey guys,

Thanks for the quick responses. Yeah i might go through and manually install NSclient again, its strange though because I'm actually using the same config (from windows.cfg and NSclient), which used to work when i had nagios on my archlinux computer. 

I'll see how it goes and report back =)

---

### Post by TheFuturian on 2010-02-23
Nagios is so last decade... I thoroughly recommend giving the community version of Opsview a goosy gander ;)

No disrespect to the Nagios community, without it Opsview would not be possible. Just to the average user Opsview is much simpler to configure.

---

### Post by koenn on 2010-02-23
Nagios takes some getting used to, but if you organise your cfg files in a logical manner and make appropriate use of the inheritance feature, it's pretty manageable. Plus, getting down and dirty with the cfg files teaches you where everything is, which makes it so much easier if you need to customize (or write from a scratch) a plugin to do something reasonably exotic.


I do think Nagios is a bit too host-oriented, and suffers a bit from "7 different ways to do the same thing without guidance about how to choose",
but it has been forked last year - [http://www.icinga.org/](http://www.icinga.org/)  - so maybe that's something to watch, and there probably is room for things like Opsview that seem to focus less on mechanism and more on easy decisions. 


Still, "so last decade' to me just sounds like 'proven technology" :)

---

### Post by kernelzilla on 2010-02-25
I ran into this today as well and found it was caused by a missing $ARG in /etc/nagios-plugins/config/nt.cfg.  This worked for me:
```


  command_line    /usr/lib/nagios/plugins/check_nt -H '$HOSTADDRESS$' -p 12489 -v $ARG1$ $ARG2$ $ARG3$


```

---

### Post by IsiaNT on 2010-08-12
commands.cfg:
 
# 'check_nt' command definition
define command {
        command_name    check_nt
        command_line    /usr/lib/nagios/plugins/check_nt -H $HOSTADDRESS$ -p 12489 -v '$ARG1$'
}

---------------
windows_server.cfg:
 
#Windows host definition template - This is NOT a real host, just a template!
define host{
        name                    windows-server  ; The name of this host template
        use                     generic-host    ; Inherit default values from the generic-host template
        check_period            24x7            ; By default, Windows servers are monitored round the clock
        check_interval          5               ; Actively check the server every 5 minutes
        retry_interval          1               ; Schedule host check retries at 1 minute intervals
        max_check_attempts      10              ; Check each server 10 times (max)
        check_command           check-host-alive        ; Default command to check if servers are "alive"
        notification_period     24x7            ; Send notification out at any time - day or night
        notification_interval   30              ; Resend notifications every 30 minutes
        notification_options    d,r             ; Only send notifications for specific host states
        contact_groups          admins          ; Notifications get sent to the admins by default
        hostgroups              windows-servers ; Host groups that Windows servers should be a member of
        register                0               ; DONT REGISTER THIS - ITS JUST A TEMPLATE
        }

-------------
 
srv-servervirt.cfg:
 
define host{
        use             windows-server  ; Inherit default values from a Windows server template (make sure you keep this line!)
        host_name       servervirt.local
        alias           symplex
        address         192.168.0.101
        }
define service{
        use                     generic-service
        host_name               servervirt.local
        service_description     NSClient+ Version
        check_command           check_nt!'CLIENTVERSION'
        }
define service{
        use                     generic-service
        host_name               servervirt.local
        service_description     Uptime
        check_command           check_nt!'UPTIME'
        }
define service{
        use                     generic-service
        host_name               servervirt.local
        service_description     CPU Load
        check_command           check_nt!'CPULOAD -l 5,100,100'
        }
define service{
        use                     generic-service
        host_name               servervirt.local
        service_description     Memory Usage
        check_command           check_nt!'MEMUSE -w 42 -c 47'
        }
define service{
        use                     generic-service
        host_name               servervirt.local
        service_description     C:\ Drive Space
        check_command           check_nt!'USEDDISKSPACE -l c -w 75 -c 90'
        }
define service{
        use                     generic-service
        host_name               servervirt.local
        service_description     D:\ Drive Space
        check_command           check_nt!'USEDDISKSPACE -l d -w 75 -c 90'
        }
define service{
        use                     generic-service
        host_name               servervirt.local
        service_description     Hyper-V mngt
        check_command           check_nt!'SERVICESTATE -d SHOWALL -l vmms'
        }
#define service{
#       use                     generic-service
#       host_name               servervirt.local
#       service_description     RDP client
#       check_command           check_nt!'PROCSTATE -d SHOWALL -l explorer.exe'
#       }
 
all work fine

---

### Post by IsiaNT on 2010-08-12
on windows 2008 server with IP: 192.168.0.101 install lastest ver of nsclient++ ([http://nsclient.org/nscp/](http://nsclient.org/nscp/)) as windows service
 
nsc.ini :
 
[modules]
NSClientListener.dll
NSCAAgent.dll
;CheckWMI.dll
FileLogger.dll
CheckSystem.dll
CheckDisk.dll
CheckEventLog.dll
CheckHelpers.dll
;# NSCLIENT++ MODULES
;# A list with DLLs to load at startup.
;  You will need to enable some of these for NSClient++ to work.
; ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! !
; *                                                               *
; * N O T I C E ! ! ! - Y O U   H A V E   T O   E D I T   T H I S *
; *                                                               *
; ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! ! !
;NRPEListener.dll
;SysTray.dll
;CheckWMI.dll
;
; Script to check external scripts and/or internal aliases.
;CheckExternalScripts.dll
;
; NSCA Agent if you enable this NSClient++ will talk to NSCA hosts repeatedly (so dont enable unless you want to use NSCA)
;NSCAAgent.dll
;
; LUA script module used to write your own "check deamon".
;LUAScript.dll
;
; RemoteConfiguration IS AN EXTREM EARLY IDEA SO DONT USE FOR PRODUCTION ENVIROMNEMTS!
;RemoteConfiguration.dll
; Check other hosts through NRPE extreme beta and probably a bit dangerous! :)
;NRPEClient.dll
; Extreamly early beta of a task-schedule checker
;CheckTaskSched.dll
 
[Settings]
use_file=1
allowed_hosts=192.168.0.2
;password=

other = defaults

---

