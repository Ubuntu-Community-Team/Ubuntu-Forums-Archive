---
title: "Securing 9.10 server"
date: 2009-11-06
forum: Server Platforms
---

### Post by jongudm on 2009-11-06
I have set up a home server (9.10 32 bit) which I am going to use for storage/backup and hosting a low-traffic web site.  I have installed apache2 and OpenSSH and both are now running.  I intend to use SSH and SFTP for administration and want to be sure that there is no other way to access the server short of breaking into the house (but that people can still browse the web site of course).  Are other access routes (like telnet, ftp, etc.) closed by default or do I need to close them manually?  If so, how do I close them?

---

### Post by BQAggie2006 on 2009-11-06
One thing that makes Ubuntu so secure is that by default, it does not enable any services or opens any ports. They leave it up to the user to do this. If you still feel a little uncomfortable, you can enable the Uncomplicated Firewall (UFW) that comes with Ubuntu and open the ports you need access to.

Enable UFW:

```
sudo ufw enable
```Allow HTTP Access (Port 80):

```
sudo ufw allow 80
```Allow SSH/SFTP Access (Port 22):

```
sudo ufw allow 22
```Check the status of the firewall:

```
sudo ufw status
```You can read more about UFW here: [https://help.ubuntu.com/9.10/serverguide/C/firewall.html](https://help.ubuntu.com/9.10/serverguide/C/firewall.html)

---

### Post by jongudm on 2009-11-06
OK, I see.  Thanks very much for your reply, that was exactly what I needed.

---

### Post by Thirtysixway on 2009-11-06
A big security help is changing the default ports, at least for things like ssh.  On my home server I had just tons of automated login attempts on the default ports.  As soon as I switched them to non-default ports, the attempts went away.

Not saying it will block attacks, just stop the automated ones from scanning say port 21, 22 for anything open.

---

### Post by jongudm on 2009-11-07
UFW up and running, will look into changing ports later.  Thanks everyone for your help!

---

### Post by evrensel on 2009-11-08
You may also consider using knockd to protect your open ports. See [http://www.zeroflux.org/projects/knock](http://www.zeroflux.org/projects/knock) for more information.

Basically, knockd will reconfigure your firewall settings (for a limited amount of time) after having received TCP syn packets in a certain order of pre-defined ports.

Following a sequence, you may then allow port TCP/22 open for 10 seconds, enough to establish ssh connection, after which the firewall stops allowing new connections.

---

### Post by jongudm on 2009-11-09
That looks very interesting!  I'll need to take a better look at this, thanks for the pointer.

And thanks again to everyone who answered or read this.

---

