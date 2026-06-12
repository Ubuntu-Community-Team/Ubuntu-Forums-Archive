---
title: "PHPMYSQL remote connection"
date: 2007-02-15
forum: Server Platforms
---

### Post by chipyoung on 2007-02-15
Sorry about the title line, I meant phpmyadmin.

I have searched the forum and googled around to try to find out if I can connect my Dapper desktop to my lamp webserver mysql database using phpmyadmin.  I currently test my web sites on my desktop (Dapper) which uses php and mysql database.  I like using phpmyadmin for this.  On my webserver I'm limited to the terminal window for database work.  This is not terrible but I would like to connect to this server from my desktop and use phpmysql.

Any help would be greatly appreciated,
Chip

---

### Post by jtc on 2007-02-15
Any particular reason why you can't simply install phpmyadmin at your server?

---

### Post by Brazen on 2007-02-15
Wait, so phpmyadmin is installed on your webserver?  You should be able to connect to the phpmyadmin webpage from your desktop.

Either you didn't describe your problem accurately, or I am not seeing what the problem is.

Is the database installed on the same server as the webserver (a big no-no, but it does work and is often done)?  Do all these computers use Ubuntu?  Do they all use some form of linux?  Need more info.

---

### Post by chipyoung on 2007-02-16
Sorry guys if I was lacking of information on my setup.

After the two of you replied, the light bulb finally came on.  All I need to do is install PHPMYADMIN on the web server, which is ubuntu 6.06 alternate version, my desktop is dapper.  For some reason...Only the DAAAA gods know, I assumed that I would need a gui installed on the web server to make this work, I guess I'm still thinking 'application' rather than jus a PHP web page.

Brazen, you did mention that having mysql installed on the webserver is a no no.  Is there anything I can do to protect my webserver with the database on it.  Also, are there any other securtiy concerns with installing PHPMYADMIN on the same server?

Thanks again,
Chip

---

### Post by Brazen on 2007-02-16
mmm... I've given big long explanations on this before, but I'm too tired so I'm going to be succint :).

For security, the problem is, if someone manages to hack into your webserver, they have now hacked into your database server by default, and vice-versa.

The biggest issues I have seen myself though, involve expansion and troubleshooting.  What happens when you need more performance and have to move to new hardware?  Instead of just moving one application (fairly simple) you have to move 2 or 4 or 5 or however many you end up putting on that one box.

What if something goes wrong?  Sometimes it may not be clear if what application is hosing your computer.  One application could be hanging your computer or causing it crash periodically, and it will not be clear which one.  If you need to reinstall your server, you now have to reinstall EVERYTHING.

In the past, especially for a home/play/testing server, installing everything was often the best option.  But now with VMWare Server, there is very little reason not to break things up into multiple virtual machines.  For instance, at home I have a Celeron 500mhz system with 512 MB ram.  I installed Ubuntu 6.06 server with nothing else but VMWare Server on it.  I create 3 virtual machine: 1 with 64 mb ram for a Samba file server, 1 with 64 mb ram for a MySQL database server, and one with 192 mb ram for an Apache web server hosting torrentflux and phpmyadmin.

---

### Post by chipyoung on 2007-02-17
Thank you Brazen for your time and reply.

Now you have me thinking about the vmware.  I didn't find it as a ubuntu package but I did find it at there site.

Again, thank you.

Chip

---

### Post by jtc on 2007-02-17
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

