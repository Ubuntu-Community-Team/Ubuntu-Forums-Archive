---
title: "setup question"
date: 2008-05-31
forum: Server Platforms
---

### Post by ItsGambit on 2008-05-31
Hello, 
 I have an Ubuntu Server 8.04 LAMP set up on my machine at home. I set it up using this guide “The Perfect Server - Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)”1 All was installed fine and it is all working. The only problem I have is that ISPconfig is giving me the “Shared IP” error page. But weirdly not after a reboot, only when I make changes to the site like add a database to the site then I will get the “Shared IP” Error. This machine is or internal use only it will NOT be on the open web. I am new to Linux Server edition I have been using the desktop edition of Ubuntu since 6 LTS. 

So my questions are: 
a)	How can I fix my problem with ISPconfig? 
b)	Is there a way that I can have just a LAMP server up and running and be able to test sites on it without using ISPconfig? 

/etc/apache2/vhosts/Vhost_ispconfig.conf
> 
 ###################################
#
# ISPConfig vHost Configuration File
#         Version 1.0
#
###################################
#
NameVirtualHost 192.168.0.22:80
<VirtualHost 192.168.0.22:80>
  ServerName localhost
  ServerAdmin root@localhost
  DocumentRoot /var/www/sharedip
</VirtualHost>
#
#
######################################
# Vhost: [www.itsgambit.myvnc.com:80](www.itsgambit.myvnc.com:80)
######################################
#
#
<VirtualHost 192.168.0.22:80>
ServerName [www.itsgambit.myvnc.com:80](www.itsgambit.myvnc.com:80)
ServerAdmin [email]webmaster@itsgambit.myvnc.com[/email]
DocumentRoot /var/www/web3/web
DirectoryIndex index.html index.htm index.php index.php5 index.php4 index.php3 index.shtml index.cgi index.pl index.jsp Default.htm default.htm
Alias  /cgi-bin/ /var/www/web3/cgi-bin/
AddHandler cgi-script .cgi
AddHandler cgi-script .pl
ErrorLog /var/www/web3/log/error.log
AddType application/x-httpd-php .php .php3 .php4 .php5
<Files *.php>
    SetOutputFilter PHP
    SetInputFilter PHP
</Files>
<Files *.php3>
    SetOutputFilter PHP
    SetInputFilter PHP
</Files>
<Files *.php4>
    SetOutputFilter PHP
    SetInputFilter PHP
</Files>
<Files *.php5>
    SetOutputFilter PHP
    SetInputFilter PHP
</Files>
php_admin_flag safe_mode Off
<IfModule mod_ruby.c>
  <Directory /var/www/web3/web>
    Options +ExecCGI
  </Directory>
  RubyRequire apache/ruby-run
  #RubySafeLevel 0
  <Files *.rb>
    SetHandler ruby-object
    RubyHandler Apache::RubyRun.instance
  </Files>
  <Files *.rbx>
    SetHandler ruby-object
    RubyHandler Apache::RubyRun.instance
  </Files>
</IfModule>
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
AddType application/vnd.wap.wmlscriptc .wmlsc .wsc
AddType text/vnd.wap.wml .wml
AddType text/vnd.wap.wmlscript .ws .wmlscript
AddType image/vnd.wap.wbmp .wbmp
Alias /error/ "/var/www/web3/web/error/"
ErrorDocument 400 /error/invalidSyntax.html
ErrorDocument 401 /error/authorizationRequired.html
ErrorDocument 403 /error/forbidden.html
ErrorDocument 404 /error/error_404.html
ErrorDocument 405 /error/methodNotAllowed.html
ErrorDocument 500 /error/internalServerError.html
ErrorDocument 503 /error/overloaded.html
AliasMatch ^/~([^/]+)(/(.*))? /var/www/web3/user/$1/web/$3
AliasMatch ^/users/([^/]+)(/(.*))? /var/www/web3/user/$1/web/$3
</VirtualHost>
#
#


ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:03:47:c0:03                                          :ce
          inet addr:192.168.0.22  Bcast:192.168.0.                                          255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fec0:3ce/64 Sco                                          pe:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500                                            Metric:1
          RX packets:4452 errors:0 dropped:0 overrun                                          s:0 frame:0
          TX packets:4777 errors:0 dropped:0 overrun                                          s:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:558641 (545.5 KB)  TX bytes:11801                                          97 (1.1 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:925 errors:0 dropped:0 overruns                                          :0 frame:0
          TX packets:925 errors:0 dropped:0 overruns                                          :0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:58488 (57.1 KB)  TX bytes:58488 (                                          57.1 KB)

itsgambit@firefly:/etc/apache2/vhosts$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:c0:03:ce
          inet addr:192.168.0.22  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fec0:3ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:559275 (546.1 KB)  TX bytes:1181899 (1.1 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:58488 (57.1 KB)  TX bytes:58488 (57.1 KB)


---

### Post by volkswagner on 2008-05-31
If the problem only happens when making changes such as to mysql, you may need to restart mysql not the machine.  If you make changes to config files you may need to restart the related service.

If you list the files in /etc/init.d you will see all the proper names for restarting using the following.

```
sudo /etc/init.d/networking restart
```

Replace "networking" with the appropriate and restart can be replaced with "stop or start"

---

### Post by windependence on 2008-05-31
You could also add /etc/init.d to your path and then you could just type:

```
networking restart

```

-Tim

---

### Post by ItsGambit on 2008-05-31
I tried restarting networking and it did not help I made another database to test... 

anything else I can try... 

Thanks in advance..

---

