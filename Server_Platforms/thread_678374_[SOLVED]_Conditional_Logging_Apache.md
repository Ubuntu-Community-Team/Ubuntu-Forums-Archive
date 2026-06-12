---
title: "[SOLVED] Conditional Logging Apache"
date: 2008-01-25
forum: Server Platforms
---

### Post by il3dsm on 2008-01-25
Basically I'm trying to lower the amount of data that gets recorded in my access.log and error.log. I've googled around and found out about conditional logging, but I can't get it to work. I've pasted this into my httpd.conf file: 

SetEnvIf Request_URI "^/robots\.txt$" dontlog

but my access.log still shows accesses to robots.txt  :confused: What am I doing wrong? (I'm using ubuntu 7.10 with LAMP and mod_security)

---

### Post by MJN on 2008-01-26
You've only done half the task - set an environment variable in response to a matched request.

You now need to tell the logging function to not include these requests based on that variable:

```
CustomLog /var/log/apache2/access.log combined env=!dontlog
```(substitute your log path and type to suit)

Does this help?

As an aside, for what reason are you trying to cut the logging down?

Mathew

P.S. Don't use httpd.conf - put the config in /etc/apache2/apache2.conf or /etc/apache2/sites-available/default

---

### Post by il3dsm on 2008-01-26
Thanks for the reply but it didn't work out. :(

I've pasted 

SetEnvIf Request_URI "^/robots\.txt$" dontlog
CustomLog /var/log/apache2/access.log combined env=!dontlog

into the apache2.conf file, restarted the server but it still logged 
192.168.2.101 - - [26/Jan/2008:11:28:58 -0500] "GET /robots.txt HTTP/1.1" 200 75 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.11) Gecko/20071127 Firefox/2.0.0.11 

The reason why I want to cut logging down is because my logs become massive very quickly, I have pictures on my site, each picture generates one log so 20 little pictures generate 20 useless log messages which I'm going to ignore when I'm viewing the log.

---

### Post by MJN on 2008-01-26
Do you have any CustomLog directives elsewhere in your config (look in /etc/apache2/sites-available/ in particular)? The reason I ask is because the last directive read takes precedence.

It ought to work - I've just put it into mine and confirmed the correct operation.

Try putting the statements in /etc/apache2/sites-available/default between the  <VirtualHost> ... </VirtualHost> directives.

Post your config if you're not sure.

With regards to cutting the logs down to aid human readability you really ought to consider some other mechanism of reading your logs as, depending on what you want to extract from them, reading them manually is usually a poor substitute for something like AWStats and other log-analysers.

Mathew

---

### Post by il3dsm on 2008-01-26
I put it into /sites-available/default and it worked :) Thanks a lot, oh and thanks for the log analyzer suggestion.

---

### Post by MJN on 2008-01-27
No problem - well done!

(Edit your original post subject to read [SOLVED] ....)

Mathew

---

