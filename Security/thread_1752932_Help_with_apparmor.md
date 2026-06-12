---
title: "Help with apparmor"
date: 2011-05-08
forum: Security
---

### Post by desire.linux on 2011-05-08
I would like to know what the "owner" code in the profiles does, since I've read some different explanations for it. I'm confused about what it really does and when you should use it and not.

Thanks in advance for help!

---

### Post by Telengard C64 on 2011-05-08
[quote=man 5 apparmor.d]Rule Qualifiers
       There are several rule qualifiers that can be applied to permission
       rules.  Rule qualifiers can modify the rule and/or permissions within
       the rule.

       audit
           Specifies that permissions requests that match the rule should be
           recorded to the audit log.

       deny
           Specifies that permissions requests that match the rule should be
           denied without logging. Can be combined with 'audit' to enable
           logging.

[b]       owner
           Specifies that the task must have the same euid/fsuid as the object
           being referenced by the permission check.[/b]
[/quote]

Is that what you want to know about?

---

### Post by desire.linux on 2011-05-09
I'm new to apparmor, and English isn't my native language, so I would prefer a simple explanation. Thanks in advance.

---

### Post by bodhi.zazen on 2011-05-09
Do you understand Linux permissions ? Every file and process has an owner.

So in apparmor you can allow access to a file 

/path_to/file rw,

And furter restrict access in apparmor to the owner of the file

owner /path_to/file rw

With the second only the owner of the file can rw the file.

Typically this option is applied to files in your home directory.

---

### Post by desire.linux on 2011-05-09
Thank you, bodhi.zazen! Now I understand it much better! :)

---

