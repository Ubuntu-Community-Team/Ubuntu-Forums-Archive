---
title: "Tomcat6 user account problems"
date: 2011-02-16
forum: Server Platforms
---

### Post by robertdbuckley on 2011-02-16
Hi,

I am running Ubuntu server 8.04 with tomcat6 and java-6-sun.

When I installed tomcat6 the system automatically created a user tomcat6 and a group tomcat6. I didn´t realize this until I tried to edit some of the webapp files and found I didn´t have the permissions.

So...I thought that if I logged into my winscp account or putty as user "tomcat6" i would be able to edit everything, but this is not so.

I tried to log in as tomcat6,but the was no set passsword. I set a password in ubuntu, but in putty my acount name doesn´t change...ie. $normalusername:/  doesn´t change to $tomcat6:/ ???

All the tomcat6 files and webapps are owned by tomcat6, but I can´t edit them unless I change to superuser.

How can I just get ubuntu to recognize the account "tomcat6" so that I can log into putty or WinSCP as this user and edit the files like a normal user?


thanks for any tips,

Robert

---

### Post by guygriffiths on 2011-10-10
I had some issues with the tomcat6 user too, and this post came fairly high on Google.  It's probably a little late for robertdbuckley, but for future reference, you need to edit /etc/passwd and change the default login shell for the tomcat6 user.  By default it is set to "/bin/false".  Changing it to "/bin/bash" (or your preferred shell) should get around this issue.

---

