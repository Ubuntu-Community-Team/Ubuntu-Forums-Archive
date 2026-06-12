---
title: "Ubuntu Wireless Home Setup"
date: 2015-04-27
forum: Server Platforms
---

### Post by RevDavid on 2015-04-27
Evening everyone,

I hope this is the right area to post this. I did a search and couldn't find what I was looking for. I am trying to setup a home network that will all communicate through my wireless connection. Basically what I have is the following...

Laptop 1 - Ubuntu 15.04
Laptop 2 - Windows 7 Professional
Laptop 3 - Windows 8.1
Desktop - Will be installing Ubuntu 15.04

What I am wanting to do after installing Ubuntu on the desktop is to make it a web server that the 3 laptops can connect to by simply clicking on a icon and accessing the information on the desktop web server. i am wanting all 3 laptops to have access to the internet. The desktop needs internet access as well but nothing from outside of the internet in. The desktop itself does not necessarily need to access the laptops since it is going to be an internal server.

If anyone can assist or point me in the right direction I would greatly appreciate it.

Thanks for your assist :D.

---

### Post by papibe on 2015-04-27
Hi RevDavid.

If you have things on the server you want to share with the other machines, a web server would not be my first suggestion.

Let's say you have your music, or you want to be able to backup your laptops to the server. In this case you may need ssh, so you can use sftp, scp and rsync to transfer files from and to the server. Another alternative could be to share directories of the server so they can be mount and easily used 'as local' directories on the laptops. For that case, take a look at NFS and samba.

Access restrictions on the serer are delicate. You need Internet access so it can be updated. You need access to the laptops because, it can't share its content unless it has access to the clients.

Does that help? Let us know if you have more questions.
Regards.

---

