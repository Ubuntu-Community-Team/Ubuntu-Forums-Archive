---
title: "Enabling PHP error reporting in Apache"
date: 2008-10-28
forum: Server Platforms
---

### Post by xpasi on 2008-10-28
Hi,

For some reason I can't seem to enable the apache PHP error reporting on my dev box in Ubuntu Hardy.

I'd like the PHP error to print inline to the HTML so I can better trace where things go wrong... currently no error messages are being displayed, and it gets a bit frustrating trying to find whats wrong ...

I've tried to set all the php.ini settings to enabled as well as things in apache configuration, but nothing seems to make any difference!

and yes, I've restarted apache (and sometimes even the whole machine) after changes :confused:

---

### Post by conjur3r on 2008-10-28
Create a blank php page with the following:

<?php
phpinfo();
?>

This will tell you what php configuration you currently have.  You can use this to confirm that you are actually editing the correct php.ini file, and/or that your changes are being reflected upon apache restarts.

If everything appears to be ok, how about adding the following to the top of your PHP file to see if it prints error messages?

error_reporting(E_ALL)

You are most likely using a php.ini file which has been hardened for production use.

---

### Post by Miro1701 on 2010-06-22
I had two variables bad configured in initial configuration.

He are new values:
error_reporting = E_ALL & ~E_NOTICE
display_errors = On 

I know this topic is old, but i wrote it for people who have same problem :)

---

### Post by Wrbhhh on 2010-06-27
> **Miro1701 said:**
> I had two variables bad configured in initial configuration.

He are new values:
error_reporting = E_ALL & ~E_NOTICE
display_errors = On 

I know this topic is old, but i wrote it for people who have same problem :)

Thanks. It helped. ;)

---

### Post by sebmaynard on 2010-08-18
Yay! I'd been battling with this too, trying to set "error_reporting" to various things, without realising that "display_errors" was off - so thanks for clearing that up :)

---

### Post by Jibize on 2010-09-26
Thanks Miro1701!

---

### Post by arrgghh on 2010-10-22
> **sebmaynard said:**
> Yay! I'd been battling with this too, trying to set "error_reporting" to various things, without realising that "display_errors" was off - so thanks for clearing that up :)

^ this

---

### Post by gesti on 2011-10-05
Time to renew this thread again :P
if you're using Xdebug and you've done all the configurations for it and you still don't get the fancy errors, then check this in your php.ini:
```
html_errors = On
```It's a stupid mistake to be expecting the fancy errors with out this but I was still sitting on this for about a month till I noticed this mistake ](*,)
So I hope I'll save some time someone with this :)

---

### Post by DJWK on 2013-02-19
Waking up this thread again...

Just if someone is looking for a thread like this and still doesn't get the errors working. There's at least two php.ini's in Ubuntus 12.04 LAMP install. The one I was editing for a while was '/etc/php5/cli/php.ini', when the one PHP was using was '/etc/php5/apache2/php.ini'. So make sure to check which of the files is loaded with phpinfo() function before wasting a couple of hours editing the wrong file...

---

### Post by Wrbhhh on 2013-02-19
> **DJWK said:**
> Just if someone is looking for a thread like this and still doesn't get the errors working. There's at least two php.ini's in Ubuntus 12.04 LAMP install. The one I was editing for a while was '/etc/php5/cli/php.ini', when the one PHP was using was '/etc/php5/apache2/php.ini'. So make sure to check which of the files is loaded with phpinfo() function before wasting a couple of hours editing the wrong file...

Well, yeah. Lol. :D

The one in the cli/ directory is used when you execute a script in the CLI (command-line interface, i.e. the shell), and the one in the apache2/ directory is used when you execute it with Apache, the web server. Try executing the same script with the browser and from the CLI (php MyScript.php) and you'll see it's using different php.inis. ;)

---

### Post by bluepicaso on 2013-05-20
> **DJWK said:**
> Waking up this thread again...

Just if someone is looking for a thread like this and still doesn't get the errors working. There's at least two php.ini's in Ubuntus 12.04 LAMP install. The one I was editing for a while was '/etc/php5/cli/php.ini', when the one PHP was using was '/etc/php5/apache2/php.ini'. So make sure to check which of the files is loaded with phpinfo() function before wasting a couple of hours editing the wrong file...

still nothing works

---

