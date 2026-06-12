---
title: "How to configure virtualhost on second ip"
date: 2014-03-27
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-03-27
I have a server with 2 ip addresses and I am trying to configure some websites to be on the second ip address.
At the moment when I restart apache I get

root@677689jkh:~# service apache2 restart
 * Restarting web server apache2                                                                              [Thu Mar 27 05:51:25 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:25 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:25 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:25 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:25 2014] [warn] NameVirtualHost 111.90.150.93:8080 has no VirtualHosts
[Thu Mar 27 05:51:25 2014] [warn] NameVirtualHost 111.90.150.92:80 has no VirtualHosts
[Thu Mar 27 05:51:25 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Thu Mar 27 05:51:25 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Thu Mar 27 05:51:25 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Thu Mar 27 05:51:25 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
 ... waiting [Thu Mar 27 05:51:26 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:26 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:26 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:26 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Thu Mar 27 05:51:26 2014] [warn] NameVirtualHost 111.90.150.93:8080 has no VirtualHosts
[Thu Mar 27 05:51:26 2014] [warn] NameVirtualHost 111.90.150.92:80 has no VirtualHosts
[Thu Mar 27 05:51:26 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Thu Mar 27 05:51:26 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Thu Mar 27 05:51:26 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Thu Mar 27 05:51:26 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts

My /etc/httpd.conf file is

NameVirtualHost 111.90.150.92:80
NameVirtualHost 111.90.150.93:8080

and the website I am trying to configure first has this file in /etc/apache2/sites/enabled

<Virtualhost 111.90.150.93:8080>
ServerAdmin webmaster@localhost
ServerName thexxxxxxxx.info
ServerAlias [www.thexxxxxxxx.info](www.thexxxxxxxx.info)
        DocumentRoot /var/www/thxxxxxxel
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/thexxxxxxx/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

My /etc/apache2/ports.conf file is 

# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost 111.90.150.92:80
Listen 80

NameVirtualHost 111.90.150.93:8080
Listen 8080

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

Obviously something is going wrong somewhere but I don't know what.

My /etc/hosts file is

127.0.0.1       localhost
111.90.150.93   server11362.abc.com     server11362

#Virtual Hosts
111.90.150.93 thxxxxxxxx.info

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by SeijiSensei on 2014-03-27
When you say you have a server with two addresses, is the second attached to a virtual Ethernet adapter like "eth0:0"?  Can you show us the output of the "ifconfig" command?

Specifying virtual addresses in the Apache configuration is not enough; the addresses themselves have to be attached to devices at the operating system level.

On one machine we have four virtual adapters, eth0:0 to eth0:3, which along with the master eth0 all have separate addresses from our /28.  In the Apache configuration I have specific Listen directives rather than a generic "Listen 80".  So try this instead:
```

NameVirtualHost 111.90.150.92:80
Listen 111.90.150.92:80

NameVirtualHost 111.90.150.93:8080
Listen 111.90.150.93:8080

```
I presume you know you don't need to use port 8080 for the second virtual.  Each IP:port combination is treated uniquely, so 111.90.150.93:80 would not conflict with 111.90.150.92:80.

Also you have the same IP address specified twice in /etc/hosts.  Is that what you want?

---

### Post by astarmathsandphysics on 2014-03-27
ifconfig returns

eth0      Link encap:Ethernet  HWaddr 70:54:d2:16:a7:a3  
          inet addr:111.90.150.92  Bcast:111.90.150.255  Mask:255.255.255.0
          inet6 addr: fe80::7254:d2ff:fe16:a7a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62476081 errors:0 dropped:317776 overruns:0 frame:0
          TX packets:52771940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7478196082 (7.4 GB)  TX bytes:63316923909 (63.3 GB)
          Interrupt:20 Memory:fe400000-fe420000 

eth0:1    Link encap:Ethernet  HWaddr 70:54:d2:16:a7:a3  
          inet addr:111.90.150.93  Bcast:111.90.150.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:fe400000-fe420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4704633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4704633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:252852321 (252.8 MB)  TX bytes:252852321 (252.8 MB)

As for having the second ip in /etc/hosts, I was trying to set up theeducationchannel.info to resolve to that ip, not knowing if it would work

NameVirtualHost 111.90.150.92:80
Listen 111.90.150.92:80

NameVirtualHost 111.90.150.93:8080
Listen 111.90.150.93:8080

I should include this in /etc/apache2/apache2.conf?
I though it would be in /etc/apache2/ports.conf

---

### Post by SeijiSensei on 2014-03-28
Yes, in ports.conf.

---

### Post by astarmathsandphysics on 2014-03-28
It is right now and I still get these errors

---

### Post by SeijiSensei on 2014-03-28
Did you remove the generic "Listen 80" and "Listen 8080" directives?

I have only complete IP:port specifications for Listen, NameVirtualHost, and all <VirtualHost> containers.

---

### Post by astarmathsandphysics on 2014-03-28
yes I just did it and I get

 * Restarting web server apache2                                                                              [Fri Mar 28 15:56:51 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:51 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:51 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:51 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:51 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:51 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:51 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:51 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:51 2014] [warn] NameVirtualHost 111.90.150.93:0 has no VirtualHosts
[Fri Mar 28 15:56:51 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:51 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:51 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:51 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:51 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
 ... waiting [Fri Mar 28 15:56:52 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:52 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:52 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:52 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:52 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:52 2014] [error] VirtualHost 111.90.150.92:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Fri Mar 28 15:56:52 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:52 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 15:56:52 2014] [warn] NameVirtualHost 111.90.150.93:0 has no VirtualHosts
[Fri Mar 28 15:56:52 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:52 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:52 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:52 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
[Fri Mar 28 15:56:52 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts

Am now down to a few errors

 * Restarting web server apache2                                                                              [Fri Mar 28 19:52:19 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 19:52:19 2014] [warn] NameVirtualHost 111.90.150.93:0 has no VirtualHosts
[Fri Mar 28 19:52:19 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts
 ... waiting [Fri Mar 28 19:52:20 2014] [warn] _default_ VirtualHost overlap on port 80, the first has precedence
[Fri Mar 28 19:52:20 2014] [warn] NameVirtualHost 111.90.150.93:0 has no VirtualHosts
[Fri Mar 28 19:52:20 2014] [warn] NameVirtualHost 111.90.150.92:0 has no VirtualHosts

---

### Post by SeijiSensei on 2014-03-29
> [Fri Mar 28 19:52:19 2014] [warn] NameVirtualHost 111.90.150.93:0 has no VirtualHosts


":0" and not ":80"?

---

### Post by astarmathsandphysics on 2014-03-29
yes.
I can change some settings can get no errors when apache2 loads but the websites on 111.90.150.93 still dont load

Could the problem be in my /etc/hosts file?

Ihave 2 ips 111.90.150.92 and 111.90.150.90 but only one is at the top of the file

127.0.0.1       localhost
111.90.150.92   server11362.abc.com     server11362

#Virtual Hosts
111.90.150.92:80 xxxxxxxxxxx.biz
111.90.150.92:80 xxxxxxxxxxxx.info
111.90.150.92:80 xxxxxxxxxxxxx.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

I think the problem is the second ip
I cant ping it.
Incidentall I changed /etc/apache2/ports.conf 
so that 

NameVirtualHost 111.90.150.92
Listen 80

NameVirtualHost 111.90.150.93
Listen 8080
became

Listen 111.90.150.92:80
Listen 111.90.150.93:8080
and now I get no errors when I restart apache2

Now I can ping it, but still the websites attached to that ip dont load

---

