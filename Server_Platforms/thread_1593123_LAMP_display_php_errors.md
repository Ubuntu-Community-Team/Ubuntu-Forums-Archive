---
title: "LAMP display php errors"
date: 2010-10-11
forum: Server Platforms
---

### Post by i-sultan on 2010-10-11
I've installed developer's LAMP server and made changes on php.ini 
[B]
display_errors On[/B]
**display_startup_errors On**

but it doesn't display any errors or even a little warning, what's the problem, what's wrong?

---

### Post by Ryan Dwyer on 2010-10-11
Did you restart Apache after making the change? Are you editing the correct php.ini? (/etc/php5/apache2/php.ini, not /etc/php5/cli/php.ini)

What does phpinfo() tell you about error reporting and displaying errors?

---

### Post by tech7 on 2011-08-08
Has anybody ever came up with a solution to this problem??  I've got the same issue and can't find anything on google that works anywhere..

---

### Post by Wim Sturkenboom on 2011-08-09
Never looked at it; just as easy to tail the apache error log ;)

---

### Post by tech7 on 2011-09-19
yeah, i'm getting really tired of doing that..  i would love to be able to just see the error when the page loads and address it instead of going back to my terminal and typing in a command to see the error.  I'm a terrible coder and the extra step doesn't help me get any better when it's already way past my bedtime.

---

### Post by Porcini M. on 2011-09-19
I use log_errors:

log_errors = On

...then errors show up in /var/log/apache2/errors.log (or thereabouts - recited from memory)

---

### Post by Wim Sturkenboom on 2011-09-19
> **tech7 said:**
> yeah, i'm getting really tired of doing that..  i would love to be able to just see the error when the page loads and address it instead of going back to my terminal and typing in a command to see the error.  I'm a terrible coder and the extra step doesn't help me get any better when it's already way past my bedtime.I usually have 3 terminals open while writing webpages; one for vi in my 'include' directory, one for vi of the actual page that I'm working on and one for tail. For the latter, why the heck do you have to repeat the command? *_tail -f_* permanently shows the latest additions to the log file. And there is also something like history in bash to prevent you from typing too much.

The problem with showing errors on the webpage is that it reveals stuff that it should not reveal (security). In the worst case a line that shows the visitor e.g. the mysql root password during the setup of a connection to a mysql server. If you have a separate development server, the risk might be acceptable; if this is a production server (hosting your website, either hosted or at home), it's a 'no go' from a security perspective.

---

### Post by SeijiSensei on 2011-09-20
[http://www.php.net/manual/en/errorfunc.configuration.php#ini.error-reporting](http://www.php.net/manual/en/errorfunc.configuration.php#ini.error-reporting)
[http://www.php.net/manual/en/security.errors.php](http://www.php.net/manual/en/security.errors.php)

---

### Post by tech7 on 2011-09-22
Yeah, I understand the risks of displaying the error in the browser.  But, I only wish to do this on my laptop lamp server to aid me while I get my script right.  Afterwards, once I get things working right, I upload the files to my remote server and plug them in from there.

---

### Post by tech7 on 2011-09-22
in terminal:
```
sudo gedit /etc/php5/apache2/php.ini
```

Scroll down to about line 531 under the "Error handling and logging" title where you will find
```
display_errors = Off
``` 

Change this to say ```
display_errors = On
```

Once you've done this and saved the file, in terminal run:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by sdpagent on 2012-06-07
I thought i had the same problem because i thought I had implemented the changes by uncommenting by removing the ';' this is not the case.
Those are just the instructions showing you the different values you can put in.

do a search for the options like error_reporting, and dont uncomment the lines starting with ';' you need to find the next occurance and change the value where it has a '=' sign.

It now works for me no problem (ubuntu server 12 (32 bit) (running inside virtualbox virtual machine of 32bit os for development)

Stu

---

