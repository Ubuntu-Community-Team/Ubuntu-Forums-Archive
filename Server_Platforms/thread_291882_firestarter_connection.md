---
title: "firestarter connection"
date: 2006-11-03
forum: Server Platforms
---

### Post by grim918 on 2006-11-03
I have this problem. When I start up firestarter it shows that there is a connection to a remote server. This connection has been there for a while and it does not go away. I also have many failed log in attempts from this IP address in my auth.log file. Does anyone know if this is something that I should be concerned about.


here is a screenshot that shows the connection.
[[img=http://img99.imageshack.us/img99/8282/screenshotnl4.th.png]](http://img99.imageshack.us/my.php?image=screenshotnl4.png)

---

### Post by wieman01 on 2006-11-03
This is odd... Can you uninstall SSH? Not sure what version is running, but look for "openssh-server". To remove it do this:
> sudo apt-get remove openssh-server
Then restart & there should be no more active SSH connection.

_**EDIT:**_
Note that it could be another SSH server as well... I am just assuming it's this one running in the background for whatever reason.

---

