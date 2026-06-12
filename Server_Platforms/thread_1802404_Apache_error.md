---
title: "Apache error:"
date: 2011-07-11
forum: Server Platforms
---

### Post by blesshy on 2011-07-11
I use ubuntu 8.04 and apache version 2.2.8.
I installed dekiwiki.
 
When I try to start apache2, the computer return this error messange.
 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
 
 
I already check /etc/hosts and /etc/apache2/sites-enabled/dekiwiki
 
 
In /etc/hosts
 
127.0.0.1 localhost
127.0.0.1 __domain.address.com__
127.0.0.1 __servername__
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
 
 
 
 
In /etc/apache2/sites-enabled/dekiwiki
 
<VirtualHost *>
ServerName _my_server_name_
#ServerAlias
....
 
 
 
 
The result of ""netstat -anp | grep '^tcp.*LISTEN'"" is like that.
 
tcp 0 0 0.0.0.0:3690 0.0.0.0:* LISTEN 5253/svnserve
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN 4857/mysqld
tcp 0 0 0.0.0.0:19150 0.0.0.0:* LISTEN 5288/gkrellmd
tcp 0 0 0.0.0.0:80 0.0.0.0:* LISTEN 5499/apache2
tcp 0 0 0.0.0.0:8081 0.0.0.0:* LISTEN 4942/mono
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 4779/cupsd
tcp 0 0 127.0.0.1:25 0.0.0.0:* LISTEN 5204/exim4
tcp 0 0 0.0.0.0:443 0.0.0.0:* LISTEN 5499/apache2
tcp6 0 0 :::19150 :::* LISTEN 5288/gkrellmd
tcp6 0 0 :::22 :::* LISTEN 4707/sshd
 
 
Then What can I do fix my apache server?

---

### Post by pqwoerituytrueiwoq on 2011-07-11
> In /etc/apache2/sites-enabled/dekiwiki
 
<VirtualHost *>
ServerName _my_server_name_

do this
In /etc/apache2/sites-enabled/dekiwiki
 ServerName _my_server_name_
<VirtualHost *>

---

### Post by blesshy on 2011-07-11
> **pqwoerituytrueiwoq said:**
> do this
In /etc/apache2/sites-enabled/dekiwiki
ServerName _my_server_name_
<VirtualHost *>
 
 
Thanks.
 
An error, "apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName", is removed.
 
But there are still errers.
 
==================
Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
==================

---

### Post by lisati on 2011-07-11
*Thread moved to **Server Platforms**.*

Could you copy and paste some of the error messages please.

---

### Post by blesshy on 2011-07-12
> **lisati said:**
> *Thread moved to **Server Platforms**.*
 
Could you copy and paste some of the error messages please.
 
 
This is all what I recieved when I restart apache2
 
[Tue Jul 12 15:57:47 2011] [warn] The Alias directive in /etc/apache2/mods-enabled/alias.conf at line 15 will probably never match because it overlaps an earlier Alias.
httpd (no pid file) not running
[Tue Jul 12 15:57:57 2011] [warn] module alias_module is already loaded, skipping
[Tue Jul 12 15:57:57 2011] [warn] module auth_basic_module is already loaded, skipping
[Tue Jul 12 15:57:57 2011] [warn] module authn_file_module is already loaded, skipping
[Tue Jul 12 15:57:57 2011] [warn] module dav_module is already loaded, skipping
[Tue Jul 12 15:57:57 2011] [warn] module dav_svn_module is already loaded, skipping
[Tue Jul 12 15:57:57 2011] [warn] The Alias directive in /etc/apache2/mods-enabled/alias.conf at line 15 will probably never match because it overlaps an earlier Alias.
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by SeijiSensei on 2011-07-12
Is the machine running a firewall (iptables, for instance)?  Is port 80 open?  I've gotten the "cannot bind" error when my iptables rules inadvertently blocked port 80.

---

### Post by Wim Sturkenboom on 2011-07-12
blesshy,sounds to me that you have parts of your configuration double

---

### Post by bharatj on 2011-09-14
> **blesshy said:**
> I use ubuntu 8.04 and apache version 2.2.8.
I installed dekiwiki.
 
When I try to start apache2, the computer return this error messange.
 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
 
 
I already check /etc/hosts and /etc/apache2/sites-enabled/dekiwiki
 
 
In /etc/hosts
 
127.0.0.1 localhost
127.0.0.1 __domain.address.com__
127.0.0.1 __servername__
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
 
 
 
 
In /etc/apache2/sites-enabled/dekiwiki
 
<VirtualHost *>
ServerName _my_server_name_
#ServerAlias
....
 
 
 
 
The result of ""netstat -anp | grep '^tcp.*LISTEN'"" is like that.
 
tcp 0 0 0.0.0.0:3690 0.0.0.0:* LISTEN 5253/svnserve
tcp 0 0 127.0.0.1:3306 0.0.0.0:* LISTEN 4857/mysqld
tcp 0 0 0.0.0.0:19150 0.0.0.0:* LISTEN 5288/gkrellmd
tcp 0 0 0.0.0.0:80 0.0.0.0:* LISTEN 5499/apache2
tcp 0 0 0.0.0.0:8081 0.0.0.0:* LISTEN 4942/mono
tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 4779/cupsd
tcp 0 0 127.0.0.1:25 0.0.0.0:* LISTEN 5204/exim4
tcp 0 0 0.0.0.0:443 0.0.0.0:* LISTEN 5499/apache2
tcp6 0 0 :::19150 :::* LISTEN 5288/gkrellmd
tcp6 0 0 :::22 :::* LISTEN 4707/sshd
 
 
Then What can I do fix my apache server?


It means some other process is using that port. So try to stop httpd or dhttpd , then start apache2 again.
--> sudo /etc/init.d/apache2 stop
--> sudo /etc/init.d/httpd (or dhttpd) stop
--> sudo /etc/init.d/apache2 start

Then in browser write 
http//:localhost:80/

Now it should work ..

---

