---
title: "Can't get modsecurity core ruleset 2.0.8 to work"
date: 2010-08-30
forum: Security
---

### Post by FuturePilot on 2010-08-30
I tried updating my modsecurity core ruleset to the latest version 2.0.8 and something seems broken. I didn't change any of my configs, I just downloaded the latest ruleset archive and extracted it just like I always do, and I end up with this:

```
* Restarting web server apache2
Syntax error on line 52 of /etc/apache2/conf.d/modsecurity/optional_rules/modsecurity_crs_40_experimental.conf:
Error parsing actions: Unexpected character at position 74: phase:2,t:none,pass,nolog,auditlog,id:'960023',rev:'2.0.8,msg:'Restricted Character Anomaly Detection Alert - Total # of special characters exceeded',logdata:'%{matched_var}',setvar:tx.anomaly_score=+%{tx.warning_anomaly_score}
   ...fail!
```

If I go back to the previous version I was using, 2.0.4. everything works fine. Has anyone else had problems with 2.0.8?

---

### Post by bodhi.zazen on 2010-08-30
I've not tried it, but looking at what you posted, it appears there is an unclosed quote at rev:'2.0.8

should probably be

rev:'2.0.8'

---

### Post by FuturePilot on 2010-08-31
Aha! That pesky little quote missing ;) There was actually the same error on line 57 as well. Well now there's more problems.

```
 * Restarting web server apache2
Syntax error on line 30 of /etc/apache2/conf.d/modsecurity/optional_rules/modsecurity_crs_42_comment_spam.conf:
Error creating rule: Could not open phrase file "/etc/apache2/conf.d/modsecurity/optional_rules/modsecurity_42_comment_spam.data": No such file or directory
   ...fail!
```
I ended up symlinking the data files from the base_rules directory but then got

```
* Restarting web server apache2
Syntax error on line 29 of /etc/apache2/conf.d/modsecurity/optional_rules/modsecurity_crs_49_header_tagging.conf:
Invalid command 'RequestHeader', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!
```

I had to
```
sudo a2enmod headers
```
Now it all seems to be working.

The only other odd thing was all the files had a weird ownership on them like
```
-rw-r--r-- 1 283429084 234561557  7117 2010-08-27 12:59 modsecurity_crs_10_config.conf
```
so I had to chown them back to root.

---

### Post by bodhi.zazen on 2010-08-31
Glad you got it sorted. You may wish to report the problems on the mod_security mailing list, my guess is there was an attempt to preserve permissions to an non-existent user (on your system) in the tar ball (just a guess).

---

### Post by FuturePilot on 2010-08-31
> **bodhi.zazen said:**
> my guess is there was an attempt to preserve permissions to an non-existent user (on your system) in the tar ball (just a guess).

That would be my guess too.

---

