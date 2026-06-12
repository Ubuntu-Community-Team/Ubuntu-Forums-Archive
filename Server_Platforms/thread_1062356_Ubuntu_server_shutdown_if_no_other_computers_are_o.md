---
title: "Ubuntu server shutdown if no other computers are on"
date: 2009-02-06
forum: Server Platforms
---

### Post by Serangan on 2009-02-06
Hi,

I'm in need of help as I want to make my Ubuntu server go into standby or hibernate if there are no other computers turned on within the network.

All the computers are able to wol the server. But since there not on all the time, I see no point as to having the server running.

So, is this possible to do? Some I was talking to suggested to have a script to ping all the computers within the network. But since I'm relatively new to Linux, I have no idea how to do this.

I know that this will require a cron job, and I'm able to set that up easily. It's just the script that i need help with.

Thanks in advanced.

---

### Post by Thirtysixway on 2009-02-08
I'm wondering if you could use nmap.  The output is similar to this

```

josh@roxas:~$ nmap 192.168.1.* -sP

Starting Nmap 4.62 ( http://nmap.org ) at 2009-02-08 11:44 EST
Host 192.168.1.1 appears to be up.
Host 192.168.1.10 appears to be up.
Host 192.168.1.11 appears to be up.
Host 192.168.1.100 appears to be up.
Host 192.168.1.103 appears to be up.
Nmap done: 256 IP addresses (5 hosts up) scanned in 0.955 seconds

```

If you could write a script to use nmap, get the last line of the response, parse out the number of hosts up, then something like if hosts == 1 then standby


Here it is in php.  You need the php package and nmap package
sudo apt-get install php
sudo apt-get install nmap

[php]
<?php
// Call the nmap command
$output = shell_exec('nmap -sP 192.168.1.*');

// Split up the output so we get the number of hosts up
$split1 = explode("addresses (", $output);
$split2 = explode(" hosts up", $split1[1]);
$hostsup = $split2[0];

// If only x number of computer are on + router, shutdown.  Take in account the server being a computer!
if($hostsup == "2") {
	$shutdown = shell_exec('shutdown -h now');
}
?>
[/php]

I'm not sure how to get this to run as root, maybe if cron is running as root this will execute correctly?
[list]Change the 192.168.1.* to fit your lan ip address correctly.  that's the setup mine [*]takes, yours may be different.
[*]Be sure to change the shutdown command I put in, I'm not sure how to make it go on standby.
[*]Also change the $hostsup == "2" part to fit your setup. Right now it's saying "if one computer is up (1 being the server and 1 being the router) then shutdown"
[/list]
The command for your cronjob would be
```

php -f /home/user/myfile.php
```

Change location/name of file accordingly.

---

### Post by HermanAB on 2009-02-08
I sure would not do that.  Even if you get WOL to work properly it will likely still be a PITA.  There is likely a good reason nobody uses WOL.

You can save a lot of power by simply setting the disk drives to power down after 5 minutes, using hdparm and a line in /etc/rc.d/rc.local.  Read 'man hdparm', it is easy to do.

Cheers,

Herman

---

### Post by Thirtysixway on 2009-02-08
> **HermanAB said:**
> I sure would not do that.  Even if you get WOL to work properly it will likely still be a PITA.  There is likely a good reason nobody uses WOL.

You can save a lot of power by simply setting the disk drives to power down after 5 minutes, using hdparm and a line in /etc/rc.d/rc.local.  Read 'man hdparm', it is easy to do.

Cheers,

Herman

So what would that reason be?

The issue here isn't getting wol working, it's shutting down the server when nobody is around.  OP said all computers/server are able to wol
> All the computers are able to wol the server. But since there not on all the time, I see no point as to having the server running.

---

### Post by Serangan on 2009-02-08
> **Thirtysixway said:**
> I'm wondering if you could use nmap.  The output is similar to this

```

josh@roxas:~$ nmap 192.168.1.* -sP

Starting Nmap 4.62 ( http://nmap.org ) at 2009-02-08 11:44 EST
Host 192.168.1.1 appears to be up.
Host 192.168.1.10 appears to be up.
Host 192.168.1.11 appears to be up.
Host 192.168.1.100 appears to be up.
Host 192.168.1.103 appears to be up.
Nmap done: 256 IP addresses (5 hosts up) scanned in 0.955 seconds

```

If you could write a script to use nmap, get the last line of the response, parse out the number of hosts up, then something like if hosts == 1 then standby


Here it is in php.  You need the php package and nmap package
sudo apt-get install php
sudo apt-get install nmap

[php]
<?php
// Call the nmap command
$output = shell_exec('nmap -sP 192.168.1.*');

// Split up the output so we get the number of hosts up
$split1 = explode("addresses (", $output);
$split2 = explode(" hosts up", $split1[1]);
$hostsup = $split2[0];

// If only x number of computer are on, shutdown.  Take in account the server being a computer!
if($hostsup == "1") {
	$shutdown = shell_exec('shutdown -h now');
}
?>
[/php]

I'm not sure how to get this to run as root, maybe if cron is running as root this will execute correctly?
[list]Change the 192.168.1.* to fit your lan ip address correctly.  that's the setup mine [*]takes, yours may be different.
[*]Be sure to change the shutdown command I put in, I'm not sure how to make it go on standby.
[*]Also change the $hostsup == "1" part to fit your setup. Right now it's saying "if one computer is up (1 being the server) then shutdown"
[/list]
The command for your cronjob would be
```

php -f /home/user/myfile.php
```

Change location/name of file accordingly.

Using this, will it ping the server? Thus not turning the server off? Or am I following it wrong? Also, (sorry only just remembered) my routers on 192.168.1.254, is there anyway to exclude that? If not, I'm happy enough to turn it off nightly.

Thanks for the replies. Turning the hard disks off will also help when the computers are on but not accessing the server.

Edit: If i change the 1 in ```
if($hostsup == "1")
``` to a 2, will that then say, if only the router and server are on, shutdown?

---

### Post by Thirtysixway on 2009-02-08
It's meant to be run from cron on the server.

oh yeah, the script will pick up the router.  If it has an IP on your lan, it will be picked up.

If you change that to a 2, it will say "if the server and the router are the only ones on, turn off the server".

in your setup, change
```
if($hostsup == "1") {
```
to
```
if($hostsup == "2") {
```
It should have been 2 in my post earlier but I forgot about the router being picked up :)

and also remember to change that shutdown command. I'm not sure how to put it in hibernate or standby.

---

### Post by Serangan on 2009-02-08
thanks for the help.

But...


I'm using webmin to control the server and, when I run the command i get ```
sh: php: not found
```

PHP5 is installed, or is sudo apt-get install php different?

ps if i run sudo apt-get install php it says package not found...

Hmm.. i got it working had to install the php5 cli pack... but when i run it, it says no output generated... is that normal?

No wait. it defiently works... lol. thanks for the help guys!

---

### Post by Thirtysixway on 2009-02-09
Glad it worked out :)

---

### Post by Serangan on 2009-02-11
hmmm... i was wondering, my wol works. but it would be nice to be able to wol it from sleep. not a cold start, my server machine takes about 2 mins to start (has to check all the memory). I have the wonderful 3c59x nic... might not be the right place to post this...

edit: starting a new thread on this one

---

### Post by Thirtysixway on 2009-02-12
[http://packages.ubuntu.com/hardy/net/etherwake](http://packages.ubuntu.com/hardy/net/etherwake)

In the description it says it works in sleep mode. Hm.

does this thread help at all?
[http://ubuntuforums.org/showthread.php?t=501439](http://ubuntuforums.org/showthread.php?t=501439)

---

### Post by Serangan on 2009-02-13
Nope. didnt work. etherwake is for ubutnu clients wanting to wake up the server i think. But i've done what that thread said, and tried waking it from sleep (put to sleep using sudo /etc/acpi/sleep.sh) but it still didnt work. Also, it seems to of crashed my network driver now...

I still have a screen on my server for the moment. So im lucky about that. but yeah.

Just for the record. im running ubuntu 8.10-desktop edition. yes i know, im going to install server edition. I downloaded it last night, but when i went to install it, the disk is corrupt. It cant find the files on the disk, might of corrupted the disk :|

Cause im not a business, im going to have 8.10 server edition, that shouldnt make a difference... i hope.

---

### Post by mika35 on 2011-09-13
How did you get cron to run it ?? Mine isn't working at all with
 */1 * * * * php -f /home/serveur/Bureau/Autowol.php

---

### Post by Thirtysixway on 2011-09-13
> **mika35 said:**
> How did you get cron to run it ?? Mine isn't working at all with
 */1 * * * * php -f /home/serveur/Bureau/Autowol.php


Try taking out the /1, so it's just 
```

* * * * * php -f /home/serveur/Bureau/Autowol.php

```

---

### Post by mika35 on 2011-09-14
Do not work..  but the script work find if i click execut with gnome-schedule..
thanks for the help

---

### Post by mika35 on 2011-09-14
I found de problem i had to tell where is shutdown in the scrip, like this for me $shutdown = shell_exec('/sbin/shutdown -h now');

---

