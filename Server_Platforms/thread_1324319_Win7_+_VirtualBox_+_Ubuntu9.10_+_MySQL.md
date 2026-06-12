---
title: "Win7 + VirtualBox + Ubuntu9.10 + MySQL"
date: 2009-11-12
forum: Server Platforms
---

### Post by mattews on 2009-11-12
Win7 + VirtualBox + Ubuntu9.10 + MySQL


Hey guys.. I think Ive got a tough one here.
Ive been trying to do this for about a week but no success yet.
I have a Ubuntu 9.10(x86)  running as guest on a Windows 7(x64) host machine using Virtual Box (3.0.10 - Latest Version).
I am not using any firewalls by the way. I have used ROOT user on Ubuntu for ALL commands.
What I want is from Win7 connect to my MySQL server installed on Ubuntu.
Now here is what Ive done and the results I am getting:

--
First I created a new VM on VirtualBox and installed Ubuntu 9.10.
On network configurations I have the following settings:

Adapter Type: Intel PRO;1000 MT Desktop (82540EM)
Attached to: Bridged Adapter
Name: Marvel Yukon Ethernet Controller (My LAN card)

--
I have a D-Link ASDL router and I have IPs for both Host and Guest:
Host: 192.168.254.1
Guest: 192.168.254.2

Both are using the same mask, DNS and everything else.
So on Ubuntu I configure the eth0 with the proper IPs I mentioned above.
Everything is working fine. Internet and I can ping host->guest and guest->host.

--
Now I installed MySQL on Ubuntu using Synaptic Manager.
I can login with root on MySQL with no problems.
So now I need to enable MySQL for remote connections.

Using "gedit /etc/mysql/my.cnf" I have:

#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address        = 127.0.0.1
bind-address        = 192.168.254.2

In many posts I saw people mentioning about skip-networing, but that setting was not present as its mentioned on the file.


--
I restart MySQL and log in again.
/etc/init.d/mysql restart
mysql> mysql -u root -p mysql

So now I grant privileges to root to be access everything from anywhere (No, I am NOT concerned with security at the moment.)

GRANT ALL ON *.* TO root@'%' IDENTIFIED BY 'root';

update db set Host='%';
update user set Host='%';

select host, user from user where user = 'root';

+---------------+------+
| host          | user |
+---------------+------+
| %             | root | 
| 127.0.0.1     | root | 
| 192.168.254.1 | root | 
| Servus2       | root | 
+---------------+------+

I guess everything in MySQL is set then.
I have also used MySQL Query Browser and MySQL Administrator to login and it worked perfectly.

--
Now, using iptables I allow all traffic:
(No, I am NOT concerned with security at the moment.)

iptables -A INPUT -p tcp --destination-port 3306 -j ACCEPT
iptables -A INPUT -p udp --destination-port 3306 -j ACCEPT
iptables -A INPUT -j ACCEPT

iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:mysql 
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

>>>Now my first question: After I put in those rules, do I need to do anything else to actually apply them? Or are they in use immediately? When I reboot I lose those configurations, so how can I keep them permanent?

Allright then, ports are open:

nmap -p 3306 192.168.254.2
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2009-11-12 15:01 BRST
Interesting ports on 192.168.254.2:
PORT     STATE SERVICE
3306/tcp open  mysql
Nmap done: 1 IP address (1 host up) scanned in 0.58 seconds

Lets see if MySQL is listening properly:

root@Servus2:/home/mateus# netstat -an | grep 3306
tcp        0      0 192.168.254.2:3306      0.0.0.0:*               LISTEN

Seems that everything is OK!!
---

>>>Second question: Using telnet from inside ubuntu I should be able to connect to mysql, shouldnt I? But thats what I get:
telnet 192.168.254.2 3306
Trying 192.168.254.2...
Connected to 192.168.254.2.
Escape character is '^]'.
=
5.1.37-1ubuntu5&Gv=j!`Bnh?Ds;hyJE\|Connection closed by foreign host.

--
Now what WOULD be the final step, to port forward the ports I am using in Virtual Box:
In Win7 console..

VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlTCP/HostPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlTCP/GuestPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlTCP/Protocol" TCP

VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlUDP/HostPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlUDP/GuestPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlUDP/Protocol" UDP

Using "VBoxManage.exe getextradata "Ubuntu-9.10" enumerate" I get the same output as above.
>>> Third question: Is there a problem on using port 3306 on both guest and host protocol?


---

>>>Fourth problem: When trying to connect using any MySQL client, all connections fail!


Im not even sure where the problem is exactly: MySQL, Ubuntu, Win7 or on Virtual Box, thats why I am posting here.

ANY help will be great! Ive checked alot of manuals and forums gathering all this information but still it isnt enough.

:)

---

### Post by rickyjones on 2009-11-12
> **mattews said:**
> Win7 + VirtualBox + Ubuntu9.10 + MySQL


Hey guys.. I think Ive got a tough one here.
Ive been trying to do this for about a week but no success yet.
I have a Ubuntu 9.10(x86)  running as guest on a Windows 7(x64) host machine using Virtual Box (3.0.10 - Latest Version).
I am not using any firewalls by the way. I have used ROOT user on Ubuntu for ALL commands.
What I want is from Win7 connect to my MySQL server installed on Ubuntu.
Now here is what Ive done and the results I am getting:

--
First I created a new VM on VirtualBox and installed Ubuntu 9.10.
On network configurations I have the following settings:

Adapter Type: Intel PRO;1000 MT Desktop (82540EM)
Attached to: Bridged Adapter
Name: Marvel Yukon Ethernet Controller (My LAN card)

--
I have a D-Link ASDL router and I have IPs for both Host and Guest:
Host: 192.168.254.1
Guest: 192.168.254.2

Both are using the same mask, DNS and everything else.
So on Ubuntu I configure the eth0 with the proper IPs I mentioned above.
Everything is working fine. Internet and I can ping host->guest and guest->host.

--
Now I installed MySQL on Ubuntu using Synaptic Manager.
I can login with root on MySQL with no problems.
So now I need to enable MySQL for remote connections.

Using "gedit /etc/mysql/my.cnf" I have:

#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address        = 127.0.0.1
bind-address        = 192.168.254.2

In many posts I saw people mentioning about skip-networing, but that setting was not present as its mentioned on the file.


--
I restart MySQL and log in again.
/etc/init.d/mysql restart
mysql> mysql -u root -p mysql

So now I grant privileges to root to be access everything from anywhere (No, I am NOT concerned with security at the moment.)

GRANT ALL ON *.* TO root@'%' IDENTIFIED BY 'root';

update db set Host='%';
update user set Host='%';

select host, user from user where user = 'root';

+---------------+------+
| host          | user |
+---------------+------+
| %             | root | 
| 127.0.0.1     | root | 
| 192.168.254.1 | root | 
| Servus2       | root | 
+---------------+------+

I guess everything in MySQL is set then.
I have also used MySQL Query Browser and MySQL Administrator to login and it worked perfectly.

--
Now, using iptables I allow all traffic:
(No, I am NOT concerned with security at the moment.)

iptables -A INPUT -p tcp --destination-port 3306 -j ACCEPT
iptables -A INPUT -p udp --destination-port 3306 -j ACCEPT
iptables -A INPUT -j ACCEPT

iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:mysql 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:mysql 
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

>>>Now my first question: After I put in those rules, do I need to do anything else to actually apply them? Or are they in use immediately? When I reboot I lose those configurations, so how can I keep them permanent?

Allright then, ports are open:

nmap -p 3306 192.168.254.2
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2009-11-12 15:01 BRST
Interesting ports on 192.168.254.2:
PORT     STATE SERVICE
3306/tcp open  mysql
Nmap done: 1 IP address (1 host up) scanned in 0.58 seconds

Lets see if MySQL is listening properly:

root@Servus2:/home/mateus# netstat -an | grep 3306
tcp        0      0 192.168.254.2:3306      0.0.0.0:*               LISTEN

Seems that everything is OK!!
---

>>>Second question: Using telnet from inside ubuntu I should be able to connect to mysql, shouldnt I? But thats what I get:
telnet 192.168.254.2 3306
Trying 192.168.254.2...
Connected to 192.168.254.2.
Escape character is '^]'.
=
5.1.37-1ubuntu5&Gv=j!`Bnh?Ds;hyJE\|Connection closed by foreign host.

--
Now what WOULD be the final step, to port forward the ports I am using in Virtual Box:
In Win7 console..

VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlTCP/HostPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlTCP/GuestPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlTCP/Protocol" TCP

VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlUDP/HostPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlUDP/GuestPort" 3306
VBoxManage.exe setextradata "Ubuntu-9.10" "VBoxInternal/Devices/e1000/0/LUN#0/Config/mysqlUDP/Protocol" UDP

Using "VBoxManage.exe getextradata "Ubuntu-9.10" enumerate" I get the same output as above.
>>> Third question: Is there a problem on using port 3306 on both guest and host protocol?


---

>>>Fourth problem: When trying to connect using any MySQL client, all connections fail!


Im not even sure where the problem is exactly: MySQL, Ubuntu, Win7 or on Virtual Box, thats why I am posting here.

ANY help will be great! Ive checked alot of manuals and forums gathering all this information but still it isnt enough.

:)

Based on what I'm reading you have a guest install of Ubuntu under VirtualBox under Windows 7. You are using bridged networking and the Ubuntu guest is getting a valid IP address from your router. We can see this because you can telnet to that IP address and can see it running.

Are you trying to connect from the internet? If so you need to forward the ports from your ROUTER, not from within Virtualbox.

Thanks,
Richard

---

### Post by mattews on 2009-11-12
Almost...
I am trying to access the MySQL server from the host (Win7).
On Win7 Ive scanned the guests ports and 3306 is open.

---

### Post by rickyjones on 2009-11-13
> **mattews said:**
> Almost...
I am trying to access the MySQL server from the host (Win7).
On Win7 Ive scanned the guests ports and 3306 is open.

So you see the port open but you cannot connect with the MySQL Administrator tool? What error message do you get?

Thanks,
Richard

---

