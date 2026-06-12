---
title: "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"
date: 2014-02-17
forum: Server Platforms
---

### Post by LinksED on 2014-02-17
Hi,
Here is my network : 
[IMG]http://img15.hostingpics.net/pics/582890network.jpg[/IMG]
Win 7 can ping 172.11.0.1 and 172.11.0.2.
All is open for IpCop,
on ubuntu server database 'mysql-sever' and 'phpmyadmin (+apache2)' are installed.
on ubuntu server (172.11.0.1) 'apache2 + php 5' are installed. here is the index.php of 172.11.0.1 :
```

<?php 
if(isset($_POST['envoi']))
{
$login = $_POST['login'];
$pass = $_POST['pass'];
print("<center>Bonjour $login</center>");

$base = mysql_connect ('172.11.0.2:3306', 'root', 'Azerty11');
mysql_select_db ('blog', $base) ; 
$sql = 'INSERT INTO users VALUES ("'.$login.'", "'.$pass.'");';
mysql_query ($sql) or die ('Erreur SQL !'.$sql.'<br />'.mysql_error());
mysql_close();
}
?> 

<form method="post">
  Login: <input type="text" name="login"><br>
  Password: <input type="text" name="pass"><br>
  <input type="submit" value="S'inscrire" name="envoi">
</form> 

```

OK, Now on Win 7 : 
[IMG]http://img15.hostingpics.net/pics/938772841.jpg[/IMG]
Click on ' s'incrire ' and 

[IMG]http://img15.hostingpics.net/pics/262477272.jpg[/IMG]

I've look for on google for this probleme but no topic are resolved.
I hope someone here can help me.

Here is the 'my.cnf' of 172.11.0.2: (without commented lines)

```
[client]
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

[mysqld_safe]
socket        = /var/run/mysqld/mysqld.sock
nice        = 0

[mysqld]

user        = mysql
pid-file    = /var/run/mysqld/mysqld.pid
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
lc-messages-dir    = /usr/share/mysql
skip-external-locking

bind-address        = 127.0.0.1
key_buffer        = 16M
max_allowed_packet    = 16M
thread_stack        = 192K
thread_cache_size       = 8

myisam-recover         = BACKUP
ry_cache_limit    = 1M
query_cache_size        = 16M

log_error = /var/log/mysql/error.log

expire_logs_days    = 10
max_binlog_size         = 100M



[mysqldump]
quick
quote-names
max_allowed_packet    = 16M

[mysql]

[isamchk]
key_buffer        = 16M
!includedir /etc/mysql/conf.d/
```

---

### Post by SeijiSensei on 2014-02-17
> ```
bind-address        = 127.0.0.1
```

For security reasons, the MySQL server only listens on the localhost interface by default.  If you want it to listen on the 172 addresses, you'll need to edit my.cnf to permit the server to bind to all addresses.  I think commenting out the bind-address directive is sufficient.

By the way, I hope you realize that 172.10/16 is not a private address.  The [official private class B]("https://tools.ietf.org/html/rfc1918") ranges from 172.16 to 172.31.  According to ARIN, a portion of 172.10 is [assigned](http://whois.arin.net/rest/net/NET-172-10-0-0-1/pft) to "GREGORY HOUT ATTORNEY AT LAW-121022160830 (C03187314)."  There's no specific allocation for 172.11, but the entire space from 172.0 to 172.15 is [assigned](http://whois.arin.net/rest/net/NET-172-0-0-0-1/pft) to AT&T.

---

### Post by LinksED on 2014-02-17
Thanks for your reply, I'have add a '#' before bind-address, restart mysql, but the error message is again here :(
(thanks for the Ips I will change it ! )

---

### Post by SeijiSensei on 2014-02-17
Follow the instructions [here](http://social.technet.microsoft.com/wiki/contents/articles/910.enabling-telnet-client-in-windows-7.aspx) to install the telnet client for Windows.  Then run the command "telnet server_ip 3306" and see whether the server replies.  If not, there's a connectivity issue of some kind.  Are all the routes correct?  Are you masquerading traffic on the ipcop device?  How about packet forwarding (see /etc/sysctl.conf for details)?  Are all the firewalling rules correct to allow connections to the MySQL port?

---

### Post by LinksED on 2014-02-18
Ok, with telnet -> 172.11.0.2 3306 -> connection error, i place win 7 in 172.11.x.x network, fail agin with telnet.
/etc/systcl.conf all lines are commented.

```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#


```

How to veiw and modify firewall setting ?

---

### Post by SeijiSensei on 2014-02-18
On the machine running ipcop, you must uncomment the line in /etc/sysctl.conf that reads:
```
#net.ipv4.ip_forward=1
```
For security reasons, the default is not to forward traffic between interfaces.  That basically disables any router.  Change that entry and reboot the ipcop machine.  Any better?

---

### Post by LinksED on 2014-02-21
/etc/sysctl.conf do not exist on Ipcop : [IMG]http://img4.hostingpics.net/pics/229882Sanstitre2.png[/IMG]

---

### Post by LinksED on 2014-02-21
ok, problem solved: 
it just enough to create a user 'root' with '%' as a client in phpmyadmin : [IMG]http://img4.hostingpics.net/pics/503793Sanstitre2.png[/IMG]

---

