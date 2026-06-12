---
title: "rkhunter warning"
date: 2010-01-07
forum: Security
---

### Post by chaopoch on 2010-01-07
I just run rkhunter and got the following output, does it mean any risk to my computer? thanks for reply.

...
Checking the network...

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    Checking for TCP port 1984                               [ Not found ]
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 6666                               [ Not found ]
    Checking for TCP port 6667                               [ Not found ]
    Checking for TCP port 6668                               [ Not found ]
    Checking for TCP port 6669                               [ Not found ]
    Checking for TCP port 7000                               [ [COLOR="Red"]Warning[/COLOR] ]
    Checking for TCP port 13000                              [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 25000                              [ Not found ]
    Checking for TCP port 29812                              [ Not found ]
    Checking for TCP port 31337                              [ Not found ]
    Checking for TCP port 33369                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 47018                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

...
  Performing filesystem checks
    Checking /dev for suspicious file types                  [ [COLOR="red"]Warning[/COLOR] ]
    Checking for hidden files and directories                [ [COLOR="red"]Warning[/COLOR] ]

Checking application versions...

    Checking version of Exim MTA                             [ [COLOR="red"]Warning[/COLOR] ]
    Checking version of GnuPG                                [ [COLOR="red"]Warning[/COLOR] ]
    Checking version of OpenSSL                              [ [COLOR="red"]Warning[/COLOR] ]

---

### Post by styxcoverbnd on 2010-01-07
I'm not sure about the Port 7000 warning. Can you open a terminal and do a 'sudo netstat -tnlp' (without the quotes) to see what program is listening on that port and look at the rkhunter log to see what else it says for that port. 

As for the filesystem check and applications warnings those are (most likely) false positives. I started a thread a few weeks ago about the application errors (found [here](http://ubuntuforums.org/showthread.php?t=1342508)) as I received similar ones after rkhunter released a new version and the autoupdate grabbed the latest definition file. For the filesystem warnings can you post what your log says are the suspicious and hidden file types. I'm assuming that they are for pulse audio, java, .static which are ok but cause the errors

---

### Post by running_rabbit07 on 2010-01-07
From what I have seen rkhunters in Ubuntu give too many false positives.

---

### Post by chaopoch on 2010-01-07
> **styxcoverbnd said:**
> I'm not sure about the Port 7000 warning. Can you open a terminal and do a 'sudo netstat -tnlp' (without the quotes) to see what program is listening on that port and look at the rkhunter log to see what else it says for that port...

I run command 'sudo netstat -tnlp' and check the rkhunter.log, I think this is just another false positive. thanks for all helps.

[COLOR="Blue"]$ sudo netstat -tnlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:1125          0.0.0.0:*               LISTEN      4399/thunderbird-bi
tcp        0      0 127.0.0.1:6600          0.0.0.0:*               LISTEN      3271/mpd        
tcp        0      0 127.0.0.1:1100          0.0.0.0:*               LISTEN      4399/thunderbird-bi
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               LISTEN      2110/hddtemp    
tcp        0      0 0.0.0.0:4662            0.0.0.0:*               LISTEN      4226/amule      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2316/cupsd      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      2058/exim4      
tcp6       0      0 127.0.0.1:6880          :::*                    LISTEN      4034/java       
tcp6       0      0 :::6881                 :::*                    LISTEN      4034/java       
tcp6       0      0 :::48682                :::*                    LISTEN      4034/java       
tcp6       0      0 :::139                  :::*                    LISTEN      2229/smbd       
tcp6       0      0 127.0.0.1:45100         :::*                    LISTEN      4034/java       
tcp6       0      0 :::42125                :::*                    LISTEN      4034/java       
tcp6       0      0 ::1:631                 :::*                    LISTEN      2316/cupsd      
tcp6       0      0 :::445                  :::*                    LISTEN      2229/smbd 


**rkhunter.log**

Warning: Network TCP port 7000 is being used by /usr/lib/jvm/java-6-sun-1.6.0.16/jre/bin/java. Possible rootkit: Possible rogue IRC bot[/COLOR]

---

### Post by running_rabbit07 on 2010-01-07
Run ```
top
``` and see if Java is in fact connecting.

---

