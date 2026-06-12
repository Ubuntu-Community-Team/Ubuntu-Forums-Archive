---
title: "pam.d/su to restrict su access. SU Module Unknown Error"
date: 2016-07-04
forum: Security
---

### Post by ulrichkenneth on 2016-07-04
[COLOR=#000000][FONT=Arial]Hello All, 

I am trying to configure my server(Ubuntu 16) to allow one of my users to only su to one user. Like "su - tadess" will work since it is allowed, but "su - root" will fail since it is not on the allow list. 
[http://blog.serverbuddies.com/how-do-i-restrict-the-use-of-su-command/](http://blog.serverbuddies.com/how-do-i-restrict-the-use-of-su-command/) is the link that I've used.

Now I'm getting the error "su: Module is unknown". 

Below is a copy of my /etc/pam.d/su file. Blue is what I changed. 




[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# The PAM configuration file for the Shadow `su' service[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]#[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# This allows root to su without passwords (normal operation)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]auth       sufficient pam_rootok.so[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# Uncomment this to force users to be a member of group root[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# before they can use `su'. You can also add "group=foo"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]#Located in /etc/pam.d/su[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# to the end of this line if you want to use a group other[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]#[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# than the default "root" (but this may have side effect of[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# denying "root" user, unless she's a member of "foo" or explicitly[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# permitted earlier by e.g. "sufficient pam_rootok.so").[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# (Replaces the `SU_WHEEL_ONLY' option from login.defs)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#0000ff][FONT=Arial] auth       required   /lib/security/pam_wheel.so group=kennethulrich[/FONT][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# Uncomment this if you want wheel members to be able to[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# su without a password.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# auth       sufficient pam_wheel.so trust[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# Uncomment this if you want members of a specific group to not[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# be allowed to use su at all.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# auth       required   pam_wheel.so deny group=nosu[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# Uncomment and edit /etc/security/time.conf if you need to set[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# time restrainst on su usage.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# as well as /etc/porttime)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# account    requisite  pam_time.so[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# This module parses environment configuration file(s)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# and also allows you to use an extended config[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# file /etc/security/pam_env.conf.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# parsing /etc/environment needs "readenv=1"[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]session       required   pam_env.so readenv=1[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# locale variables are also kept into /etc/default/locale in etch[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# reading this file *in addition to /etc/environment* does not hurt[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]session       required   pam_env.so readenv=1 envfile=/etc/default/locale[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# Defines the MAIL environment variable[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# However, userdel also needs MAIL_DIR and MAIL_FILE variables[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# in /etc/login.defs to make sure that removing a user [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# also removes the user's mail spool file.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# See comments in /etc/login.defs[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]#[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# "nopen" stands to avoid reporting new mail when su'ing to another user[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]session    optional   pam_mail.so nopen[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# Sets up user limits according to /etc/security/limits.conf[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# (Replaces the use of /etc/limits in old login)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]session    required   pam_limits.so[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# The standard Unix authentication modules, used with[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# NIS (man nsswitch) as well as normal /etc/passwd and[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]# /etc/shadow entries.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]@include common-auth[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]@include common-account[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]@include common-session[/FONT][/COLOR]

---

### Post by TheFu on 2016-07-04
Never tried it this way. But I have used sudoers for something like this.  The sudoers manpage is pretty awesome.  Not sure I'd allow them to actually switch fully to another userid. A little too much power, IMHO.  OTOH, letting them run the specific commands with specific options as another userid - that I could get behind.

---

### Post by Habitual on 2016-07-05
Sudo: you're doing it wrong pdf in my signature?

---

