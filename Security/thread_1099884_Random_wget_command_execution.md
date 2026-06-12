---
title: "Random wget command execution"
date: 2009-03-18
forum: Security
---

### Post by XanTrax on 2009-03-18
I have noticed on a few rare occasions, my netstat command output would look normal except for one thing:

```

[16:58:02][kozler@kozler-desktop:~]$ sudo netstat -tnap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:139           0.0.0.0:*               LISTEN      6084/smbd       
tcp        0      0 192.168.1.100:139       0.0.0.0:*               LISTEN      6084/smbd       
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN      6028/hddtemp    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      11360/sshd      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5372/cupsd      
tcp        0      0 127.0.0.1:445           0.0.0.0:*               LISTEN      6084/smbd       
tcp        0      0 192.168.1.100:445       0.0.0.0:*               LISTEN      6084/smbd       
tcp        0    106 10.27.2.21:59873        208.78.69.70:80         ESTABLISHED 13472/wget      
tcp6       0      0 :::22                   :::*                    LISTEN      11360/sshd     

```

The wget command. I manged to catch it in the process list still and this is what I see:

```

[16:58:23][kozler@kozler-desktop:~]$ ps -Aef | grep -i wget
kozler   13665 13664  0 16:58 pts/1    00:00:00 wget http://checkip.dyndns.org/ -q -O -
kozler   13668 13547  0 16:58 pts/4    00:00:00 grep --color=auto -i wget

```

My question is, is this something internal to ubuntu?  I see that I am the user executing it "apparently" but I assure you that I am physically NOT executing the command, though, it is being run under my name. I know what dydns is and I am pretty knowledgeable in server environments, but, researching this yields nothing.

Anyone have any idea how to stop this?  I know its something small but im not at ALL comfortable with a random wget command being executed on my machine at arbitrary times, regardless if is connecting to dydns for assistance in hostname resolution.

---

### Post by cariboo on 2009-03-19
It looks pretty self explanitory. If you are using dyndns, it looks like it is getting a file from the dyndns server, or just reporting your ip address.

Jim

---

### Post by Dr Small on 2009-03-19
> **XanTrax said:**
> regardless if is connecting to dydns for assistance in hostname resolution.

Well, that is exactly what it is doing.

---

### Post by XanTrax on 2009-03-19
I can see that, but, thats just the thing....im not connecting to dydns (directly) so I was seeing if maybe anyone had any idea if something else might be causing it.  I havent ever seen dydns being used until recently.  Maybe my Universities done something with their DNS servers for a little bit?

I knew what it was doing, but like I said, I am just pretty uncomfortable with a random command like that (accessing the internet) being executed on its own at aribtrary times...What I was trying to ask was if anyone could maybe give me some more insight on to how I could possibly find out what is causing the wget command to execute on its own.

---

### Post by cariboo on 2009-03-19
It is probably a cron job. When I was using noip it checked every thirty minutes to see if my external ip address had changed. In the case of noip I had to run a program called noip2. I would check with dyndns to see what the name of the program is that does the ip address checking.

Jim

---

### Post by koenn on 2009-03-19
> **cariboo907 said:**
>  ..to see what the name of the program is that does the ip address checking.

should be ddclient

> **XanTrax said:**
> ... give me some more insight on to how I could possibly find out what is causing the wget command to execute on its own.
things don't get installed or run on their own. someone has installed and scheduled wget, or ddclient or so

---

### Post by Dr Small on 2009-03-19
> **koenn said:**
> should be ddclient


things don't get installed or run on their own. someone has installed and scheduled wget, or ddclient or so
It could be ddclient or ipcheck. I use ipcheck and use it once a day at 12PM with cron (since it's a rare thing for my ip to change). To the OP, check cron, and look for ddclient or ipcheck.

---

### Post by mongo72 on 2009-03-19
> **XanTrax said:**
> I have noticed on a few rare occasions, my netstat command output would look normal except for one thing:

The wget command. I manged to catch it in the process list still and this is what I see:

```

[16:58:23][kozler@kozler-desktop:~]$ ps -Aef | grep -i wget
kozler   13665 13664  0 16:58 pts/1    00:00:00 wget http://checkip.dyndns.org/ -q -O -
kozler   13668 13547  0 16:58 pts/4    00:00:00 grep --color=auto -i wget

```



To id the program that is actually making, the request, you would have had to seen the parent of the wget command above, which looks like it was PID 13664.  Try dumping the ps -Aef to a file, if the wget is in there, look up the parent.  

That should id the program it sounds like you are looking for, or at least get you further along in the search.

---

### Post by XanTrax on 2009-03-20
Well, it was not a cronjob or ddclient or anything else of that sort.  It turned out to be Conky executing a script to get my newest external IP.  Thank you to cariboo907 for reminding me that I had something that displayed my external IP and got it dynamically.  This is what was causing that random wget to be seen:

```

#!/bin/bash
# eigene öffentliche ip anzeigen

wget http://checkip.dyndns.org/ -q -O - |
grep -Eo '\<[[:digit:]]{1,3}(\.[[:digit:]]{1,3}){3}\>'

```


Silly me.

Also, I wasnt freaking out or anything, I just couldnt figure out what it was and wanted to get some insight on it. 

Thanks for all your help guys

---

