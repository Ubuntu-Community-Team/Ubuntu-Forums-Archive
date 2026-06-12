---
title: "Bug fix for Church Website in A box Could not change theme"
date: 2009-09-25
forum: Ubuntu Christian Edition
---

### Post by david_kt on 2009-09-25
The bug: Could not change theme 
(admin >> Advance setting >> theme)
will result in error.

Basically it is because CWIAB is build on
old php, and some commands are not compatible with php5. Please
attached the solution. Just replace the file:

/var/www/modules/AutoTheme/includes/atAPI.php
/var/www/modules/Autolinks/pnuserapi.php

with attached file. For example you download the attached file on desktop, then the steps are:

1. Open terminal and cd Desktop
2. tar xvzf cwiab_bug_fix.tar.gz
2. sudo mv atAPI.php /var/www/modules/AutoTheme/includes/
3. sudo mv pnuserapi.php /var/www/modules/Autolinks/

After that you should be able to change theme.

DK

---

