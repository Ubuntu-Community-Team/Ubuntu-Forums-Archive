---
title: "PHP suddenly VERY slow"
date: 2011-01-28
forum: Server Platforms
---

### Post by JLahm on 2011-01-28
All of my PHP web pages are now loading incredibly slow. I created a simple "Hello World!" script and timed retrieving it from a terminal using wget and it took 3min 9seconds. A wget of the home page of a PHP-based site also took 3min 9seconds. I have a PHP script that I run from the command line that I use to look for malicious FTP attempts and it took - you guessed it - 3min 9seconds. I am running Ubuntu 8.04 LTS and have applied all of the latest updates for that version.

One thing I did notice was a proliferation of apache2 processes. With every request for a page I seem to get 7 or so new apache2 processes.

Any help would be greatly appreciated! Thanks all.

Jim

---

### Post by JLahm on 2011-01-28
A few additional notes:
[LIST]
[*]regular HTML pages load just fine
[*]Ruby pages work fine
[*]Perl pages work fine
[*]I don't see any error messages in the logs
[/LIST]

I have found reference to a TCP socket timeout of 189 seconds (sum of tries for 3 seconds, 6 seconds, 12, 24, 48 and 96 seconds) but am not sure it is related.

Jim

---

### Post by dtfinch on 2011-01-28
Sounds like it's trying to connect to some other server on every request, waiting until the connection attempt times out 189 seconds later.

---

### Post by JLahm on 2011-01-28
dtfinch: That was my thought too. But, I didn't think it explained why creating a file that just contained 'echo "Hello World";' and running it from the command-line (not through a browser) would still take 189 seconds? In other words, I entered: php test.php

Jim

---

### Post by dtfinch on 2011-01-28
Does "netstat -np --inet" show it trying to connect to anything when you run "php test.php"?

---

