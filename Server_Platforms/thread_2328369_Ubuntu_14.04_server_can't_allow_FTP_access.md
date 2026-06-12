---
title: "Ubuntu 14.04 server can't allow FTP access"
date: 2016-06-20
forum: Server Platforms
---

### Post by chimiqua on 2016-06-20
[COLOR=#333333]Hi all, [/COLOR]
[COLOR=#333333]I recently set up a server with ufw firewall.[/COLOR]

[COLOR=#333333]I have added a rule to allow port 21 access so Wordpress can install plugins.  [/COLOR]

[COLOR=#333333]I used sudo ufw allow 21[/COLOR]
[COLOR=#333333]sudo ufw allow 21/tcp [/COLOR]
[COLOR=#333333]and also sudo ufw allow proto tcp from any to any port 80[/COLOR]

[COLOR=#333333]I have then used sudo ufw disable/enable to stopt/start it.[/COLOR]

[COLOR=#333333]I have then also restarted the server.[/COLOR]

[COLOR=#333333]For some strange reason it still does not allow FTP.

 I have tried using FileZilla and putty. In putty i get a time out error and in FileZilla I get Connection attempt failed with "ECONNREFUSED - Connection refused by server".

[/COLOR][COLOR=#333333]Out put of ufw status so you can see [/COLOR]

[COLOR=#333333]yet2learn@Yet2Learn:~$ sudo ufw status[/COLOR]
[COLOR=#333333]Status: active[/COLOR]

[COLOR=#333333]To Action From[/COLOR]
[COLOR=#333333]-- ------ ----[/COLOR]
[COLOR=#333333]22 ALLOW Anywhere[/COLOR]
[COLOR=#333333]4444/tcp ALLOW Anywhere[/COLOR]
[COLOR=#333333]80/tcp ALLOW Anywhere[/COLOR]
[COLOR=#333333]443/tcp ALLOW Anywhere[/COLOR]
[COLOR=#333333]25/tcp ALLOW Anywhere[/COLOR]
[COLOR=#333333]21/tcp ALLOW Anywhere[/COLOR]
[COLOR=#333333]22 (v6) ALLOW Anywhere (v6)[/COLOR]
[COLOR=#333333]4444/tcp (v6) ALLOW Anywhere (v6)[/COLOR]
[COLOR=#333333]80/tcp (v6) ALLOW Anywhere (v6)[/COLOR]
[COLOR=#333333]443/tcp (v6) ALLOW Anywhere (v6)[/COLOR]
[COLOR=#333333]25/tcp (v6) ALLOW Anywhere (v6)[/COLOR]
[COLOR=#333333]21/tcp (v6) ALLOW Anywhere (v6)[/COLOR]

[COLOR=#333333]any ideas what I am doing wrong?[/COLOR]

---

### Post by LHammonds on 2016-06-20
You need to allow SSH (PuTTY) access from your PC.

Let's say your local LAN is 192.168.0.x, this is how you would configure the firewall to allow SSH from any PC on your LAN:

```
sudo ufw allow from 192.168.0.0/24 to any port 22
```

To allow FTP/SFTP from anywhere:

```

sudo ufw allow proto tcp to any port 21
sudo ufw allow proto tcp to any port 990

```

**EDIT:** Whoops, I noticed your ufw status output a bit late.  Try temporarily disabling your firewall to ensure the problem is the firewall blocking access to services.

---

### Post by TheFu on 2016-06-20
FTP uses more than 1 port for higher performance, unless you configure *passive ftp*. There is the control port and the dynamic, data, port. The firewall needs to be dynamically controlled if active FTP is configured.

[https://www.wordfence.com/learn/how-to-harden-wordpress-sites/](https://www.wordfence.com/learn/how-to-harden-wordpress-sites/) for a little related content.  They suggest using sftp and NOT plain FTP.  That is much easier to secure, since sftp, scp, and ssh all work over the same port which can be configured.  Plus there are tools to recogniae brute force attacks and block those sources as needed.  Securing ssh is a well-traveled path.

---

