---
title: "Correct setup and usage of accounts. Best practice advice needed."
date: 2024-08-24
forum: Server Platforms
---

### Post by swerve225 on 2024-08-24
Hi.

I am new to server administration and am in need of advice on which accounts to setup for working on the server.

I notice that the /cgi-bin folder is owned by "root".

and the /html folder is owned by "www-data".

So the account I created when installing the server is unable to create files in either of these directories.

So my question is, since my server (24.04 LTS) will be a public facing server, how should I create the accounts for putting content in these two directories?

Should I just create one sudo priviledged account who can access both /html and /cgi-bin.

Or is it best practice to have seperate accounts for administering these folders?

I was going to create two seperate accounts, but then was unsure, because if I compile my .cpp back-end programs in the cgi-bin folder with my cgi-bin user account, will that prevent them being used in my /html folder?  

I would appreciate any advice on how best to go about this. Kinda confused. 

Many thanks.

---

### Post by currentshaft on 2024-08-24
rsa

---

