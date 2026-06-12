---
title: "How do I secure  MythWeb from the outside world?"
date: 2006-08-02
forum: Server Platforms
---

### Post by xinix on 2006-08-02
When I first installed Mythtv a while back I also installed mythweb and really liked it.  It wasn't long until I realized that at that point my computer was open to the world.  So, I uninstalled apache and forgot about mythweb.  The current incarnation of mythweb requires that users setup password to access it (making it a little more secure).  My problem is that anyone can still see that my computer is running  a server and I don't want that.  I'd like to give it another try but want to block all outside access to the server.  Is there any way to setup apache so that it only serves to my computer.  Also what is a good firewall to use?  I'm guessing that a firewall would be involved in hiding apache from the outside world.

Thanks.

---

### Post by bward1 on 2007-03-02
In order for the outside world to be able to see in, your router has to be set to forward traffic on a given port to that server, and the server has to accept traffic on that port.  Port 80 is the standard for apache, but you can change which ports it listens on by changing the file /etc/apache2/ports.conf.  If the webserver is listening on a port that the router does not forward than the outside world should not be able to access it.

---

### Post by genesis[OFT] on 2007-03-03
And if you DO still want to be able to acess mythWeb from the outside world, however, ensure that only YOU know that the server runs there, you might want to take a look at Port Knocking.

---

### Post by bward1 on 2007-03-03
There are ways to secure your mythweb connection other than just not telling anyone it exists.  [http://www.mythtv.org/wiki/index.php/Securing_MythWeb](http://www.mythtv.org/wiki/index.php/Securing_MythWeb)  -- I used the second option presented here and everything worked fine.  One thing to note though, in ubuntu apache config files are found in /etc/apache2/ not /etc/httpd/ but other than that it is fairly easy to setup.  This will require a username and password to login (or even cooler, to login anywhere except for your LAN) so it will be secure.

---

