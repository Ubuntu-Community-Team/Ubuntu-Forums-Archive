---
title: "webmin access problem"
date: 2008-03-11
forum: Server Platforms
---

### Post by victordemain on 2008-03-11
I am running webmin-1.400 on ubuntu 7.10 (gutsy), linux kernal 2.6.22-14-generic with GNOME 2.20.1
I am running a local (LAN connected (my connection for the LAN is a NETGEAR router))  -  ubuntu 6.06 LAMP server.
When I try [http://localhost:10000](http://localhost:10000) or [http://mydomain(words](http://mydomain(words) or IP):10000 I get: 
"SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3.2
Protocol mismatch."
I have changed ports to no avail I have used https, I have exhausted all I know (not much as I am new to Linux - but have used posts and Google but cannot find this error message anywhere.
Can anyone point me in the right direction.
What I have seen of linux so far I like - so please help me solve this.
Vic

---

### Post by SpaceTeddy on 2008-03-11
this sounds as if your ssh server is running on port 10000 - why ever that would be the case.

can you please post the ouput of this command:
```
netstat -lnp
```

there should be entries like these in there
```
tcp        0      0 192.168.1.1:10000      0.0.0.0:*               LISTEN     5706/perl           
tcp        0      0 192.168.0.1:10000      0.0.0.0:*               LISTEN     5706/perl   
```

which would mean that webmin (it is basicially perl) is running and listening on the correct port. anything else would be wrong.

PS: i have never seen that error message in a webbrowser, but i know you get that when you telnet into a ssh server to see if it is responding...

---

### Post by victordemain on 2008-03-12
ID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4 543/mysqld
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4 Hi
Output asked for:-
301/cupsd
tcp        0      0 127.0.0.1:50874         0.0.0.0:*               LISTEN     4 247/hpiod
tcp        0      0 127.0.0.1:54654         0.0.0.0:*               LISTEN     4 252/python
tcp6       0      0 :::2222                 :::*                    LISTEN     4 655/sshd
tcp6       0      0 :::80                   :::*                    LISTEN     4 825/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4 655/sshd


My server address at 192.168.0.6 doesn't appear to be there - is that normal(??)
Sorry to be slow getting back only came in 30 mins ago! Been giving Science tuition.
Vic

---

### Post by SpaceTeddy on 2008-03-12
there seems to be nothing listening on port 10000 (as you suggested) and webmin does not seem to be running at all. This rises two questions... 

1.) why is webmin not running
2.) how did that message get in your browser if there is not even something running on the port.

manually check if there is any perl related stuff running with
> sudo ps aux |grep perl

and try to start your webmin server with
> sudo /etc/init.d/webmin start

after the webmin start, check again with netstat if something is listening on the port now. If you are in doubt, paste the output here again :)

---

### Post by victordemain on 2008-03-12
Sorry messed the formatting up somehow
Should be as below-

ID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     4 543/mysqld
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4 301/cupsd
tcp        0      0 127.0.0.1:50874         0.0.0.0:*               LISTEN     4 247/hpiod
tcp        0      0 127.0.0.1:54654         0.0.0.0:*               LISTEN     4 252/python
tcp6       0      0 :::2222                 :::*                    LISTEN     4 655/sshd
tcp6       0      0 :::80                   :::*                    LISTEN     4 825/apache2
tcp6       0      0 :::22                   :::*                    LISTEN     4 655/sshd

---

### Post by vpsville on 2008-03-12
webmin is not running.

try:
sudu /etc/init.d/webmin start

---

### Post by victordemain on 2008-03-16
You are right it had loaded but somehow it was corrupted on the download I assume(?) and obviously wouldn't run.
So I felt the best option was to start all over again with a fresh upload of everything. Lamp server and then webmin - and low and behold it is all working properly now.
Thanks for the advice it set me on the road to finding errors and thinking seriously about how to use linux. It has been a fairly steep learning curve and I look forward to becoming more competent with all the open source stuff.
so again thanks for your input.
Vic De Main

---

