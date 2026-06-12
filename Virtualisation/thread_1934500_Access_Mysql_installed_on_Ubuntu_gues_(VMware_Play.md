---
title: "Access Mysql installed on Ubuntu gues (VMware Player)"
date: 2012-03-02
forum: Virtualisation
---

### Post by turki_00 on 2012-03-02
Hi,

I am using VMware (v 1.3) and I have Windows 7 as a host (with public IP) and Ubuntu (10.10) as a guest OS (with private IP that is assigned by VMware 192.xxx.xxx.xxx). 

in Ubuntu, I have a mysql server that I can access it from the localhost (ubuntu) with no problems.

Now, I have a separate (remote) machine that I want to connect to the mysql server on the ubuntu VMware.

the command I am using from the remote machine:
mysql -u UserName –h WindowsIP –p

But I can't connect:
ERROR 2003 (HY000): Can't connect to MySQL server on WindowsIP

the windows firewall is off.
I can ping, access the remote machine from the Ubuntu box itself, but I can't do it the way around

so basically I can ssh or mysql:
Ubuntu (Vmware)---->remote machine (Ubuntu)

but I can't:
remote machine -->windows7---->Ubuntu (VMware)--->Mysql
and this is what I am trying to achieve here.

I appreciate any help,
turki

---

### Post by turki_00 on 2012-03-02
--UPDATE--

Windwos IP address 130.168.38.131
(Vmware network: NAT
VMware Network Adapter VMnet8: 192.168.230.134)

when I try to connect from remote client to windows host, following is the error.
Command 1:
mysql -h 130.168.38.131 -p
Enter password: ****
ERROR 2003 (HY000): Can't connect to MySQL server on '130.168.38.131' (111) server

in mysql server (ubuntu guest) I change the bind-address to host 130.168.38.131 (host ip) in /etc/mysql/my.cnf file

However, I noticed that mysql is refusing to restart/start when I use any value in bind-address.

also, I create the remote user in the mysql:

create user 'root'@'130.168.38.131' IDENTIFIED by 'turki';

GRANT ALL PRIVILEGES ON *.* TO 'root'@'130.168.38.131' IDENTIFIED BY 'turki' WITH GRANT OPTION;

and still can't connect from remote client!

please help

---

### Post by turki_00 on 2012-03-04
Found a solution,

All what i need beside the comment the bind-address in my.cf file for mysql and create and grant root user from % 

I have to edit the NAT settings of the VmWare player.
see this link:
[http://www.carbonwind.net/Virtualization/VMware-Player-Networking-Options/VMware-Player-Networking-Options.htm](http://www.carbonwind.net/Virtualization/VMware-Player-Networking-Options/VMware-Player-Networking-Options.htm)

just do the port forwarding 

and don't forget to forward the ports from 3306 to 3306 in windows 7 firewall (advanced)

---

### Post by nothingspecial on 2012-03-06
*Thread moved to **Virtualization**.*

---

