---
title: "Centra_Columns not OK when logging into new phpMyAdmin install"
date: 2015-10-16
forum: Server Platforms
---

### Post by Robertjm on 2015-10-16
Hi all,

I just installed Wiley Werewolf to a Parallels virtual machine and am trying to get PHP running. Everything installed. However, when I first log into PhpMyAdmin, I get a warning message about it not being fully configured (paraphrasing). When I click on the "see why" link, everything is green (OK), except for:

$cfg['Servers'][$i]['central_columns'] ... 	not OK
Managing Central list of columns: Disabled

Mind you this is a virgin install, so I'm not exactly sure what is triggering this, or what I need to modify in my installation to get rid of it.

Help will be greatly appreciated. I've never encountered this error before. But, it's been quite some time. But, maybe this is something installed since 14.04. 

Thanks!

Robert

---

### Post by sandyd on 2015-10-16
Moved to *Server Platforms*

---

### Post by sandyd on 2015-10-16
central_columns is a PMA feature that uses the table pma_central, which is part of the PhpMyAdmin PMA database.

If you haven't imported the PMA database (see [here]("https://wiki.phpmyadmin.net/pma/Configuration_storage")) you will see that message.

---

