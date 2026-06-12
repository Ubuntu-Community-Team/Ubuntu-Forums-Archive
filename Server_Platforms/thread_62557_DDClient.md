---
title: "DDClient"
date: 2005-09-05
forum: Server Platforms
---

### Post by coxc24 on 2005-09-05
I have just installed the server install of Ubuntu on an old workstation. I intend to use it for FTP, maybe a Web page and eventually a torrent tracker (for legitmate files only).

I have used apt-get install ddclient and it ran without any issues. But now when I try to ssh to my DynDns url, I cannot login to the server. Putty shows the IP of my server on the network so I know its not the router blocking the request.

I had no problems when I used DDClient on my Debian server and the only thing I can think may cause this is if a Firewall is installed on the Ubuntu install by default?

Any help would be appreciated.

---

### Post by Lofticus on 2005-12-02
This answer comes a bit late, but there are few things you have to configure.

First, you should open the needed ports in your router (thats port 80 for http and port 22 for ssh/scp, I don't know whats the port for ftp, but that shouldn't be hard to google).

Second, if you want to ssh/scp to your computer ssh needs to be installed (not installed per default, don't know why) or apache for a web server (dont forget to open the ports!)

And then your /etc/ddclient.conf should look like this:
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=checkip.dyndns.org/, web-skip='IP Address'
server=members.dyndns.org
login=myloginname
password=mypassword
myhost.dyndns(for example).org

that should do the trick

---

