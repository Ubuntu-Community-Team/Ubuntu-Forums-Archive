---
title: "FTP server issue"
date: 2006-02-03
forum: Server Platforms
---

### Post by shawnzyoo on 2006-02-03
well I have success with my FTP server! <proftp>
I can access it from with my own LAN
but
I would like to be able to access it from outside my LAN
i set up my LInksys router to port forward 20 to 21
and when i venture to my site i am prompted for my username/password
which I then enter and nothing happens
I know FTP runs on two ports
I just don't think my router is forwarding them both correctly
does anyone here have any experience/suggestions on this topic?
is it a basic router issue or a Linksys specific issue?
Thanks for any help

---

### Post by Syirrus on 2006-02-03
It sounds like you have set everything up properly if you can access username / password screen from outside of your LAN.  It seem that you may need to configure your FTPD to authenicate you as a user. I use vsftpd and I'm not familar with how to setup access to proftpd.  If you use webmin, I'm sure they have modules with proftpd which will make it a breeze to configure.

btw, if you are looking for speed and reliability in a FTPD, vsftpd is very very fast and reliable. 
Syirrus

---

### Post by shawnzyoo on 2006-02-03
when i try going to my localhost
it logs in just fine is the only thing
so i would think my user is workingn allright

---

### Post by feelmjawlk on 2006-02-03
I have also problems getting my ftp server to work. If I telnet port 21 from a computer connected to my LAN I'm greeted with :

```

bjorn@dumburken:~$ telnet 192.168.0.115 21
Trying 192.168.0.115...
Connected to 192.168.0.115.
Escape character is '^]'.
220 ProFTPD 1.2.10 Server (FTP server) [192.168.0.115]

```

If I telnet port 22 I get:
```

bjorn@dumburken:~$ telnet 192.168.0.115 22
Trying 192.168.0.115...
Connected to 192.168.0.115.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.1p1 Debian-7ubuntu4
Connection closed by foreign host.

```

If I ask a friend to telnet port 22 from the internet he connects just fine. But if I ask him to telnet port 21 the connection is timed out. My router is set up to forward port 20, 21, 22 to my ftp-server. And the ports are opened, yet the connection is refused. It feels like the solution should be in /etc/proftpd.conf but have not found any settings for which ip-ranges to accept incoming connections from. Any help would be greatly appreciated!

---

### Post by Smandola on 2006-02-03
Hi Everyone,
I'm not an expert, but I have been experiencing the same problem.  I am running PROFTPD, and I can connect to my ftp server using the 192.168.1.X or localhost, with no problem.  However when I attempt to connect from outside (using my isp IP), I can not. 

I found out that if you are on your own network, and you try to go out of your network, and loop back into it, its likely that your router is not capable of doing the loop back.  

I know that sounds confusing, so as an example: if you are on a pc (IP 192.168.1.100), and your FTP Server (IP 192.168.1.50).  Now say that you have your router configured to allow Port 21 open and is routed to 192.168.1.50 (your FTP Server).  From your pc (192.168.1.100), If you FTP to 192.168.1.50, you should have no problems.  Now lets say you use your external ip (external IP of your router, that your ISP provides - either static or dynamic (not the 192.168.1.X)).  This likely won't work do to what is called a loop back at the router level. 

If you go to your friends/neighbors/work network, and try to connect to your FTP Server (using your isp ip) its likely you will be able to connect.  The reason is because you aren't looping back on your own router.  

I think that there may be some testing tools out there that try to access your FTP server from outside your network, while you are still locally connected.

I know this sounds really confusing.  If I find a thread that can explain this better I'll attach it in another post.  

Hope this helps.
r.

---

### Post by feelmjawlk on 2006-02-04
Thank you smandola for helping out but as I said:
 
> If I ask a friend to telnet port 22 from the internet he connects just fine. But if I ask him to telnet port 21 the connection is timed out.

That friend connects my ISP-ip through the internet. I am fully aware that I can not connect to my own internet-ip address.

EDIT: Update: shields up at [http://www.grc.com/](http://www.grc.com/) reports that my port 21 is stealth. Whatever that is supposed to mean?

EDIT: The "Stealth"-port led me to the conclusion that it was my router that was not properly configured. I found an application support option for ftp-server. Ah well.. sometimes the answer is sitting right in front of you.

---

