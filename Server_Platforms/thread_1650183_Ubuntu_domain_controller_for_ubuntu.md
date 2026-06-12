---
title: "Ubuntu domain controller for ubuntu"
date: 2010-12-21
forum: Server Platforms
---

### Post by Borislavov on 2010-12-21
Hello,
sorry if the category is wrong, I couldn't  find any regarding my question.

We are migrating from Windows to Ubuntu in our office and we have windows domain controller which we want to migrate to ubuntu too.
Is there any HOWTO or tutorial for building Ubuntu Server for authentication (OpenLDAP for example) and settings for the Ubuntu Desktops to authenticate against Ubuntu Server and store their profiles in one place (Samba, WebDav, NFS may be).

If found how to authenticate ubuntu agains Windows Domain Controller and How to create Ubuntu Domain controller for Windows clients, but we want to exclude windows from the scheme.
We want only Ubuntus in our network including Servers and Clients. How can we do that?

Thanks

---

### Post by sapremias on 2010-12-21
If you are going to get rid of all Windows machines then stop thinking of your network in terms of "Windows Services". A hard lesson that I had to learn myself. Ubuntu is capable of logging in to with LDAP credentials which Active Directory is a Microsoft superset of. You can use OpenLDAP as central authentication for this. If you are running a mixed network with Linux and Windows, then unfortunately you have to consider Windows Services as part of your network.
Have a look at this thread...
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

---

### Post by Borislavov on 2010-12-21
On this link it seems to be microsoft related article. I will try this configuration with Ubuntu Server with LDAP, SAMBA and Ubuntu Desktop. If somebody has more precise article, please post here, i will test everything and will share my experience.

---

### Post by elico on 2010-12-24
and do you want to convert any windows machine to ubuntu?
if so you can use other methods to replace the Windows AD.
also there is a nice STACK machine for directory services.

---

### Post by HermanAB on 2010-12-24
Howdy, there are many cnetralized authentication services for UNIX:
NIS, NIS+, LDAP, PAM MySQL, even RADIUS... the list goes on and on, but the simplest one is good old NIS.

---

### Post by Borislavov on 2010-12-24
we want to replace windows machines and build brand new working group based on openldap (because we use ldap for emails, vps, internal system authentication and etc.) for ubuntu desktops. 
We will not convert anything.

---

### Post by elico on 2010-12-25
openLDAP it is..
if you want to manage the LDAP using webinterface you can install phpldapadmin.
if you will use LDAP and all ubuntu machines you will might want to use NIS for filesharing...
and it depends on your needs.

---

