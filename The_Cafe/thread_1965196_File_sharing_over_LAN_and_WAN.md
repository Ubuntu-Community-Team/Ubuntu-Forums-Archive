---
title: "File sharing over LAN and WAN"
date: 2012-04-25
forum: The Cafe
---

### Post by rmcellig on 2012-04-25
**WAN**

At the moment, I am using Dropbox to share and store files. I love it! I was wondering if there may be an open source alternative solution that might be free. I am aware of other services like Wuala, Sugarsync etc... This is not what I am looking for. What I am interested in is alternative ways to share files with my friends, and hopefully the ability to store data as well.


What are my options?

**LAN**

At the moment, I am using Samba to share files over my LAN (consists of PC's, Macs, and Linux machines. I understand that there is an app called Freenas. It would be nice to have a central location of shared file that all computers in my LAN can access and use to share files as well.

 is anyone using this? 

Would I be able to se it up on a Linux machine with all the shared files on an external USB drive?

What are my options?

Should I post this in another forum?

---

### Post by Docaltmed on 2012-04-25
Ubuntu One has the ability to share files to a limited audience, and as you might guess, it's pretty well integrated.

Have you tried it?

---

### Post by rmcellig on 2012-04-25
Ya. I forgot to mention Ubuntu One. I have tried it. I'm just looking for something else. Maybe a peer to peer solution that might be open source?

---

### Post by HermanAB on 2012-04-25
scp
netcat
giver
ftp
nfs
samba

and:
rsync
unison

and things like:
webdav
opendocman
knowledgetree

and even things like:
subversion
git
cvs
rcs

The list goes on and on...

---

### Post by Ceiber Boy on 2012-04-25
The solution to your question (WAN) is dependent on how far your willing to go, you could pay for a fixed IP from your ISP and set up a FTP or even an SFTP Ubuntu server, and give your friends accounts to login and share information and act as online file storage.

For the LAN, SSH with key based authentication would be ideal, as with for the WAN. However a LAN normally considered a more secure environment than a WAN as your behind your own firewall, although it's not without risk! SMB is commonly used for compatibility between various devices, eventhough it's security could leave something to be desired

Regards

---

