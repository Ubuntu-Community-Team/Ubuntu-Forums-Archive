---
title: "PHP include not working -- Cannot include header.php file insite index.php"
date: 2015-04-07
forum: Server Platforms
---

### Post by abhimanyu0003 on 2015-04-07
I've installed Apache2. By pointing my browser to http://localhost, I can open the index.php file.

In the index.php file, I've used a piece of code:

[PHP]<?php include 'header.php'; ?>[/PHP]

And the header.php file is **in the same directory** as the index.php file.

Now, when I open the index.php via going to localhost on my browser, I see all the content but not the contents of the header.php file. That is, it's not being included.

I've also tried:
[LIST]
[*]$[DOCUMENT_ROOT]."/header.php"
[*]./header.php
[*]/home/<username>/site/header.php
[*]../header.php
[/LIST]

Looks like the include is just not working at all.

PURPOSE: I want a header.php and a footer.php to include them on all my webpages. My website is, right now, OFFLINE (so absolute paths are not workable). Apache2 is installed and PHP is working (pointing to http://localhost, I can see my index.php in the browser).

---

### Post by spjackson on 2015-04-07
> **abhimanyu0003 said:**
> 
[PHP]<?php include 'header.php'; ?>[/PHP]

That should work. Does the Apache user (usually www-data) have read access to header.php? Is there a message in /var/log/apache2/error.log?

---

### Post by abhimanyu0003 on 2015-04-07
> **spjackson said:**
> That should work. Does the Apache user (usually www-data) have read access to header.php? Is there a message in /var/log/apache2/error.log?

Yes, the www-data group has full access to all subdirectories and the file (755 permission).

There are a lot of messages in the error log file...

---

### Post by spjackson on 2015-04-07
> **abhimanyu0003 said:**
> 
There are a lot of messages in the error log file...
And any relevant to this problem?
```

grep header.php /var/log/apache2/error.log

```
And if that reveals nothing, browse to your page then post the messages with the appropiate timestamp.

---

### Post by abhimanyu0003 on 2015-04-07
No, there's no mention of header.php in the log file.

> **spjackson said:**
> And if that reveals nothing, browse to your  page then post the messages with the appropiate timestamp.

I don't understand?

---

### Post by spjackson on 2015-04-09
> **abhimanyu0003 said:**
> No, there's no mention of header.php in the log file.

That is strange. Do you know that index.php is even being processed by php? Do you have other php statements in there that you can be sure are being executed? Or is it just plain HTML apart from the include statement?
> **abhimanyu0003 said:**
> 
I don't understand?
What I meant by that is if you browse to your index.php at say 13:00:00 on 9 April 2015, then find the messages in error.log that bear that date and time and post them.

---

### Post by abhimanyu0003 on 2015-04-09
I added a statement in the footer: <?php echo"Hi! This is the footer."?>

But even this isn't shown in the browser. I guess my suspicion is right -- the PHP is just not working at all.

I opened index.php with both, the PHP call to the header and the echo statement at 6:12 PM. The log file was pretty weird. No log with this time found. Here's the content of the log file with the timestamp of 9th April (today):

[Thu Apr 09 06:59:17.819044 2015] [mpm_event:notice] [pid 1002:tid 3074726464] AH00489: Apache/2.4.6 (Ubuntu) configured -- resuming normal operations
[Thu Apr 09 06:59:17.872875 2015] [core:notice] [pid 1002:tid 3074726464] AH00094: Command line: '/usr/sbin/apache2'
[Thu Apr 09 09:13:13.947605 2015] [mpm_event:notice] [pid 1002:tid 3074726464] AH00491: caught SIGTERM, shutting down
[Thu Apr 09 17:48:16.964449 2015] [mpm_event:notice] [pid 1001:tid 3074509376] AH00489: Apache/2.4.6 (Ubuntu) configured -- resuming normal operations
[Thu Apr 09 17:48:17.010387 2015] [core:notice] [pid 1001:tid 3074509376] AH00094: Command line: '/usr/sbin/apache2'

No mention of header.php and no activity at 18:12. The messages are just of the shut-up and shut-down of the Apache server... Now I'm really confused about what's happening...

---

### Post by SeijiSensei on 2015-04-09
> **abhimanyu0003 said:**
> I've installed Apache2.
Did you install PHP as well?  For people new to Ubuntu, the best method to install a fully-functional web server with Apache, PHP, and MySQL is to use the method described in the ["LAMP" server documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP"):
```

sudo apt-get update
sudo apt-get install lamp-server^

```

---

### Post by abhimanyu0003 on 2015-04-09
Actually, trying to install the lamp server was the first thing I did. I couldn't. It said many packages were dependent and the dependencies won't be installed for some reason. I cannot recreate the exact phrase, but it went like this: "xxx package depends on abc, but abc won't be installed." There were like five or six such packages.

So, to take its screenshot, I tried installing the lamp-server^ again, and IDK how, this time it worked... I thought PHP was pre-installed but it was under the NEW packages... So PHP is now installed. Things are working fine now...

THANKS A LOT FOR GIVING MY POINTLESS PROBLEM SO MUCH TIME AND FINALLY HELPING ME OUT! THANK YOU BOTH.

---

