---
title: "Connecting Samba BDC to Samba PDC"
date: 2008-01-22
forum: Server Platforms
---

### Post by ryjal on 2008-01-22
I have a Samba PDC up and running and it works great. I now want to set up a ubuntu Samba BDC for logon's and home directories if the PDC slows down or has problems. I have set up another Ubuntu server to act as the BDC. I used this [link]("http://www.enterprisenetworkingplanet.com/netos/article.php/3457461")  to start with. Here is the smb.conf for the BDC

[global]
     workgroup = WORKGROUP
     netbios name = DAPPER
     passdb backend = tdbsam
     domain master = No
     domain logons = Yes
     os level = 33
     add user script = /usr/sbin/useradd -m '%u'
     delete user script = /usr/sbin/userdel -r '%u'
     add group script = /usr/sbin/groupadd '%g'
     delete group script = /usr/sbin/groupdel '%g'
     add user to group script = /usr/sbin/usermod -G '%g' '%u'
     add machine script = /usr/sbin/useradd -s /bin/false -d /dev/null '%u'
     wins server = [ IP Address to wins server ]

Now I used this command

**net rpc join -S [NT netbios name or IP]  -UAdministrator%password**

Command runs and states that it has connected to my domain. The problem I am having is when I try to Migrate user and machine accounts to the BDC. This is the command I am trying to use but it just fails and I have searched the net for the answer and I am not seeing it.

**net rpc vampire -S [NT netbios name or IP] -W [domainname] -UAdministrator%password**

This is the output to the above command

[B]Fetching DOMAIN database
Failed to fetch domain database: NT code 0x1c010002[/B]

Anyone have any ideas.

Now the page that I used to set up my Samba DBC, sets up the there Samba BDC to a NT PDC server and creates an account for there Samba BDC on the NT PDC. Do I need to do this for a Samba PDC? I am not sure and could not find any documentation on it.

Thanks for all the help

---

### Post by freebeer on 2008-01-22
I think your problem lies with your choice of password backend.  The docs found here: [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-bdc.html](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-bdc.html) imply that tdbsam won't work.

---

### Post by ryjal on 2008-01-23
Thanks for the replay

So Basically I need to set up a LDAP server to handle the accounts instead of tdbsam. Anybody have any ideas or How-to's on how to move from a tdbsam to LDAP.

---

### Post by HansWilhelm on 2008-05-05
Here is a link to a good example of how to migrate from a tdbsam to an ldap backend. 
[http://eldapo.blogspot.com/2004/08/samba-and-ldap.html](http://eldapo.blogspot.com/2004/08/samba-and-ldap.html)

Also, once you've migrated your data you will probably want to use syncrepl to keep your BDC up to date.

---

