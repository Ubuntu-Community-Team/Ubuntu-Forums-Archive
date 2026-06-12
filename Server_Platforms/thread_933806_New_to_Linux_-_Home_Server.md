---
title: "New to Linux - Home Server"
date: 2008-09-29
forum: Server Platforms
---

### Post by twinpeaksr on 2008-09-29
Hi!

INTRO:
Just started to work with Linux, recently, after much research I was pointed to Ubuntu as a good distribution to start with.  Giving it a shot I managed to get one laptop running 8.04 Desktop, and with much trial and headache, even got 8.04 Server running on my Server (I know, duh).

Being new, I still have some issues and was hoping this forum could help me out.

DISCLAIMER: 
I am really new to Linux, but through searching the web and forums, I gained some basic knowledge.  I also know the basics of networking (need for IP addresses, DHCP functions, etc...) and basic server types (Web Server is Apache, Samba, and that is about it).  I have a hardware guy, so that is in good shape, but still struggle with the software.  I will respond as I can but with a new baby, work and finishing another degree, it may take a day or two to respond.

SETUP:
Currently I have 
- Server - (3Ghz, 1GB RAM, 40GB Boot, 1.5TB RAID5 Array, 8.04 Server)
- Workstation - (2.4Ghz, 4GB RAM, Dual 320GB, Vista 64bit)
- Laptop (2.4Ghz, 3GB RAM, 160GB, Vista 32bit)
- Linux Laptop (1.6Ghz, 1.25GB RAM, 30GB, 8.04 Desktop)
- Wife's computer (2Ghz, 1GB RAM, 60GB Hard Drive, XP, will move to 8.04 Desktop)

As you can see I have a mix of Linux and Windows, which is part of what is causing my issues.

GOAL:
What I want to do is have the server take care of all the network stuff (IP assignment, name translation, permissions to server drives), as well as be a file server to both windows and linux, and have future expansion to include web server, proxy server (protect the kids), and database server (have many basic databases).

COMPLETED:
So far I have 8.04 Server installed, Samba running (Read/Write seems to work fine on the 2 users), and NFS/NIS setup with Read only access to server shares.  All with no GUI installed (I am impressed with myself, sorry).  Also have the Webmin running, but only with IP address.

ISSUES:
- Allow the server to be accessed by name not just IP - The server is named "Trinity" and will show up as such on windows machines, but for Webmin only works based on IP.  I believe this has something to do with DNS.
- NFS/NIS - not sure which I am using or what NIS even stands for, but found that I need it to share files with the linux boxes and even got it to partially work.  but can not write to the server as the drives are all locked to read only.
- Identify what I need to get the Network server working - I know I need a DHCP server, but do I need DNS, Wins, Netbios, etc...  A little confused on what I need to install, I am sure there is data to install these, but I have not found anything that tells me what I need to install.
- Remote Admin - Is there something outside of Webmin that I can pull up a terminal as if I am at the server?

Sorry for all the questions, but I started into this and it is getting addictive...it is exciting when it works, and I would like to get our network setup right so that I can build from there.  If there is any data that I need to provide let me know, any help is greatly appreciated.

Thanks!

~R~

---

### Post by thefekete on 2008-09-29
First off, let me recomend two books that have been a huge help and even saved my rear a few times:

[_How Linux Works_ *by Brian Ward*]("http://www.amazon.com/How-Linux-Works-Brian-Ward/dp/1593270356/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1222739356&sr=8-1") - Covers everything you need to know to get around a linux server (Ubuntu, Redhat, whatever). It's a great starter book that covers the essentials.

[_Linux Administration Handbook (2nd Edition)_ *by Evi Nemeth, Garth Snyder, Trent R. Hein*]("http://www.amazon.com/Linux-Administration-Handbook-2nd-Nemeth/dp/0131480049/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1222739481&sr=8-1") - This is essential for running a linux server and network. This book covers just about every service you'd want to run. This thing is long, but very detailed and even has sections to explain the differences in distributions (really nice). I literally take it to work and back home with me every day I use it so much...

So I'm serious, before you do anything else get these books.

As far as your issues go:

**Server Name:** as you noticed, winturd picks up on the server name through samba. In order to access it from Linux machines you can run a full blown local DNS server (pain in the butt and not worth it for one server) -OR- simply create an entry in each Linux machine's '/etc/hosts' file. Just add a line like the following to the bottom:
```
192.168.0.123    server-name
```
This causes each linux machine to automatically substitute "server-name" with the IP you specify any time you enter it as an address (from firefox or the command line).

**Gateway Router:** I actually just linked some howto's in another thread, check out the reply:
[http://ubuntuforums.org/showpost.php?p=5879060&postcount=9](http://ubuntuforums.org/showpost.php?p=5879060&postcount=9)

**Remote Administration:** SSH is your friend. It will basically give you a terminal prompt over a secure connection as if you were sitting at the server. I'd also recommend [DenyHosts]("http://http://denyhosts.sourceforge.net/") if you're going to have this sitting on the internet... But its not necessary.

Unfortunately, I haven't tooled around with NFS/NIS. However, the Admin Handbook covers '/etc/hosts' distribution via NIS and has a lot of info on NFS as well.

Hope that helps... If you only get one of those books, get the Handbook. It's worth it's weight in gold...



-dan

---

### Post by lykwydchykyn on 2008-09-30
NIS is a centralized authentication directory, kind of a precursor to LDAP/AD/eDirectory.  You shouldn't need it just to share files.  In fact, all you really need is SSH.  You can then use SFTP or sshfs (on the linux clients) to share files.  But NFS will work too.  Whatever works best for you.

You can set up a simple DNS server using DNSmasq.  It's very easy to set up, and can just use the server's /etc/hosts file.  It's quite lightweight and perfect for name resolution on a small network.  Much easier than hacking host files (where is it on Windows again? c:\windows\system32\drivers\yada\yada\yada\...).

You should not have any need for WINS, on a small network leaving your Windows machines resolving via broadcast should be acceptable.

---

### Post by twinpeaksr on 2008-09-30
Thanks for the info, sorry for the delay.  I will definitly look into the books, always good to have a reference.  On the hosts, I am assuming I can update both the Linux and Windows machines, but what would be a more permanent repair for the IP issue?  I have others who bring in computers to the network, but it would be nice to have it to work for that.  Would it also fix the issue with Webmin (currently only works for IP address)?

Thanks for the info on NIS, sounds like I do not need that, how does SSH work? Is it better to use SSH than NFS?  What is the difference between the two?

Thanks again for all the help, will be trying this tomorrow (sorry, been sick the last 2 days).

~R~

---

