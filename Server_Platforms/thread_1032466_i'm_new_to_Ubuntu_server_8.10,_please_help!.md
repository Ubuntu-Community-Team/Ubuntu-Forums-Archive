---
title: "i'm new to Ubuntu server 8.10, please help!"
date: 2009-01-06
forum: Server Platforms
---

### Post by unix7777 on 2009-01-06
Hello everybody,

I just have install 8.10 ubuntu server and i need to know what i should do.
I wan to use the server as FTP(file server no samba!) and print server.
In the process of installation i installed only SSH.
My opinion is that i have to manage first the startup daemons(processes).Than to set the firewall (i installed shorewall) but i can find how to set the rules.

Thank you previously!!!

---

### Post by nkassi on 2009-01-06
You can use SSH as an SFTP server which should work with most ftp client out there currently. 

As for your firewall, I'm not sure how shorewall works but you can also look online for tutorial on setting up iptables. Many basic firewall scripts already exists for your situation.

---

