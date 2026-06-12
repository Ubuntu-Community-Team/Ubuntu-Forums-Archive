---
title: "Mysql install trouble"
date: 2007-02-26
forum: Server Platforms
---

### Post by Sengkim on 2007-02-26
Hi all!

Today I was unable to log in to my mysql server (running on Edgy). Since the mysql server was just installed I figured I just lost my root pwd and just did a remove of mysql (by running sudo apt-get remove mysql-server).

Then I did an install again but the problem stuck. So I removed mysql again and then deleted all mysql stuff I could find (/etc/init.d/mysql, /var/lib/mysql, /var/run/mysql and all binairies in sbin and bin).

When I do an install now, I don't even get the question if I want to proceed. It just installs. But, it still doesn't work. The setup is not done (so no dir mentioned above or so). 

Since I'm a neebie I'm a bit stuck. Someone know something to help?

Thanks!!

BB
Peter

---

### Post by phossal on 2007-02-26
I might try installing mysql-client also. Do you get any error messages currently?

---

### Post by Sengkim on 2007-02-26
Well, I did install the client stuff also but the same. No question if I want to proceed and nothing installed...

BB
Peter

---

