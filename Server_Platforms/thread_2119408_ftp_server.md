---
title: "ftp server"
date: 2013-02-23
forum: Server Platforms
---

### Post by mourgolikos on 2013-02-23
Hello,
this is my first post on this forum and my really first attempt to build up my own server.
I have never set up a server before so some things might not be obvious for me :p.

I have downloaded the Ubuntu server 12.04 version and I am willing to install it to my laptop to use it as a server with remote access over the internet.

My primary goals are:
1. to have access with an FTP client over the internet to the files stored on the server
2. and create (remotely) my own databases using mySQL

I would love if someone could tell me how to make this happen!

As I mentioned this is my first try to do something like that so please be as specific as you can.
thanks a lot :D

---

### Post by volkswagner on 2013-02-23
A good place to start is the sticky at the top of the server forum.  Go to the [Server 10.04 documentation]("https://help.ubuntu.com/10.04/serverguide/index.html").

A few more details on your setup will be helpful.

What type of client are you connecting with (Windows, Mac OSX, Linux)?
How many users will be connecting?


FTP is not a secure protocol.  You should be looking at SFTP for connections over the internet.  This can be accomplished over ssh or using an FTP client like Filezilla's SFTP connection.

You can administer MySQL using the command line (via ssh) or you can install a frontend like PHPmyAdmin.

Get familiar using [SSH]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html").

---

### Post by mourgolikos on 2013-02-23
I am willing to use only windows to connect.
I don't really care about the number of users. I would say just 2 at a time.

---

### Post by donniezazen on 2013-02-23
Rather use [https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by mourgolikos on 2013-02-24
I will go through the link that VW gave me about SSH.
As it concerns the guide donnie I' ve already tried to configure my laptop using this. It didn't work out well. I was getting errors during the setup and messages telling me that the commands/files etc. have not been found. That's why I came here.
Also, how should I configure my network? Do I need a static IP? If so how do I set it? Do i need to make any changes to the router?
How should I configure the ssh?

---

### Post by mourgolikos on 2013-02-24
I installed the 32-bit Ubuntu server 12.04 without the LTS.
Then I gave a look at the SSH guide and I followed step by step the instructions to set up the SFTP server from [here]("http://yetanothercomputingblog.blogspot.co.uk/2012/05/ubuntu-setup-sftp-server.html")
How do I access my server now?
I get an error saying connection refused

---

### Post by volkswagner on 2013-02-25
You get connection refused while using an ftp client?

Are you trying from local LAN or outside of your LAN?  You should verify you can access the server internally, then open the correct port on your router, pointing to your servers internal ip address.  This will allow outside access to the ftp server.

I have never seen instructions like the one you followed for sftp setup.  I have no idea what the edits to ssh_config mean, nor why they would be necessary.

According to the instructions you followed, you will likely need user accounts for "yourself".  One account will be the normal user for system administration (allowing ssh access) and the second will be your ftp account.  Is this what you have done?

---

### Post by LHammonds on 2013-02-25
Not sure if this would directly help you but I have documented how I install an Ubuntu Server for production use in my signature.  I also have documented how to setup FTPS (FTP over SSL) using Very Secure FTP daemon (vsftpd).  I also have a guide for MySQL server too.

Once you have your server setup and can connect to it from another machine inside your network, you will need to figure out how to get your router/switch/modem configured to allow outside traffic to be directed to your server (routing IP addresses and ports).  You will need to know the IP address that the entire world sees you (go to [www.whatismyip.com](www.whatismyip.com)).  If this IP address changes (non-static) then you might want to look at a dynamic DNS service so you can always find your home connection no matter where you are.

LHammonds

---

### Post by mourgolikos on 2013-02-26
> **volkswagner said:**
> You get connection refused while using an ftp client?

Are you trying from local LAN or outside of your LAN?  You should verify you can access the server internally, then open the correct port on your router, pointing to your servers internal ip address.  This will allow outside access to the ftp server.

I have never seen instructions like the one you followed for sftp setup.  I have no idea what the edits to ssh_config mean, nor why they would be necessary.

According to the instructions you followed, you will likely need user accounts for "yourself".  One account will be the normal user for system administration (allowing ssh access) and the second will be your ftp account.  Is this what you have done?

I get that error while trying to connect with filezilla from my laptop which is connected to the same connection via wireless. I am pointing my servers ip address (the one showing up when I type "ifconfig eth0). I have been using the same account for everything though.

---

### Post by mourgolikos on 2013-02-26
> **LHammonds said:**
> Not sure if this would directly help you but I have documented how I install an Ubuntu Server for production use in my signature.  I also have documented how to setup FTPS (FTP over SSL) using Very Secure FTP daemon (vsftpd).  I also have a guide for MySQL server too.

Once you have your server setup and can connect to it from another machine inside your network, you will need to figure out how to get your router/switch/modem configured to allow outside traffic to be directed to your server (routing IP addresses and ports).  You will need to know the IP address that the entire world sees you (go to [www.whatismyip.com](www.whatismyip.com)).  If this IP address changes (non-static) then you might want to look at a dynamic DNS service so you can always find your home connection no matter where you are.

LHammonds

I might reinstall the OS again and then follow your guides so it would be easier for you guys to help me! :-)

---

### Post by volkswagner on 2013-02-26
Did you specify port 22 in Filezilla connection setting?

---

### Post by mourgolikos on 2013-02-27
> **volkswagner said:**
> Did you specify port 22 in Filezilla connection setting?

Yes I did. I even tried to change to 2222 to both server and Filezilla but it didn;t work either

---

### Post by tenmoi on 2013-02-27
Don't ever use vsftpd for your server. I installed it and it refuses to be removed unless you modify its config file.

I don't know if the problem exists in 12.04, but this software is crap. Use something else.

Cheers,

---

### Post by mourgolikos on 2013-02-28
> **tenmoi said:**
> Don't ever use vsftpd for your server. I installed it and it refuses to be removed unless you modify its config file.

I don't know if the problem exists in 12.04, but this software is crap. Use something else.

Cheers,

I 've seen many ppl saying this! Thanks for the tip!

---

### Post by ranger12 on 2013-03-01
Well huh, I am running Ubuntu Server 12.0.4.2 on a dedicated file server and have had vsftpd running for 8 or 9 months now and haven't had any problems with it whatsoever.  I don't use Windows on the workstation, I have Desktop 12.0.4.2 on it and I can access my ftp server 3 different ways. 2 different ways with nautilus and 1 with firefox. I have it setup for anonymous download only and it works fine. Of course you mentioned you are using a Windows client and Filezilla so that is another animal.

---

### Post by LHammonds on 2013-03-01
> **tenmoi said:**
> this software is crap. Use something else.
Just because you can't figure out how to make something work doesn't make it "crap."  I've been using vsftpd in production for quite a few months now and have not had any problems.  Once I got it up-and-running, adding new accounts and expanding its use has been extremely easy to maintain.  The steps I documented in my sig on how to set it up can be repeated by anyone to make a similar server.

LHammonds

---

### Post by tenmoi on 2013-03-02
Maybe 'crap' is too strong a word. But it's not reliable software as it has a bug that's been in existence since 8.10 or so. Don't ever google or ask here how you can remove it.

---

### Post by ranger12 on 2013-03-02
Well since the software runs and runs reliably on my server I have no need to remove it. :) As a matter of fact, I just switched it from anonymous to user account login and configured it to allow only me to upload and all others download only. It works fine here.

---

