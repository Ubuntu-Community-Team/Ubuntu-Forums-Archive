---
title: "Fail2Ban"
date: 2016-12-27
forum: Security
---

### Post by Leberyo on 2016-12-27
I've set up Fail2Ban using instructions found online. I'm looking to have Fail2Ban protect our Nginx http-auth login but it will not take action as required. For example, it lets people try to login in as many times as they want.
I've turned on Fail2Ban Nginx-Auth on jail.local :

```
[nginx-http-auth]
enabled = true
port    = http,https
logpath = /var/log/nginx/*-error.log
filter = nginx-http-auth
action = iptables-multiport[name=NoLoginFailures, port="http,https"]
maxretry = 4
bantime  = 54000
findtime = 3600
```


I've also done this on nginx-http-auth.conf:
```

[Definition]

failregex = ^ \[error\] \d+#\d+: \*\d+ user "\S+":? (password mismatch|was not found in ".*"), client: <HOST>, server: \S+, request: "\S+ \S+ HTTP/\d+\.\d+", host: "\S+"\s*$
            ^ \[error\] \d+#\d+: \*\d+ no user/password was provided for basic authentication, client: <HOST>, server: \S+, request: "\S+ \S+ HTTP/\d+\.\d+", host: "\S+"\s*$
            ^ \[error\] \d+#\d+: \*\d+ access forbidden by rule, client: <HOST>, server: \S+, request: "\S+ \S+ HTTP/\d+\.\d+", host: "*.MYDOMAIN.com"

ignoreregex =


```

but when running:
```
fail2ban-regex -v /var/log/nginx/MYDOMAIN.com-error.log /etc/fail2ban/filter.d/nginx-http-auth.conf
```

I get

Running tests
=============

Use   failregex filter file : nginx-http-auth, basedir: /etc/fail2ban
Use         log file : /var/log/nginx/MYDOMAIN.com-error.log
Use         encoding : UTF-8


Results
=======

```
Failregex: 0 total
|-  #) [# of hits] regular expression
|   1) [0] ^ \[error\] \d+#\d+: \*\d+ user "\S+":? (password mismatch|was not found in ".*"), client: <HOST>, server: \S+, request: "\S+ \S+ HTTP/\d+\.\d+", host: "\S+"\s*$
|   2) [0] ^ \[error\] \d+#\d+: \*\d+ no user/password was provided for basic authentication, client: <HOST>, server: \S+, request: "\S+ \S+ HTTP/\d+\.\d+", host: "\S+"\s*$
|   3) [0] ^ \[error\] \d+#\d+: \*\d+ access forbidden by rule, client: <HOST>, server: \S+, request: "\S+ \S+ HTTP/\d+\.\d+", host: "*.MYDOMAIN.com"
`-

Ignoreregex: 0 total

Date template hits:
|- [# of hits] date format
|  [151] Year(?P<_sep>[-/.])Month(?P=_sep)Day 24hour:Minute:Second(?:,Microseconds)?
|  [0] (?:DAY )?MON Day 24hour:Minute:Second(?:\.Microseconds)?(?: Year)?
|  [0] Day(?P<_sep>[-/])Month(?P=_sep)(?:Year|Year2) 24hour:Minute:Second
|  [0] Day(?P<_sep>[-/])MON(?P=_sep)Year[ :]?24hour:Minute:Second(?:\.Microseconds)?(?: Zone offset)?
|  [0] Month/Day/Year:24hour:Minute:Second
|  [0] Month-Day-Year 24hour:Minute:Second\.Microseconds
|  [0] TAI64N
|  [0] Epoch
|  [0] Year-Month-Day[T ]24hour:Minute:Second(?:\.Microseconds)?(?:Zone offset)?
|  [0] ^24hour:Minute:Second
|  [0] ^<Month/Day/Year2@24hour:Minute:Second>
|  [0] ^Year2MonthDay  ?24hour:Minute:Second
|  [0] MON Day, Year 12hour:Minute:Second AMPM
|  [0] ^MON-Day-Year2 24hour:Minute:Second
`-

Lines: 151 lines, 0 ignored, 0 matched, 151 missed [processed in 0.01 sec] 
Missed line(s): too many to print.  Use --print-all-missed to print all 151 lines


```
It says that 151 lines are missed. Would somebody know why this happens ?

---

