---
title: "[SOLVED] fail2ban not banning and does nothing - Ubuntu Server 16.04 LTS"
date: 2019-11-27
forum: Server Platforms
---

### Post by ihgromovnik on 2019-11-27
1. edited /etc/ssh/sshd.conf
2. add AllowGroups group-name
3. sudo sshd -T
4. add yourself/other ssh-users to "group-name"
5. log out - log in (all allowed ssh users)
6. restart ssh service
7. test fail2ban with VPN


**************************************************************************

I have fail2ban on all my servers working, Debian 8/9 and Ubuntu 18.10.
However, fail2ban on Ubuntu 16.04 does not work properly.

The same setup as usual:

$apt install fail2ban 
$systemctl enable fail2ban.service
$systemctl daemon-reload

# fail2ban-server -V
Fail2Ban v0.9.3

### vim /etc/fail2ban/jail.local ###
maxretry = 3
findtime = 43200
bantime = 3600

[sshd]
enabled = true
port    = 22
filter = sshd
logpath = %(sshd_log)s
action = %(action_mwl)s

$systemctl restart fail2ban.service
* I get a notification if jail is started or stopped

~# fail2ban-client status sshd
Status for the jail: sshd
|- Filter
|  |- Currently failed: 0
|  |- Total failed:     0
|  `- File list:        /var/log/auth.log
`- Actions
   |- Currently banned: 0
   |- Total banned:     0
   `- Banned IP list:

###Testing fail2ban###

trying to connect without ssh keys I get:

"Permission denied (publickey). && Connection refused after five attempts, not three"

###auth.log###
Nov 28 12:17:01 localhost CRON[20121]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 28 12:17:01 localhost CRON[20121]: pam_unix(cron:session): session closed for user root
Nov 28 12:17:54 localhost sshd[20301]: Connection closed by ip_without ssh key port 58612 [preauth]
Nov 28 12:17:59 localhost sshd[20304]: Connection closed by ip_without ssh key port 58626 [preauth]
Nov 28 12:18:04 localhost sshd[20392]: Connection closed by ip_without ssh key port 58640 [preauth]
Nov 28 12:18:09 localhost sshd[20397]: Connection closed by ip_without ssh key port 58646 [preauth]
Nov 28 12:18:14 localhost sshd[20400]: Connection closed by ip_without ssh key port 58648 [preauth]

** first two lines are confusing
Nov 28 12:17:01 localhost CRON[20121]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov 28 12:17:01 localhost CRON[20121]: pam_unix(cron:session): session closed for user root


###fail2ban.log###
2019-11-25 06:25:08,105 fail2ban.server         [17124]: INFO    rollover performed on /var/log/fail2ban.log
2019-11-25 06:25:10,079 fail2ban.filter         [17124]: INFO    Log rotation detected for /var/log/auth.log


Am I missing something?
Regards,
gromovnik

---

### Post by TheFu on 2019-11-28
Support for 18.10 ended last July.  18.04 is the supported LTS release.  Or you could load 19.10 which will lose support next July,  in about 8 months.

---

