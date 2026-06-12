---
title: "New home server setup - suggestions please!"
date: 2008-12-10
forum: Server Platforms
---

### Post by Jeztastic on 2008-12-10
Hi,

I've got a Dell Optiplex GX1 - Piii 450 with 768 MB RAM, which I want to turn into a headless file server and music centre with a squeezebox (which I hope to get from Santa).

The plan is:

_Server_

Connected to the router and to some speakers

Running:

- Ubuntu 8.10 server edition
- ssh
- Samba
- sFTP
- CUPs
- Squeezecenter
- Squeezeslave
- Transmission

_Client_

XP Home Laptop

Via Web Interface -

Webmin
Transmission
Squeezecenter
CUPS
Softsqueeze

Other Interface -

WinSCP

Comments and suggestions please! I hope eventually to be able to access it outside the home network, and use WOL. 

I know this is a somewhat frivolous post, but I am getting impatient waiting for the Hard Drive and PCI-SATA card to arrive.

I have also heard that Debian may be a better server choice. How easy would it be to get the above setup running with Debian?

---

### Post by pdtpatrick on 2008-12-10
You plan on putting all of this on one server? lol gonna be interesting how many attempts you gonna get from people trying to exploit your FTP server security :)

---

### Post by CrucifiedEgo on 2008-12-10
That seems pretty standard.  Check out Jinzora -- that's what i've been using for a media center for years. for FTP, try torrentflux for a web interface.  if you set it up you can download it to a share you can access using samba, which is a very nice config (for me at least).  

Personally, I'd use 8.04 server instead of 8.10.  Reason being, support for 8.04 will last much longer than 8.10, unless you plan on dist-upgrading every few months.  

when you open it up to the outside world, take a look at fail2ban -- it will prevent hackers from brute forcing your logins, and it can work with sshd, ftp, even apache.

---

### Post by Jeztastic on 2008-12-11
Thanks for the suggestion, Crucified Ego. I am going with Transmission because it will run as a daemon with a java interface on the client, but I don't have to setup a full LAMP server to run it. I've tried that in the past, and to be honest it's way more than I need, and a little bit too complicated for my linux skills.

Is fail2ban basically a firewall? Was going to ask a few more questions about that. I take it Ubuntu will have ports to outside world closed by default? As you can see, I'm a little hazy on details of security, not done my research yet.

---

### Post by Iowan on 2008-12-11
[Here]("http://www.ubuntux.org/preventing-brute-force-attacks-with-fail2ban-on-debian-etch") is an article on **fail2ban**, as well as their [Main Page]("http://www.fail2ban.org/wiki/index.php/Main_Page")

---

### Post by Jeztastic on 2008-12-12
Thanks, that's really handy. It looks like a really useful service. 
Any recommendations on guides to IPtables?

---

### Post by lykwydchykyn on 2008-12-12
For people new to Linux, I'd recommend using a front-end to iptables.  Webmin has a nice graphical (web-based) front-end, and firehol is a decent console-based front-end.  I know there are many others too, but that's what I use.

Consider, though, that to open ports to the outside you're going to have to forward them through your router explicitly.  My approach is only to forward the ports I want accessible.

BTW, ssh and sftp are both installed when you install openssh-server.  So that's pretty straightforward.

---

### Post by Jeztastic on 2008-12-12
Oh great, didn't realise Webmin had an IPtables frontend.

That's a good point about opening ports through the router.

So I don't have to install vsftpd or proftpd as well as openssh-server?

---

### Post by lykwydchykyn on 2008-12-12
No, and you don't want to.  Because vsftpd and proftpd only provide regular FTP, not sFTP.  openssh-server provides ssh and sftp.

Of course, it means windows clients need to use winscp; but since XPSP3 windows hasn't had a decent built-in ftp client anyway, so they're going to need to get some kind of client software either way.

---

