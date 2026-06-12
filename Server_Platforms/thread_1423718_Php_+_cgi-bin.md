---
title: "Php + cgi-bin"
date: 2010-03-07
forum: Server Platforms
---

### Post by deltatux on 2010-03-07
Hey guys,

I got a little problem, I have this assignment which requires me to execute a PHP script as if it's a CGI script. This goes against everything I know about PHP scripts since I've never heard of this and I have been playing with PHP since I started maintaining my own website in 2004. Normally, from what I understood, you place Perl scripts in CGI-BIN, but not PHP. Unfortunately, I can't argue w/ my prof for obvious reasons.

So right now I'm trying to get this PHP script to work inside the CGI-BIN as if it's a CGI script.

Here's the script:
```

#!/usr/bin/php

<html><body>
<?php
 $link = mysql_connect("localhost", "user_name", "password") or die;
 print "Everything works OK!";
 mysql_close($link);
?>
</body></html>

```

Here's my httpd.conf:
> 
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/

<Directory /usr/lib/cgi-bin>
Options +ExecCGI
AddHandler cgi-script .cgi .pl .php


I got a perl test script running and it printing Hello World but I can't get the PHP variant to work.

Please help. I installed the default LAMP stack that came with Ubuntu Server.

Thanks,
deltatux

---

