---
title: "Apache2 not displaying pages"
date: 2007-08-29
forum: Server Platforms
---

### Post by Almighty on 2007-08-29
Hello all, I am having a pretty serious problem of apache not displaying any of my pages. I can ping the local address fine, as well as ping the url fine.


 I have confirmed that the proces is running.

```
ps ax | grep apache2

6322 ?        Ss     0:00 /usr/sbin/apache2 -k start -DSSL
 6325 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6326 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6327 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6328 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6329 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6382 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6384 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6385 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL
 6433 pts/1    S+     0:00 grep apache2



```

and my apache error log shows this

```
[Tue Aug 28 19:44:34 2007] [error] [client 66.249.72.179] File does not exist: /var/www/robots.txt
[Tue Aug 28 22:16:18 2007] [notice] caught SIGTERM, shutting down
[Tue Aug 28 22:16:19 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Tue Aug 28 22:20:08 2007] [notice] caught SIGTERM, shutting down
[Tue Aug 28 22:21:26 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Tue Aug 28 22:24:06 2007] [notice] caught SIGTERM, shutting down
[Tue Aug 28 22:24:07 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Tue Aug 28 22:24:17 2007] [notice] caught SIGTERM, shutting down
[Tue Aug 28 22:24:25 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Tue Aug 28 22:26:31 2007] [notice] caught SIGTERM, shutting down
[Tue Aug 28 22:26:32 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Tue Aug 28 22:30:41 2007] [notice] caught SIGTERM, shutting down
[Tue Aug 28 22:31:33 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Wed Aug 29 10:03:53 2007] [notice] caught SIGTERM, shutting down
[Wed Aug 29 10:05:12 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Wed Aug 29 10:08:41 2007] [notice] caught SIGTERM, shutting down
[Wed Aug 29 10:08:47 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Wed Aug 29 10:26:03 2007] [notice] caught SIGTERM, shutting down
[Wed Aug 29 10:28:24 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Wed Aug 29 10:39:44 2007] [notice] caught SIGTERM, shutting down
[Wed Aug 29 10:40:20 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations
[Wed Aug 29 10:56:47 2007] [notice] caught SIGTERM, shutting down
[Wed Aug 29 10:56:48 2007] [notice] Apache/2.0.55 (Ubuntu) mod_jk/1.2.14 PHP/5.1.2 configured -- resuming normal operations

```

In addition to that, my tomcat server isn't running also.That leads me to believe whatever is wrong is joining them together, Netstat -a shows that www is listening but not connected no matter what I do I cannot connect.

My FTP and SSH server seem to work fine, This problem is only secluded to the webservers, Any help would be awesome,


Thanks in advance.

---

### Post by Almighty on 2007-08-29
One more thing... The server has been set up and working for quite some time now. I just posted the error log to when it first started to happen.

---

### Post by uncolorcoordinated on 2007-08-29
I'm having a similar problem, though it's a bit more extreme: my FTP and SSH won't work either. 

I tried pinging to the machine and that works fine.

I can see my web page if I browse to [http://localhost](http://localhost) or the machine's IP address directly on the server, but if I try to see the page remotely it won't show up.

I've checked out the error and access logs and I don't see anything blatantly wrong, so I'm stuck and don't know how to proceed. 

Interestingly, the apache2 access logs don't register my attempts to look at the page remotely using the server's IP address, so it must be something wrong with the networking.

I tried netstat -a but www, ftp, and others are listed as LISTENING.

Does anyone have any ideas on how to start resolving this?

Thanks!

---

### Post by Almighty on 2007-08-29
Ok two people have this problem....there has got to be someone on here that could help us out.

This is a poduction machine, and I have people blowing up my inbox.

EDIT: I have just tried to view my FTP over the web and that's a no go I keep getting

" The connection was reset    

The connection to the server was reset while the page was loading."

Error page

---

### Post by reckless2k2 on 2007-08-29
what error do you get when you view the page from another machine on your lan? what does the http page show from that remote machine?

did you install something else recently that's using port 80 now instead of apache2? what's been updated or upgraded recently?

/etc/init.d/apache2 force-reload

---

### Post by reckless2k2 on 2007-08-29
um...are you talking about apache or ftp now?

did you install a firewall or change iptables recently? 

what's your netstat -tap or -nat?

---

### Post by gombadi on 2007-08-29
What do you mean by can't connect?  connection refused, error returned, blank page?

If it is listening but can't connect then firewall?
Have a look at the firewall with this -
```
iptables -vnL
```

You say you can ping the url - clarify please. Does that actually connect to the webserver and log a connection to the access.log file?

You say this is a production machine so it must have been working in the past - so what has changed in the last few hours. Packages updated, conf files changed etc?

Any error in the mod_jk logs or the tomcat logs?

---

### Post by Almighty on 2007-08-29
I haven't installed any other applications other than trying to get a VPN up and running but that was days ago. Why should it be a problem now? I haven't changed my iptables or adjusted my firewall settings , and I update and upgrade once a week to make sure all security and packages are up to date.

I tried the force reload and I still get nothing other than "The connection was reset" from FireFox.

Netstat -tap shows
```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN     4914/mysqld
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     5035/smbd
tcp        0      0 *:5900                  *:*                     LISTEN     5438/vino-server
tcp        0      0 *:sunrpc                *:*                     LISTEN     3766/portmap
tcp        0      0 *:10000                 *:*                     LISTEN     5339/perl
tcp        0      0 *:663                   *:*                     LISTEN     5145/rpc.statd
tcp        0      0 localhost:9050          *:*                     LISTEN     5065/tor
tcp        0      0 *:1723                  *:*                     LISTEN     5019/pptpd
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     5035/smbd
tcp6       0      0 *:www                   *:*                     LISTEN     6893/apache2
tcp6       0      0 *:ftp                   *:*                     LISTEN     5185/proftpd: (acce
tcp6       0      0 *:ssh                   *:*                     LISTEN     5053/sshd
tcp6       0      0 *:1978                  *:*                     LISTEN     5185/proftpd: (acce
tcp6       0      0 http://failhammer.k:ssh crimemachine:2147       ESTABLISHED6808/sshd: duane [p
tcp6       0      0 http://failhammer.k:ssh crimemachine:2019       ESTABLISHED6697/sshd: duane [p

```

and netstat  -nat shows

```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:663             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::80                   :::*                    LISTEN
tcp6       0      0 :::21                   :::*                    LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 :::1978                 :::*                    LISTEN
tcp6       0    264 ::ffff:192.168.1.29:22 ::ffff:192.168.1.31:2147 ESTABLISHED
tcp6       0      0 ::ffff:192.168.1.29:22 ::ffff:192.168.1.31:2019 ESTABLISHED

```

Every things seems to be working.

You guys will have to forgive me if I know nothing about iptables. I run my firewall through a modded linksys router.

When I say I can ping the machine, I can send out an echo request and receive it with no problems. I have tried it using the ip address and the domain name with equal successful results.

I see in the tomcat logs that apache 
```
Aug 29, 2007 10:03:54 AM org.apache.coyote.http11.Http11BaseProtocol pause
INFO: Pausing Coyote HTTP/1.1 on http-8080
Aug 29, 2007 10:03:55 AM org.apache.catalina.core.StandardService stop
INFO: Stopping service Catalina
Aug 29, 2007 10:03:56 AM org.apache.coyote.http11.Http11BaseProtocol destroy
INFO: Stopping Coyote HTTP/1.1 on http-8080
Aug 29, 2007 10:03:56 AM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: Failed shutdown of Apache Portable Runtime
```


I don't really know what to make of it.

I hate being a rookie.

---

### Post by freebeer on 2007-08-29
Ok, but have you forwarded the ports in your router to the server?

---

### Post by Almighty on 2007-08-30
Yes sir I have. As I said, it was a production machine that worked VERY well. I am always singing the praises of Ubuntu and how "simple" it was to get everything up and running. Now it bit be in the you know where.

---

### Post by uncolorcoordinated on 2007-08-30
My problem seems to have fixed itself. The only explanation I have is that last Friday my workplace had a flooding problem and everyone had to scramble to disconnect everything to avoid greater damage. I imagine that whever computer that was acting as a firewall got set up incorrectly when it was restarted again. Yesterday we flooded again, everyone scrambled to disconnect, but when everything got connected again, I could see my server.

Almighty: lesson learned here is that our setup is perfectly fine. My netstat -nat and netstat -tap were very similar to yours and there is nothing in my iptables because the firewalling is handled on another machine. I think that other machine is your problem. Look for whatever might be affecting the connection between your server and the rest of the world, because I'm pretty sure your machine is perfectly fine.

Sorry I can't be of more help... Happy hunting!

---

### Post by reckless2k2 on 2007-08-30
ok almighty..now throw the 000-default at us in /etc/apache2/sites-enabled along with the contents of the director you are trying to serve (/var/www/location/*). 

it should be reading an html, htm, php...etc file in there

also we are still waiting on what the LAN and WAN error page is received. PAGE 404..etc. what is the error or is it blank page? AND.............you got a static IP on the web server?

---

### Post by Almighty on 2007-08-30
I'm stuck at work for the time being so I don't have access to the box right now.

I thought I posted the error page that comes up in a previous post, if I hadn't I appologize. 

All I get from a local or remote machine is 

```
The connection was reset   
        
The connection to the server was reset while the page was loading

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

```

And yes the server has a static IP on my lan.

---

### Post by reckless2k2 on 2007-08-30
did you say something about having apache2 and apache-tomcat on your machine? verify this via synaptic when you get home.

---

### Post by Almighty on 2007-08-30
Yes I have Apache2 and Tomcat 5.5 loaded on the machine, and they both worked until yesterday.

---

### Post by reckless2k2 on 2007-08-30
i'm using simple apache2. you might want to modify your thread so tomcat people can view this. i think this is a tomcat issue. i know sometimes there are specific apache/apache-tomcat issues that i wouldn't be able to help with. i'm sure some tomcat people can chime in on it. it looks as though your apache is fine so i'm banking on it being a tomcat and apache together issue.

---

### Post by Almighty on 2007-08-30
Thanks for the advice so far.

---

### Post by reckless2k2 on 2007-08-30
sorry i couldn't be of more help. i'm notsure why you need tomcat. if you remove it, i think your apache pages would be fine. probably not what you're looking for though.

---

### Post by Almighty on 2007-08-30
Well I use tomcat to run a streaming media server from the site. I think I will try to find another router and see if that will work. I have no other ideas so far.

---

### Post by Almighty on 2007-09-06
Well it looks like the router was at fault. I just ended up reflashing it and reconfiguring the settings. 

Thanks all.

---

