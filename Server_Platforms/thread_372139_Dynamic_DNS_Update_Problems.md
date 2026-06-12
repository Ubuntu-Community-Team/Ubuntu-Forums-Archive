---
title: "Dynamic DNS Update Problems"
date: 2007-02-27
forum: Server Platforms
---

### Post by ditane on 2007-02-27
A while back I tried to switch to ubuntu, and because I had many windows  programs that I have to use that I couldn't use on linux, it just didn't stick.  I then setup a server, initially with XP, because that is what I knew, using cygwin for most of what I did.  I have recently switched over my server to kubuntu.  On my windows server I used a program from noip.com and an account from them to access my server remotely since I have a dynamic IP.  They have a linux solution, but to a newbie like me, it was really just confusing.  After reading a couple of things here, I tried to use dyndns and a program called DDclient ([http://linux.cudeso.be/linuxdoc/ddclient.php](http://linux.cudeso.be/linuxdoc/ddclient.php)) to update it.  So far I haven't been able to get it to work.  There is a line in the config file for it which the guide I used said to set as
```
use=if,   if=ppp0
``` 
I am not sure if this should be left as ppp0 or if that is just a placeholder, but when I run the debug on the program on DDclient, it returns
```
DEBUG:    get_ip: using if, ppp0 reports <undefined>
WARNING:  unable to determine IP address

```
I am behind a router and my eth0 reads as the computers IP address relative to the router, not my external IP, and the only other Network Interface I can find in the Network Interfaces section of KInfoCenter is the loopback interface.
Any clue as to what I should do to get DDclient to read the external IP address of my network, or does anyone else have another solution that isn't very complicated, because the harder stuff still is beyond me.

---

### Post by ditane on 2007-02-27
Ok, while after continuing to search on what to do about this i found something that helped (use the use=web line instead of the use=if, if=ppp0 line)  I am still quite new, so it took me a while.  However, after getting this to work my debug still gives a problem of 

```
Can't locate IO/Socket/SSL.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/ddclient line 1666.

```

I am investigating this still, but I figured I would update what I knew in case anyone had any pointers while I am looking.
Any help would be greatly appreciated.

---

### Post by ditane on 2007-02-27
Another update, while looking at the ddclient.conf file I decided to try out commenting out the line reading
```
ssl=yes
```

I got it to work, but are their any adverse affects?

---

### Post by hedrinbc on 2007-02-28
Just put this in the ddclient.conf file:

```

use=web

```
It's that simple!

Hope this helps,
-Ben

---

### Post by Knightwise on 2007-06-01
Ok , I did all the things that where talked about above. But my question is : 
Does Ddclient just look at the WEB ip at startup ? Because my IP changes from time to time (its a dodgy ADSL line) But how do I tell DDclient to 'poll' the outside web adress from time to time and ONLY send an update to the DYNDNS servers when it has changed ?

---

