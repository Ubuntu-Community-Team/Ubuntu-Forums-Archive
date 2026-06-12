---
title: "Apache and File Permissions"
date: 2009-04-02
forum: Server Platforms
---

### Post by rohitthakral on 2009-04-02
Hi Guys, Apologies if this is trivial stuff but I need help as I can't figure out the right configuration. Here is the setup - I am using Apache2 as the web server, VSFTPD as the FTP server.

I have used /home/USERNAME/ as every user's hosting space. Now the problem comes when they upload PHP scripts and because they uploaded it they are owned by these users. Apache can read them but can not do transfer/create/remove actions on these files/directories.

If I change the permission to 777, it's not secure and is not recommended. So, I need help so that I just create a new user and give them their username and password and they can uploade files to the server and apache can do operations on the same file/folder. Of course every user should have their own web permissions as well.

Thanks for you help.

Rohit

---

### Post by kamaji792 on 2009-04-03
I don't fully understand the security implications of what you are doing, however:

Can't you set the permissions to 704.  Full rights to the user and read rights to everyone else?

---

### Post by rohitthakral on 2009-04-06
> **kamaji792 said:**
> I don't fully understand the security implications of what you are doing, however:

Can't you set the permissions to 704.  Full rights to the user and read rights to everyone else?
Ok.. Don't get it. Sorry for being dumb.

But if I do that user will be able to modify files using FTP etc. but Apache will not be able to create/edit files/folders. Isn't that correct?

---

### Post by lykwydchykyn on 2009-04-06
Why does apache need to edit the scripts?  I've never had www-data own any web content, it works fine.  Apache (www-data) just needs read/execute to run scripts.

What am I missing here?

---

