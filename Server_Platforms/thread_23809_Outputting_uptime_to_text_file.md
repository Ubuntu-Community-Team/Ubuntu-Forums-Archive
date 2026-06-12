---
title: "Outputting uptime to text file"
date: 2005-04-04
forum: Server Platforms
---

### Post by Trickyphillips on 2005-04-04
I'm interested in displaying my uptime on a website, and was wondering how I could output my uptime to a text file which would be in my /var/www directory. I'm pretty new to Linux, so try to keep things simple.  8) 

Thanks!

---

### Post by jameswilhelm on 2005-04-04
I do this on my webserver at home and it works fine. Instead of writing uptime to a text file, I use Server Side Includes. In the body of the webpage, added the following:

<!--#exec cmd="uptime"-->

This displays the uptime at the time the webpage was requested. I've also added commands like "uname -a", "httpd -v", etc.  You can also format the displayed text.

You should set up your server to allow server side includes. See:

[http://httpd.apache.org/docs-2.0/howto/ssi.html](http://httpd.apache.org/docs-2.0/howto/ssi.html)

I use the XBitHack method.

I suppose you could run the command from cron and output the command to a text file:

* * * * * uptime > /var/www/html/my_uptime.txt

This will update 'my_uptime.txt' every minute.

A more flexible way would be to do this from a script, but I haven't tried that yet.

Any comments on security issues around this are welcome.

---

### Post by Trickyphillips on 2005-04-04
Thanks! I have "uptime > /var/www/my_uptime.txt" run once every minute now. Is there any way to truncate it, so it displays *only* the uptime? Right now, it shows "[current time] [uptime], [number of users logged in], [load average]". I want it to show uptime only, if possible. 

Thanks! :-D

---

### Post by jameswilhelm on 2005-04-04
I should thank you - have been threatening to do this for a while now, but have been too lazy. Below is a Perl script that works on my server. Put it in the cgi-bin directory and set permissions to 755.

http://<server>/cgi-bin/uptimescript.pl

..should work. You should have Perl installed and presumably your webserver is running.

Be warned (or afraid)!!! This works but....
I'm not a programmer of any description - my Perl stinks. A real Perl programmer can probably do all of this in four lines and will want to know why I did not use the nice Perl HTML modules to do this. There is definitely room for improvement, but this is what I'll be using at home.


#!/usr/bin/perl
#
#


# Run uptime command and pipe output to this script.
open UPTIME, "uptime |";
$data = <UPTIME>;
close UPTIME;

# Split output and extract wanted bits.
@parts = split /\ /, $data;
($hours,$minutes) = split /\:/, $parts[5];

# Get rid of comma at end of minutes.
$minutes = substr($minutes, 0, 2);

# Assemble webpage.

$page = "<html><head><title>UPTIME</title></head>";
$page .= "<body>";
$page .= "<h1><b>";
$page .= "Server up: ";
$page .= $parts[3]." days ".$hours." hours ".$minutes." minutes";
$page .= "</b></h1>";
$page .= "</body>";
$page .= "</html>";

print "Content-type: text/html \n\n";
print $page;

exit(1);

---

### Post by CrustyDOD on 2005-04-04
No need for SSI or cron

[PHP]
$uptime = @exec('uptime'); //executes uptime command
$show_uptime = explode(" ", $uptime); //splits output by space
$show_uptime = str_replace(",", "", $show_uptime); //removes ugly comma
echo $show_uptime[4]; //displays uptime on page
//print_r($show_uptime); <---- this will output full array if you want to use other info
[/PHP]

---

### Post by jameswilhelm on 2005-04-04
See, four lines! Not Perl, though :-)

Nice.

Thanks.

---

### Post by Rottweiler on 2005-04-04
You guys sure are making this hard :-)

Take a looksee at 'man cut'

---

### Post by HungSquirrel on 2005-04-05
> **CrustyDOD]No need for SSI or cron

[PHP]
$uptime = @exec('uptime') said:**
> ; //displays uptime on page
//print_r($show_uptime); <---- this will output full array if you want to use other info
[/PHP]
 Thanks for that, crusty.  I was far too lazy to look up how to execute console commands in PHP.  Now that I know, I'll be having all kinds of fun!

uname -a comes to mind:

[php]<?php

        echo @exec('uname -a') . '<br />';      // prints kernel version

?>[/php]

---

### Post by Trickyphillips on 2005-04-05
> **HungSquirrel]Thanks for that, crusty.  I was far too lazy to look up how to execute console commands in PHP.  Now that I know, I'll be having all kinds of fun!

uname -a comes to mind:

[php]<?php

        echo @exec('uname -a') . '<br />' said:**
> 
 Thanks for helping, everyone. I've got things working well now. :)

---

### Post by HungSquirrel on 2005-04-05
The php @exec function doesn't seem to work with all console commands, for example echo, grep, and cat.  :(

Edit: but @passthru does!

---

### Post by CrustyDOD on 2005-04-06
Why do you need those commands to be executed?
Echo? Doesn't this just displays a text in console? like: echo show this text, or does it have some special function? I'm new to linux so..

Anyway, here's the link to all exec functions that you can use: [http://si.php.net/exec](http://si.php.net/exec) 

Btw, for me all these commands are working using exec or shell_exec..

---

### Post by HungSquirrel on 2005-04-06
> Why do you need those commands to be executed?
Echo? Doesn't this just displays a text in console? like: echo show this text, or does it have some special function? I'm new to linux so..
I was trying to use it to print environment variables.  I don't need it on a page, I was just messing around because that's what I do.  :)

For grep, I was using it to display for users the DirectoryIndex values in my apache2.conf file.  Grep works in exec if you put it in a variable, but not if you just echo it.  I'm not sure why.

[php]<?php

$dirindex = @exec('grep -i directoryindex /etc/apache2/apache2.conf');

$show_dirindex = explode(' ', $dirindex);

for ($i = 1; $i < count($show_dirindex); $i++) {
     echo $show_dirindex[$i] . " ";
}

?>[/php]

Yields:
```
index.html index.cgi index.pl index.php index.xhtml
```

---

