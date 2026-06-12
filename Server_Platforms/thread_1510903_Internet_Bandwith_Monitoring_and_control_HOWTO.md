---
title: "Internet Bandwith Monitoring and control HOWTO"
date: 2010-06-16
forum: Server Platforms
---

### Post by sanu01 on 2010-06-16
A how on setting up an internet connection on Ubuntu 10.04 server and control its distribution to other users in the local network. 

The aim of this tutorial is to give the ubuntu user a easy way to control his internet traffic which is achieved restricting users on how much they can download, what sites they can go to, what ports can be opened and so on. 

For this we shall use a program named traffpro. 

> 
Minimal Requirements:
* CPU 800 MHz or more  
 * RAM 256 MB  
 * 4 GB HDD  
 * Two  network cards or other communications interfaces  Lets assume our network has the following scheme:
[B]
ISP Providers Gateway:
Network[/B]

> • IP: 80.80.80.225[B]Our Servers Interfaces (eth0 and eth1)

[/B]> **Eth0 - External NIC:**

• IP: 80.80.80.80

• Netmask: 255.255.255.0

• Gateway: 80.80.80.225

• DNS: 80.80.80.2 80.80.80.2> [B]Eth1 - Internal NIC connecting LAN users:
[/B]
• IP: 172.16.10.250

• Netmask: 255.255.255.0We also have a user in the lan and shall name him **TestUser **with the following info
User

> [B]Test User:
[/B]
• IP: 172.16.10.11

• Netmask: 255.255.255.0

• Gateway: 172.16.10.250

• DNS: 172.16.10.250
 So lets get started.
1. Download the ubuntu server 10.04 cd (32/64 bit)
2. Update it 

**Configure operating system**
1. Edit the file */etc/network/interfaces* and change it as follows

```
sudo nano /etc/network/interfaces

```> auto eth0

iface eth0 inet static

address 80.80.80.226

netmask 255.255.255.0

network 80.80.80.0

broadcast 80.80.80.255

gateway 80.80.80.225

# dns-* options are implemented by the resolvconf package, if installed

dns-nameservers 80.80.80.2 80.80.80.2

auto eth1

iface eth1 inet static

address 172.16.10.250

netmask 255.255.255.0

network 172.16.10.0

broadcast 172.16.10.2552. Apply settings:
> sudo /etc/init.d/networking restart**Install the necessary packages**
```
apt-get install mysql-server mysql-client libmysqlclient15-dev apache2  apache2-doc php5 php5-mysql libapache2-mod-php5
```Edit **/etc/mysql/my.cnf** and edit it as follows:

> key_buffer=128M
table_cache=2048Thats it. Our LAMP server is now working. 
**Now we install additional packages so that traffpro can install and  work smoothly.**

```
sudo apt-get install iptables-dev libssl-dev openssl build-essential libmysql++-dev dialog
```Reboot the system..

Now upload the latest version of traffpro 1.3.4 to the home directory. 
Extract it using the tar command (Read Installation Guide)

Thange change to the installation directory.
cd install_free/
Load the installer.
./install.sh

Basic Configuration
1. The installer will offer you two options for the layout Text or  Graphical. I choose the graphical installer
To use the graphical installer you should have a screen resolution of  more than 800x600.
2. Language installer. Select "English"
3. Next its a simple Question and Answer based installation.. Everything  is simple and understandable.
4. Please note that the the system is only guaranteed to work on Red Hat  based Distros
5. Selecting distribution. Since we are installing on Debian, we choose  the second item.
6. Build the control daemon and choose ‘Yes'
7. Build timer or not? Answer "Yes".
8. Save Previous Traffpro Configuration? We are installing the system  from scratch, so answer "No".
9. Update the system (yes) or install New one? No!
10. Start Traffpro in daemon mode? Answer "Yes".
11. Specify the database location. In our case, "localhost".
12. Database Username. type "root" 
13. User password. Enter "traffpro" or  whichever password you used for  mysql
14. Enter database name: "traffpro".
15. Enable MAC control featurel? YES
16. Enable Port detail feature? "on". Useful stuff.
17. Enable SSecurity feature and Traffic control? If you do not want to  bother, select no. I discuss
example where protection of the server is enabled.
18.Set external interface name. In our case it is eth0.
19. Input the External IP address. In our case it is 80.79.178.226. If  you have a dynamic IP, it is better to leave the field empty.
20. Port to listen on the monitor. We leave as default.
21. The size of the queue packets. We leave as default.
22. Specifies the name of the administrator. For example, I left it as  "admin".
23. Password. For example "admin"
24. Enable scheduler? Answer "Yes".
25. The installation starts
26. Continue installation? Silly question. Of course "YES".
27. Add a database administrator? Answer "Yes".
28. Run Traffpro installation? Yes of course.
29. Here we are told that we will live happily ever after =)
Now the installation of Traffpro finished.

The above settings are stores in the following configuration file
> /etc/traffpro/traffpro.cfgAlso there is an additional configuration file named traffpro_rule.cfg where you can add iptable rules if you wish. 
**Basic iptables rules**
traffpro_rule.cfg located in /etc/traffpro uses iptable rules which are  loaded by traffpro when it starts up. It is needed so that the firewall  works securely. 
You can add your rules here. 

Server Protection..Our file will have the following rules:
# Allow SSH access.

iptables -A INPUT -m tcp -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -m tcp -p tcp --sport 22 -j ACCEPT

# Allow port 80 access. 

iptables -A INPUT -m tcp -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -m tcp -p tcp --sport 80 -j ACCEPT

So lets move on now. 
**Test the installation **
1. Load traffpro
sudo /etc/init.d/traffpro start
2. Write in terminal:
ps x | grep traffpro | grep -v \"grep\"

If the program is working we shall see the following output
4760 ? Ssl 1:12 /opt/traffpro/billing-daemon/bin/billing daemon=true

4774 ? Ssl 0:01 /opt/traffpro/billing-daemon/bin/timer daemon=true
You can also have a look at the logs in case any errors came up
:
tail /var/log/syslog

Now lets add our [B]TestUser
[/B]Open the following page in your server
> [http://yourserver/traffpro/index.php/admin_login](http://yourserver/traffpro/index.php/admin_login)where yourserver is the LAN ip of your server
Type in your login details as user “admin” and password “admin”.
1. The first thing you need to add a groups of users:
> Clients » Group » New Group
• Name - Group Name eg “accounting”.

• Type of traffic - unlimited.

• Allowed Ports - I allowed the following ports:

• 80 - HTTP

• 5190 - ICQ

• 110 - POP3

• 143 - IMAP

• 2041-2044 - Mail Agent.• Click “Apply”
Our group has been added. Now we add a user within this group. 
Our group has been added. 

[B]Now we add a user within this group. 
[/B] 
> Clients » Free » Clients » New client

• Network Name - user login name. Type “**TestUser**”

• Password - Type “user”

• Group - Choose group “Accounting”

• Traffic Type - Unlimited

• Plan of adding traffic - Amount of traffic to be added every month.   (if set to 0 &#1052;b, then you have to add traffic manually)

• IP - Clients ip address 172.16.10.11

• MAC - Users mac address. If you did not enable mac address control  then type 00:00:00:00:00:00. This field must be filled!

On the "Add User info tab" you can add additional data about users.After that click **"Apply." **You User has been added!

Now go to the **TestUsers** computer and set it up as follows

**Client Settings**
> Start » Control Panel » Network Settings » Connect to the Local Network »> Properties » TCP/IP Internet Protocol » Properties
Use the following IP address:

• IP-adress: 172.16.10.11
• Subnet Mask: 255.255.255.0
• Gateway: 172.16.10.250

Use the following DNS-servers:
•Primary DNS server: 172.16.10.250To verify that the link is up do the following:
> Start » Run » cmd » ping ya.ru -tIf you see the following:
> ping ya.ru

&#1054;&#1073;&#1084;&#1077;&#1085; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;&#1084;&#1080; &#1089; ya.ru [213.180.204.8] &#1087;&#1086; 32 &#1073;&#1072;&#1081;&#1090;:

&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 213.180.204.8: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;=4ms TTL=56

&#1054;&#1090;&#1074;&#1077;&#1090; &#1086;&#1090; 213.180.204.8: &#1095;&#1080;&#1089;&#1083;&#1086; &#1073;&#1072;&#1081;&#1090;=32 &#1074;&#1088;&#1077;&#1084;&#1103;=4ms TTL=56Then it means your connection is fine.

You can view how much traffic the client is using by using the monitors located in the admins start page. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=160615&stc=1&d=1276679094[/IMG]

---

