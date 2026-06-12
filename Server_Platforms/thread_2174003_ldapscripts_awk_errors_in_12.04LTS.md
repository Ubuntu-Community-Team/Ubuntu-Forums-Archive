---
title: "ldapscripts awk errors in 12.04LTS"
date: 2013-09-12
forum: Server Platforms
---

### Post by iva2k on 2013-09-12
I had ldap setup and ldapscripts working in 10.04LTS. After upgrading to 12.04LTS, ldapscripts (all commands) bork out with these errors:

```
sudo ldapaddgroup testgroup
awk: cmd. line:1: /^[ \t]*host/ sub(/^[ \t]*host[ \t]*/
awk: cmd. line:1:                                      ^ unexpected newline or end of string
awk: /^[ \t]*host/ ""); sub(/[ \t]*(#.*)?$/
awk:                 ^ syntax error
awk: each rule must have a pattern or an action part
awk: cmd. line:1: /^[ \t]*host/ ""); sub(/[ \t]*(#.*)?$/
awk: cmd. line:1:                                       ^ unexpected newline or end of string
awk: /^[ \t]*host/  ""); print $0
awk:                  ^ syntax error
awk: each rule must have a pattern or an action part
awk: /^[ \t]*host/  ""); print $0
awk:                     ^ syntax error
awk: cmd. line:1: /^[ \t]*uri/ sub(/^[ \t]*uri[ \t]*/
awk: cmd. line:1:                                    ^ unexpected newline or end of string
awk: /^[ \t]*uri/ ""); sub(/[ \t]*(#.*)?$/
awk:                ^ syntax error
awk: each rule must have a pattern or an action part
awk: cmd. line:1: /^[ \t]*uri/ ""); sub(/[ \t]*(#.*)?$/
awk: cmd. line:1:                                      ^ unexpected newline or end of string
awk: /^[ \t]*uri/  ""); print $0
awk:                 ^ syntax error
awk: each rule must have a pattern or an action part
awk: /^[ \t]*uri/  ""); print $0
awk:                    ^ syntax error
awk: cmd. line:1: /^[ \t]*rootbinddn/ sub(/^[ \t]*rootbinddn[ \t]*/
awk: cmd. line:1:                                                  ^ unexpected newline or end of string
awk: /^[ \t]*rootbinddn/ ""); sub(/[ \t]*(#.*)?$/
awk:                       ^ syntax error
awk: each rule must have a pattern or an action part
awk: cmd. line:1: /^[ \t]*rootbinddn/ ""); sub(/[ \t]*(#.*)?$/
awk: cmd. line:1:                                             ^ unexpected newline or end of string
awk: /^[ \t]*rootbinddn/  ""); print $0
awk:                        ^ syntax error
awk: each rule must have a pattern or an action part
awk: /^[ \t]*rootbinddn/  ""); print $0
awk:                           ^ syntax error
awk: cmd. line:1: /^[ \t]*base/ sub(/^[ \t]*base[ \t]*/
awk: cmd. line:1:                                      ^ unexpected newline or end of string
awk: /^[ \t]*base/ ""); sub(/[ \t]*(#.*)?$/
awk:                 ^ syntax error
awk: each rule must have a pattern or an action part
awk: cmd. line:1: /^[ \t]*base/ ""); sub(/[ \t]*(#.*)?$/
awk: cmd. line:1:                                       ^ unexpected newline or end of string
awk: /^[ \t]*base/  ""); print $0
awk:                  ^ syntax error
awk: each rule must have a pattern or an action part
awk: /^[ \t]*base/  ""); print $0
awk:                     ^ syntax error
awk: cmd. line:1: /^[ \t]*nss_base_group/ sub(/^[ \t]*nss_base_group[ \t]*/
awk: cmd. line:1:                                                          ^ unexpected newline or end of string
awk: /^[ \t]*nss_base_group/ ""); sub(/[ \t]*(#.*)?$/
awk:                           ^ syntax error
awk: each rule must have a pattern or an action part
awk: cmd. line:1: /^[ \t]*nss_base_group/ ""); sub(/[ \t]*(#.*)?$/
awk: cmd. line:1:                                                 ^ unexpected newline or end of string
awk: /^[ \t]*nss_base_group/  ""); print $0
awk:                            ^ syntax error
awk: each rule must have a pattern or an action part
awk: /^[ \t]*nss_base_group/  ""); print $0
awk:                               ^ syntax error
awk: cmd. line:1: /^[ \t]*nss_base_passwd/ sub(/^[ \t]*nss_base_passwd[ \t]*/
awk: cmd. line:1:                                                            ^ unexpected newline or end of string
awk: /^[ \t]*nss_base_passwd/ ""); sub(/[ \t]*(#.*)?$/
awk:                            ^ syntax error
awk: each rule must have a pattern or an action part
awk: cmd. line:1: /^[ \t]*nss_base_passwd/ ""); sub(/[ \t]*(#.*)?$/
awk: cmd. line:1:                                                  ^ unexpected newline or end of string
awk: /^[ \t]*nss_base_passwd/  ""); print $0
awk:                             ^ syntax error
awk: each rule must have a pattern or an action part
awk: /^[ \t]*nss_base_passwd/  ""); print $0
awk:                                ^ syntax error
awk: cmd. line:1: /^[ \t]*nss_base_hosts/ sub(/^[ \t]*nss_base_hosts[ \t]*/
awk: cmd. line:1:                                                          ^ unexpected newline or end of string
awk: /^[ \t]*nss_base_hosts/ ""); sub(/[ \t]*(#.*)?$/
awk:                           ^ syntax error
awk: each rule must have a pattern or an action part
awk: cmd. line:1: /^[ \t]*nss_base_hosts/ ""); sub(/[ \t]*(#.*)?$/
awk: cmd. line:1:                                                 ^ unexpected newline or end of string
awk: /^[ \t]*nss_base_hosts/  ""); print $0
awk:                            ^ syntax error
awk: each rule must have a pattern or an action part
awk: /^[ \t]*nss_base_hosts/  ""); print $0
awk:                               ^ syntax error
Error adding group testgroup to LDAP

```

After that I purged ldapscripts, reinstalled/reconfigured from scratch, checked and rechecked everything, but awk errors remain and ldapscripts don't work.

Any thoughts?

---

### Post by iva2k on 2013-09-12
Digging further, I removed gawk package to fall back on mawk, and errors changed to:
```

$ sudo ldapaddgroup testgroup
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: syntax error at or near print
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: syntax error at or near print
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: syntax error at or near print
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: syntax error at or near print
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: syntax error at or near print
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: syntax error at or near print
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: missing ) near end of line
awk: line 1: extra ')'
awk: line 1: syntax error at or near print
Error adding group testgroup to LDAP
```

I can't believe that ldapscripts package could be broken and nobody noticed - there must be something else in the setup that triggers the error.

---

### Post by iva2k on 2013-09-13
There appears to be a bug in Ubuntu/debian patch to ldapscripts that borks trying to load configuration from /etc/ldap.conf.

Help thyself:

```

sudo cp /usr/share/ldapscripts/runtime.debian /usr/share/ldapscripts/runtime.debian.orig
sudo -b gedit /usr/share/ldapscripts/runtime.debian

```

Find the line in getfield function:
```

	local value="$(awk "/^[ \t]*$field/ {sub(/^[ \t]*$field[ \t]*/,\"\"); sub(/[ \t]*(#.*)?\$/, \"\"); print \$0}" "$conffile")"

```
And change it to:
```

	local value=$(awk "/^[ \t]*$field/ {sub(/^[ \t]*$field[ \t]*/,\"\"); sub(/[ \t]*(#.*)?\$/, \"\"); print \$0}" "$conffile")

```

The change is simply to remove quotes around $(...). I wonder how it was tested and passed?

---

### Post by iva2k on 2013-09-14
I reported a bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/ldapscripts/+bug/1225440](https://bugs.launchpad.net/ubuntu/+source/ldapscripts/+bug/1225440)

---

### Post by iva2k on 2013-09-14
[removed]

---

