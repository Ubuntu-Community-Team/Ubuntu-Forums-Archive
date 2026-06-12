---
title: "Network is probably not using DHCP Protocol"
date: 2012-08-19
forum: Server Platforms
---

### Post by felinoel on 2012-08-19
So I am setting up a new server with Ubuntu Server 12.04 and I am getting this error, I tried searching but I couldn't find anyone with this error and my version.


EDIT:
Also, I see others getting this error are using wireless connections, mine is wired.

---

### Post by CharlesA on 2012-08-19
That usually means it cannot contact the DHCP server, how do you have it set up?

---

### Post by felinoel on 2012-08-19
> **CharlesA said:**
> That usually means it cannot contact the DHCP server, how do you have it set up?

Hmmm, well I just have a cord connected to a router, nothing fancy.

---

### Post by CharlesA on 2012-08-19
Post the output of this please:

```
sudo dhclient
```

---

### Post by felinoel on 2012-08-19
> **CharlesA said:**
> Post the output of this please:

```
sudo dhclient
```

Oh umm, I got this error in the installation, should I bypass the autoconfig of the network to get to the terminal then?



lol you included sudo, most don't.

---

### Post by CharlesA on 2012-08-19
> **felinoel said:**
> Oh umm, I got this error in the installation, should I bypass the autoconfig of the network to get to the terminal then?



lol you included sudo, most don't.

You should need to use sudo, otherwise you get
```
ubuntu@ubuntu-desktop:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

[B]can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted[/B]
```

```
ubuntu@ubuntu-desktop:~$ sudo !!
sudo dhclient
[sudo] password for ubuntu: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/08:00:27:08:1c:e9
Sending on   LPF/eth0/08:00:27:08:1c:e9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 10.0.2.15 from 10.0.2.2
DHCPREQUEST of 10.0.2.15 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.2.15 from 10.0.2.2
bound to 10.0.2.15 -- renewal in 34799 seconds.

```

Can you post the output please.

---

### Post by felinoel on 2012-08-20
> **CharlesA said:**
> You should need to use sudo, otherwise you get
```
ubuntu@ubuntu-desktop:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

[B]can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted[/B]
```

```
ubuntu@ubuntu-desktop:~$ sudo !!
sudo dhclient
[sudo] password for ubuntu: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/08:00:27:08:1c:e9
Sending on   LPF/eth0/08:00:27:08:1c:e9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 10.0.2.15 from 10.0.2.2
DHCPREQUEST of 10.0.2.15 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.0.2.15 from 10.0.2.2
bound to 10.0.2.15 -- renewal in 34799 seconds.

```

Can you post the output please.Right... well you skipped over my question so I will assume it was a yes.

Anyways when I type in sudo dhclient I get no response, not even it saying that the command doesn't work, just nothing.

---

### Post by CharlesA on 2012-08-20
Check dmesg and see what it says after you run dhclient.

---

### Post by sandyd on 2012-08-20
> **felinoel said:**
> Right... well you skipped over my question so I will assume it was a yes.

Anyways when I type in sudo dhclient I get no response, not even it saying that the command doesn't work, just nothing.
post output of this
```

killall dhclient
sudo tail -f /var/log/syslog

```
in another terminal, type in
```

sudo dhclient
``` and post the ouput of the first terminal

Might be useful to do it in a livecd instead.

---

### Post by felinoel on 2012-08-20
> **CharlesA said:**
> Check dmesg and see what it says after you run dhclient.Ummm, both times a wall of text flew across my screen for dmesg

> **sandyd said:**
> post output of this
```

killall dhclient
sudo tail -f /var/log/syslog

```
in another terminal, type in
```

sudo dhclient
``` and post the ouput of the first terminal

Might be useful to do it in a livecd instead.
```
killall dhclient

dhclient: no process found
```

---

### Post by sandyd on 2012-08-20
> **felinoel said:**
> Ummm, both times a wall of text flew across my screen for dmesg


```
killall dhclient

dhclient: no process found
```
ignore the error - keep on going

---

### Post by felinoel on 2012-08-20
> **sandyd said:**
> ignore the error - keep on going
Just do sudo tail -f /var/log/syslog even though it spouts an error? I see, ok will do when I get back home.

---

### Post by felinoel on 2012-08-20
> **sandyd said:**
> ignore the error - keep on going

```
tail: cannot open `/var/log/syslog/' for reading: Not a directory
```

I have a feeling this is because Charles from the first page sort of told me to bypass setting up the network?

---

### Post by CharlesA on 2012-08-20
> **felinoel said:**
> ```
tail: cannot open `/var/log/syslog/' for reading: Not a directory
```

I have a feeling this is because Charles from the first page sort of told me to bypass setting up the network?
No slash:

```
sudo tail -f /var/log/syslog
```

---

### Post by felinoel on 2012-08-20
> **CharlesA said:**
> No slash:

```
sudo tail -f /var/log/syslog
```Huzzahs are in order, eff do I need to type all this out? Sigh...


EDIT:
Wait... more keeps popping up, do I need to type all this out?
Looks like it is talking about my mouse?

---

### Post by CharlesA on 2012-08-20
It is supposed to refresh. ;)

Just run the dhclient command in different terminal and then copy/paste the log.

---

### Post by felinoel on 2012-08-20
> **CharlesA said:**
> It is supposed to refresh. ;)

Just run the dhclient command in different terminal and then copy/paste the log.

Different terminal... ok I am in the server version of Ubuntu without a GUI installed, how do I run a different terminal?

---

### Post by sandyd on 2012-08-20
Use Control + alt + F2 to switch to a different terminal.

You can use Control + alt + F1 to switch to the original terminal.

---

### Post by felinoel on 2012-08-20
> **sandyd said:**
> Use Control + alt + F2 to switch to a different terminal.

You can use Control + alt + F1 to switch to the original terminal.

Ok, first I tried the killall dhclient command but that said no process again, then I just tried the sudo dhclient command and that said nothing at all again.


EDIT:
Could it be a bad port?
I was able to use Firefox before with it when I had the same Ubuntu running but installed the GUI and then got being with some side gig and came back to it a week later to finish setting it up to find it no longer connecting to the internet...?
So I reinstalled it over it thinking that I had messed with too many settings and that it would be better to start fresh.

---

### Post by felinoel on 2012-08-21
Someone elsewhere is telling me that he thinks I may need to set up a manual static ip?

---

### Post by CharlesA on 2012-08-21
Something is wrong with your dhclient, run these and post the output:

```
sudo dhclient
```
```
echo $?
```

You can get around it by setting a static IP, yes, but it would be better to figure out what the root cause is.

---

### Post by felinoel on 2012-08-21
> **charlesa said:**
> something is wrong with your dhclient, run these and post the output:

```
sudo dhclient
```
```
echo $?
``````
0
```

---

### Post by felinoel on 2012-08-21
When I run sudo lshw -class network I get a bunch of stuff but at the top it says, "network DISABLED"

... how do I enable this?


    
EDIT:
Maybe this will help?
[http://ubuntuforums.org/showthread.php?t=1436828](http://ubuntuforums.org/showthread.php?t=1436828)
How do I do this in Terminal without a gui?

---

### Post by CharlesA on 2012-08-21
> **felinoel said:**
> ```
0
```
Well, that means dhclient isn't crashing, which is good, I guess.

Not sure what you mean by disabled.

---

### Post by felinoel on 2012-09-06
> **CharlesA said:**
> No slash:

```
sudo tail -f /var/log/syslog
```

I got a new network card because the lighting looked off and now when I go to do this (because the internet still won't work) I get 

Noel named[887]: error {network unreachable} resolving 'www.google.com/A/IN': 192.228.79.201#53
Noel named[887]: error {network unreachable} resolving 'www.google.com/A/IN': 192.33.4.12#53
Noel named[887]: error {network unreachable} resolving 'www.google.com/A/IN': 128.63.2.53#53
*some more like this, then*
Noel sudo: pam_encryptfs: pam_sm_authenticate: /home/me is already mounted



> **CharlesA said:**
> Well, that means dhclient isn't crashing, which is good, I guess.

Not sure what you mean by disabled.Ummm?
It specifically states, "*-network DISABLED"

EDIT:
Oh hey, like this.
[http://ubuntuforums.org/showthread.php?t=1490833](http://ubuntuforums.org/showthread.php?t=1490833)
Too bad the posted solution is for the GUI version and since I can't get online I can't install the GUI...

---

### Post by CharlesA on 2012-09-07
Can you ping:
```
74.125.224.195
```

---

### Post by HugoSerrano on 2012-09-07
Hello!

First, check your network card and cable.
Check the NIC (Network Interface Card) and see if the lights are blinking. 
Do the same on router/switch. Check if the port number got the light on/blink.

If yes on both, boot up a ubuntu livecd and check if you can get an IP. If yes, you should be ok on hardware.

Give feedback!

Best Regards!
Hugo Serrano.

---

### Post by felinoel on 2012-09-07
> **CharlesA said:**
> Can you ping:
```
74.125.224.195
```Will try when I get home.

> **HugoSerrano said:**
> Hello!

First, check your network card and cable.
Check the NIC (Network Interface Card) and see if the lights are blinking. 
Do the same on router/switch. Check if the port number got the light on/blink.

If yes on both, boot up a ubuntu livecd and check if you can get an IP. If yes, you should be ok on hardware.

Give feedback!

Best Regards!
Hugo Serrano.I tested the cable on a regular computer, the cable works, and the card appears to blink correctly.

---

### Post by felinoel on 2012-09-07
> **CharlesA said:**
> Can you ping:
```
74.125.224.195
```

Network is unreachable.

---

### Post by CharlesA on 2012-09-07
It is definitely a network issue. Does the same thing happen when you boot a livecd ?

---

### Post by felinoel on 2012-09-07
> **CharlesA said:**
> It is definitely a network issue. Does the same thing happen when you boot a livecd ?The server doesn't have a disc drive because... it is a server.

I am trying to find where my jump drive Ubuntu installer went to atm but I think one of my housemate's cats ran off with it, they always walk around with socks and other stuff in their mouth... <.<;

---

### Post by felinoel on 2012-09-07
> **HugoSerrano said:**
> Hello!

First, check your network card and cable.
Check the NIC (Network Interface Card) and see if the lights are blinking. 
Do the same on router/switch. Check if the port number got the light on/blink.

If yes on both, boot up a ubuntu livecd and check if you can get an IP. If yes, you should be ok on hardware.

Give feedback!

Best Regards!
Hugo Serrano.> **CharlesA said:**
> It is definitely a network issue. Does the same thing happen when you boot a livecd ?So for some reason I just installed it instead of running a livecd (must be force of habit) but while I was doing that new screens appeared that hadn't before?! "Configure the network" is popping up and asked if I wanted to use eth0 or eth1. When I tried eth0 it said that my network isn't using DHCP protocol, its DHCP server may be slow, or some network hardware is not working.



EDIT:
I went back and switch to eth1, because that is my new network card I just got, and it appears to be working?!?!!!!!

EDIT:
During the midst of my celebration I got the apparently common blank purple screen issue, wonderful.

---

### Post by CharlesA on 2012-09-07
Add nomodset to the list of boot options on the grub screen and it should load up ok.

---

### Post by felinoel on 2012-09-08
> **CharlesA said:**
> Add nomodset to the list of boot options on the grub screen and it should load up ok.I just reset it to try one of the fixes I found online and it seems to work fine now?

---

### Post by felinoel on 2012-09-08
I don't want to make a new thread for just this, but I was following a guide and it said to save and exit... but it doesn't say how?

[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)
> Now check if php is working :

```
$sudo vi /var/www/info.php
```

and add

```
<?php
phpinfo();
?>
```

save and exit

---

### Post by CharlesA on 2012-09-09
As long as you used sudo to run vi, you should be able to hit esc then type:
```
:wq
```

and not get any errors.

However, you might try running nano instead of vi, as the learning curve isn't as steep.

```
sudo nano /var/www/info.php
```

Ctrl + X to exit, it will prompt you to save changes.

---

