---
title: "website lags for 60 seconds"
date: 2018-02-14
forum: Server Platforms
---

### Post by micahpage on 2018-02-14
I have a website under LAMP using MyBB Forum software. Its a small forum but has been getting larger over the months. However i and other users have experienced random websites problems where the server will take up to 60 seconds to respond and sometimes just 4 seconds is dreadfully slow. Usually its almost instantaneous within a single second to load. It usually it one of fastest sites i visit daily. 

Im wondering if the default apache settings for timeouts are bogging it down after more people are showing up. This is my current settings 
```
#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 5


```

I checked the RAM with htop and only about 1/4 of the ram was used during the slow period. 

Should i increase MaxKeepAliveRequests to 200? Or decrease KeepAliveTimeout to 3? 

Is there another setting that could be bogging it down?

---

### Post by LHammonds on 2018-02-14
Those timeout values are for killing long-running processes to keep a stuck process from tying up your server indefinitely.

A typical site without problems shouldn't be touching those timeout limits with exception to doing uploads of VERY large files...cause they can take a while to upload.

You will need to isolate where the lag is happening.  Are there any partitions that are close to filling up...are there issues with a hard disk failing, etc.

Examine the apache log files, mysql log files, system logs, etc.

One thing I like to do is keep a log open while performing tasks so I can see what is being added to the log in realtime.

Example:
```
tail -f /var/log/apache2/error.log
```

LHammonds

---

### Post by micahpage on 2018-02-14
thank you for your response...


There is nothing in mysql.err or mysql.log or error.log at all

---

### Post by micahpage on 2018-03-05
I checked the log files but i dont see anything that woud slow down the server drastically. There are some errors but its pertaining to a plugin notemoderator issue which wouldnt effect speed.

```
root /var/log/apache2 # tail error.log[Mon Mar 05 09:18:47.294890 2018] [:error] [pid 4124] [client 185.86.93.21:41242] script '/var/www/metulburr.com/admin/login.php' not found or unable to stat, referer: https://python-forum.io/admin/login.php
[Mon Mar 05 09:19:56.857172 2018] [core:crit] [pid 4124] (13)Permission denied: [client 82.117.130.3:32981] AH00529: /var/www/metulburr.com/images/notemoderator/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable and that '/var/www/metulburr.com/images/notemoderator/' is executable, referer: https://python-forum.io/Thread-Nginx-Uwsgi-Django-111-Connection-refused-while-connecting-to-upstream?pid=25448
[Mon Mar 05 09:21:03.556824 2018] [core:crit] [pid 4151] (13)Permission denied: [client 88.160.113.190:50453] AH00529: /var/www/metulburr.com/images/notemoderator/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable and that '/var/www/metulburr.com/images/notemoderator/' is executable, referer: https://python-forum.io/cache/themes/theme1/notemoderator.css
[Mon Mar 05 09:21:34.187712 2018] [:error] [pid 4140] [client 179.186.156.47:26837] script '/var/www/metulburr.com/wp-login.php' not found or unable to stat
[Mon Mar 05 09:22:07.589989 2018] [:error] [pid 4161] [client 178.43.245.106:59123] script '/var/www/metulburr.com/wp-login.php' not found or unable to stat
[Mon Mar 05 09:23:31.506396 2018] [core:crit] [pid 4169] (13)Permission denied: [client 196.36.218.55:60137] AH00529: /var/www/metulburr.com/images/notemoderator/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable and that '/var/www/metulburr.com/images/notemoderator/' is executable, referer: https://python-forum.io/cache/themes/theme1/notemoderator.css
[Mon Mar 05 09:25:10.086914 2018] [:error] [pid 4168] [client 157.39.46.234:54304] script '/var/www/metulburr.com/wp-login.php' not found or unable to stat
[Mon Mar 05 09:25:23.408174 2018] [core:crit] [pid 4238] (13)Permission denied: [client 1.186.41.175:60285] AH00529: /var/www/metulburr.com/images/notemoderator/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable and that '/var/www/metulburr.com/images/notemoderator/' is executable, referer: https://python-forum.io/cache/themes/theme1/notemoderator.css
[Mon Mar 05 09:26:32.261106 2018] [core:crit] [pid 4285] (13)Permission denied: [client 147.171.44.204:59400] AH00529: /var/www/metulburr.com/images/notemoderator/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable and that '/var/www/metulburr.com/images/notemoderator/' is executable, referer: https://python-forum.io/cache/themes/theme1/notemoderator.css
[Mon Mar 05 09:27:50.839940 2018] [:error] [pid 4249] [client 41.58.92.107:54038] script '/var/www/metulburr.com/wp-login.php' not found or unable to stat
root /var/log/apache2 # 



```

---

