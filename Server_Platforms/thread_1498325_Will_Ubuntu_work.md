---
title: "Will Ubuntu work?"
date: 2010-05-31
forum: Server Platforms
---

### Post by pontiacg5 on 2010-05-31
Hello,

I am trying to set up a LAN with some basic file and printer sharing, as well as either a VPN or FTP server. I am setting up a server for an office with about 4 computers and one remote computer at a home office. I would like the server to back up a selected group of folders on all of the computers as well as share some printers between them all as well. If all of the other computers are windows computers will Ubuntu work for something like this?

I would also like to host a website and e-mail server as well if the server is not loaded down too much. 

Can someone point me in the right direction? I know I can get windows server to work, but I would like to use something else if possible.

---

### Post by Zemblan on 2010-05-31
Linux is capable of doing all the things you mentioned. For interaction with windows systems, folder sharing etc have a look at 'samba'. You might consider either desktop Ubuntu, or the server version which comes without the gui.
There are a number of ftp servers available in the repositories, including: proftpd, wu-ftpd.
Obvious choice for a web server is apache, but there are others.
There are also multiple email servers. Linux is perfect for use as a server, very stable and secure.

---

### Post by ruuden on 2010-05-31
> **Zemblan said:**
> Linux is capable of doing all the things you mentioned. For interaction with windows systems, folder sharing etc have a look at 'samba'. You might consider either desktop Ubuntu, or the server version which comes without the gui.
There are a number of ftp servers available in the repositories, including: proftpd, wu-ftpd.
Obvious choice for a web server is apache, but there are others.
There are also multiple email servers. Linux is perfect for use as a server, very stable and secure.


What he said :)

It's good to see more people that want to use ubuntu as their server solution for their business.

---

### Post by hictio on 2010-05-31
If possible for you, I would keep the servers separated by their purpose, specially the one that will host the VPN (and perhaps the FTP server); that is one for the services that will be exposed to the internet, and another one for the internal services.
For the VPN, as well as firewall, web proxy, etc, etc, I would recommend you [Endian Community Edition](http://www.endian.com/en/community/) (yes, it is not Ubuntu Server ;) )
Unless you have a bazillion users, you can get away with pretty low spec box as the router/ firewall/ VPN server for your LAN.

---

