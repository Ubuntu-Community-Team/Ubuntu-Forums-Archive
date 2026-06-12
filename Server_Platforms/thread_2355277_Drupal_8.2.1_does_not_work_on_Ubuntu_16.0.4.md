---
title: "Drupal 8.2.1 does not work on Ubuntu 16.0.4"
date: 2017-03-11
forum: Server Platforms
---

### Post by deepakdeshp on 2017-03-11
Hello,
I downloaded and installed Drupal 8.2.1 on Ubuntu 16.0.4 server successfully. I can login as admin successfully. But and url on the site does not open,

Code:
[http://server/drupal/admin/appearance](http://server/drupal/admin/appearance)
gives error
Code:
CODE: [SELECT ALL]("https://forums.linuxmint.com/viewtopic.php?f=47&t=241378#")
The requested URL /drupal/admin/appearance was not found on this server.

. is the error .I saw that the folder admin isnt created on the server . Same thing happened with Drupal 7 too

Any clues to the problems please.
If I have helped you solve a problem, please add [SOLVED] to your first post title, it helps other users looking for help, and keeps the forum clean.
I am using Mint 18 Cinnamon 64 bit with AMD processor .


[RIGHT][/RIGHT]

---

### Post by ian-weisser on 2017-03-11
Same thing happened in Drupal 7 that you manually installed?
Or same thing happened in the Ubuntu package drupal7 v7.44-1ubuntu1~16.04.0 ?

---

### Post by deepakdeshp on 2017-03-11
Same thing happened in the Ubuntu package Drupal 7

---

### Post by ian-weisser on 2017-03-12
Did you check the bug reports to see if anyone else has reported this problem?
Can you reliably replicate the problem with a fresh 16.10 install (usually in a VM), and the stock 16.10 version of Drupal. 17.04 too?

---

### Post by deepakdeshp on 2017-03-13
> **ian-weisser said:**
> Did you check the bug reports to see if anyone else has reported this problem?
Can you reliably replicate the problem with a fresh 16.10 install (usually in a VM), and the stock 16.10 version of Drupal. 17.04 too?
Thank you for your reply. But the problem had to be found out with the existing set up. Drupal and Ubuntu are both world famous softwares and this problem wasnt reported anywhere.

[COLOR=#242729][FONT=Arial]I found the answer here [https://www.drupal.org/node/2134281](https://www.drupal.org/node/2134281)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I added these 3 lines 

```
<Directory /var/www> AllowOverride all</Directory>
```to the following file[/FONT][/COLOR]
```
/etc/apache2/sites-available/000-default.conf
[COLOR=#242729][FONT=Arial]
```and I am able to browse all the links on the first apache page now.[/FONT][/COLOR]

---

### Post by ian-weisser on 2017-03-13
> **deepakdeshp said:**
> [...] the problem had to be found out with the existing set up[COLOR=#242729][FONT=Arial].[/FONT][/COLOR]

Interesting. That seems the opposite of what you wrote in Post #3: "[COLOR=#000000]Same thing happened in the Ubuntu package Drupal 7[/COLOR]"

---

### Post by deepakdeshp on 2017-03-14
Yes I tried with Ubuntu package also , but since the problem was in [COLOR=#000000][FONT=&quot]/etc/apache2/sites-available/000-default.conf, it didnt work with both Drupal versions.[/FONT][/COLOR]

---

