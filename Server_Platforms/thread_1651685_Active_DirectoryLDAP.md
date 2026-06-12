---
title: "Active Directory/LDAP?"
date: 2010-12-23
forum: Server Platforms
---

### Post by kpayton on 2010-12-23
Alright don't kill me for asking this but I have a question for you guys, its kind of one of those can Ubuntu Server do this:

Anyways.  I have a client of mine who is an office of 5 computers.  Currently they log into a work group, and just connect to a NAS Device it's all happy.  Well not they want to sign into more than one computer and play music computers.  

My question is I don't think we need an Active Directory for 5 people, but can Ubuntu Server edition work for something that Im trying to do.

Basically the users need Drive mappings and password syncs.  Thats it.  They don't need Roaming profiles or anything.

---

### Post by windependence on 2010-12-24
[http://ubuntuforums.org/archive/index.php/t-516565.html](http://ubuntuforums.org/archive/index.php/t-516565.html)
 
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/ProfileMgmt.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/ProfileMgmt.html)
 
If Im not mistaken you need to setup a samba path to store the **profile**, and ensure that the **profile** is available.

Then you need to tell your AD box to use profiles, and tell the AD box where the profiles are stored.

You should have the option of storing profiles locally (as in on the AD controller box) or on the network somewhere (as in a NAS box)  Just tell the AD where the profiles are stored and you should be good.
 
I think you're going to have to set up roaming profiles to keep them all happy. Links above will help you with this.
 
HTH
 
-Tim

---

### Post by HermanAB on 2010-12-24
Howdy,

With 5 to 10 users, you do not need a directory system - it will be more bother than it is worth.

Note that a Samba server has very good support for simple password authentication built in.  The trick is to create the user accounts on the Samba server exactly the same as on Windows to begin with.  For example, if the Windows login is herman with password 12345, then run smbpasswd -a herman and set the password to 12345.  From then on, if the user changes his password in Windows after connecting to the Samba server, Samba will also change its password to match and the user will not be pestered with password prompts.

---

