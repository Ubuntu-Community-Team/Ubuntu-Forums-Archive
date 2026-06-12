---
title: "SSH? FTP? programs running when logged off? Wake on LAN?"
date: 2006-09-19
forum: Server Platforms
---

### Post by Skylive on 2006-09-19
Hi! everyone, I'm new to Ubuntu and I would like to ask some obvious questions.

I would firstly like to state that everything here must work, [COLOR="Blue"]without the user being logged on. (If it is possible to do so).[/COLOR] I hope that everything can go through port 443 if possible, as I will be connecting through a firewall that only has port 443, and 21 open.

First question: How do I setup SSH? I would like to control my computer remotely on port 443, but I would like to do so in GUI mode. I'm not good with the console, and I would like to avoid it. If ssh cannot use GUI, other than VNC, what else will work?

Second question: Which is the best ftp server program? That will work with the user not logged on, if possible.

Three: How can I wakeup my Ubuntu remotely? I would like to save power, and only switch on my computer when I need to transfer files using an FTP server program. Is there a remote wake-up-on-LAN program available, to do what I want? fyi, I would be using a windows computer to turn on my Ubuntu computer... possible to do so?

Thank you for all the help in advance, feel free to give any advice, or opionions.:D

---

### Post by karamba_kid on 2006-09-19
Those services as well as most other unix services will run when all users are logged off.  For remote access to my windows machine I use TightVNC tunnelled over OpenSSH of course.  With ssh doing all the tunnelling I can get away with just having the one port that I have ssh running on open.  It's really not that hard to setup and get working from the command line.  Just don't be intimidated and read the documentation for it.  If your looking to access the Linux box remotely you may be interested in freenx.  I haven't used it but I have heard it's a lot faster than VNC.  For waking up your machine remotely a lot of desktops have a feature called Wake On LAN.  I would look for somekind of settings in the BIOS.  I'm not the one to ask about doing anything fancy like having it suspend and wake up to where it left off or anything like that. Infact I haven't ever played with wake on lan so I'm not the one to offer any advice setting that one up, but I do know that once the system boots the services (ssh,Apache, etc) will be running and listening for connections.

---

### Post by Skylive on 2006-09-19
Hi! Thanks your the super fast response... well, no one knows a GUI remote access software??? If not, I'll just stick to Freenx.

What program should I use for running a SFTP/FTP server? I'm afraid that this question has not been answer, so i myaswell be put up again.

Anyone know any good free Wake on LAN softwares?

---

