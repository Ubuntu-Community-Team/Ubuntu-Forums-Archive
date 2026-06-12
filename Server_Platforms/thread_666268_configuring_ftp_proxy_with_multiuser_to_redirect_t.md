---
title: "configuring ftp proxy with multiuser to redirect to single user ftp-server"
date: 2008-01-13
forum: Server Platforms
---

### Post by Smind on 2008-01-13
Hi to all!

this is my situation:
a workgroup that have to access as root to an ftp server outside lan.
This ftp server have only one user root, and i need to log user activity.

So i thinked, a ftp-proxy!
I should install a ftp-proxy that redirect lan user to ftp server as root.
I need, if it is possible, a ftp-proxy with mysql auth, that connect to remote ftp server as root and accept only user in mysql database.

then when i connet to lanuser:lanuserpass@ftp.lanproxy.com if auth succes ti redirect to root:rootpass@ftp.remoteserver.com

Any solution?

---

### Post by HermanAB on 2008-01-13
Uhmm, if the FTP server is running on *nix, then activity will already be logged in /var/log/messages, /var/log/secure or something else.  So just scan the log files.

Cheers,

Herman

---

### Post by Smind on 2008-01-14
the ftp server is not inside the lan,
i'm not the owner of this server, i've only simil-root access.

i'm searching something that bounce a local domain like ftp.loacal.lan to ftp.remote.com, and i need to manage users access and logs.

but the local bouncer must connect to root to remote server.

multi user to single user !!!

help!

---

### Post by HermanAB on 2008-01-14
Hmm, that is not a trivial matter at all.  The problem is that FTP occurs in two phases:  First it sets up a control channel, then it switches to a data channel on a random high port.  The protocol actually reverses and the client becomes the server for the data transfer.  This is what makes FTP servers so efficient - they reverse the most intensive work load back onto the clients.  So a FTP proxy is not a simple thing.

So, the only way I can think of doing what you want to do is with tcpdump piped into grep, or with ngrep.  That is, by sniffing the network packets.

Cheers,

Herman

---

### Post by Smind on 2008-01-14
ok, any how to or some else?

i don't konw any of your solution :D

---

### Post by Smind on 2008-01-15
The solution? mount the remote ftp as partition and install pure-ftpd that punt it's root to this drive :D

the solution here [http://forum.smokinglinux.com/configuring-ftp-proxy-t2080.html?p=29030&posted=1#post29030](http://forum.smokinglinux.com/configuring-ftp-proxy-t2080.html?p=29030&posted=1#post29030)
thanks to crashlab

---

