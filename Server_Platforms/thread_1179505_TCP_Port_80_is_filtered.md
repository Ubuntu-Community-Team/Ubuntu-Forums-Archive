---
title: "TCP Port 80 is filtered"
date: 2009-06-05
forum: Server Platforms
---

### Post by janeLHX on 2009-06-05
Dear friends,

I have this problem from the beginning, when I have just started using my new dedicated server with Ubuntu 8.04 LTS - Plesk 8.6 - 64bit. 

From time to time, all of the sudden, day or nigh, once a week, or 4 times a day my site stops working, and all of my users get the error "unable to connect" in their browsers. I just know that when this happens I can only access Plesk panel on port 8443, and restart the server, and after that everything woks fine. I have noticed that when my site works fine and I type the command nmap -sT -O localhost I get the message that the port 80 is open, but when the site is down I get that the port is filtered, "80/tcp   filtered http"

Can you please tell me what could be the problem ?

---

### Post by LepeKaname on 2009-06-06
Do you have root access to the server?

If so, I recommend you to install munin+monit, it will help you to:

1- To know better what is causing the problem, with charts of system activity history like access to the server, memory, cpu, etc. (munin)
2- To restart your web server every time it is offline or it has an overload, and let you know (send email). (monit)

I hope this work.

BTW. you nick letters "LHX" are they related to "LHX Attack chopper" old good game?

---

### Post by janeLHX on 2009-06-06
Yes man, that's the game. I have played it when I was like ten, and few years ago I have found the full version so I have decided to keep the name, it's great :)

About the server. I thank you for your help, I have root access but sincerely I don't want to mess with my server, and install lots of things, that's why I have Plesk panel, an just a few more programs. I have a huge site and if I disrupt it somehow it won't be good. I don't know how much of the system resources those programs will consume, so at the end, if everything else fails, I will install them, but for now I just want to hear if someone had the similar problem. If you know about some program, that can be installed on my local computer, and that can read log files that I have downloaded from my server, it would be great.

By the way, I see that you know things, and I want to ask you one more question. Before this my site was on Windows platform, and I had constant DOS attacks from some hacker groups. Do you know if this might be the problem, and do you know some software that can prevent DOS attacks now when I have changed my platform to Ubuntu. I don't say that they are attacking now, but just in case.

Thank you

---

### Post by LepeKaname on 2009-06-06
There are many tools out there in Linux to prevent attacks like "fail2ban". With that tool any any flood attack will be stopped immediately.

Munin do not take so much of resources, it worth it... There are many reasons why apache may be having problems. Munin can give you hints of what is happening. You can just turn it on only for a period until you get the reason of the problem. 

Does apache logs are returning some errors? If so, can yo post it here? 

Monit it is not so necessary... you can create your own script to monitor apache. 

Yea, I used to play a lot LHX also around that time... though I never could have all the medals. None of the subsequent "Chopper" games filled me as that one. I even have the exe file somewhere around here. 
[ Interesting: Apache (web server) and Apache (chopper) ] :D

---

### Post by windependence on 2009-06-07
> **janeLHX said:**
> Yes man, that's the game. I have played it when I was like ten, and few years ago I have found the full version so I have decided to keep the name, it's great :)

About the server. I thank you for your help, I have root access but sincerely I don't want to mess with my server, and install lots of things, that's why I have Plesk panel, an just a few more programs. I have a huge site and if I disrupt it somehow it won't be good. I don't know how much of the system resources those programs will consume, so at the end, if everything else fails, I will install them, but for now I just want to hear if someone had the similar problem. If you know about some program, that can be installed on my local computer, and that can read log files that I have downloaded from my server, it would be great.

By the way, I see that you know things, and I want to ask you one more question. Before this my site was on Windows platform, and I had constant DOS attacks from some hacker groups. Do you know if this might be the problem, and do you know some software that can prevent DOS attacks now when I have changed my platform to Ubuntu. I don't say that they are attacking now, but just in case.

Thank you

To do this correctly, you really need to have your firewall on a separate box. A good hardware  firewall would be best, or something like pfsense on an old box would be OK. The reason for this is because if you are getting DDOS attacks, if you put your firewall on the same box as your server, you could be taken down as the firewall can become overloaded and eat up all your CPU effectively doing what the hacker wanted to do anyway.

-Tim

---

### Post by janeLHX on 2009-06-07
I just had the same problem again. Port 80 is filtered and when I use top command I get this
```

Tasks: 376 total,   1 running, 375 sleeping,   0 stopped,   0 zombie
Cpu(s): 25.0%us,  0.2%sy,  0.0%ni, 74.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4056376k total,  4014232k used,    42144k free,    22276k buffers
Swap:   999992k total,   443288k used,   556704k free,   628788k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5131 mysql     20   0 2595m 526m 3756 S  100 13.3   1104:06 mysqld
 5386 list      20   0 74176 6440 2692 S    1  0.2   0:29.46 python
18005 root      20   0 19124 1472  932 R    1  0.0   0:00.26 top
 5370 list      20   0 74184 4544 2692 S    1  0.1   0:27.80 python
 4314 root      39  19     0    0    0 S    0  0.0   7:01.44 kipmi0
 5896 tomcat    20   0  416m  19m 2472 S    0  0.5   2:08.50 jsvc
    1 root      20   0  4032  692  596 S    0  0.0   0:02.06 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.46 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.08 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.28 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.06 watchdog/1
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/2
   10 root      15  -5     0    0    0 S    0  0.0   0:00.38 ksoftirqd/2
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.06 watchdog/2

```

I'll get the error logs tonight, and show them to you.

---

### Post by LepeKaname on 2009-06-07
Try restarting mysql because it is taking all your CPU. Apache failure may be related (but not so probable) to that... 

I was checking your "TOP" output and it seems that your memory is getting full sometimes (look at the swap value), which I feel it is not usual. You have 1GB swap, and you are using almost half of it now. I suggest you to create an additional 1GB swap file and enabled it with swapon. Because if that swap gets full your server will freeze (it may be never use it, but just for precaution). 

As I recommended you, use munin (munin uses around 6.5MB of memory), that may help a lot to solve this problem. After solving it, you can uninstall it.

---

### Post by windependence on 2009-06-08
How much physical RAM is in this box?

-Tim

---

### Post by janeLHX on 2009-06-08
4 GB. But I have 50 000 visits a day, and 10 times more open pages.

---

### Post by janeLHX on 2009-06-08
Lapekaname, you have been more than useful, I will check that program out and try to fix my memory. Maybe after that everything will be fine, and we will fly again, like those choppers :)

---

### Post by LepeKaname on 2009-06-08
Has been a pleasure to help... If it was fixed, please post it here.
Cya.

---

