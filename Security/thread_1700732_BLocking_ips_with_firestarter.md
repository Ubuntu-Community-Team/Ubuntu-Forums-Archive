---
title: "BLocking ips with firestarter?"
date: 2011-03-05
forum: Security
---

### Post by heinns on 2011-03-05
Hi, im just wondering how do you block ips with Firestarter, i noticed there are 2 connections that came up out of nowhere and i want to block them as it seems like they are malware.

---

### Post by runeh76 on 2011-03-05
Hi

Although Firestarter is fully functional, active development ended in 2005 with version 1.0.3. 

Use it if u want, but havent u heard about GUFW & Mobloquer ?  :)

---

### Post by heinns on 2011-03-05
> **runeh76 said:**
> Hi

Although Firestarter is fully functional, active development ended in 2005 with version 1.0.3. 

Use it if u want, but havent u heard about GUFW & Mobloquer ?  :)


I tried gufw before and didn't like it, i like being able to have a look at all the active connections on my computer.

---

### Post by runeh76 on 2011-03-05
Open connections:
```
netstat -t
``` or ```
netstat -t -n
```

---

### Post by heinns on 2011-03-05
> **runeh76 said:**
> Open connections:
```
netstat -t
``` or ```
netstat -t -n
```


Alright thanks, ill uninstall firestarter and reinstall gufw.

Also can you tell me if these connections are all safe, and not malware?

tcp        0      0 :36787               syd01s01-in-f100.1e:www ESTABLISHED
tcp        1      0 :42274               feijoa.canonical.co:www CLOSE_WAIT 
tcp        0      0 :42281               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 :42280               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 42278               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 :42276               feijoa.canonical.co:www ESTABLISHED
tcp        1      0 :42273               feijoa.canonical.co:www CLOSE_WAIT 
tcp        0      0 :42279               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 :42277               feijoa.canonical.co:www ESTABLISHED
tcp        1      0 :42275               feijoa.canonical.co:www CLOSE_WAIT

---

### Post by stmiller on 2011-03-05
You can use ufw:

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

PS: those connections are to canonical (aka ubuntu) probably checking for updates, or using the ubuntu one service. 

:) Cheers,

---

### Post by uRock on 2011-03-05
> **heinns said:**
> tcp        0      0 :36787               syd01s01-in-f100.1e:www ESTABLISHED
tcp        1      0 :42274               feijoa.canonical.co:www CLOSE_WAIT 
tcp        0      0 :42281               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 :42280               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 42278               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 :42276               feijoa.canonical.co:www ESTABLISHED
tcp        1      0 :42273               feijoa.canonical.co:www CLOSE_WAIT 
tcp        0      0 :42279               feijoa.canonical.co:www ESTABLISHED
tcp        0      0 :42277               feijoa.canonical.co:www ESTABLISHED
tcp        1      0 :42275               feijoa.canonical.co:www CLOSE_WAIT
I am guessing you ran the command while connected to Ubuntu Forums.

Moved to Security Discussions.

---

### Post by heinns on 2011-03-05
> **uRock said:**
> I am guessing you ran the command while connected to Ubuntu Forums.

Moved to Security Discussions.

I did, but this time i didn't and i get the following.

netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 :41197               syd01s01-in-f100.1e:www TIME_WAIT  
tcp        0      0 :41202               syd01s01-in-f100.1e:www TIME_WAIT  


> **stmiller said:**
> You can use ufw:

[http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

PS: those connections are to canonical (aka ubuntu) probably checking for updates, or using the ubuntu one service. 

:smile: Cheers,


Just tried ufw and typed the following command 
sudo ufw deny from 94.129.186.108
Rule added
And i still see it active in firestarter.

---

### Post by inobe on 2011-03-05
> **heinns said:**
> I tried gufw before and didn't like it, i like being able to have a look at all the active connections on my computer.

EtherApe

example:

---

### Post by runeh76 on 2011-03-05
**heinns** u are in safe :)

canonical-->updates

do a little google about: time_wait close_wait and established etc..
Its fun to learn things  :)
Ubuntu isn't a Windows!


Take care

---

### Post by heinns on 2011-03-05
> **runeh76 said:**
> **heinns** u are in safe :)

canonical-->updates

do a little google about: time_wait close_wait and established etc..
Its fun to learn things  :)
Ubuntu isn't a Windows!


Take care

Hm so the Ip's all belong to canonical?
94.129.186.108
2.83.130.153

If so thank god, i thought i was infected.

---

### Post by The Cog on 2011-03-06
> **heinns said:**
> Just tried ufw and typed the following command 
sudo ufw deny from 94.129.186.108
Rule added
And i still see it active in firestarter.

Aaargh!
You cannot use both firewall front-ends. They both configure iptables, and they can't both do it. You don't know what the rules will end up looking like. If you want to use ufw instead, then you need to use synaptic to **completely** (including configuration files) remove firestarter.

My guess is that you have two problems adding that deny:
1: Adding the deny to ufw after the connection has been establised is too late - ufw will only prevent further connections.
2: The connection was outbound, and you were trying to ban inbound connections.

---

