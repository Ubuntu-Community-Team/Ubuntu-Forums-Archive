---
title: "File sharing over the internet"
date: 2013-01-15
forum: Server Platforms
---

### Post by Tjalleman on 2013-01-15
I’m an Ubuntu Server newbe and I have a few questions concerning file sharing over the internet. I’ve read several threads at this forum and others and googled a lot and found tons of information. With that information in mind, I have to choose witch way of file sharing is the best for me. Unfortunately I haven’t found exactly a way to manage the file sharing I have in mind, so I hope you guys can help me out! 

My setup:
- Ubuntu Server 12.04
- LAN-file sharing with Samba (works great)
- A special group for my friends (‘Friends’)
- Some directories/actions are restricted for this group by editing the permission rights (e.g. Documents and writing)

What I am trying to do:
- Share files over the internet. For myself, to access my files from anywhere on earth. And for friends, mainly to share pictures and music.
- Do this web-based, thus without special client software
- stick to the permission rights

What I already found:
- There are several ways to establish online file sharing: ftp, openssh/sftp, apache
- ftp is not a secure way to do this, but it is web-based.
- openssh/sftp is the most secure way to do this because of the ssh-tunnel. Unfortunately this needs ssh-client software which can be problematic if I’m in an internet café and cannot install software.

My questions:
- As far as I know, ftp sharing is the best way to accomplish my file sharing, but this is not really secure. How unsecure is this sharing? Is it possible for someone to hack into my system and copy all the data?
- Is there a way to access an openssh/sftp file sharing web-based? If yes, how do I manage this?
- Or is there another way to manage this?

Help would be appreciated very much! Thanks in advance!

---

### Post by Cheesemill on 2013-01-15
I use [AjaXplorer]("http://ajaxplorer.info/") running over https on my server.

---

### Post by Tjalleman on 2013-01-15
Thanks for the suggestion! I’ve installed LAMP and Ajaxplorer en indd it works! At least, I can loggin from my LAN. Still, I’ve three questions:
1: This is probably a noob-question: how do I connect to my server via internet?
2: Is it possible to sync the Ubuntu-users with the ajaxplorer-users?
3: Is it possible to let ajaxplorer sync the folder structure as it is? Including the persmission rights?

---

### Post by LHammonds on 2013-01-15
[OwnCloud]("http://owncloud.org/") is another option.

---

### Post by Mopar1973Man on 2013-01-15
Ok here is how I've got my little test server setup.

First off I went out to [http://www.no-ip.com/](http://www.no-ip.com/) got a domain name for my computer. Then installed Webmin 1.610 [http://www.webmin.com/](http://www.webmin.com/) you might want Virtualmin [http://www.virtualmin.com/](http://www.virtualmin.com/)  if you going to host more than one site. Virtualmin installs all the servers for you (Apache, PHP, MySQL, email, etc.)

Then you can host your files as needed. If you want to go a step farther you could most likely add some PHP software for control purpose and then keep the public out of your site too.

---

### Post by d4m1r on 2013-01-17
Simple...Just install and run a SFTP service on that box...

Then anyone with a Ubuntu, Windows, or OS X, SFTP client installed locally on their PC, could connect to the server securely and transfer files to and from the box. You are also then able to control group and user permissions.

---

