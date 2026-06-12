---
title: "Best partition Scheme for Ubuntu Server"
date: 2012-11-10
forum: Server Platforms
---

### Post by ketan985 on 2012-11-10
I am going to deploy Ubuntu server having  Following servers  on it
  
Bind server, dhcp server, LAMP Server, Openssh  Server, Ldap server,  Monodb database, FTP server,mail server,  Samba server, NFS server , in  future I want to set Openstack for PAAS. 


  Currently I have Raid 5 with 10TB.  How should I make my Partition Scheme So never get problem in future and  easily expand Storage size. Suggest me such a partition Scheme with  giving specific percentage of Storage to partitions like /, /boot, /var,  /etc.

---

### Post by thnewguy on 2012-11-10
Your requirements will vary depending on how the server is used and how you plan to backup your server, whether your LAMP server will serve up one website or the sites of all your users, how many users, etc.

Have you considered setting up virtual machines for your individual services? Having one self-contained virtual machine you can move around and expand as needed will probably be better for you than having one physical machine locked into a configuration. Especially where you plan to run so many different services.

---

