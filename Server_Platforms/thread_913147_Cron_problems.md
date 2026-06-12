---
title: "Cron problems"
date: 2008-09-07
forum: Server Platforms
---

### Post by RoscaDaniel on 2008-09-07
Hello everybody,

I am using for the first time ubuntu server, the latest version and I like it a lot, but I have a little problem which cause a lot of problems on my website.
I am using crontab to run some php script at different hours. I have this command:

```
0 1 * * * /usr/bin/php /home/cracing/public_html/cursa/cursa1-incepere.php

```

As I know, I access crontab like this:

```
sudo -u (username)cracing crontab -e
```

I added the line and I saved, I checked, I have that file in that folder, but it is not running. What should I do to solve the problem?

Sorry for my bad English.

Thank you,
Rosca Daniel

---

### Post by cdtech on 2008-09-07
Be sure your &#8220;cursa1-incepere.php&#8221; has the necessary permissions to be executable (&#8221;chmod 755 cursa1-incepere.php&#8221;).

---

### Post by akudewan on 2008-09-07
> **RoscaDaniel said:**
> 
I am using crontab to run some php script at different hours.


Do you wish to run this at 1am or every one hour ?

---

### Post by RoscaDaniel on 2008-09-07
I have, but still it is not working. Yes, every day at 1 am I want to run.

---

### Post by cdtech on 2008-09-07
Are you sure your PHP is working?
Save this script as "info.php"
```
<html>
<head>
<title> PHP Test Script </title>
</head>
<body>
<?php
phpinfo( );
?>
</body>
</html> 
```
and point your browser to the script to see if PHP is even running.

---

### Post by RoscaDaniel on 2008-09-07
PHP is working. It is a browser game, all the scripts are working, without crontab, so I can not execute some functions for the game.

Should I do more on the server for crontab configuration ?

Let me explain more about the game. I have like this in cron tab:

```
0 1 * * * /usr/bin/php /home/cracing/public_html/curse/cursa1-incepere.php
0 2 * * * /usr/bin/php /home/cracing/public_html/curse/cursa1-terminare.php
```

First line, start the race and second one has to finish it, but no one is executed by the cron, if I execute them manually they are working.

---

### Post by akudewan on 2008-09-07
Does the file /var/log/cron.log have any relevant info ?

---

### Post by RoscaDaniel on 2008-09-07
That file does not exist on the server. I search it now and it does not appear.

Later Edit: I solved the problem, it was about user permissions for using cron.

---

