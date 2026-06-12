---
title: "PHP5 permission issues"
date: 2010-10-05
forum: Server Platforms
---

### Post by renegadeandy on 2010-10-05
Hey!

I am trying to install Jinzero a media server on my ubuntu server.

I already had apache2 installed and have installed php5 etc.

When I try to access index.php I get an http error 500 and when I check the logs of my apache2 it shows:

[PHP]
[Tue Oct 05 23:58:34 2010] [error] [client 94.173.5.77] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0
[Tue Oct 05 23:58:34 2010] [error] [client 94.173.5.77] PHP Fatal error:  Unknown: Failed opening required '/var/www/jinzora-3.0/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
[/PHP]

Any ideas guys?!

Thanks,

Andy

---

### Post by renegadeandy on 2010-10-05
I am aware this is typically a permissions issue - however the files all have 0777 and the folder /var/www/jinzora/ also has 0755??

---

