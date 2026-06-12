---
title: "Need help configuring OpenLDAP"
date: 2009-11-05
forum: Server Platforms
---

### Post by tristanhall on 2009-11-05
I'm trying to create the equivalent of Novell's roaming profiles with Ubuntu Server 9.04, OpenLDAP and Samba.
I know how to create and manage Samba but I can't seem to figure out how to configure OpenLDAP with their new configuration setup. When I use
```
apt-get install slapd ldap-utils migrationtools
```
I am not prompted for anything it just goes. I also can't find the slapd.conf file anywhere. My current setup is
Ubuntu Server 9.10
Samba
LAMP
SSH
FTP
 
I've removed OpenLDAP for the time being. It would be extremely helpful to hear from someone seasoned in Novell and Ubuntu. I am totally lost on how to configure OpenLDAP to work with Samba and how to do anything with OpenLDAP. I am a beginner at Ubuntu but am learning quickly. Putting things in simplest form would be helpful but I can always Google stuff if I need to.

---

### Post by Iowan on 2009-11-05
I haven't gotten LDAP working yet, but wonder if you've seen any of the "Perfect Server" articles on [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu").

---

### Post by whoop on 2009-11-07
Every current tutorial I have found on this topic is not up-to-date with the latest ubuntu versions.

This very complete one ([http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)) was written for ubuntu 7.10 but it works (for most parts) with 8.04. After 8.04 it probably wont work any more as there are some crucial changes made to LDAP.

So please **vote** for this brainstorm idea: [http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/) , as we need updated documentation on this topic (especially since a new LTS is about to be released).

---

### Post by tristanhall on 2009-11-10
I finally found this guide.
[http://ubuntuforums.org/showthread.php?t=1313472&highlight=No+LDIF-format+config+file+found+for+olcDatabase%3D%7B1%7Dhdb%2Ccn%3Dconfig](http://ubuntuforums.org/showthread.php?t=1313472&highlight=No+LDIF-format+config+file+found+for+olcDatabase%3D%7B1%7Dhdb%2Ccn%3Dconfig)
 
It was exactly what I needed.

---

