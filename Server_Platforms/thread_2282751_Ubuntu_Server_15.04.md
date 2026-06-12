---
title: "Ubuntu Server 15.04"
date: 2015-06-16
forum: Server Platforms
---

### Post by Miral_Hassni on 2015-06-16
Hi All
I am new here I have successfully installed Ubuntu Server 15.04 with these options:
1. Basic Ubuntu Server
2. SSH Server
3. Gnome Desktop Environment

Now i need to make this PC my web server i host my domains here  please tell me step by step guide me how can i do it, because i am paying money for hosting i need my own hosting with my pc I have also static IP and tell me which software is the best web server with this version of Ubuntu Server.

Thanks Regards

Miral Hassni

---

### Post by TheFu on 2015-06-16
a) production servers probably should run an LTS release, not a 9-month support release.
b) [https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) explains how to do many things.

If you are really new to Linux and/or Unix in general, some background knowledge will really help and save you hours, days, weeks, months of frustration. [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

And please do not forget about security. There are many guides for Ubuntu Security - help.ubuntu.com and wiki.ubuntu.com have lots of information.

---

### Post by Miral_Hassni on 2015-06-17
first link works but 2nd one not working [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

---

### Post by Miral_Hassni on 2015-06-17
and please guide me which is the best server for web server in Ubuntu 15.04 
1. Apache
2. Lamb
3. Xampp
4. Nginx
Please guide me i am new

---

### Post by QIII on 2015-06-17
You'll get a different answer from everyone about which is "best". Mine is a LEMP server (nginx), but I can't tell you if it would be best for yours.

However, I will say that I would not recommend a Desktop Environment on a web server.  Every unnecessary service running on your exposed server is a security threat -- every service is a potential attack surface.  DEs run a host of services.  You want to reduce services to the barest minimum, not add to them.

I would suggest that it would be much better to do without the DE and learn to administer your server via the terminal, and that over a secure protocol if the web server is remote from you.

I'll also echo TheFu:  Use an LTS version on a server.

---

### Post by Miral_Hassni on 2015-06-17
OKey thanks 
I have installed apache2 and active my localhost please anyone can help me how i can host my domain in my new ubuntu server i have puchased domain name is " http://balochwebdesigner.com" also i have an static IP Address please help me urgent

---

### Post by TheFu on 2015-06-17
> **Miral_Hassni said:**
> first link works but 2nd one not working [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

There are 2 possible reasons this isn't working.
1) I take the server down a few minutes daily for backups. I don't recall the exact time for THAT specific server, but when you posted this message _could_ be it. Last night the backup took 
```
StartTime 1434521111.00 (Wed Jun 17 02:05:11 2015)
EndTime 1434521208.82 (Wed Jun 17 02:06:48 2015)
ElapsedTime 97.82 (**1 minute 37.82 seconds**)
``` also, the timestamps show it was an hour after your post.

2) Your ISP or country could block my server for some, unknown, reason. Perhaps using Tor or a VPN with an exit node in a different country? I've seen where some people in India and Thailand have issues connecting - don't know why. Don't think there is anything political or offensive on my blog.

Perhaps a cached version from Google can be seen?

Whenever someone says "urgent" - inside my mind I ask - "So how much does it pay?"

I cannot speak for anyone else here, but I'm here to help you learn. If you are new to Linux, that learning curve is steep. I didn't start running a web server until I'd been using Unix/Linux for over 3 years and programming on Unix was my day job. Having appropriate expectations is important. Sure, you CAN install a web server and you CAN put files into the correct locations well before the level of understanding necessary to secure that server has been reached. We all do it.  However, if you've just learned algebra, it usually isn't smart to attempt 1st semester calculus as the next step. A few other classes are needed first.

I agree with QIII - the "best" web server depends on the purpose you have for it. I mainly run nginx as a reverse proxy into webapps/web-services and have for about 8 yrs. Also have apache2.4 on 1 machine with parts of those websites have been running some version of apache since 1998-ish.  

"Best" isn't an easy question.  The great thing about Linux/Unix is nearly infinite flexibility. If you want 1 answer, you will be very frustrated. There is almost always 50 different ways to do anything, because we each have slightly different needs and skills. "Best" for someone extremely new to Linux often isn't the same as "best" for someone with 15 yrs experience.  Be very cautious whenever someone provides an answer without asking 20 questions first. They are probably VERY NEW and are sharing from very limited experience.

---

### Post by Miral_Hassni on 2015-06-17
> **TheFu said:**
> There are 2 possible reasons this isn't working.
1) I take the server down a few minutes daily for backups. I don't recall the exact time for THAT specific server, but when you posted this message _could_ be it.

2) Your ISP or country could block my server for some, unknown, reason. Perhaps using Tor or a VPN with an exit node in a different country? I've seen where some people in India and Thailand have issues connecting - don't know why. Don't think there is anything political or offensive on my blog.

Perhaps a cached version from Google can be seen?

Whenever someone says "urgent" - inside my mind I ask - "So how much does it pay?"

I cannot speak for anyone else here, but I'm here to help you learn. If you are new to Linux, that learning curve is steep. I didn't start running a web server until I'd been using Unix/Linux for over 3 years and programming on Unix was my day job. Having appropriate expectations is important. Sure, you CAN install a web server and you CAN put files into the correct locations well before the level of understanding necessary to secure that server has been reached. We all do it.  However, if you've just learned algebra, it usually isn't smart to attempt 1st semester calculus as the next step. A few other classes are needed first.

I agree with QIII - the "best" web server depends on the purpose you have for it. I mainly run nginx as a reverse proxy into webapps/web-services and have for about 8 yrs. Also have apache2.4 on 1 machine with parts of those websites have been running some version of apache since 1998-ish.  

"Best" isn't an easy question.  The great thing about Linux/Unix is nearly infinite flexibility. If you want 1 answer, you will be very frustrated. There is almost always 50 different ways to do anything, because we each have slightly different needs and skills. "Best" for someone extremely new to Linux often isn't the same as "best" for someone with 15 yrs experience.  Be very cautious whenever someone provides an answer without asking 20 questions first. They are probably VERY NEW and are sharing from very limited experience.
Now i use proxy to open the link

---

### Post by Miral_Hassni on 2015-06-17
I have installed apache successfully in my new ubuntu server 15.04 i368 now i am accessing my server through my IP in my network only i cant access server or i can not access apache index file from other networks like my office have another network when i go to their i open my server ip address which is 192.168.1.2 but not opening when i used to my own network like i have connect my laptop throug a Wifi from my own network server ip address opening i can access also my ftp server well.


please anyone can help me this regard how i configure apache that also i acess or open my website from other networks also i have a domain and static ip for the purpose but i dont know how to configure these.


Regards

---

### Post by CharlesA on 2015-06-17
You'd need to have it open to the Internet, but if you are running this on your desktop machine, it could expose you to attackers.

Even though this series is mostly about Nginx, you can apply the fundamentals to Apache, as well.
[http://arstechnica.com/series/web-served/](http://arstechnica.com/series/web-served/)

---

### Post by cariboo on 2015-06-18
Merged two similar threads

---

