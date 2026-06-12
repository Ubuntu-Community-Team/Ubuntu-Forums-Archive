---
title: "Possible enhancement - Intelligent log rotation for performance / problem monitoring"
date: 2019-04-17
forum: Ubuntu, Linux and OS Chat
---

### Post by peter.h.m.brooks on 2019-04-17
This may exist already, if so, please let me know - I'd like to get it!

It is very useful to use logrotate to keep log files from growing to become a nuisance. ISTM that a lot of useful diagnostic information is being lost. I'd like an admin utility that rotates logs (probably using log rotate), but, also:

- Keeps track of the fill-rate of logs
- Uses fuzzy logic to keep track of whether the system is acting 'normally', or is 'busy', or is 'less active'
- Uses the status of the system to tell if particular log files are acting unusually
- Is aware of the volatility of log files, so, if one is extremely variable, knows that and will report a lack of volatility as 'unusual'
- Reports unusual activity - using some statistical measure of 'unusual' -  >1/2&#963;, >&#963;, >2&#963; etc.

I think this would be very useful to alert administrators when a system starts to behave differently, with any luck, long before serious incidents start. It should help with security too.

If such a thing exists, or was written, the next enhancement would be to tie it to similar analysis of utmp so that unusual user activity is logged and, if coincident with unusual log activity, is reported along side it.

A further enhancement would be to produce profiles or fingerprints of log-files on the system, so that, if unusual activity is noticed, it can be linked to a change in the profile. What I mean is that, if a log file usually contains a mix of 10 sorts of log message, if a new sort starts to appear, or one reduces in frequency, this can be reported too. Clearly this would be much more time and CPU consuming, but would help for quicker analysis of why there is unusual activity.

Do such things exist? Is this something that's been tried before and found to difficult or of little use?

If not, is anybody else interested in developing these ideas further?

---

### Post by TheFu on 2019-04-17
Nothing that I know exactly like this exists, but 
Monitoring
Alarming
and logwatch do exist.  These are meant for servers, but can work on desktops too. No desktop GUI, but they do update websites.
I use logwatch and get daily reports of any problems, including security issues.

For example, ```

 ################### Logwatch 7.4.2 (02/27/16) #################### 
        Processing Initiated: Wed Apr 17 06:25:06 2019
        Date Range Processed: yesterday
                              ( 2019-Apr-16 )
                              Period is day.
        Detail Level of Output: 0
        Type of Output/Format: mail / text
        Logfiles for Host: blog44
 ################################################################## 
 
 --------------------- httpd Begin ------------------------ 

 A total of 1 sites probed the server 
    185.232.22.11
 
 Requests with error response codes
    400 Bad Request
       /robots.txt: 6 Time(s)
```
It goes on for every non-200 error on that web proxy system and is customizable.  ssh failures, SASL failures, and many other issues are logged, then reported.  For example, one of my older CPUs was having some issues. This was reported in the logs and logwatch included it in the daily report.  Low storage and heating problems show up too.  Based on the logwatch data, you can setup automatic IP firewall rules with fail2ban.  Don't let some IP keep hammering at your webapp or email server logins.  For ssh, 1 failed attempt and it is blocked. If you use ssh-keys, there won't be any failed attempts by you.

For monitoring, there are lots of tools - cacti, zabbix, munin, SysUsage ... probably 15 others. Try a few out. Many of these have built-in alarming.
All of them will require than an MTA be setup, at least for outbound email.  All my systems can send email, but only a few can receive it.  I would never suggest sending logwatch reports over the public internet. There's lots of sensitive data in those logs.  Definitely don't send them to gmail.

---

### Post by peter.h.m.brooks on 2019-04-17
Thank you for that, I am familiar with the tools you mention. I&#8217;m happy setting up alarms and thresholds with monitoring.

what I was most interested in was the intelligent automated analysis of log file behaviour that I mentioned.

---

