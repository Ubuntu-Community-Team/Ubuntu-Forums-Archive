---
title: "directory exception in htaccess"
date: 2009-07-30
forum: Server Platforms
---

### Post by ticknubbs on 2009-07-30
I have been looking all day on how to make an exception for a directory in htaccess with no luck thus far. I have a web directory with htaccess and pass set up however I need to allow all access to two of the directories in that folder without moving them out into another directory. 

Here is what I have right now...


```
<FilesMatch "(location_identification|family_relation)\.php$">
  Allow from all
  Satisfy any
</FilesMatch>


AuthName "Secure Login"
AuthType Basic
AuthUserFile /home/myself/public_html/site/.htpasswd
Require valid-user
```


and I need to make an exception to a directory named 'allow' located within site. I have tired several things with no luck and am looking for a fresh idea. Anybody have any?

---

### Post by RetchingRabbit on 2009-07-30
These directives can be nested, like html code itself. Seems like that might open up some more granular possibilities....

---

