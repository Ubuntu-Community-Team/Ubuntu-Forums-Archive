---
title: "can't login to vmware server"
date: 2010-05-25
forum: Virtualisation
---

### Post by blackrook on 2010-05-25
hi I very new to this so here goes i got a very good friend of mine to help me install vmware2.0 server on the ubuntu server10.04 it was a tense moment there (after trying a dozen times myself) my friend help me with the installation of it and now that it's install I can't logon to it I try every password I could think of and nothing just the error message wrong user name or password is there anyway I can fix this PS I really don't want to uninstall it and start all over again thank you

---

### Post by cariboo on 2010-05-26
A bump for the move.

---

### Post by deltacomp on 2011-11-01
Hello, hopefully you have already found a solution to this problem seeing it is over a year old. If anyone else comes across this issue, I hope this is helpful. I recently installed VMWare to run several servers, after install and following a great [tutorial ]("https://help.ubuntu.com/community/VMware/Server")I was not able to login to the server. :confused:
I read online that setup will automatically use "root" for the user name, and your root password as the password. If you can not login, I suggest you create a root password in terminal

sudo passwd root (hit enter)

Followed by your new password, 
and your new password again. 

Once this is done, type vmware in terminal and it should open firefox for you with a login screen. 

[Root password change help. ]("https://help.ubuntu.com/community/RootSudo")

---

