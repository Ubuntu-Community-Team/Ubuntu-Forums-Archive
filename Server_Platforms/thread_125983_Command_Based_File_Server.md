---
title: "Command Based File Server"
date: 2006-02-05
forum: Server Platforms
---

### Post by Flashstar on 2006-02-05
Hi, I'm fairly new to linux at the moment and I was wondering if anyone could walk me through setting up a simple linux fileserver. When I installed linux on the computer which i'm planning on using for a server, I selected server mode at the beginning, so i'm stuck with a command line. I don't mind using UBUNTU like this though, so if someone could show me how to install and set up SAMBA, then configure it, that would be awesome. Also, what else can you do with a Linux server an Windows clients?:-k I read the online guide and it only tells you how to configure UBUNTU through a GUI.

---

### Post by el3ktro on 2006-02-05
Installing Samba is easy: Just type "sudo apt-get install samba" to do this. Setting up Samba depends highly on what you want to do for it, but I REALLY suggest you to go to [www.samba.org](www.samba.org) for that, in the left-hand menu you'll find an entry called "Samba by example" which guides you step-by-step to set up a Samba server. It's really easy, you have to edit only one confiuration file called "/etc/samba/smb.conf" and this config file has probably the user-friendliest and most logic syntax I've ever seen in a config file (others could learn from this, really (pointing my finger at X.org))

Well what else could you do with a Linux server:

- Set up a mail server, so that all your mails are stored on the server, and you can get them via IMAP on your Windows machine. The server could filter out spam before it even gets in your Inbox, and it can scan all mails for viruses

- You could make regular backups of your important data to your server

- If you have more than one Windows machine, perhaps setting up a WWW proxy would be a nice idea

- You could install something like mldonkey to have a 24/7 P2P fetching machine (bad advice, this is very likely to be illegal in your country, but I just wanted to tell you anyway)

- Install a firewall on your server and route all Inet traffic trough the server for hihger security of your Windows machines ( depends on how your Internet connection works)

- Well thousands of other things, like running a Doom/Quake/UT2004 game server, installing FTP and SSH together with dyndns or noip so you can access your server from anywhere in the world and upload/download files, control it remotely etc.

The only limit is your phantasy \\:D/ 


Tom

---

