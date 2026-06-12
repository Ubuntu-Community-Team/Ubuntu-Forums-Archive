---
title: "Moving from Windows 2008 Server to Ubuntu Server 12.04"
date: 2012-08-08
forum: Server Platforms
---

### Post by Vidorin on 2012-08-08
Hello, I'm looking to move away from Microsoft and use Ubuntu's server operating system because knowing how great Ubuntu is, I can not deal with the substandard software that is Windows, anymore. I would like to set up a network fileshare, enable a remote access client and run Neverwinter Nights Linux Server client 1.69 but I am unsure where instructions are for that. I googled it and I found nothing really.  So I ask the community for its assistance, thank you in advance everyone.  :D

---

### Post by Vidorin on 2012-08-11
85 views and no replies.  Well I will say that I may try and use Ubuntu Desktop instead of Server.  But I'd still need to figure out how to do what I want to do in that.  Such as setting up remote access to it, the Neverwinter Nights Linux Server Client, the Neverwinter Nights Extender (NWNX) also to work in Ubuntu 12.04 and a fileshare.  But the Fileshare I believe I can just use Samba.

---

### Post by darkod on 2012-08-11
Yeah, for fileshare use Samba.

When you say remote access, what exactly do you mean? Access for you to manage it remotely or users will need to enter the server remotely too?

If it's only remote administering, you usually use SSH for that, so when installing the server version and the menu to select roles comes up, select Samba andOpenSSH.

As for Neverwinter, I have no idea what that is.

---

### Post by LHammonds on 2012-08-11
If you would like to know how I setup an Ubuntu Server, take a look at my signature.

---

### Post by SeijiSensei on 2012-08-12
Did you read the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/index.html")?

---

