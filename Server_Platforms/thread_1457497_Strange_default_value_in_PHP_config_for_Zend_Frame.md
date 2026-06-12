---
title: "Strange default value in PHP config for Zend Framework package"
date: 2010-04-18
forum: Server Platforms
---

### Post by ofn on 2010-04-18
Hi.
One interesting story happend to me few days ago.
I installed **Zend Framework** from repository and enabled it by editing /etc/php5/conf.d/zend-framework.ini. There was one strange line:

[FONT=Courier New];include_path=${include_path}":/usr/share/php/libzend-framework-php"[/FONT]

Hmm, thought I... *does php ini engine evaluate this kinda bash vars?*
But, naive as a child, simply uncommented it and... totally forgot about it. (Actually, I don't use Zend in my work, so this was just an equipment test).
**Next day apache was down** and only reason for that I considered in my messing with init jobs. But after some crazy hours clue was found in /var/log/kern/log:

[FONT=Courier New]Apr 16 18:45:59 ofn-desktop kernel: [   50.646513] apache2[2134]: segfault at 4 ip 012b60c1 sp bfd0e1e0 error 4 in libphp5.so[f98000+4eb000][/FONT]

So, changing config line in /etc/php5/conf.d/zend-framework.ini to 

[FONT=Courier New]include_path="/usr/share/php/libzend-framework-php"[/FONT]

 helped to resurrect apache, but destroyed previously declared include_path. And then I realized, that **THERE IS NO WAY TO APPEND DATA TO include_path VARIABLE IN php.ini**, but only in time of script execution as mentioned [here]("http://stackoverflow.com/questions/1135206/how-to-append-a-path-to-phps-include-path-in-htaccess"). Well, this is quite other story.

[SIZE=3]*So, people, pay more attention to default values in config files - they're not always perfect. And good luck.*[/SIZE]
[CENTER][INDENT][LEFT][FONT=Courier New]CAST
[/FONT][/LEFT]
[/INDENT][LEFT][FONT=Courier New]PHP 5.2.10-2ubuntu6.4
[/FONT]
[FONT=Courier New] Apache/2.2.12 (Ubuntu)
Zend Framework 1.9.4[/FONT]
[/LEFT]
[/CENTER]

---

