---
title: "Samba not accessable externally."
date: 2006-04-28
forum: Server Platforms
---

### Post by projectle on 2006-04-28
I am attempting to set up an external file server for some of our employees to be able to remotely backup some of their files from their windows boxes to our network, however I have run into a bit of a snag. 

I installed Samba and everything is working fine inside our local subnet, however at this moment I am unable to connect into our Samba server from outside our network. 

This system is directly connected to the outside world on a static IP with no firewall currently enabled (it will have one as soon as I figure out what is going on though)

In the smb.conf file, I have added "hosts allow = ALL", yet I am still only able to connect in locally. 

Any help would be greatly appreciated.

---

### Post by behemot on 2006-04-28
To give your users access to files you need to deploy ftp server.
Vsftpd is in the repos and it is very easy to setup. You could find the howto in the Howto section of this forum.

Do not delay enabling firewall on external IP.  Do it ASAP.  Install an inexpensive router unitil you figure out how setup firewall and port forwarding.

Integrity of your network is compromized.

---

### Post by projectle on 2006-04-28
Lets assume that I did wish to employ Samba for file access, how would I get it functioning?

---

### Post by behemot on 2006-04-28
If you go with this assumption you would have to setup VPN server.  It could be PPTP server or openvpn.
Your users would have to use vpn client software to connect to your internal subnet.  To get more info, search for "virtual private network" in this forums and on the net.

And just keep your firewall on.

---

### Post by projectle on 2006-04-28
Thank you for the VPN suggestion, however there is something that I am wondering about...

Why can a Windows Box hosting a SMB share or an OSX box hosting a Samba share be accessable outside its own local network and a Linux box is not?

---

### Post by behemot on 2006-04-28
You may wish to have a look at this article:

[http://www.linux-mag.com/2001-05/smb_01.html](http://www.linux-mag.com/2001-05/smb_01.html)

---

### Post by LuisC-SM on 2006-04-29
[QUOTE=projectle]Why can a Windows Box hosting a SMB share or an OSX box hosting a Samba share be accessable outside its own local network and a Linux box is not?[/QUOTE]
Take a look to [this Tutorial]("http://www.howtoforge.com/samba_setup_ubuntu_5.10"), of course it's possible!

Regards

Luis C. Suárez

---

