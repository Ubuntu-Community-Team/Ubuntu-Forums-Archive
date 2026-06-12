---
title: "fail2ban not blocking SSH bruteforce"
date: 2021-12-30
forum: Security
---

### Post by lieta on 2021-12-30
Hi.
I installed fai2ban package using apt on Ubuntu 20.04.3. Package version is 0.11.1-1.
I followed these steps to identify the problem:
[https://www.fail2ban.org/wiki/index.php/FAQ_english#Fail2ban_is_running_but_not_banning_SSH_bruteforce](https://www.fail2ban.org/wiki/index.php/FAQ_english#Fail2ban_is_running_but_not_banning_SSH_bruteforce)
The command
```
fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf
```
doesn't give the expected "[COLOR=#000000][FONT=monospace]Success" result.
[/FONT][/COLOR]```
# fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf

Running tests
=============


Use   failregex filter file : sshd, basedir: /etc/fail2ban
Use         maxlines : 1
Use      datepattern : Default Detectors
Use         log file : /var/log/auth.log
Use         encoding : UTF-8




Results
=======


Failregex: 12644 total
|-  #) [# of hits] regular expression
|   4) [3765] ^Failed \b(?!publickey)\S+ for (?P<cond_inv>invalid user )?<F-USER>(?P<cond_user>\S+)|(?(cond_inv)(?:(?! from ).)*?|[^:]+)</F-USER> from <HOST>(?: (?:port \d+|on \S+)){0,2}(?: ssh\d*)?(?(cond_user): |(?:(?:(?! from ).)*)$)
|   6) [2] ^[iI](?:llegal|nvalid) user <F-USER>.*?</F-USER> from <HOST>(?: (?:port \d+|on \S+|\[preauth\])){0,3}\s*$
|  14) [3765] ^<F-NOFAIL>pam_[a-z]+\(sshd:auth\):\s+authentication failure;</F-NOFAIL>(?:\s+(?:(?:logname|e?uid|tty)=\S*)){0,4}\s+ruser=<F-ALT_USER>\S*</F-ALT_USER>\s+rhost=<HOST>(?:\s+user=<F-USER>\S*</F-USER>)?(?: (?:port \d+|on \S+|\[preauth\])){0,3}\s*$
|  19) [3] ^<F-NOFAIL>Received <F-MLFFORGET>disconnect</F-MLFFORGET></F-NOFAIL> from <HOST>(?: (?:port \d+|on \S+)){0,2}:\s*11:
|  20) [5100] ^<F-NOFAIL><F-MLFFORGET>(Connection closed|Disconnected)</F-MLFFORGET></F-NOFAIL> (?:by|from)(?: (?:invalid|authenticating) user <F-USER>\S+|.+?</F-USER>)? <HOST>(?:(?: (?:port \d+|on \S+|\[preauth\])){0,3}\s*|\s*)$
|  21) [9] ^<F-MLFFORGET><F-MLFGAINED>Accepted \w+</F-MLFGAINED></F-MLFFORGET> for <F-USER>\S+</F-USER> from <HOST>(?:\s|$)
`-


Ignoreregex: 0 total


Date template hits:
|- [# of hits] date format
|  [77445] {^LN-BEG}(?:DAY )?MON Day %k:Minute:Second(?:\.Microseconds)?(?: ExYear)?
`-


Lines: 77445 lines, 8877 ignored, 3767 matched, 64801 missed
[processed in 3.50 sec]


Ignored line(s): too many to print.  Use --print-all-ignored to print all 8877 lines
Missed line(s): too many to print.  Use --print-all-missed to print all 64801 lines



```[COLOR=#000000][FONT=monospace]
[/FONT][/COLOR]

---

