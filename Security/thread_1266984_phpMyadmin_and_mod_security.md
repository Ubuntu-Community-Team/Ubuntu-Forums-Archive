---
title: "phpMyadmin and mod_security"
date: 2009-09-15
forum: Security
---

### Post by phillw on 2009-09-15
I've recently put mod_security onto my apache2 system and now have 
> **Method Not Implemented**

 GET to /phpmyadmin/tbl_change.php not supported.

  

If I try to edit a record by using phpyadmin. I've a dig round and it does seem to point to mod-security stopping phpmyadmin.

[http://www.gray.me.uk/linux-administration-and-management/modsecurity-and-phpmyadmin](http://www.gray.me.uk/linux-administration-and-management/modsecurity-and-phpmyadmin)

suggests

```
<LocationMatch “/phpMyAdmin/sql.php”>
SecRuleRemoveById 959004
SecRuleRemoveById 959005
SecRuleRemoveById 959906
</LocationMatch>
 
```

And adding the note > 
The downside to this rule is it switches off SQL Injection Attack protection, but I suppose as this particular part of phpMyAdmin is there just to execute SQL commands….

The only two pieces of user information that are read are escaped with mysql_real_escape_string  Is it safe to remove these rules when using mysql_real_escape_string for my input verifications ?

And, if so, where do the amendment to the rules need to be put

Regards,

Phill.

---

### Post by vikram1 on 2010-01-04
mod_security still blocks this page, probably because it doesn't
exclude all possible matches. It seems to apply to the line below
(from rules.conf) with "id:300016".
It's not clear to me if it applies to the next line as well.
 
Rule IDs are applied either to rules (single line) or rule chains
(multiple lines). Rule 300016 is a chained rule thus exclusion applies
to the second line too.

BTW, you should exclude all rules related to SQL Injection in order to
get PHPMyAdmin to work properly.
===============
[saturn ac compressor](http://www.1airconditioning.com/saturn_ac_compressor.htm)
[chicago party bus](http://www.chicagolimousine1.com)

---

