---
title: "apache2 - How to kow how run the process"
date: 2010-12-22
forum: Server Platforms
---

### Post by lamanabie on 2010-12-22
Hello I have ubuntu server 10.10 with apache2 .. 
I want to know who run the process on my server . for example:
I have 4 users Bob, Spongbob, Bubblebob, www they have their webspace in public_html folder in their home folder. And if they run some long php script I want know who from them run it.
But when I run command from 'www' account to see his processes I just see this: 

www@edkoserver:~$ ps aux | grep apache2
root      3418  0.0  0.5 172808 11276 ?        Ss   Dec18   1:03 /usr/sbin/apache2 -k start
www-data 12261  0.0  0.5 178700 11032 ?        S    Dec19   0:03 /usr/sbin/apache2 -k start
www-data 12262  0.0  0.5 179820 12068 ?        S    Dec19   0:02 /usr/sbin/apache2 -k start
www-data 13171  0.0  0.5 178692 11020 ?        S    Dec19   1:01 /usr/sbin/apache2 -k start
www-data 13664  0.0  0.5 178704 11032 ?        S    Dec19   0:32 /usr/sbin/apache2 -k start
www      15642  0.0  0.0   8956   880 pts/0    S+   17:45   0:00 grep --color=auto apache2
www-data 26949  0.0  0.5 178800 11456 ?        S    Dec20   0:32 /usr/sbin/apache2 -k start
www-data 27100  0.0  0.5 178776 10988 ?        S    Dec20   0:01 /usr/sbin/apache2 -k start
www-data 27242  0.0  0.5 179708 11792 ?        S    Dec20   1:00 /usr/sbin/apache2 -k start
www-data 27243  0.0  0.5 178540 10872 ?        S    Dec20   0:32 /usr/sbin/apache2 -k start
www-data 27274  0.0  0.9 187508 19544 ?        S    Dec20   0:01 /usr/sbin/apache2 -k start
www-data 27278  0.0  0.4 177644  9968 ?        S    Dec20   0:01 /usr/sbin/apache2 -k start
www@edkoserver:~$ 

So I just know that apache2 is running under deafult secure account www-data .. but who ask to run apache2 ? How to know this.
Thanks Metiu.

---

### Post by jhollinger on 2010-12-22
Most of those Apache processes were started by the system when it was booted. They are always running, even when Apache is not being used. (Apache may create more or kill some if load changes.) So the output from "ps aux" isn't going to help you.

"apache2ctl fullstatus" might tell you what's happening right now, but to look at historical data, you need to have each user's webspace in it's own Virtual Host, and give each Virtual Host its own log. Then you can look through the logs to see what's been running.

It's difficult to be more specific without knowing more about your setup.

---

