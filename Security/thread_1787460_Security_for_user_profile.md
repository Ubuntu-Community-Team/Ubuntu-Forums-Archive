---
title: "Security for user profile"
date: 2011-06-21
forum: Security
---

### Post by Kulas101 on 2011-06-21
Hi,

I've been using ubuntu for more than a year now and I've quite enjoyed and have become fond of it that my winxp is now only just for my games. But still i'm just a user and not really savvy on the workings of ubuntu. 

I suggested to my friend that we use ubuntu as our internet cafe OS, this not only would introduce our customers to the beauty of Linux and Ubuntu but would cut our license cost to zero.
So we go about developing our i-cafe time manager in java and have successfully run it in ubuntu.


_The challenge:_
(Well for us but not to many people here.) :)
Secure the client side application so the users will not be able to stop it from executing and tampering with it upon User01 login.
Client application should run only with the users group not with the admin/sudoers group.


_The User PC station setup:_

Ubuntu 10.04 LTS, an admin and a user login account.
Admin login with password, User01 will login without password.
The Admin has the sudo powers, User01 has been setup as a desktop user with limited accces as per Users Setting in the ubuntu System > Administration > Users and Groups options. 


_What we have done so far:_

We put the program in the 
System > Preferences > Startup Application
The program is in the folder where Admin has the access but the user can execute, view and run it but not delete it (used chmod 755 for Admin).
Using gconf-editor have removed access to panel, removed some applications on the menu especially the Systems menu and disable Alt+F2.


For normal i-cafe users this should be enough, but for the other 20% of our customers which are curious, internet and computer savvy and are very motivated to have unlimited time use, this is quite weak. I know some people here might laugh and flame us for this noobness but as I've mentioned we are not very familiar with the inner workings and security of ubuntu, we are just happy users. 


_What we think we can do but not sure how:_

Put a password to gconf-editor
Put a password to the Startup Application option
Run it thru Admin on User01 login (we are very clueless with this).
Use this daemon thing which we have no idea what it is and my head went to the recycle bin when I try to read about it.


If any ubuntu gurus and users can point us in the right direction we'd really appreciate the help.
We'd really like a simple solution to this.
Thanks.  ;)

---

### Post by Lars Noodén on 2011-06-21
You could copy the user's home directory and then refresh from that master copy every reboot using rsync.  The option --delete removes files in the copy that are not present in  the master.

---

### Post by Kulas101 on 2011-06-21
thanks Lars ;)

this is great! rsync also solved the problem of cleaning the User01 file systems at the end of day.

we will be testing this one later after operating hours.
i'll update you the results.

thank you very much  :KS

---

