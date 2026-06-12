---
title: "Apparmor+Privoxy = Ram using 100% and then the swap file!"
date: 2010-09-10
forum: Security
---

### Post by mr-woof on 2010-09-10
Hi all,

I've had a bit of a strange problem tonight, I'm running Ubuntu 10.04 at the moment, all updates etc. After reading on these fine forums about Apparmor I installed the documentation and the extra profiles, with the idea of having a proper play around with it once I had some spare time. So in my mind, I had left it unconfigured.

Again after reading about Privoxy last night, I installed it, setup the proxy settings in Firefox and went to bed. I turned on the machine tonight, to find Firefox couldn't see the proxy, tried:

"sudo /etc/init.d/privoxy status" 

and it was running, give it a restart and Firefox was fine again, but I noticed in Conky the ram was starting to get eaten up by a process called something like "Apparmor notifier", it went past 95% and then started going onto the swap file. Normally the machine uses about 30%-40% of 2gb with all sorts of programs running.

Managed to give the machine a restart and as soon as I opened Firefox it went mental again, I've removed both and all seems well again. Any ideas what happened? Any logs etc that I can look at? The Apparmor and Privoxy directories are both empty now.

Anyone come across this before? 

Thanks all :)

---

### Post by bodhi.zazen on 2010-09-10
Any errors in /var/log/messages ??

---

### Post by mr-woof on 2010-09-10
I seem to be struggling loading the file in nano, it's 1.1gb is that a normal sort of size? What would be the best way to use grep to filter out the file? 

I've just tried grep error /var/log/messages, only getting a couple about opera from the last week or and 

grep Privoxy /var/log/mesages
grep Apparmor /var/log/messages

not getting anything

---

### Post by bodhi.zazen on 2010-09-10
1.1 Gb is HUGE for /var/log/messages.

I would either use tail or better move it to messages.old and make a new smaller file.

```
tail -F /var/log/messages
```

My guess is something is amiss on your system, hopefully the log will give a clue.

If you like, here is my apparmor privoxy profile :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.sbin.privoxy](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.sbin.privoxy)

I doubt your problem is with a privoyx aa profile though.

---

### Post by mr-woof on 2010-09-10
Thanks bodhi, I hope when you say something amiss you don't mean nasty and infected type of amiss?

I used the tail -F command and outputted to a txt file, it's mostly this:

Sep 10 22:58:36 Ubuntu kernel: [ 8872.381906] [UFW AUDIT] IN=lo OUT= MAC=00:00:00:00:00:00:00:00:00:00:00:00:08:00 SRC=127.0.0.1 DST=127.0.0.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=33279 DF PROTO=TCP SPT=43697 DPT=31416 WINDOW=1827 RES=0x00 ACK URGP=0 

Port 31416 is my boinc manager, I run seti@home :) But, since I've been playing around with the smoothwall box it can't connect to the internet, do you think that's the reason the message log is so big?

Edit: I've also knocked the ufw logging level down to low from full and I'm connected straight into the router now, lets see if that makes any difference

---

### Post by bodhi.zazen on 2010-09-10
Well, your logs may be full from UFW, so that is a start. Keep watching ...

---

### Post by mr-woof on 2010-09-10
now i'm back straight into the router, all I'm seeing is the same as before but with port 3074, which is the ps3.

---

### Post by bodhi.zazen on 2010-09-10
> **mr-woof said:**
> now i'm back straight into the router, all I'm seeing is the same as before but with port 3074, which is the ps3.

At the moment I am not as concerned about network traffic, wondering if apparmor / privoxy / or firefox are giving you a problem.

How about if you temporarily disable UFW logging. In the long run, if you are not intending to monitor your logs , keep it disabled.

With a file size of over a Gb, either you are logging a ton of network traffic or you have a recurring error message.

For monitoring network traffic I would advise you use snort. Snort will watch your traffic and alert you to concerning events, I can not imagine reviewing 1 gb of network traffic, lol. Any concering traffic is almost certainly lost in the background "noise"

---

### Post by mr-woof on 2010-09-10
UFW logging has now been disabled, I was seeing a lot of port 3064 traffic coming from the ps3, since I've turned it off. Tail is not showing anything since. 

Do you think it's a good idea to try and re-create the problem in a virtual machine and see what happens?

---

### Post by bodhi.zazen on 2010-09-10
> **mr-woof said:**
> UFW logging has now been disabled, I was seeing a lot of port 3064 traffic coming from the ps3, since I've turned it off. Tail is not showing anything since. 

Do you think it's a good idea to try and re-create the problem in a virtual machine and see what happens?

If you are concerned with the traffic from the ps3, try wireshark =)

If you are not getting error messages, try rebooting and see what happens with privoxy. Privoxy starts automatically without any problem in Ubuntu 8.x -> 10.04 as well as with Debian and Fedora 10-13 (in other words no problems here, lol).

---

### Post by mr-woof on 2010-09-10
Ha Ha I love wireshark :)

I've installed Privoxy again, it's working using the default port 8118. So i'm going to reboot and see what happens

---

### Post by bodhi.zazen on 2010-09-10
> **mr-woof said:**
> Ha Ha I love wireshark :)

I've installed Privoxy again, it's working using the default port 8118. So i'm going to reboot and see what happens

Wireshark FTW :twisted: :lolflag:

---

### Post by mr-woof on 2010-09-10
I can confirm, privoxy is working fine and Tail is reporting no errors etc, last messages in messages:

Sep 10 23:58:16 Ubuntu kernel: [   17.795514] vboxdrv: fAsync=0 offMin=0x1ad offMax=0x77a
Sep 10 23:58:16 Ubuntu kernel: [   17.795823] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Sep 10 23:58:17 Ubuntu kernel: [   18.996113] ppdev: user-space parallel port driver

---

### Post by bodhi.zazen on 2010-09-10
> **mr-woof said:**
> I can confirm, privoxy is working fine and Tail is reporting no errors etc, last messages in messages:

Sep 10 23:58:16 Ubuntu kernel: [   17.795514] vboxdrv: fAsync=0 offMin=0x1ad offMax=0x77a
Sep 10 23:58:16 Ubuntu kernel: [   17.795823] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Sep 10 23:58:17 Ubuntu kernel: [   18.996113] ppdev: user-space parallel port driver

Sweet, hope privoxy serves you well =)

---

### Post by wacky_sung on 2010-09-11
I think you shall try Polipo (proxy cache server) & DNSmasq to boost up your web surfing speed.

---

### Post by wacky_sung on 2010-09-11
In additional,you can add free dns filter / cache server to give extra boost to your web surfing by adding it in Dnsmasq.

[http://ubuntuforums.org/showthread.php?t=1551267](http://ubuntuforums.org/showthread.php?t=1551267)

---

### Post by mr-woof on 2010-09-11
This is becoming rather annoying now, I've just turned the machine on, 

sudo /etc/init.d/privoxy status

is showing privoxy as running, but when I try and connect using Firefox I get the proxy server is refusing connections, restart privoxy and all is well. 

I'm tailing /var/log/messages with no errors, nothing in the /var/log/privoxy/logfile either

---

### Post by wacky_sung on 2010-09-11
> **mr-woof said:**
> This is becoming rather annoying now, I've just turned the machine on, 

sudo /etc/init.d/privoxy status

is showing privoxy as running, but when I try and connect using Firefox I get the proxy server is refusing connections, restart privoxy and all is well. 

I'm tailing /var/log/messages with no errors, nothing in the /var/log/privoxy/logfile either

I believe it may be has to do with your firewall or the setting of privoxy.By default,if you do not change any setting it shall work just fine except for some sites it will cause some issues.

---

### Post by bodhi.zazen on 2010-09-11
> **mr-woof said:**
> This is becoming rather annoying now, I've just turned the machine on, 

sudo /etc/init.d/privoxy status

is showing privoxy as running, but when I try and connect using Firefox I get the proxy server is refusing connections, restart privoxy and all is well. 

I'm tailing /var/log/messages with no errors, nothing in the /var/log/privoxy/logfile either

Edit /etc/privoxy/config and change

> listen-address localhost:8118to

```
listen-address 127.0.0.1:8118
```

---

### Post by mr-woof on 2010-09-11
I've changed it, I'm going to restart. :)

---

### Post by mr-woof on 2010-09-11
Seems to be working now :) It's quite funny, Privoxy has taken the Banner from the top of the Smoothwall web front, I thought it didn't look right, it took me a minute or so to work out what was missing :)

---

### Post by bodhi.zazen on 2010-09-11
> **mr-woof said:**
> Seems to be working now :) It's quite funny, Privoxy has taken the Banner from the top of the Smoothwall web front, I thought it didn't look right, it took me a minute or so to work out what was missing :)

You can whitelist your smoothwall router/web page if you wish.

---

