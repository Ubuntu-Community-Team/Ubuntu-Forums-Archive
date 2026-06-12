---
title: "Cannot login to ifolder server from windows client"
date: 2008-01-20
forum: Server Platforms
---

### Post by jimp180 on 2008-01-20
I built the server on ubuntu 7.10 base system from svn 4 days ago (not sure what version or how to check)folowing this [https://help.ubuntu.com/community/iFolderEnterpriseServer](https://help.ubuntu.com/community/iFolderEnterpriseServer)
I am able to log into the admin and create accounts, I am also able to log in to webaccess as the user I created but I am unable to log in via a client on a windows machine. I have tried with 3.4 , 3.5, and 3.6 clients, all with the same result, they seem to find the server ok but the server wont validate the login info, keeps saying "invalid user name or password".I know I am using the correct credentials, like I said they work when I login via the webaccess .
any suggestions as to where and what to check?

---

### Post by lisdeksia on 2008-03-12
Hi,

When you stop the Apache webserver(console), do get any error messages? Are you using the default port (80)?

---

