---
title: "Ubuntu 12.04 LTS and Nagios"
date: 2013-08-06
forum: Server Platforms
---

### Post by dominic3 on 2013-08-06
Hi Guys, this is my first post on the forum, I hope I make this post in the correct section.

I have installed Nagios on my Ubuntu server.
Nagios is running, Apache also is running.

When I want to monitor a website of mine Nagios says:

Host State Information
  [TABLE]
[TR]
[TD] [TABLE]
 [TR]
[TD="class: stateInfoTable1"] [TABLE]
 [TR]
[TD="class: dataVar"]Host Status:[/TD]
[TD="class: dataVal"]  DOWN  
 (for  0d  0h 30m 44s)[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Status Information:[/TD]
[TD="class: dataVal"]PING CRITICAL - Packet loss = 100%[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Performance Data:[/TD]
[TD="class: dataVal"]rta=5000.000000ms;5000.000000;5000.000000;0.000000 pl=100%;100;100;0[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Current Attempt:[/TD]
[TD="class: dataVal"]1/10  (HARD state)[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Last Check Time:[/TD]
[TD="class: dataVal"]2013-08-06 19:45:21[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Check Type:[/TD]
[TD="class: dataVal"]ACTIVE[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Check Latency / Duration:[/TD]
[TD="class: dataVal"]0.000 / 10.018 seconds[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Next Scheduled Active Check:  [/TD]
[TD="class: dataVal"]2013-08-06 19:50:31[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Last State Change:[/TD]
[TD="class: dataVal"]2013-08-06 19:19:31[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Last Notification:[/TD]
[TD="class: dataVal"]2013-08-06 19:19:31 (notification 1)[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Is This Host Flapping?[/TD]
[TD="class: dataVal"]  NO  
 (4.01% state change)[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]In Scheduled Downtime?[/TD]
[TD="class: dataVal"]  NO  
[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Last Update:[/TD]
[TD="class: dataVal"]2013-08-06 19:50:11  ( 0d  0h  0m  4s ago)[/TD]
[/TR]
 [/TABLE]
 [/TD]
[/TR]
 [/TABLE]
 [/TD]
[/TR]
 [TR]
[TD] [TABLE]
 [TR]
[TD="class: stateInfoTable2"] [TABLE]
 [TR]
[TD="class: dataVar"]Active Checks:[/TD]
[TD="class: dataVal"]  ENABLED  
[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Passive Checks:[/TD]
[TD="class: dataVal"]  ENABLED  
[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Obsessing:[/TD]
[TD="class: dataVal"]  ENABLED  
[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Notifications:[/TD]
[TD="class: dataVal"]  ENABLED  
[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Event Handler:[/TD]
[TD="class: dataVal"]  ENABLED  
[/TD]
[/TR]
 [TR]
[TD="class: dataVar"]Flap Detection:[/TD]
[TD="class: dataVal"]  ENABLE
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

The site is up and running, it does the same for other sites, including Google.com

When I enter the check_http command, Ubuntu states that the command is not found.

LS from plugins folder:
root@h2200554:/etc/nagios3/conf.d# ls
contacts_nagios2.cfg      generic-service_nagios2.cfg  services_nagios2.cfg
extinfo_nagios2.cfg       hostgroups_nagios2.cfg       test-google.cfg
generic-host_nagios2.cfg  localhost_nagios2.cfg        timeperiods_nagios2.cfg

Cat from test-google.cfg
root@h2200554:/etc/nagios3/conf.d# cat test-google.cfg
define host{
            use                     generic-host
            host_name               google
            alias                   google
            address                 google.com
            }

    define service{
            use                         generic-service
            host_name                   google
            service_description         HTTP
            check_command               check_http
            }

What is the cause of this problem and how can I fix this?

Your help is higly appreciated.

---

### Post by dominic3 on 2013-08-06
Figured out how I can run a plugin from the CLI.

root@h2200554:~# cd /usr/lib/nagios/plugins
root@h2200554:/usr/lib/nagios/plugins# ./check_http -I [www.google.com](www.google.com)
HTTP OK: HTTP/1.0 302 Found - 1002 bytes in 0,062 second response time |time=0,062269s;;;0,000000 size=1002B;;;0
root@h2200554:/usr/lib/nagios/plugins#

So if this is working, why is it not working in Nagios?

---

### Post by dominic3 on 2013-08-07
Anyone?

---

### Post by Habitual on 2013-08-07
try 
```
 **/usr/local/nagios/libexec/check_http -H google.com**
```
or
```
/usr/lib/nagios/plugins/check_http -H google.com 
```

[http://nagiosplugins.org/man/check_http](http://nagiosplugins.org/man/check_http)
[http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194](http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=194)

---

