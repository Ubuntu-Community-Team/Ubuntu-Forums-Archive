---
title: "Trouble with php5 - can't see page."
date: 2015-06-28
forum: Server Platforms
---

### Post by RobRobinson on 2015-06-28
I know for sure that I have Apache2 installed correctly because when I open my browser and click the link I get:

```
[h=1]Index of /[/h][TABLE]
[TR]
[TH][IMG]http://192.168.254.15/icons/blank.gif[/IMG][/TH]
[TH][Name]("http://192.168.254.15/?C=N;O=D")[/TH]
[TH][Last modified]("http://192.168.254.15/?C=M;O=A")[/TH]
[TH][Size]("http://192.168.254.15/?C=S;O=A")[/TH]
[TH][Description]("http://192.168.254.15/?C=D;O=A")[/TH]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[TR]
[TD][IMG]http://192.168.254.15/icons/unknown.gif[/IMG][/TD]
[TD][hullo.php]("http://192.168.254.15/hullo.php")[/TD]
[TD="align: right"]2015-06-28 13:52[/TD]
[TD="align: right"]121[/TD]
[TD] [/TD]
[/TR]
[TR]
[TD][IMG]http://192.168.254.15/icons/unknown.gif[/IMG][/TD]
[TD][test.php]("http://192.168.254.15/test.php")[/TD]
[TD="align: right"]2015-06-28 16:49[/TD]
[TD="align: right"]18[/TD]
[TD] [/TD]
[/TR]
[TR]
[TH="colspan: 5"][HR][/HR][/TH]
[/TR]
[/TABLE]
Apache/2.4.7 (Ubuntu) Server at 192.168.254.15 Port 80
```

But when I click one of those php links, all I get is a blank page.

What the hell am I doing wrong?

Thank you in advance,

Rob

---

### Post by cariboo on 2015-06-28
I'd suggest you post the contents of your php files as attachments, instead of directly linking to them, as I can see your server is unreachable. Be sure to tar the files, as  files with php extensions are disallowed by the attachment manager.

---

### Post by RobRobinson on 2015-06-28
The php files are correct.  The site is accessible if you click where name is in orange.

---

### Post by CharlesA on 2015-06-28
> **RobRobinson said:**
> The php files are correct.  The site is accessible if you click where name is in orange.

It shows your private IP, so no one outside your local network can access them.

As for the directory listing, that is being shown because there is no index.php or index.html file in that directory.

You can also check your apache logs to see what is throwing errors:

```
tail /var/log/apache2/error.log
```

Edit:

If the logs don't tell you much you can always create a file that has these contents:
[php]<?php phpinfo() ?>[/php]

[http://php.net/manual/en/function.phpinfo.php](http://php.net/manual/en/function.phpinfo.php)

It will show some info about your server set up.

---

### Post by adam153 on 2015-06-28
Not sure if it's required for PHP but I know I installed some php resource before installing my forum.  Google: Ubuntu LAMP install (Linux Apache MySql PHP)

---

### Post by CharlesA on 2015-06-28
The logs should tell you what the problem is. If you are just getting a blank page and not the contents of the php file, something is either not right in those files (opening or closing <?php ... ?>) etc.

---

### Post by RobRobinson on 2015-06-28
the php code in test.php is exactly like your php code

---

### Post by CharlesA on 2015-06-29
> **RobRobinson said:**
> the php code in test.php is exactly like your php code

Then the only way you will be able to figure out what is wrong is to post the what the apache error logs are showing.

---

### Post by RobRobinson on 2015-06-29
This is what the error log came up with:

```
[Sun Jun 28 19:51:01.651013 2015] [:error] [pid 13705] [client 192.168.254.39:58712] PHP Fatal error:  Unknown: Failed opening required '/media/rob/robox/www/hullo.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0, referer: http://ubuntuforums.org/showthread.php?t=2284347
[Sun Jun 28 20:29:52.318398 2015] [core:error] [pid 13707] (13)Permission denied: [client 192.168.254.39:59260] AH00132: file permissions deny server access: /media/rob/robox/www/testing.html, referer: http://192.168.254.15/
[Sun Jun 28 20:30:07.841110 2015] [:error] [pid 13709] [client 192.168.254.39:59264] PHP Warning:  Unknown: failed to open stream: Permission denied in Unknown on line 0, referer: http://192.168.254.15/
[Sun Jun 28 20:30:07.841192 2015] [:error] [pid 13709] [client 192.168.254.39:59264] PHP Fatal error:  Unknown: Failed opening required '/media/rob/robox/www/test.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0, referer: http://192.168.254.15/
[Sun Jun 28 20:57:51.682745 2015] [mpm_prefork:notice] [pid 13702] AH00169: caught SIGTERM, shutting down
[Sun Jun 28 20:57:52.850322 2015] [mpm_prefork:notice] [pid 14543] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.9 configured -- resuming normal operations
[Sun Jun 28 20:57:52.850436 2015] [core:notice] [pid 14543] AH00094: Command line: '/usr/sbin/apache2'
[Sun Jun 28 20:58:42.019800 2015] [mpm_prefork:notice] [pid 14543] AH00169: caught SIGTERM, shutting down
[Mon Jun 29 05:32:49.620097 2015] [mpm_prefork:notice] [pid 1576] AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.9 configured -- resuming normal operations
[Mon Jun 29 05:32:49.647016 2015] [core:notice] [pid 1576] AH00094: Command line: '/usr/sbin/apache2'

```

---

### Post by CharlesA on 2015-06-29
What are the permissions for those files?

The default DocumentRoot for Apache 2.4 should be /var/www/html, but you can change that if needed.

---

