---
title: "apache config question"
date: 2010-11-14
forum: Security
---

### Post by methodtwo on 2010-11-14
Hi there
In an apache security howto that i recently read it suggested that these two lines should be in the config file:
```
Options FollowSymLinks 
AllowOverride None 
```
It said that these line would ensure that apache would not have access to files outside of it's web root.
However i've also read that it is a good idea to have:
```
Options -followSymlinks
```
Here it said that you should use this within a directory tag, to ensure that attackers are not able to follow symlinks to sensitive files like /etc/shadow. Surely if this were true you would want Options -FollowSymlinks in the directory tag of "/" right?.
So should the first code example be in the directory tag for the "/" directory or should i use the second code example in the directory tag for the "/" directory?. If not, then could you kindly explain why not(use either of these suggestions).
Thank you very much for your time
regards methodtwo

---

### Post by methodtwo on 2010-11-14
I know that the directory tag for the "/" directory should contain these lines:
```
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order deny,allow
    Deny from all
</Directory>

```
So the "Options  -FollowSymlinks" should be set on a per directory basis right?. And not in the tag for the "/" directory?

---

