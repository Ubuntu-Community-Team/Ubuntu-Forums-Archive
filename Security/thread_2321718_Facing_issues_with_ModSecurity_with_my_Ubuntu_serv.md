---
title: "Facing issues with ModSecurity with my Ubuntu server"
date: 2016-04-24
forum: Security
---

### Post by Sourav_Saha on 2016-04-24
Hey,

I'm a newbie here and facing a couple issue with my server. Wanted to harden the security of my Ubuntu server but facing some issues. Googled a lot but can't see any solution of these problems. Any suggestion on how to fix these?

I have installed mod_security. When I add the new symlinks to apache '/etc/apache2/mods-available/security2.conf" I get the following error:

```
Job for apache2.service failed because the control process exited with error code. See "systemctl status apache2.service" and "journalctl -xe" for details.
```

When I comment the line line --> Include "/etc/modsecurity/activated_rules/*.conf"

Apache starts working again.

Running systemctl status apache2.service shows

```
Syntax error on line 35 of /etc/modsecurity/activated_rules/modsecurity_crs_10_ignore_static.conf
```

Here is the line 35 content

```
SecAction "phase:2,t:none,nolog,pass,skipAfter:END_STATIC_CONTENT_CHECK"
```

Right now I am using OWASP ModSecurity core rule set version 2.2.4 and the latest version is 2.2.9 ([https://github.com/SpiderLabs/owasp-modsecurity-crs](https://github.com/SpiderLabs/owasp-modsecurity-crs)) Can that be the cause? If yes how can I update it to the latest version?

---

