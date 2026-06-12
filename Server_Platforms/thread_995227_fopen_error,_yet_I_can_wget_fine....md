---
title: "fopen error, yet I can wget fine..."
date: 2008-11-27
forum: Server Platforms
---

### Post by tommyrot on 2008-11-27
Hey folks,

I'm pretty new to the Ubuntu server side of things, and have gradually been getting my out-of-the-box 8.04.1 LAMP setup working how I want. However, there's one little thing that I can't seem to fix.

Whenever I attempt to execute the following fopen script... 

[INDENT][INDENT]<?php

$filename = "http://www.yahoo.com.au";
$handle = fopen($filename, "r");
$html = fread($handle, filesize($filename));
fclose($handle);

echo $html;

?>[/INDENT][/INDENT]

... I get the following errors:

[INDENT][INDENT]Warning: fopen([http://www.yahoo.com.au](http://www.yahoo.com.au)) [function.fopen]: failed to open stream: Connection timed out in /var/www/brushtail_3.1/sql/fopen.php on line 5[/INDENT][/INDENT]

I can wget the desired URL without any problems (which would suggest that the network side of things is configured ok?), and I've enabled the **allow_url_fopen = On** value in my php.ini file.

Any thoughts about what I need to check from here?

Thanks in anticipation,

Tom

---

### Post by MJN on 2008-11-27
Hi Tom,

I know absolutely nothing about PHP but until someone that does comes along I can offer some suggestions from what I do know about.

Firstly, do you use a proxy? Or just straight connections? (I'm wondering if wget might be proxy-aware but PHP isn't)

Secondly, have you tried running a packet sniffer (e.g. Wireshark) to see if the HTTP GET request gets sent out? If so, where to? And what, if anything, comes back?

Certainly the 'Connection timed out' error implies a request is being sent but no reply is being received which begs the immediate question of where this request is being sent...

Mathew

---

