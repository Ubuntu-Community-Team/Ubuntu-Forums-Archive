---
title: "Cron wont execute command"
date: 2010-09-05
forum: Server Platforms
---

### Post by Serangan on 2010-09-05
Hi,

Ive got a strange issue.

Ive just upgraded to Ubuntu 10.04 and until then, cron jobs were working perfectly.

Now when I add the job it wont do anything. If I run it from terminal it runs perfectly.

this is what sudo crontab -l looks like
```
# m h  dom mon dow   command
* * * * * php -f /home/start/hostsup.php

```

hostsup.php is a script that calls nmap, checks if any other computers are running, it then calls autoshutdown (located in the same directory) that checks if CPU and network are below a certain threshold. If it satisfies the requirements, the server turns off.

Like i said, if i run ```
sudo php -f home/start/hostsup.php
``` it works with out a problem.

Is anyone able to help me with my problem?

Much appreciated if anyone can help me.

---

### Post by Ryan Dwyer on 2010-09-05
The cron job is running as your normal user account which likely doesn't have permission to do that stuff. Add it manually to /etc/crontab, specifying root as the user to run as.

---

### Post by Serangan on 2010-09-05
That hasn't fix my problem. Thanks anyway.

I added the following
```

* *     * * *   root    php -f /home/start/hostsup.php

```

But if I changed the command to
```

* *     * * *   root    /home/start/autoshutdown

```

So im guessing its something to do with the php file.
[PHP]
<?php

$myFile = "executed.txt";
$fh = fopen($myFile, 'w') or die("can't open file");
$stringData = "Hello World\n";
fwrite($fh, $stringData);
fclose($fh);

// Call the nmap command
$output = shell_exec('nmap -sP 192.168.1.1-20');

// Split up the output so we get the number of hosts up
$split1 = explode("addresses (", $output);
$split2 = explode(" hosts up", $split1[1]);
$hostsup = $split2[0];

// If only x number of computer are on + router, shutdown.  Take in account the$
if($hostsup == "2") {
    $shutdown = shell_exec('/home/start/autoshutdown');
}
?>
[/PHP]
The above was written by Thirtysixway for me (many thanks) has been working perfectly before upgrading.

The php file is owned by root, and has permissions 755.

Ive got the write to file bit there just so i know if its being run or not while im trying to work out whats wrong.

---

### Post by Ryan Dwyer on 2010-09-05
When root executes your file the current working directly is /root/. Look there for executed.txt.

It might also be worth checking /var/log/syslog for clues.

---

### Post by BkkBonanza on 2010-09-05
Since this worked before the upgrade I would suspect that perhaps PHP was upgraded as well. Sometimes there are behavioural differences in PHP between upgrades. You might check the versions and see if changed, reverting PHP may help verify. If this is it then you could look at the PHP release notes to see what functions may have changed and alter the code to suit.

---

### Post by LightningCrash on 2010-09-05
crontab has a limited path... use full paths to every command, even nmap and php.

that's probably why yours works under a root shell

---

### Post by Serangan on 2010-09-06
> **Ryan Dwyer said:**
> When root executes your file the current working directly is /root/. Look there for executed.txt.

It might also be worth checking /var/log/syslog for clues.

I got it! I redid the permissions of it. And it just started working.
Also I looked in /root/ and there is executed.txt
I was excepting it to make the file in the same directory as hostsup.php

Would having full paths to every command be beneficial now?

Thanks for the help.

---

