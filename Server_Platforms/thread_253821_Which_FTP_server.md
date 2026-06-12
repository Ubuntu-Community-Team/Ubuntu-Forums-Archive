---
title: "Which FTP server?"
date: 2006-09-08
forum: Server Platforms
---

### Post by BrendanP on 2006-09-08
Hi,

I'm on about my 3rd day of having Ubuntu installed, and so far I am quite impressed. I'm quickly getting the hang of things.

The main reason I installed Ubuntu (on my old PC) is to play around with the web server. (I do a lot of personal web development stuff so I already have Apache running on my XP laptop).

I've managed to succesfully set up Apache and PHP to do the [http://myserver/~user](http://myserver/~user) thing to direct to /home/user/public_html. Now I want to set up FTP to do the same (ie. you log in as a certain user and it shows ONLY that user's home directory and lets me upload to that user's public_html folder).

Which FTP software is the best for doing this? I've seen several mentioned on these forums and I've played around with several of them but I can't get any of them to work as desired.

I'm only using this server for myself (ie. on my LAN, which is behind a router... so no outside access). Remember I'm realtively new at the whole Linux thing.

Thanks in advance for your suggestions and recommendations.

- Brendan

---

### Post by BrendanP on 2006-09-08
Oh, one more slight issue... I can't access the web server from my XP machine using [http://hostname/](http://hostname/) (using the IP address works fine).

I could fix it using the HOSTS file in windows, but it should just work, right?

Also, can I get it to do something like [http://user.hostname/](http://user.hostname/) instead of [http://hostname/~user/](http://hostname/~user/) ? (This is not vital but it would be cool).

---

### Post by erland on 2006-09-09
> **BrendanP said:**
> Which FTP software is the best for doing this? I've seen several mentioned on these forums and I've played around with several of them but I can't get any of them to work as desired.

I'm only using this server for myself (ie. on my LAN, which is behind a router... so no outside access). Remember I'm realtively new at the whole Linux thing.

I have successfully been using vsftpd, but I am not sure its the best.
Here is the how I choose to set it up, this also makes it safer to open for outside access if you like.
[http://blog.erland.homeip.net/?p=57](http://blog.erland.homeip.net/?p=57)

> **BrendanP said:**
> Oh, one more slight issue... I can't access the web server from my XP machine using [http://hostname/](http://hostname/) (using the IP address works fine).

To be able to access your linux machine from Windows with hostname you will need to install samba on your linux machine. (I set it up according to [http://blog.erland.homeip.net/?p=55](http://blog.erland.homeip.net/?p=55))

To be able to access tour Windows machine from linux with hostname you will need to install winbind on your linux machine. (I set it up according to  [http://blog.erland.homeip.net/?p=56](http://blog.erland.homeip.net/?p=56))

> **BrendanP said:**
> 
Also, can I get it to do something like [http://user.hostname/](http://user.hostname/) instead of [http://hostname/~user/](http://hostname/~user/) ? (This is not vital but it would be cool).I'm not sure you can do this without hard coding each username in your apache settings. The way to do this is to define virtual hosts for each user in the apache configuration.

---

### Post by BrendanP on 2006-09-09
Thanks for your response. I'll check out those links and see what I can do.

---

### Post by BrendanP on 2006-09-09
erland, I installed vsftpd as per your link. Using SmartFTP on Windows to connect, I get the following messages:

[18:58:51] SmartFTP v2.0.997.4
[18:58:54] Resolving host name "192.168.0.100"
[18:58:55] Connecting to 192.168.0.100 Port: 21
[18:58:58] Connected to 192.168.0.100.
[COLOR="Red"][18:58:58] 500 OOPS: vsftpd: missing argv[0][/COLOR]
[18:58:58] Cannot login waiting to retry (30s)...
[18:58:58] Server closed connection

---

### Post by rastilin on 2006-09-09
Personally I use pure-ftpd when I need to run a server. It chroots into a username's "/home/###" directory when someone logs in as that user and also supports anonymous connections to "/home/ftp" althugh I'm not sure that's enabled by default in Ubuntu.

---

### Post by chrisfay on 2006-09-09
> I could fix it using the HOSTS file in windows, but it should just work, right?

Also, can I get it to do something like [http://user.hostname/](http://user.hostname/) instead of [http://hostname/~user/](http://hostname/~user/) ? (This is not vital but it would be cool).

Is there a reason you don't want to add the hostnames in the hosts file? Have you checked the entries in your /windows/system32/drivers/etc/lmhosts file? This file contains the mappings of IP addresses to computernames (NetBIOS) names.

To reach computers on your lan all you need to do is add something like this in your /etc/hosts file:
IP  sub.do.main

You're other option is to install bind on the Ubuntu box and add hostnames that way. If you only need to add a few, its much easier to just add them in the hosts file rather than configuring all your computers to use bind.

---

### Post by erland on 2006-09-09
> **BrendanP said:**
> erland, I installed vsftpd as per your link. Using SmartFTP on Windows to connect, I get the following messages:

[18:58:51] SmartFTP v2.0.997.4
[18:58:54] Resolving host name "192.168.0.100"
[18:58:55] Connecting to 192.168.0.100 Port: 21
[18:58:58] Connected to 192.168.0.100.
[COLOR="Red"][18:58:58] 500 OOPS: vsftpd: missing argv[0][/COLOR]
[18:58:58] Cannot login waiting to retry (30s)...
[18:58:58] Server closed connection

Sorry, I have not seen that error before. It has always worked right out of the box for me following that procedure. 
Are you able to connect by opening a command prompt(DOS-window) and just enter "ftp 192.168.0.100" ?

---

### Post by BrendanP on 2006-09-09
> **erland said:**
> Sorry, I have not seen that error before. It has always worked right out of the box for me following that procedure. 
Are you able to connect by opening a command prompt(DOS-window) and just enter "ftp 192.168.0.100" ?
Same message.

C:\Documents and Settings\Brendan>ftp 192.168.0.100
Connected to 192.168.0.100.
500 OOPS: vsftpd: missing argv[0]
Connection closed by remote host.

I'll try pure-ftpd and see if I can get it configured.


As for the other things (samba and winbind), I got them both working properly.

---

### Post by BrendanP on 2006-09-09
> **chrisfay said:**
> Is there a reason you don't want to add the hostnames in the hosts file? Have you checked the entries in your /windows/system32/drivers/etc/lmhosts file? This file contains the mappings of IP addresses to computernames (NetBIOS) names.

To reach computers on your lan all you need to do is add something like this in your /etc/hosts file:
IP  sub.do.main

You're other option is to install bind on the Ubuntu box and add hostnames that way. If you only need to add a few, its much easier to just add them in the hosts file rather than configuring all your computers to use bind.
Nope, I just like to make things difficult :P

I just thought there'd be another way to do it. As I said, the whole reason I installed Ubuntu on my old computer (which has been sitting around for the past 9 months gathering dust) is simply to play around.

---

### Post by garyfreder on 2006-09-09
Howdy,

I installed the LAMP version of the server way over 10 minutes ago, so I know uhhh - almost nothing ;-)

but that should never slow someone down from giving an opinion.

You said you are using the server to do personal web development. Have you looked at what WebDAV in apache can do for you? We have it on our apache web server on both XP and on Fedora. My family finds it useful, we can edit a simple html page and put it on the server using Nvu etc.

I am starting to configure my brand new Ubuntu server that will be visible to the world (oh no) and was thinking of keeping ftp off.

Just a comment.

Gary

---

### Post by BrendanP on 2006-09-09
I have file sharing between the two computers working now with Samba, so I can just transfer files that way.

Thanks for your suggestion though, I'll look into it...

---

### Post by garyfreder on 2006-09-11
Look at WebDAV. We like it a lot better than ftp.

---

### Post by atrophic on 2006-09-13
> **BrendanP said:**
> Also, can I get it to do something like [http://user.hostname/](http://user.hostname/) instead of [http://hostname/~user/](http://hostname/~user/) ? (This is not vital but it would be cool).

assuming hostname will resolve to the computer (or a (sub)domain name is attached to it, you can use mod_rewrite to redirect the URLs

---

