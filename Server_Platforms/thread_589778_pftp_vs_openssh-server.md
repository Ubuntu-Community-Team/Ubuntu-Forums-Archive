---
title: "pftp vs openssh-server"
date: 2007-10-24
forum: Server Platforms
---

### Post by bone2006 on 2007-10-24
I was reading this tutorial on installing the perfect server with ubuntu 7.10 and every tutorial installs openssh-server and the pftp or another ftp server.

My question is that I've been using openssh server then creating users using the adduser command.  The new user doesn't have admin priveledges and it sets up an SFTP server.  Maybe it's the lazy way of doing it, because openssh server is already installed, seems like one less  program (PFTP) program I have to worry about having a possible security flaw.

So is there anything wrong with using openssh-server as an SFTP server?  I'm talking about having two admin accounts and maybe 4 or 5 other accounts on the system using openssh-server for the SFTP server.......vs setting up and installing other server for PFTP and then turning it into a SFTP server?


[http://howtoforge.com/perfect_server_ubuntu7.10](http://howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by whit on 2007-10-27
pftp? I don't see that one in the repositories. If you're giving people SSH accounts, SFTP comes for free. The only reason to also give them FTP is if they need more complex file manipulation options than SFTP gives them. SFTP is far more secure.

If you decide you need and FTP server anyway, you might look at pure-ftpd as well as the more-standard proftpd. I've been happier with it, having run both, and it has a better security record.

---

### Post by bone2006 on 2007-10-28
maybe I don't understand what FTP server manipulation can be done that you can't do with the openssh-server?

I'm referring to setting up a server, then installing openssh-server.  Now I have a a choice on where to go from here.  One choice is installing FTP server as in the link pure-ftp or any server, doesn't matter............not the point............

Or create an account on the server and have them use the SFTP server to login.  The only thing I can figure is that they can read all the data that's on the system if they have a system wide account, not sure if you can stop them from accessing certain directories.  

If your saying file manipulation.........what can't I do with using SFTP that comes with openssh-server that I can do by setting up a seperate FTP server?

---

### Post by MJN on 2007-10-29
My advice/opinion: Stick with SFTP and avoid FTP at all costs.

SFTP is trivial to securely configure (indeed it works straight out of the box) and is firewall/NAT friendly (count the number of threads on here where FTP users are having trouble with PASV/ACTIVE connections).

The end of FTP is nigh, well okay not quite, but unless you *need* it stay away.

Mathew

---

### Post by cox377 on 2007-11-16
> **bone2006 said:**
> maybe I don't understand what FTP server manipulation can be done that you can't do with the openssh-server?

I'm referring to setting up a server, then installing openssh-server.  Now I have a a choice on where to go from here.  One choice is installing FTP server as in the link pure-ftp or any server, doesn't matter............not the point............

Or create an account on the server and have them use the SFTP server to login.  The only thing I can figure is that they can read all the data that's on the system if they have a system wide account, not sure if you can stop them from accessing certain directories.  

If your saying file manipulation.........what can't I do with using SFTP that comes with openssh-server that I can do by setting up a seperate FTP server?

Did you manage to find an answer on how to restrict users access to one directory and without shell access

---

