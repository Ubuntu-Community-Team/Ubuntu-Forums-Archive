---
title: "Problem with amavis"
date: 2010-08-25
forum: Server Platforms
---

### Post by bnelson01 on 2010-08-25
Setup my mail server and everything seems to be working fine except for amavis. When I try to start it I get the following error:

```
Stopping amavisd: amavisd-new.
Starting amavisd: Error in config file "/etc/amavis/conf.d/50-user": Global symbol "$sa_kill_level_dflt" requires explicit package name at /etc/amavis/conf.d/50-user line 16.
(failed).
```And here is my 50-user file:

```
use strict;

#
# Place your configuration directives here.  They will override those in
# earlier files.
#
# See /usr/share/doc/amavisd-new/ for documentation and examples of
# the directives you can use in this file
#
$myhostname = 'lists.bbfilez.com';
@local_domains_acl = qw(.);
$log_level = 1;
$syslog_priority = 'info';
# $sa_tag_level_dflt = 2.0; # add spam info headers if at, or above that level
# $sa_tag2_level_dflt = 6.31; # add 'spam detected' headers at that level
$sa_kill_level_dflt = 8.0; # triggers spam evasive actions
# $sa_dsn_cutoff_level = 10; # spam level beyond which a DSN is not sent
# $final_spam_destiny = D_PASS;
# $final_spam_destiny = D_REJECT; # default
# $final_spam_destiny = D_BOUNCE; # debian default
$final_spam_destiny = D_DISCARD; # ubuntu default, recommended as sender is usually fake


#------------ Do not modify anything below this line -------------
1;  # ensure a defined return
```It seems to be dying on the $sa_kill_level_deflt line but I can't figure out what the problem is as it's exactly what the example says to use. Any help is greatly appreciated.

---

### Post by dcere on 2013-02-25
I know it is a little bit late, but hope it helps:

$sa_kill_level_dflt does not exist. $sa_kill_level_d**e**flt, however, does.

---

