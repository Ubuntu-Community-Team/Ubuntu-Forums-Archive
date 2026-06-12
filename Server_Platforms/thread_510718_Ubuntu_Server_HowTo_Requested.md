---
title: "Ubuntu Server HowTo Requested"
date: 2007-07-26
forum: Server Platforms
---

### Post by EvilMarshmallow on 2007-07-26
Ok, I need to linux environment gurus to help me out here...

A SMALL nonprofit that I work with is moving into a larger building, and they want me to design the LAN.  Complete with server, network hardware, VoIP phones, the works.

I can do everything but set up the server in Ubuntu.  I'm a linux noob, although I've got a lot of Windows experience (like that helps! :lolflag:)

They're already halfway to the point where they could have Ubuntu desktops... basically all they do in their offices is use OpenOffice for Windows and web surfing as needed.

I don't have a lot of money to spend so I have to stack a lot of features on a single server until they're able to buy more hardware.

I want to set up a server to do the following:

[LIST=1]
[*]Authenticate users against the Server's list for easy account management
[*]Provide mailboxes for each user that I can manage from a central location (we have a domain name already through a hosting company; how do I set up a mail server?)
[*]Share files among the users from this server
[*]Roaming profiles; I'd like for their settings to follow them anywhere in the building
[*]Remote access, so I can manage stuff from home
[/LIST]

So, fellow Ubuntu-geeks... if you were going to do this, how would you make it happen?  Feel free to just provide links to how-to's for parts of the process... I can follow good directions!

---

### Post by Subnet on 2007-07-27
For the authentication you could use OpenLDAP or Samba. Here is a link to a howto at howtoforge on setting up a mail server: [http://www.howtoforge.org/perfect_setup_ubuntu704]("http://www.howtoforge.org/perfect_setup_ubuntu704"). Samba can help out with sharing files between users as well. Here is a howto on setting samba up: [http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto").  You could always use SSH or VPN for your remote management. Well, I hope those few tips help ya out.

Subnet

---

### Post by bmathis on 2007-07-27
sounds like a great project, i wished i lived close to help you out. I think subnet pretty much answered your question. 

Samba or LDAP for authentication
Postfix, Courier IMAP/POP, Squirrelmail, and SpamAssassin for Email (this is my setup, its fast and easy to configure)
Samba for files sharing with Windows or NFS
SSH or VPN for remote management. Another alternative is Webman.

Please, when completed, share your documentation it will be a great resource for anyone looking to do the same thing.

---

