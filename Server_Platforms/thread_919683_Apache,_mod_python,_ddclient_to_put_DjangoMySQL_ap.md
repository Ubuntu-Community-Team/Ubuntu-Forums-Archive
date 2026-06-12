---
title: "Apache, mod_python, ddclient to put Django/MySQL app out to www"
date: 2008-09-14
forum: Server Platforms
---

### Post by ssavelan on 2008-09-14
So, I have a Django app working with MySQL database.  I want admins to be able to start populating data from remote locations.  I got a static ip through dyndns and have installed everything through the package manager (except for django).  


Something is not working, but the only error message I can get is from:

```

skylar@ubuntuABC:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]


```

ddclient senses nothing wrong:

```

skylar@ubuntuABC:~$ sudo /etc/init.d/ddclient restart
[sudo] password for skylar: 
 * Restarting Dynamic DNS service update utility ddclient                [ OK ] 

```

networking restart doesn't have any problem as I can see:

```

skylar@ubuntuABC:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                              * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.eth1.pid with pid 29774
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:09:5b:20:83:3c
Sending on   LPF/eth1/00:09:5b:20:83:3c
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.2.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:09:5b:20:83:3c
Sending on   LPF/eth1/00:09:5b:20:83:3c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.2.100 from 192.168.2.1
DHCPREQUEST of 192.168.2.100 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.2.100 from 192.168.2.1
bound to 192.168.2.100 -- renewal in 120285 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
                                                                                                            [ OK ]


```

This may provide some useful information but I'm not exactly sure what to see from it:

```

skylar@ubuntuABC:~$ sudo netstat -anp | grep '^tcp.*LISTEN'
tcp        0      0 127.0.0.1:8000          0.0.0.0:*               LISTEN      25418/python    
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5376/mysqld     
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      30688/apache2   
tcp        0      0 192.168.2.100:53        0.0.0.0:*               LISTEN      23489/named     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      23489/named     
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      23489/named     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      5689/exim4      
tcp6       0      0 :::53                   :::*                    LISTEN      23489/named     
tcp6       0      0 ::1:953                 :::*                    LISTEN      23489/named

```

What else?  I followed some tutorials and howto to make minor changes to my conf files in trying to solve these problems.  I set ddclient configuration file as it seemed to be agreed on in some posting specifically pertaining to hardy.  Maybe there is something obvious to see here.  I can send my conf files along if this is not enough information to go with.  Where do you think is the most likely source of the problem.  Django/MySQL seem to be running really strong on the local server and I think I followed the documentation to switch to going to www with the app so I think the problem is with apache/apache-mod_python or ddclient... but the ddclient stuff seemed straightforward enough and I am not finding any erros there so that leaves me with apache.conf and other apche configuration files.  Anyone got a clue?  There are also issues with the router I am running behind and such but I opened port 8080 for HTTP (just in case 80 is blocked by default) and that is where I run apache.

I have a bellsouth connection, perhaps I need to turn their firewall and block off too.

Another thing I was wondering is: do I need bind /(bind9, dnsutils) or is that for something different.  Should I use nginx?  I haven't really looked in to these programs that much but they come up in my searches.

It is a pretty specific problem.  Nontheless, if I can put the pieces together on this I might try to make a howto on "Putting your Django-app on the www for free with Ubuntu-server."  or something like that.

If anyone can give me any hints or could use more information, thanks for taking the time to help with my issue.

Cheers

---

### Post by Vegan on 2008-09-14
can I see you /etc/hosts file too please

---

### Post by ssavelan on 2008-09-15
> **Vegan said:**
> can I see you /etc/hosts file too please

sure thing.  I am actually trying this with a fresh install of ubuntu server with no LAMP as per this guide.  I was able to reproduce the behavior on this other computer.

[http://ubuntuforums.org/showthread.php?t=632841]("http://ubuntuforums.org/showthread.php?t=632841")

Following this thread from a new install gives me this:

```

skylar@ABCtest:~$ sudo /etc/init.d/ddclient restart
 * Restarting Dynamic DNS service update utility ddclient                [ OK ] 
skylar@ABCtest:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
skylar@ABCtest:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
skylar@ABCtest:~$ 

```

Oh yeah, and the /etc/hosts file:

```

127.0.0.1       localhost
127.0.1.1       ABCtest

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by pqrs541 on 2008-09-16
Threats: I'll slap you so hard, your clothes will be outtalk style.[wow gold](http://www.mmoinn.com) This'll jar your preserves. Don't you be making' me open a can o' whoop-*** on yaw! [buy wow gold](http://www.mmoinn.com)[World of warcraft Gold](http://www.mmoinn.com)[cheap wow gold](http://www.mmoinn.com)[power leveling](http://www.mmoinn.com)

---

