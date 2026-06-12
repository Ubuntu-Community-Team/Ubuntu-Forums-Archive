---
title: "Windows login samba PDC giving error windows cannot locate your roaming profile"
date: 2008-02-14
forum: Server Platforms
---

### Post by cpthk on 2008-02-14
Hi

Default samba setting is that we have to add windows client computer name into username in samba. For example: computer name JOHN has to be add into samba username JOHN$. Is it possible to let samba ignore it, that all computer with the right username and password may log in. This would save me lots of time.

Thanks.

---

### Post by lnx4me on 2008-02-14
I'm not real certain from your post exactly what your asking. the trailing $ on john indicates what I would interpret as a machine acount. the user name and password for a real user is different than a machine account. The other part about roaming profiles suggest that you may have that enabled in the smb.conf file. if so typically roaming profiles are stored in the home directory for the user. this can also be specified in the smb.conf file.

---

### Post by cpthk on 2008-02-15
Yes, I understand the $ means machine account. My question is can I let samba ignore machine account and letting all machine to log in. Because I have so many windows clients, that I don't want to set one by one and also I don't need that.

---

### Post by rickyjones on 2008-02-15
> **cpthk said:**
> Yes, I understand the $ means machine account. My question is can I let samba ignore machine account and letting all machine to log in. Because I have so many windows clients, that I don't want to set one by one and also I don't need that.

I don't believe this is possible. Part of having a domain is for the security of it, so that any old computer can't just log in unless it is specifically allowed.

-Richard

---

### Post by lnx4me on 2008-02-15
Okay,
 you dont need to run a PDC for allowing systems to logon using username and password. the security part comes form the setting security=user in the smb.conf file. If all you want is to setup samba to have a share that all users can access by username and password yes that can be done. Post the contents of the smb.conf file and lets look at it. OR using the default smb.conf file you can change:
workgroup=MYDOMAIN    this is not a domain from the windows POV.
security=user
then uncomment the homes share and set write enable=yes

then you would use the smbpasswd -a command to add the user to the database. for example:
you have a user named john 
you would do the following

smbpasswd -a john

then you need to supply the same password for john as the unix box password for john. 
then on the windows box your not joining a domain. change the workgroup option to be the same as the workgroup in samba.
after this john should be able to access his home directory on the unix box. using the username john and his password.

---

### Post by lnx4me on 2008-02-15
Also you might want to check out samba 3 by examole: the book is on the web at :
[http://us1.samba.org/samba/docs/man/Samba-Guide/](http://us1.samba.org/samba/docs/man/Samba-Guide/)
This should give you all the information you can imagine. I have built about 40 or 50 fileservers in small offices less than 10 clients. this book has been an exceptional reference. so much so if I look to my left its on the book shelf.

---

### Post by cpthk on 2008-02-16
> **lnx4me said:**
> Okay,
 you dont need to run a PDC for allowing systems to logon using username and password. the security part comes form the setting security=user in the smb.conf file. If all you want is to setup samba to have a share that all users can access by username and password yes that can be done. Post the contents of the smb.conf file and lets look at it. OR using the default smb.conf file you can change:
workgroup=MYDOMAIN    this is not a domain from the windows POV.
security=user
then uncomment the homes share and set write enable=yes

then you would use the smbpasswd -a command to add the user to the database. for example:
you have a user named john 
you would do the following

smbpasswd -a john

then you need to supply the same password for john as the unix box password for john. 
then on the windows box your not joining a domain. change the workgroup option to be the same as the workgroup in samba.
after this john should be able to access his home directory on the unix box. using the username john and his password.

I basically want to lock the computers that a person without account and password cannot use the computer at all, not even let the user log in to windows.

---

### Post by lnx4me on 2008-02-16
Okay,
change the way users login on the windows machines. Are they vista, xp or ??? You can usually set the press CRTL-Alt-DEL option to login. In XP I think its change the way users login. 

Did you take a look at the link?

---

### Post by lnx4me on 2008-02-16
To require users to press CTRL+ALT+DELETE before logging on
You must be logged on as an administrator or a member of the Administrators group on a computer that is part of a network domain in order to complete this procedure. Network policy settings may also prevent you from completing this procedure.

Open User Accounts in Control Panel. 
Click the Advanced tab. 
In Secure logon, select the Require users to press Ctrl+Alt+Delete check box. 
 Notes

To open User Accounts, click Start, click Control Panel, and then double-click User Accounts. 
Pressing CTRL+ALT+DELETE before logging on guarantees that the authentic Windows logon prompt appears. Requiring the use of CTRL+ALT+DELETE increases security and helps to thwart certain Trojan horse programs. 
Related Topics

This is from an XP pro machine

---

