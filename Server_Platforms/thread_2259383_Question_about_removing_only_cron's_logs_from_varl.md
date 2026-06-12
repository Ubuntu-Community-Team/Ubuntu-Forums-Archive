---
title: "Question about removing only cron's logs from /var/log/auth.log"
date: 2015-01-04
forum: Server Platforms
---

### Post by yusui-tomikawa on 2015-01-04
I am using Ubuntu 14.04.1 LTS 64bit minimal on a VPS service.
After installing the "cron", the following logs were on /var/log/auth.log.


CRON[4041]: pam_unix(cron:session): session opened for user root by (uid=0) 
CRON[4041]: pam_unix(cron:session): session closed for user root


Since cron's log is existing on /var/log/cron.log, I stopped output of cron logs on /var/log/auth.log by this way: [http://ubuntuforums.org/archive/index.php/t-1256801.html](http://ubuntuforums.org/archive/index.php/t-1256801.html)
But meanwhile, it seems that output of SSH login logs "systemd-logind[XXX]: New session XXX of user root." are stopped also.
I guess I can not check whether new session is opening or not without this log.
I want to remove only cron log from /var/log/auth.log.
How should I do it?

The following is my** /etc/pam.d/common-session-noninteractive**
> 
#
# /etc/pam.d/common-session-noninteractive - session-related modules
<<snipped>>
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.


# here are the per-package modules (the "Primary" block)
session [default=1]                     pam_permit.so
# here's the fallback if no module succeeds
session requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session required                        pam_permit.so
# The pam_umask module will set the umask according to the system default in
# /etc/login.defs and user settings, solving the problem of different
# umask settings with different shells, display managers, remote sessions etc.
# See "man pam_umask".
session optional                        pam_umask.so
# and here are more per-package modules (the "Additional" block)
[COLOR=#ff0000]**session [success=1 default=ignore] pam_succeed_if.so service in cron quiet use_uid**[/COLOR]
session required        pam_unix.so
# end of pam-auth-update config


---

