---
title: "Edgy Server 6.10, LAMP installation, PHP files download instead of display"
date: 2007-03-16
forum: Server Platforms
---

### Post by dudinatrix on 2007-03-16
Apache is running, I can view /var/www/ from my browser, but when I try to make a phpinfo.php and load it up, Firefox prompts me to download the file. I tried uncommenting the php handlers in /etc/apache2, but that didn't do anything. I also tried putting a handler in /var/www/.htaccess, but that didn't work either.

There are no errors in /var/log/apache2/error.log

Any ideas?

---

### Post by betchern0t on 2007-03-18
Hi,
    if you do an echo "Content-Type: text/html; charset=utf-8"; before you output the html this problem will most of the time go away. Essentially your browser doesn't know what the stuff coming at it is. By default the web server version of php is supposed to spit this out. I think it is actually a symptom of something more dire. Still struggling with the problem, but looks like on my setup for some reason apache is running the cli version of php. Symptoms include phpinfo being returned as text rather than html.

Cheers Paul

---

### Post by betchern0t on 2007-03-19
I figured out my problems in the end - so stupid I could kick myself. By default apache2 with php on ubuntu expects php scripts to be run from the document root ie where you put the html files. I had assumed that they ran from cgi-bin. the other thing I had done which clouded the issue was to add the location of php cli at the top of the file (#!/usr/bin/php) which meant that the server was running it as a os level script with interesting results.

Cheers Paul

---

### Post by betchern0t on 2007-03-19
BTW if you force a reload of apache2 then it lists the modules it loads in the errorlog in the restart line. HTH

Cheers Paul

---

### Post by wray.justin on 2007-03-19
> **dudinatrix said:**
> I can view /var/www/ from my browser

Are you opening /var/www within the browser, or are you using [http://localhost/]("http://localhost/")

---

