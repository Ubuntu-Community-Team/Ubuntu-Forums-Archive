---
title: "Cron being executed by another IP?"
date: 2011-12-01
forum: Security
---

### Post by VcDeveloper on 2011-12-01
I'm running Drupal 7 and I've created two cron jobs for my development and production website, but I have these cron runs by another IP:

```
Nov 29 16:04:12 anointed-server drupal: http://------.com|1322611438|cron|94.41.60.187|http://------.com/user/login?destination=welcome|http://yandex.ru/yandsearch?text=the+current+page+feel|0||Cron run completed.
Nov 30 23:05:48 anointed-server drupal: http://------.com|1322723147|cron|217.64.173.227|http://------.com/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:51 anointed-server drupal: http://------.com|1322723149|cron|217.64.173.227|http://------.com/db/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:53 anointed-server drupal: http://------.com|1322723151|cron|217.64.173.227|http://------.com/dbadmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:54 anointed-server drupal: http://------.com|1322723154|cron|217.64.173.227|http://------.com/myadmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:56 anointed-server drupal: http://------.com|1322723155|cron|217.64.173.227|http://------.com/mysql/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:58 anointed-server drupal: http://------.com|1322723157|cron|217.64.173.227|http://------.com/mysqladmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:58 anointed-server drupal: http://------.com|1322723142|cron|217.64.173.227|http://------.com/muieblackcat||0||Cron run completed.

```

... how is this able to be logged in "messages" instead of access denied in my web error logs?

---

### Post by OpSecShellshock on 2011-12-01
It's hard to say what happened without more information. Do you know what your server's response to this activity might have been? The "muieblackcat" line indicates that this has to do with an automated attack tool, and so from that I gather that the previous entries are part of an attempt to find vulnerable files and directories which may or may not be there depending on your server (and man is it a noisy attack tool!). I've seen these sorts of requests in IDS events many times, but I've never seen them from the perspective of a messages log. Are these events similar to what your legitimate cron runs look like?

---

### Post by VcDeveloper on 2011-12-01
> **OpSecShellshock said:**
> It's hard to say what happened without more information. Do you know what your server's response to this activity might have been? 

here is my web site access log say for 217.64.173.227:
```
217.64.173.227 - - [30/Nov/2011:23:05:47 -0800] "GET //scripts/setup.php HTTP/1.1" 404 5687 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:48 -0800] "GET //admin/scripts/setup.php HTTP/1.1" 403 481 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:49 -0800] "GET //admin/pma/scripts/setup.php HTTP/1.1" 403 484 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:49 -0800] "GET //admin/phpmyadmin/scripts/setup.php HTTP/1.1" 403 486 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:49 -0800] "GET //db/scripts/setup.php HTTP/1.1" 404 5698 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:51 -0800] "GET //dbadmin/scripts/setup.php HTTP/1.1" 404 5700 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:54 -0800] "GET //myadmin/scripts/setup.php HTTP/1.1" 404 5703 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:55 -0800] "GET //mysql/scripts/setup.php HTTP/1.1" 404 5694 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:57 -0800] "GET //mysqladmin/scripts/setup.php HTTP/1.1" 404 5700 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:42 -0800] "GET /muieblackcat HTTP/1.1" 404 5677 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:58 -0800] "GET //typo3/phpmyadmin/scripts/setup.php HTTP/1.1" 404 5709 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:05:59 -0800] "GET //phpadmin/scripts/setup.php HTTP/1.1" 404 5700 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:01 -0800] "GET //phpMyAdmin/scripts/setup.php HTTP/1.1" 404 5701 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:02 -0800] "GET //phpmyadmin/scripts/setup.php HTTP/1.1" 403 484 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:02 -0800] "GET //phpmyadmin1/scripts/setup.php HTTP/1.1" 404 5697 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:03 -0800] "GET //phpmyadmin2/scripts/setup.php HTTP/1.1" 404 5705 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:05 -0800] "GET //pma/scripts/setup.php HTTP/1.1" 404 5693 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:06 -0800] "GET //web/phpMyAdmin/scripts/setup.php HTTP/1.1" 404 5706 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:07 -0800] "GET //xampp/phpmyadmin/scripts/setup.php HTTP/1.1" 404 5710 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:08 -0800] "GET //web/scripts/setup.php HTTP/1.1" 404 5692 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:09 -0800] "GET //php-my-admin/scripts/setup.php HTTP/1.1" 404 5711 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:11 -0800] "GET //websql/scripts/setup.php HTTP/1.1" 404 5698 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:12 -0800] "GET //phpmyadmin/scripts/setup.php HTTP/1.1" 403 484 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:12 -0800] "GET //phpMyAdmin/scripts/setup.php HTTP/1.1" 404 5703 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:13 -0800] "GET //phpMyAdmin-2/scripts/setup.php HTTP/1.1" 404 5705 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:15 -0800] "GET //php-my-admin/scripts/setup.php HTTP/1.1" 404 5704 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:16 -0800] "GET //phpMyAdmin-2.2.3/scripts/setup.php HTTP/1.1" 404 5717 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:17 -0800] "GET //phpMyAdmin-2.2.6/scripts/setup.php HTTP/1.1" 404 5708 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:21 -0800] "GET //phpMyAdmin-2.5.4/scripts/setup.php HTTP/1.1" 404 5712 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:22 -0800] "GET //phpMyAdmin-2.5.5-rc1/scripts/setup.php HTTP/1.1" 404 5715 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:24 -0800] "GET //phpMyAdmin-2.5.5-rc2/scripts/setup.php HTTP/1.1" 404 5717 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:25 -0800] "GET //phpMyAdmin-2.5.5/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:26 -0800] "GET //phpMyAdmin-2.5.5-pl1/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:27 -0800] "GET //phpMyAdmin-2.5.6-rc1/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:28 -0800] "GET //phpMyAdmin-2.5.6-rc2/scripts/setup.php HTTP/1.1" 404 5723 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:30 -0800] "GET //phpMyAdmin-2.5.6/scripts/setup.php HTTP/1.1" 404 5710 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:31 -0800] "GET //phpMyAdmin-2.5.7/scripts/setup.php HTTP/1.1" 404 5717 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:32 -0800] "GET //phpMyAdmin-2.5.7-pl1/scripts/setup.php HTTP/1.1" 404 5724 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:33 -0800] "GET //phpMyAdmin-2.6.0-alpha/scripts/setup.php HTTP/1.1" 404 5718 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:34 -0800] "GET //phpMyAdmin-2.6.0-alpha2/scripts/setup.php HTTP/1.1" 404 5723 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:36 -0800] "GET //phpMyAdmin-2.6.0-beta1/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:37 -0800] "GET //phpMyAdmin-2.6.0-beta2/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:38 -0800] "GET //phpMyAdmin-2.6.0-rc1/scripts/setup.php HTTP/1.1" 404 5715 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:39 -0800] "GET //phpMyAdmin-2.6.0-rc2/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:40 -0800] "GET //phpMyAdmin-2.6.0-rc3/scripts/setup.php HTTP/1.1" 404 5724 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:42 -0800] "GET //phpMyAdmin-2.6.0/scripts/setup.php HTTP/1.1" 404 5710 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:43 -0800] "GET //phpMyAdmin-2.6.0-pl1/scripts/setup.php HTTP/1.1" 404 5718 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:44 -0800] "GET //phpMyAdmin-2.6.0-pl2/scripts/setup.php HTTP/1.1" 404 5722 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:45 -0800] "GET //phpMyAdmin-2.6.0-pl3/scripts/setup.php HTTP/1.1" 404 5721 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:49 -0800] "GET //phpMyAdmin-2.6.1-rc2/scripts/setup.php HTTP/1.1" 404 5721 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:50 -0800] "GET //phpMyAdmin-2.6.1/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:52 -0800] "GET //phpMyAdmin-2.6.1-pl1/scripts/setup.php HTTP/1.1" 404 5715 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:53 -0800] "GET //phpMyAdmin-2.6.1-pl2/scripts/setup.php HTTP/1.1" 404 5719 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:54 -0800] "GET //phpMyAdmin-2.6.1-pl3/scripts/setup.php HTTP/1.1" 404 5725 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:55 -0800] "GET //phpMyAdmin-2.6.2-rc1/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:57 -0800] "GET //phpMyAdmin-2.6.2-beta1/scripts/setup.php HTTP/1.1" 404 5723 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:58 -0800] "GET //phpMyAdmin-2.6.2-rc1/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:06:59 -0800] "GET //phpMyAdmin-2.6.2/scripts/setup.php HTTP/1.1" 404 5711 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:00 -0800] "GET //phpMyAdmin-2.6.2-pl1/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:01 -0800] "GET //phpMyAdmin-2.6.3/scripts/setup.php HTTP/1.1" 404 5711 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:02 -0800] "GET //phpMyAdmin-2.6.3-rc1/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:04 -0800] "GET //phpMyAdmin-2.6.3/scripts/setup.php HTTP/1.1" 404 5705 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:05 -0800] "GET //phpMyAdmin-2.6.3-pl1/scripts/setup.php HTTP/1.1" 404 5715 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:06 -0800] "GET //phpMyAdmin-2.6.4-rc1/scripts/setup.php HTTP/1.1" 404 5718 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:08 -0800] "GET //phpMyAdmin-2.6.4-pl1/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:09 -0800] "GET //phpMyAdmin-2.6.4-pl2/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:10 -0800] "GET //phpMyAdmin-2.6.4-pl3/scripts/setup.php HTTP/1.1" 404 5717 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:11 -0800] "GET //phpMyAdmin-2.6.4-pl4/scripts/setup.php HTTP/1.1" 404 5723 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:12 -0800] "GET //phpMyAdmin-2.6.4/scripts/setup.php HTTP/1.1" 404 5713 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:14 -0800] "GET //phpMyAdmin-2.7.0-beta1/scripts/setup.php HTTP/1.1" 404 5726 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:15 -0800] "GET //phpMyAdmin-2.7.0-rc1/scripts/setup.php HTTP/1.1" 404 5719 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:16 -0800] "GET //phpMyAdmin-2.7.0-pl1/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:17 -0800] "GET //phpMyAdmin-2.7.0-pl2/scripts/setup.php HTTP/1.1" 404 5716 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:18 -0800] "GET //phpMyAdmin-2.7.0/scripts/setup.php HTTP/1.1" 404 5707 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:20 -0800] "GET //phpMyAdmin-2.8.0-beta1/scripts/setup.php HTTP/1.1" 404 5726 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:21 -0800] "GET //phpMyAdmin-2.8.0-rc1/scripts/setup.php HTTP/1.1" 404 5719 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:22 -0800] "GET //phpMyAdmin-2.8.0-rc2/scripts/setup.php HTTP/1.1" 404 5718 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:23 -0800] "GET //phpMyAdmin-2.8.0/scripts/setup.php HTTP/1.1" 404 5706 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:25 -0800] "GET //phpMyAdmin-2.8.0.1/scripts/setup.php HTTP/1.1" 404 5714 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:26 -0800] "GET //phpMyAdmin-2.8.0.2/scripts/setup.php HTTP/1.1" 404 5718 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:27 -0800] "GET //phpMyAdmin-2.8.0.3/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:28 -0800] "GET //phpMyAdmin-2.8.0.4/scripts/setup.php HTTP/1.1" 404 5714 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:29 -0800] "GET //phpMyAdmin-2.8.1-rc1/scripts/setup.php HTTP/1.1" 404 5720 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:30 -0800] "GET //phpMyAdmin-2.8.1/scripts/setup.php HTTP/1.1" 404 5713 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:32 -0800] "GET //phpMyAdmin-2.8.2/scripts/setup.php HTTP/1.1" 404 5712 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:33 -0800] "GET //sqlmanager/scripts/setup.php HTTP/1.1" 404 5701 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:34 -0800] "GET //mysqlmanager/scripts/setup.php HTTP/1.1" 404 5709 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:35 -0800] "GET //p/m/a/scripts/setup.php HTTP/1.1" 404 5693 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:36 -0800] "GET //PMA2005/scripts/setup.php HTTP/1.1" 404 5700 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:38 -0800] "GET //pma2005/scripts/setup.php HTTP/1.1" 404 5699 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:39 -0800] "GET //phpmanager/scripts/setup.php HTTP/1.1" 404 5698 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:40 -0800] "GET //php-myadmin/scripts/setup.php HTTP/1.1" 404 5708 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:42 -0800] "GET //phpmy-admin/scripts/setup.php HTTP/1.1" 404 5706 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:43 -0800] "GET //webadmin/scripts/setup.php HTTP/1.1" 404 5694 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:44 -0800] "GET //sqlweb/scripts/setup.php HTTP/1.1" 404 5696 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:45 -0800] "GET //websql/scripts/setup.php HTTP/1.1" 404 5698 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:46 -0800] "GET //webdb/scripts/setup.php HTTP/1.1" 404 5696 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:47 -0800] "GET //mysqladmin/scripts/setup.php HTTP/1.1" 404 5698 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:49 -0800] "GET //mysql-admin/scripts/setup.php HTTP/1.1" 404 5710 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:50 -0800] "GET //databaseadmin/scripts/setup.php HTTP/1.1" 404 5705 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:51 -0800] "GET //admm/scripts/setup.php HTTP/1.1" 404 5694 "-" "-"
217.64.173.227 - - [30/Nov/2011:23:07:52 -0800] "GET //admn/scripts/setup.php HTTP/1.1" 404 5690 "-" "-"

```here is my web site access log say for 94.41.60.187:
```
94.41.60.187 - - [29/Nov/2011:16:03:58 -0800] "GET /user/login?destination=welcome HTTP/1.1" 200 5615 "http://yandex.ru/yandsearch?text=the+current+page+feel" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/system/system.base.css?lvcivh HTTP/1.1" 200 2154 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/system/system.menus.css?lvcivh HTTP/1.1" 200 961 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/system/system.theme.css?lvcivh HTTP/1.1" 200 1521 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/system/system.messages.css?lvcivh HTTP/1.1" 200 682 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/comment/comment.css?lvcivh HTTP/1.1" 200 441 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/date/date_popup/themes/datepicker.1.7.css?lvcivh HTTP/1.1" 200 1207 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/field/theme/field.css?lvcivh HTTP/1.1" 200 535 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/search/search.css?lvcivh HTTP/1.1" 200 532 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/google_webfont_loader_api/fonts/palaoe_bora/render_stylesheet.css?lvcivh HTTP/1.1" 200 508 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/feedback/feedback.css?lvcivh HTTP/1.1" 200 860 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /misc/jquery.once.js?v=1.2 HTTP/1.1" 200 1381 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/panels/js/panels.js?lvcivh HTTP/1.1" 200 587 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/node/node.css?lvcivh HTTP/1.1" 200 408 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/feedback/feedback.js?lvcivh HTTP/1.1" 200 978 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/mollom/mollom.css?lvcivh HTTP/1.1" 200 460 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /misc/textarea.js?v=7.9 HTTP/1.1" 200 732 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/logintoboggan/logintoboggan.css?lvcivh HTTP/1.1" 200 628 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/date/date_api/date.css?lvcivh HTTP/1.1" 200 1692 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /sites/all/modules/views_slideshow/js/views_slideshow.js?lvcivh HTTP/1.1" 200 3141 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:13 -0800] "GET /modules/book/book.css?lvcivh HTTP/1.1" 200 699 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:17 -0800] "GET /sites/------.com/themes/corporateclean/images/search-button.png HTTP/1.1" 200 1239 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:17 -0800] "GET /sites/------.com/files/googleanalytics/ga.js?lvcivh HTTP/1.1" 200 13317 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:17 -0800] "GET /sites/------.com/themes/corporateclean/logo.png HTTP/1.1" 200 23246 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"
94.41.60.187 - - [29/Nov/2011:16:04:18 -0800] "GET /misc/feed.png HTTP/1.1" 200 910 "http://------.com/user/login?destination=welcome" "Opera/9.80 (Windows NT 5.1; U; ru) Presto/2.2.15 Version/10.10"

```here is my web site error log say for 217.64.173.227:
```
[Wed Nov 30 23:05:48 2011] [error] [client 217.64.173.227] client  denied by server configuration:  /srv/drupal/7/production/drupal-7.9/admin
[Wed Nov 30 23:05:49 2011] [error] [client 217.64.173.227] client denied  by server configuration: /srv/drupal/7/production/drupal-7.9/admin
[Wed Nov 30 23:05:49 2011] [error] [client 217.64.173.227] client denied  by server configuration: /srv/drupal/7/production/drupal-7.9/admin
[Wed Nov 30 23:06:02 2011] [error] [client 217.64.173.227] client denied by server configuration: /usr/share/phpmyadmin/scripts
[Wed Nov 30 23:06:06 2011] [error] [client 217.64.173.227] Negotiation:  discovered file(s) matching request:  /srv/drupal/7/production/drupal-7.9/web (None could be negotiated).
[Wed Nov 30 23:06:08 2011] [error] [client 217.64.173.227] Negotiation:  discovered file(s) matching request:  /srv/drupal/7/production/drupal-7.9/web (None could be negotiated).
[Wed Nov 30 23:06:12 2011] [error] [client 217.64.173.227] client denied by server configuration: /usr/share/phpmyadmin/scripts

```There not being executed from my system according to my syslogs:
```
Nov 30 22:55:01 anointed-server CRON[4664]: (root) CMD (http://drupal7.------.com/cron.php?cron_key=yRXQs3HenATC1ULwocOSyOxOvVqWg3LyTVe30uF3fSg)
Nov 30 22:55:01 anointed-server CRON[4665]: (root) CMD (http://------.com/cron.php?cron_key=yRXQs3HenATC1ULwocOSyOxOvVqWg3LyTVe30uF3fSg)
Nov 30 23:00:01 anointed-server CRON[5438]: (root) CMD (http://------.com/cron.php?cron_key=yRXQs3HenATC1ULwocOSyOxOvVqWg3LyTVe30uF3fSg)
Nov 30 23:00:01 anointed-server CRON[5439]: (root) CMD (http://drupal7.------.com/cron.php?cron_key=yRXQs3HenATC1ULwocOSyOxOvVqWg3LyTVe30uF3fSg)
Nov 30 23:05:48 anointed-server drupal: http://------.com|1322723147|cron|217.64.173.227|http://------.com/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:51 anointed-server drupal: http://------.com|1322723149|cron|217.64.173.227|http://------.com/db/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:53 anointed-server drupal: http://------.com|1322723151|cron|217.64.173.227|http://------.com/dbadmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:54 anointed-server drupal: http://------.com|1322723154|cron|217.64.173.227|http://------.com/myadmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:56 anointed-server drupal: http://------.com|1322723155|cron|217.64.173.227|http://------.com/mysql/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:58 anointed-server drupal: http://------.com|1322723157|cron|217.64.173.227|http://------.com/mysqladmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:58 anointed-server drupal: http://------.com|1322723142|cron|217.64.173.227|http://------.com/muieblackcat||0||Cron run completed.
Nov 30 23:17:01 anointed-server CRON[8064]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 23:55:01 anointed-server CRON[13910]: (root) CMD (http://------.com/cron.php?cron_key=yRXQs3HenATC1ULwocOSyOxOvVqWg3LyTVe30uF3fSg)
Nov 30 23:55:01 anointed-server CRON[13911]: (root) CMD (http://drupal7.------.com/cron.php?cron_key=yRXQs3HenATC1ULwocOSyOxOvVqWg3LyTVe30uF3fSg)
Dec  1 00:00:01 anointed-server CRON[14691]: (root) CMD (http://------.com/cron.php?cron_key=yRXQs3HenATC1ULwocOSyOxOvVqWg3LyTVe30uF3fSg)

```So it from the HTTP level.

> **OpSecShellshock said:**
> 
The "muieblackcat" line indicates that this has to do with an automated attack tool, and so from that I gather that the previous entries are part of an attempt to find vulnerable files and directories which may or may not be there depending on your server (and man is it a noisy attack tool!). I've seen these sorts of requests in IDS events many times, but I've never seen them from the perspective of a messages log. Are these events similar to what your legitimate cron runs look like?

Yes, Here my cron job messages up to the first un-known IP:
```
Nov 27 13:02:21 anointed-server drupal: http://------.com|1322427708|cron|127.0.0.1|http://------.com/||0||Cron run completed.
Nov 27 13:03:13 anointed-server drupal: http://------.com|1322427772|cron|127.0.0.1|http://------.com/||0||Cron run completed.
Nov 27 15:45:43 anointed-server drupal: http://------.com|1322437514|cron|127.0.0.1|http://------.com/|http://------.com/|0||Cron run completed.
Nov 27 15:46:53 anointed-server drupal: http://------.com|1322437593|cron|127.0.0.1|http://------.com/are-you-a-lost-sheep-of-Yisrael|http://------.com/|0||Cron run completed.
Nov 27 18:48:19 anointed-server drupal: http://------.com|1322448480|cron|127.0.0.1|http://------.com/admin/structure/types/manage/natsarim_video_messages?render=overlay|http://------.com/are-you-a-lost-sheep-of-Yisrael|0||Cron run completed.
Nov 27 22:49:29 anointed-server drupal: http://production.------.com|1322462955|cron|192.168.0.101|http://production.------.com/||0||Cron run completed.
Nov 28 07:20:18 anointed-server drupal: http://------.com|1322493597|cron|127.0.0.1|http://------.com/admin/reports/status?render=overlay|http://------.com/are-you-a-lost-sheep-of-Yisrael|0||Cron run completed.
Nov 28 22:17:05 anointed-server drupal: http://------.com|1322547423|cron|127.0.0.1|http://------.com/||0||Attempting to re-run cron while it is already running.
Nov 28 22:17:15 anointed-server drupal: http://------.com|1322547419|cron|127.0.0.1|http://------.com/||0||Cron run completed.
Nov 28 22:23:49 anointed-server drupal: http://------.com|1322547827|cron|127.0.0.1|http://------.com/||0||Attempting to re-run cron while it is already running.
Nov 28 22:23:51 anointed-server drupal: http://------.com|1322547830|cron|127.0.0.1|http://------.com/curlypage/1/view|http://------.com/sites/all/modules/curlypage/curlypage/flag.swf?flag150|0||Attempting to re-run cron while it is already running.
Nov 28 22:24:55 anointed-server drupal: http://------.com|1322547894|cron|127.0.0.1|http://------.com/||0||Attempting to re-run cron while it is already running.
Nov 28 22:24:56 anointed-server drupal: http://------.com|1322547896|cron|127.0.0.1|http://------.com/curlypage/1/view|http://------.com/sites/all/modules/curlypage/curlypage/flag.swf?flag150|0||Attempting to re-run cron while it is already running.
Nov 28 22:25:30 anointed-server drupal: http://------.com|1322547929|cron|127.0.0.1|http://------.com/|http://------.com/are-you-a-lost-sheep-of-Yisrael|0||Attempting to re-run cron while it is already running.
Nov 28 22:25:32 anointed-server drupal: http://------.com|1322547931|cron|127.0.0.1|http://------.com/curlypage/1/view||0||Attempting to re-run cron while it is already running.
Nov 28 22:25:43 anointed-server drupal: http://------.com|1322547941|cron|127.0.0.1|http://------.com/user/login?destination=welcome|http://------.com/|0||Attempting to re-run cron while it is already running.
Nov 28 22:25:45 anointed-server drupal: http://------.com|1322547944|cron|127.0.0.1|http://------.com/curlypage/1/view||0||Attempting to re-run cron while it is already running.
Nov 28 22:25:49 anointed-server drupal: http://------.com|1322547948|cron|127.0.0.1|http://------.com/|http://------.com/user/login?destination=welcome|0||Attempting to re-run cron while it is already running.
Nov 28 22:25:59 anointed-server drupal: http://------.com|1322547955|cron|127.0.0.1|http://------.com/admin/structure/curlypage?render=overlay|http://------.com/|0||Attempting to re-run cron while it is already running.
Nov 28 22:26:02 anointed-server drupal: http://------.com|1322547795|cron|127.0.0.1|http://------.com/are-you-a-lost-sheep-of-Yisrael||0||Cron run completed.
Nov 29 09:25:49 anointed-server drupal: http://------.com|1322587530|cron|127.0.0.1|http://------.com/admin/config/media/file-system?render=overlay|http://------.com/admin/config/media/file-system?render=overlay|0||Cron run completed.
Nov 29 12:15:18 anointed-server drupal: http://------.com|1322597682|cron|127.0.0.1|http://------.com/||0||Cron run completed.
Nov 29 12:46:34 anointed-server drupal: http://------.com|1322599576|cron|127.0.0.1|http://------.com/||0||Cron run completed.

```
Now here is the un-know IP:
```
Nov 29 16:04:12 anointed-server drupal: http://------.com|1322611438|cron|94.41.60.187|http://------.com/user/login?destination=welcome|http://yandex.ru/yandsearch?text=the+current+page+feel|0||Cron run completed.

```my other set of cron job messages up to the other un-known IP:
```
Nov 30 13:09:02 anointed-server drupal: http://------.com|1322687311|cron|127.0.0.1|http://------.com/admin/reports/status?render=overlay|http://------.com/|0||Cron run completed.
Nov 30 13:09:04 anointed-server drupal: http://------.com|1322687307|cron|127.0.0.1|http://------.com/admin/reports/status?render=overlay|http://------.com/page-content/donation-summary|0||Cron run completed.

```Now here is the other un-know IP:
```
Nov 30 23:05:48 anointed-server drupal: http://------.com|1322723147|cron|217.64.173.227|http://------.com/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:51 anointed-server drupal: http://------.com|1322723149|cron|217.64.173.227|http://------.com/db/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:53 anointed-server drupal: http://------.com|1322723151|cron|217.64.173.227|http://------.com/dbadmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:54 anointed-server drupal: http://------.com|1322723154|cron|217.64.173.227|http://------.com/myadmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:56 anointed-server drupal: http://------.com|1322723155|cron|217.64.173.227|http://------.com/mysql/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:58 anointed-server drupal: http://------.com|1322723157|cron|217.64.173.227|http://------.com/mysqladmin/scripts/setup.php||0||Attempting to re-run cron while it is already running.
Nov 30 23:05:58 anointed-server drupal: http://------.com|1322723142|cron|217.64.173.227|http://------.com/muieblackcat||0||Cron run completed.

```...and here is the rest of my cron jobs up to today:
```
Dec  1 09:12:43 anointed-server drupal: http://------.com|1322759561|cron|127.0.0.1|http://------.com/||0||Attempting to re-run cron while it is already running.
Dec  1 09:12:46 anointed-server drupal: http://------.com|1322759564|cron|127.0.0.1|http://------.com/curlypage/1/view|http://------.com/sites/all/modules/curlypage/curlypage/flag.swf?flag150|0||Attempting to re-run cron while it is already running.
Dec  1 09:12:46 anointed-server drupal: http://------.com|1322759551|cron|127.0.0.1|http://------.com/admin/reports/status?render=overlay|http://------.com/|0||Cron run completed.
Dec  1 09:13:00 anointed-server drupal: http://------.com|1322759560|cron|127.0.0.1|http://------.com/||0||Cron run completed.
Dec  1 09:13:32 anointed-server drupal: http://------.com|1322759599|cron|127.0.0.1|http://------.com/admin/reports/status/run-cron?render=overlay|http://------.com/|0||Cron run completed.
Dec  1 16:25:20 anointed-server drupal: http://------.com|1322785501|cron|127.0.0.1|http://------.com/page-content/donation-summary||0||Cron run completed.

```

---

### Post by Dangertux on 2011-12-01
Muie Blackcat is an automated web application exploitation platform. It has three notable elements to it.  It has a scanner, which is looking for common vulnerabilities -- since you're using Drupal I'm going to go ahead and assume it may have found one. My assumption is based on this line.

```

Nov 30 23:05:58 anointed-server drupal: http://------.com|1322723142|cron|217.64.173.227|http://------.com/muieblackcat||0||Cron run completed.

```

This indicates that the third element of the application which is a web shell. Usually a simple php script that allows remote access with the user privileges of the exploited web-server (usually www-data). 

The second element is an automated exploitationhcih  framework -- which you've probably already experienced. 

You should consider checking your server for the presence of a web-shell or 40 or 50. 

Hope this is helpful.

---

### Post by VcDeveloper on 2011-12-01
Ok thanks! I just notified Drupal and hoping they could shine more light on this if its my system or the Drupal Core needs a patch.

In the mean time I will check for these scripts.

---

