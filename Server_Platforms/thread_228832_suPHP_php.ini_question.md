---
title: "suPHP php.ini question"
date: 2006-08-03
forum: Server Platforms
---

### Post by Oxygene on 2006-08-03
Hello,

I've been using mod_php4 for ages and it was nice to use
```
php_flag session.use_trans_sid on
```
for example, because I don't like to set such options globally in the php.ini file.

Now I wanted to make everything more secure and installed suPHP.
Php_flag is not supported by this apache2 module. Instead, one can use suPHP_ConfigPath to set the path where the php.ini resides.

I've got the following questions:

[LIST=1]
[*]Can a user change the setting of suPHP_ConfigPath in a .htaccess file?
[*]If I let the user provide his own php.ini, can he override **every** possible php.ini-setting like maximal memory usage etc.?
[/LIST]

I would consider the second point to be a security problem. Can I avoid it but allow the user to set "session.use_trans_sid on" on a directory basis nonetheless?

As I understand it, the php.ini-thing with suPHP_ConfigPath does not cascade over sub-directories so that you always have to provide a full php.ini configuration. Am I right on this point?

---

