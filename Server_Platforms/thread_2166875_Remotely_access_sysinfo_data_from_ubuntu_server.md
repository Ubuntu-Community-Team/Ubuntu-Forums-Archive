---
title: "Remotely access sysinfo data from ubuntu server?"
date: 2013-08-11
forum: Server Platforms
---

### Post by burgergetsbored on 2013-08-11
this maybe a stupid question and might not be possible but I'm wondering is it possible to get the information from landscape-sysinfo so I can physically manipulate it? I want to be able to visualize it myself on a webpage but have no idea how to actually get it off the server as data. Cheers for any advice! 


    ```

    System load:  0.0                Processes:           XXX
    Usage of /:   2.5% of 452.69GB   Users logged in:     0
    Memory usage: 10%                IP address for lo:   XXX.XXX.XXX.XXX
    Swap usage:   0%                 IP address for eth0: XXX.XXX.XXX.XXX
    Temperature:  40 C
```

---

### Post by Habitual on 2013-08-12
Without knowing your skill level, here's something I put together for "remote load average" on a remote host.
It could be modified to run landscape-sysinfo as the shell_exec   parameter.

It should give you an idea, or get you started towards a solution...
[PHP]<?php
$FTEXT = "load average: ";
$output = shell_exec("ssh -qi /home/jj/.ssh/somekey_rsa user@123.456.789.123 w | awk -F "$FTEXT" '{ print $2 }'");
echo "db2's load averages are $output" ;
?>[/PHP]

so, I'd use that for your situation like...
```
<?php
$output = shell_exec(/path/to/landscape-sysinfo ); **[COLOR=#ff0000]#/path/on/the/remote/host/to/landscape-sysinfo[/COLOR]**
echo "$output" ;
?>
```

save it as say, sysinfo.php in the /var/www/html or similar on the host you want this information **from.** 
chmod it safely for web use as 
```
chmod 644 /var/www/html/sysinfo.php
```
and you **may** have to chown it to the user that runs the webserver (you didn't specify apache, but topic says Ubuntu) typically www-data or something like that. Systems vary on this.

Execute it using the browser typically as
[http://remote/sysinfo.php](http://remote/sysinfo.php)

Have fun!

---

### Post by burgergetsbored on 2013-08-12
Wow easy as that!? I have an alright skill level in PHP but not really in anything ubuntu server related! Just do a bit here and there for fun at home. I've just had a browse online and can't find out where landscape-sysinfo resides. It's just a basic install of ubuntu server, nothing modified so where would I find it? Thanks!

---

### Post by tgalati4 on 2013-08-12
If you search the web, there are some very detailed system status pages that are programmed in PHP.  Just download the PHP script and put it in your /var/www (or your webpage home directory).  You can rename it to anything you want and just call up the page as needed.

---

### Post by burgergetsbored on 2013-08-13
Oh thanks! Never knew such things existed in PHP. I do want to be able to just get the raw data mind as I want to play around with it myself rather than using pre-created interfaces, I've found a few (namely phpsysinfo) which I'll download and see if I can make any sense of the code so I can use it on my own project! Thanks.

---

### Post by tgalati4 on 2013-08-13
There are simple utilities to get all of the piece parts:

 System load:  0.0                Processes:           XXX
    Usage of /:   2.5% of 452.69GB   Users logged in:     0
    Memory usage: 10%                IP address for lo:   XXX.XXX.XXX.XXX
    Swap usage:   0%                 IP address for eth0: XXX.XXX.XXX.XXX
    Temperature:  40 C

w
who
sensors
free
df -h
ifconfig

Each command has switches to alter the output to just what you want.  The phpsysinfo is one of several system status pages out there.

---

### Post by Habitual on 2013-08-13
> **burgergetsbored said:**
> Wow easy as that!? I have an alright skill level in PHP but not really in anything ubuntu server related! Just do a bit here and there for fun at home. I've just had a browse online and can't find out where landscape-sysinfo resides. It's just a basic install of ubuntu server, nothing modified so where would I find it? Thanks!

[PHP]
<?php 
$output = shell_exec(/usr/bin/landscape-sysinfo );
echo "$output" ; 
?>
[/PHP]

from Ubuntu 12.04 LTS....

---

### Post by burgergetsbored on 2013-08-13
> **tgalati4 said:**
> There are simple utilities to get all of the piece parts:

 System load:  0.0                Processes:           XXX
    Usage of /:   2.5% of 452.69GB   Users logged in:     0
    Memory usage: 10%                IP address for lo:   XXX.XXX.XXX.XXX
    Swap usage:   0%                 IP address for eth0: XXX.XXX.XXX.XXX
    Temperature:  40 C

w
who
sensors
free
df -h
ifconfig

Each command has switches to alter the output to just what you want.  The phpsysinfo is one of several system status pages out there.

I know I can call the commands from the server to get the output on screen, the bit I was completely lost on was how to actually get them so I can manipulate them i.e put them onto a web page or in a sql database.

---

### Post by tgalati4 on 2013-08-13
As *Habitual* has shown, you can use *shell_exec()* to run the commands inside a simple PHP script.  Put that script in /var/www/mysysteminfo.php then call it from a webpage.

---

### Post by burgergetsbored on 2013-08-14
Cheers guys, server is slightly disassembled at the moment but will give it a go as soon as it's back up!

---

