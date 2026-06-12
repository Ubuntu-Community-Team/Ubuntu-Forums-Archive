---
title: "phpMyAdmin - PHP Fatal error: Allowed memory size of 268435456 bytes exhausted"
date: 2011-05-08
forum: Server Platforms
---

### Post by kingcu on 2011-05-08
I have the memory limit set to 128M in php.ini and  all I try to do is just upload a Excel 2007 sheet of size 130KB, which  contains only 100 rows. The max file upload limit is set to 20MB in php.ini. The error message in apache log reads:

```

[Mon May 09 11:40:47 2011] [error] [client 192.168.1.71] PHP Fatal error:  Allowed memory size of 268435456 bytes exhausted (tried to allocate 71 bytes) in /usr/share/phpmyadmin/libraries/PHPExcel/PHPExcel/Cell.php on line 0, referer: http://192.168.1.228/phpmyadmin/tbl_import.php?db=ddms&table=DRUG_STANDARD&token=482ee27e980f82cfc62b98f44b271686

```

I tried to increase the memory limit to 256MB and then to 512MB, but got the same error message every time. And of course, after I change php.ini, I restarted apache. Any idea what's going on here?

---

### Post by dtfinch on 2011-05-09
It might be this known issue: [http://phpexcel.codeplex.com/workitem/13151](http://phpexcel.codeplex.com/workitem/13151)

If you're uploading a table from a spreadsheet, I'd try tab delimited. Just copy from Excel and paste into a plain text editor.

---

### Post by kingcu on 2011-05-09
Thanks for the info. I exported the data to a csv file and then it imported with no problem. I'll stay away from MS spreadsheet from now on, :-).

---

