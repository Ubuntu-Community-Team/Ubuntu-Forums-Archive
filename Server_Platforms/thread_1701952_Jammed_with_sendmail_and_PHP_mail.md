---
title: "Jammed with sendmail and PHP mail"
date: 2011-03-07
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-03-07
Hi everyone,

I've an 10.10 ubuntu server where I use PHP to send mails (from a CMS). 
I've some problems:

1º I've install sendmail, but not sure what to configure. Initially it works but VERY VERY slow (like a minute for every mail) - I've change my /etc/hosts cause read something about configure it to make it fire. But now doesnt work at all.

2º Do you recommend me other MTA?, easier or better?. Then, how to unistall sendmail?.

3º I want to use @mydomainname.com, wich is mine. But Im newbie and not sure what to do. Have to change MX records?, make them point what?. 

Thanks a lot in advance! :P

---

### Post by windependence on 2011-03-07
Install postfix. Sendmail should have been installed already. Postfix is a drop in replacement for sendmail, which is quite old and difficult to configure. Your CMS should work without too many tweaks to Postfix. If you don't, you should have a static IP to do this because most mail servers will not accept mail from you if you have a dynamic IP. You only need to configure Postfix for smtp if you are only worried about sending mail out. Most of the time you need to do little or nothing to have this work. Start here after installing Postfix. you do NOT have to uninstall sendmail but you will have to disbale it if Postfix doesn't do it during the install:
 
[http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html)
 
-Tim

---

