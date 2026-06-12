---
title: "ufw doesnt work propely."
date: 2016-08-03
forum: Security
---

### Post by mrfrenzoid on 2016-08-03
Hello everyone, this is my first time posting a topic, i hope that you guys can help me, also sorry if i make any gramatical mistake, i don't speak much english for now.

So my problem is that my machine that i only use as ts3 host got ddosed from China and i wanted to configure the ufw to prevent those kinds of attacks, almost all the ddos are from the same ip or another ip from France, i configures the ufw, enabled it, and restarted the machine, but as you can see on the screenshot, the ddoser keeps opening more ports and making my server lagg a lot, any idea about how to make the ufw work propely or how to stop the ddoser?


[http://image.prntscr.com/image/2cfc747f9b424164b14c3a4a4869e4eb.png](http://image.prntscr.com/image/2cfc747f9b424164b14c3a4a4869e4eb.png)

As you can see there are 4 conections from the same IP, even if i have done the deny reglamentsfor that ip, also sometimes it goes to 50 - 90 connections and then the machine implodes.



Have a nice day! Best regards, Frenzoid.

---

### Post by yoshii on 2016-08-03
I really wish I knew a good answer.  This type of thing concerns me as well.  And I don't feel comfortable with some aspects of the OS software.  
And I feel like the developers aren't currently providing any of us with much user-friendly stuff.  Comodo I could understand, on Windows.  But I just don't have the flair for this on Linux and I don't trust the false sense of security offered by sites like this where it's an afterthought instead of a default install.  Linux is not invulnerable just because it's not Windows.

---

### Post by steeldriver on 2016-08-03
From `man ufw`:

```

       Rule  ordering  is  important  and the first match wins. Therefore when
       adding rules, add the more specific rules first with more general rules
       later.

```

So you probably need to move the DENY rules for the specific addresses that are causing problems BEFORE the general ALLOW rules

---

### Post by mikey93898 on 2016-08-04
I hope I'm not intruding here, but I would also like to recommend CSF as an alternative. It uses IPTables and automatically adds people to DROP for a wide variety of offenses very quickly, including port scans, hammering, and failed logins. Just the other day my buddy decided to port scan my server and was immediately temp-bann'ed for like 3 hours. It's really a nice convenient tool.

---

### Post by mrfrenzoid on 2016-08-04
Hello and thanks you guys very much for your support :D, i didn't expeted this much help, also sorry for my bad english hehe :oops:




**Steeldriver:** the default general rule is to deny any other access that is not in the table, it supposed to be a withelist.. anyways i still got ports opened from another ips that are not in the table, anyways i will try to order the rules and then check the connections, also, when you update the rules, those are instantly applied or i need to restart the machine :confused:?


**Mikey93898:** I'll give it a try, i really don't really know how IPTables work :-k, anyways i will check to learn more about it.
[COLOR=#000000]**Yoshii:** same here, the problem is that i don't know much about GNU/Linux bases, only the basics, atleast to know when i get ddosed [/COLOR]:lolflag: hehe, i readed the ufw is like a firewall wich works like a withelist or blacklist depending on the defalt rule applied, anyways i got a withelist and i still got ports opened from ips that are not on the ufw table (ufw status verbose).



Thanks to everyone for now, i will see what i can do with the new info hehe, thanks! 
Best regards: MrFrenzoid.

---

### Post by mrfrenzoid on 2016-08-04
Hello again, so i did this, i organizated the rules and this is my results..

When i add a new rule it automatly applies.
When i remove a rule i need to reboot the machine to apply the changes, (even if i use the ufw reload it still doesnt work).

I arranged the rules like this and setted the default incoming to deny (with ufw default deny):
[http://image.prntscr.com/image/9f9f6fc548cd4ef791331124cdcf9294.png](http://image.prntscr.com/image/9f9f6fc548cd4ef791331124cdcf9294.png)

As you can see the 185 ip still can open ports on my server, and i dont know how and why. Is not a big problem when he opens 2 or 3 ports, but sometines it goes to 60+ ports on my server, and the machine collapses. :mad:


after that i tryed the CSF, but is too confusing, i configured it to deny any ping test, disabling the test mode, and restarted the CSF, i tryed it and the ping still was enabled, sorry but with my poor english i atleast understood the instructions of the CSF.

Any idea what could i try next?


Best regards, MrFrenzoid.

---

### Post by steeldriver on 2016-08-04
They can connect because you are ALLOWing from Anywhere to ports 22, 30033, 9987 first - and that rule takes precedence

Basically you have two approaches:


[LIST=1]
[*](blacklist approach) DENY access for specific hosts or IP ranges **first**, then ALLOW access to everyone (else) e.g. 
[/LIST]
 ```

steeldriver@xenial-vm:~$ sudo ufw deny from 192.168.1.65
Rule added
steeldriver@xenial-vm:~$ sudo ufw allow from any to any port 22
Rule added
Rule added (v6)

steeldriver@xenial-vm:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] Anywhere                   DENY IN     192.168.1.65
[ 2] 22                         ALLOW IN    Anywhere
[ 3] 22 (v6)                    ALLOW IN    Anywhere (v6)

```

 2. (whitelist approach) user the DEFAULT DENY rule, and then ALLOW specific hosts or subnet ranges, e.g.
```

steeldriver@xenial-vm:~$ sudo ufw allow from 192.168.1.0/26 to any port 22
Rule added
steeldriver@xenial-vm:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22                         ALLOW IN    192.168.1.0/26

```

---

### Post by mrfrenzoid on 2016-08-04
Hello, and thank you for your time, anyways as i sayd on the last reply, i have a withelist system (default deny on outgoing and incoming) and a rule that specifies that nothing can go to anywhere except the rules of above of that rule.

the problem is that still i got connections from this dude, he opens ports that are not allowed to connect.

[http://image.prntscr.com/image/ab3463a3ea804273ae1f506ae0b41f31.png](http://image.prntscr.com/image/ab3463a3ea804273ae1f506ae0b41f31.png)

As you can see, he's connecting from the 37979 port to my 102 port, from 32881 port to my 443 port and 35478 port to my 80 port.


Isnt supposed to deny unknown connections that are not listened on the ufw table?
Or im still doing something wrong?
Did i explained my self right this time?

Best regard, MrFrenzoid.

---

### Post by Doug S on 2016-08-05
> **mrfrenzoid said:**
> As you can see, he's connecting from the 37979 port to my 102 port, from 32881 port to my 443 port and 35478 port to my 80 port. The port 37079 stuff is from someone else. Your main culprit, 185.8.49.4, is from your same provider, so you could complain to them.

I am not familiar with "NetHogs" output, so am not entirely sure what it means. Does it just mean a connection is being attempted, but not succeeding? Does it display stuff before the iptables rules? Could we see the output for "netstat -ntu", which would show the state? Example (external IP address changed):```
doug@DOUG-64:~$ [COLOR="#FF0000"]netstat -ntu[/COLOR]
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 192.168.111.1:22        192.168.111.101:59852   ESTABLISHED
tcp        0      0 192.168.111.1:445       192.168.111.101:50116   ESTABLISHED
tcp        0      0 173.180.XXX.YYY:80         46.137.76.236:62866     SYN_RECV
tcp        0    304 192.168.111.1:22        192.168.111.101:50830   ESTABLISHED
```

---

### Post by wildmanne39 on 2016-08-06
Please use thumbnails or Url's when posting images because many people have slow internet conections and loading pages with large images is very difficult for them.

---

### Post by mrfrenzoid on 2016-08-06
Hello, also, does ufw allows port limitations?

Oh yes, it does, sorry hehe.

---

### Post by CharlesA on 2016-08-06
I use CSF on my publicly facing servers and it seems to be easier for me to deal with than ufw or iptables directly.

In any case, if you are under DDoS, you need to work with your provider to get them to either blackhole your server, or purchase DDoS a mitigation service if they offer it.

A firewall alone won't stop a DDoS - even if all traffic was dropped, the machine would still be receiving packets and them dropping them, which would kick it off the network or cause it to be unusable (the whole point of a Denial of Service attack).

---

### Post by mrfrenzoid on 2016-08-07
Humh, i see.. i'll ask them to see what posibilities i have, also i tryed to configure the CSF, but i think i did something wrong and it doesnt work as well.. 

Anyways, if someone is wondering how does a DDoS looks like, here's a vid: [https://www.youtube.com/watch?v=Sh2GKKv-Ukg&feature=youtu.be](https://www.youtube.com/watch?v=Sh2GKKv-Ukg&feature=youtu.be)

I'll try to check if i can edit the standard limited acces for ports from the ufw, i think the default is 6 times per 30 secs, i need to change it to 1 time per 20sec, i don't know im explaining myself properly.

---

### Post by ChuangTzu on 2016-08-19
a good default ufw setup is:  sudo ufw enable sudo ufw default deny sudo ufw deny ssh 

 This will block incoming traffic and ssh.  Note: if you use ssh to login remotely then do not add the last rule.  Linux is secure by design, however, that default security is only as good as the person using it keeps it.  If you click on malware infested sites, download packages from all over the net, plug in usb sticks you find on the ground etc... then even Linux can be hacked, it is harder but not impossible.

---

