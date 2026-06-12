---
title: "Allowing a friend to FTP and send files to one of my drives"
date: 2007-07-26
forum: Server Platforms
---

### Post by iPat on 2007-07-26
Let's say I want to allow a friend to connect to my computer remotely and upload some files onto one of my drives. What would be the easiest way to go about doing this.

I need a pretty idiot-proof guide on how to do this, I don't really have any background in this stuff.

---

### Post by dcstar on 2007-07-27
> **iPat said:**
> Let's say I want to allow a friend to connect to my computer remotely and upload some files onto one of my drives. What would be the easiest way to go about doing this.

I need a pretty idiot-proof guide on how to do this, I don't really have any background in this stuff.

Create a new basic user account for your friend (then he can log in with his own username and password using FTP), and then set up your network environment to allow incoming FTP connections.

The first part is easy, the second may be tough depending on your setup and what security you want to compromise.

Once you get both of these sorted out, your friend can connect in and dump files into his user directory, which you should then be able to access (as the system owner).

---

### Post by iPat on 2007-07-27
> **dcstar said:**
> Create a new basic user account for your friend (then he can log in with his own username and password using FTP), and then set up your network environment to allow incoming FTP connections.

The first part is easy, the second may be tough depending on your setup and what security you want to compromise.

Once you get both of these sorted out, your friend can connect in and dump files into his user directory, which you should then be able to access (as the system owner).

I installed GPROFTPD on my system and added a user account for my friend. However, I still don't understand how he's going to connect to me. What I mean is, what address would he put into his ftp client in order to log in to me?

---

### Post by HermanAB on 2007-07-27
Hmm, a few things to consider:
a. Is you server directly on the net or is there a firewall between you and the net?
b. If a firewall, then you have to allow incoming FTP connections on port 21 and forward it to your server.
c. Forwarding FTP connections is difficult, since it uses a random high port for the data transfer, so you need a FTP connection tracker.
d. FTP is insecure.  The user name and password are exchanged as plain text.
e. SSH on the other hand, is secure and only requires one incoming port to be opened, port 22.
f. Getting SSH through a firewall is easy.
g. The FileZilla program (sourceforge) can do both FTP and SSH (SFTP).
h. You have to use long, randomized passwords or >9 characters, otherwise you *will* be hacked.

Just my tuppence worth!

Herman

---

### Post by iPat on 2007-07-28
> **HermanAB said:**
> Hmm, a few things to consider:
a. Is you server directly on the net or is there a firewall between you and the net?
b. If a firewall, then you have to allow incoming FTP connections on port 21 and forward it to your server.
c. Forwarding FTP connections is difficult, since it uses a random high port for the data transfer, so you need a FTP connection tracker.
d. FTP is insecure.  The user name and password are exchanged as plain text.
e. SSH on the other hand, is secure and only requires one incoming port to be opened, port 22.
f. Getting SSH through a firewall is easy.
g. The FileZilla program (sourceforge) can do both FTP and SSH (SFTP).
h. You have to use long, randomized passwords or >9 characters, otherwise you *will* be hacked.

Just my tuppence worth!

Herman


Is it possible you can point me in the direction (or explain yourself) what I need to do in order to set up ssh on my machine? I still don't understand what address my friend will be connecting to in order to connect to me.

---

### Post by HermanAB on 2007-07-28
Sshd is probably running already. Try this:
$ ssh yourusername@localhost

If you get a login prompt and can log in as yourself, then congratulations, you now have a login to your own login, but through SSH!  Type 'exit' to quit and get back to normal.

Do you have a homerouter/firewall?  Linksys, Dlink, whatever?  If so, log into that with your browser and check its IP address, that is the one your friend will have to use.  However, for that to work, you have to enable Port Forwarding in the Linksys/whatever and forward port 22 to your machine.

Herman

---

### Post by weblordpepe on 2007-07-28
SSH replaces:
FTP
Telnet
rlogin
And a few others.

Basically, if you have a SSH daemon (a SSH server) running, users can connect to your computer and on that one SSH port, they can transfer files, terminal in, use the computer as a proxy, you name it.

I use SSH to share files etc. Do the following on your server:
**sudo apt-get install sshd**
And set up the user, and they can SSH in right away and dump files there using a sFTP client (any decent FTP client will do this)

Your alternatives are:
A normal FTP server
Samba (Windows shares).
Floppy disks :)

---

### Post by Gremlinzzz on 2007-07-28
heres what the guide says [http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#FTP_Server)
:guitar:

---

