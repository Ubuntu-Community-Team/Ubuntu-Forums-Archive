---
title: "Ubuntu as a user server"
date: 2006-02-28
forum: Server Platforms
---

### Post by chedabob on 2006-02-28
is there a certain way that i can set ubuntu up as a server for all the usernames? i want to set it up this way, so that all the computers can retrieve files and user information from one server. also, can gnome menu editor work with all users in a group, or is it just specific to each user?

---

### Post by localzuk on 2006-02-28
Hi and welcome!

Are you wanting the clients to use Windows or Ubuntu/linux?

If it is windows - take a look at a program called 'samba'. There is a lot of information about it on this site and the web in general.

I believe the menu editor is specific to each user but I am not sure.

Hope to help

---

### Post by krewemaynard on 2006-02-28
[QUOTE=chedabob]is there a certain way that i can set ubuntu up as a server for all the usernames? i want to set it up this way, so that all the computers can retrieve files and user information from one server. also, can gnome menu editor work with all users in a group, or is it just specific to each user?[/QUOTE]

If you have Linux clients, you may want to look into setting up /home as an NFS export on your server, and having remote clients mount it as their /home directory. The closest I did to that was running thin X clients, but they ran all programs on the remote server, so it's a little different. Google for 'roaming profiles linux', see if that helps.

---

### Post by localzuk on 2006-02-28
For centralised login you could use NIS. 
This site provides information for redhat based machines - but it can easily be used in ubuntu (I do not know what the packages are called).
[http://www.freeos.com/articles/2843/](http://www.freeos.com/articles/2843/)

---

### Post by LordHunter317 on 2006-03-01
No, whatever you do, please don't use NIS.  Use LDAP and Kerberos instead.  Please, I beg you.  Let that POS Sun technology die.

---

### Post by localzuk on 2006-03-01
I only suggested NIS due to having just read about it elsewhere. *claims innocence* :)

---

### Post by nihilocrat on 2006-03-01
[QUOTE=LordHunter317]No, whatever you do, please don't use NIS.  Use LDAP and Kerberos instead.  Please, I beg you.  Let that POS Sun technology die.[/QUOTE]

I heard about this and I want to know if there's a HOWTO or something about setting it up in Ubuntu. Is the LDAP/Kerberos combination able to handle both Windows and Linux clients or just Linux? I currently have no knowledge of Open Source replacements for Active Directory or other directory services other than NIS.

---

