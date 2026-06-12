---
title: "[SOLVED] Help setting up IRC server with encryption"
date: 2008-09-03
forum: Server Platforms
---

### Post by null-cipher on 2008-09-03
I'm looking to set up an IRC server on a little hobby server I'm running.
The server is running Ubuntu Server Edition 7.04.

I have installed the ircd-hybrid and hybserv packages, and I was just curious to see if anybody had any pointers on what sorts of modifications I would need to make to the ircd.conf to get SSL working.
I chose hybrid as it had SSL mentioned in it's package description.

I have tried to connect to the server from my desktop machine using my irc client, and I am getting a connection refused error.
Not suprising as I haven't modified the config file yet...

As always, any help is greatly appreciated.
Thanks

---

### Post by bbala2020 on 2008-09-08
I've a desktop edition of ubuntu hardy installed.. I want to install an Irc server so as to enable chat in my LAN. I want to setup either with encryption or without encryption.. How do i set it?

---

### Post by kennedy7 on 2008-11-23
open /etc/ircd-hybrid/ircd.conf with this command: "sudo gedit /etc/ircd-hybrid/ircd.conf" there will be pointers along the way. Second go to where it says "name of server" and change the name to whatever you want. 
Then change the description. Then go to line "listen" and change the vhost thing to your ip. then change the port it listens on to 6667 or 6665.
Thats all you need to do so that you can connect to it.
The rest will easily explain itself.
PS. i got a working irc server. For real!

---

### Post by usererror on 2009-01-21
I've got my IRC server up and running on a local network only, but does anyone know how to make it more secure?

I want to make it so certain rooms have passwords.
I also want it to automatically make certain user names operators automatically.  Can that be done?

I thought I did this via the ircd.conf file but it's not working.

---

