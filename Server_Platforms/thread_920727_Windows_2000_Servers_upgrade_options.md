---
title: "Windows 2000 Servers upgrade options"
date: 2008-09-15
forum: Server Platforms
---

### Post by Mart on 2008-09-15
I am sure I'm not the only sys admin in this mess.  I've a bunch of outdated unsupported 2000 servers that need upgraded and about $10 to figure out how to do it.  I think where I work has become so use to the fact that I'll make something work that they have forgotten that sometimes a little funding is a good thing.

I'm not here asking should I upgrade to 2008 server or not.  I'm more or less looking for someone else who may have or is doing what I'd like to do, switch to Ubuntu Server.  Can a moderately competent "linux" sys admin setup and maintain a stable replacement for Windows 2000 with AD?  I've a few Linux servers in place now (email, web, mysql, vmware, backups) that have run flawlessly for a couple years but for some reason I am having trouble swallowing the openldap pill. 

There is no way I can get rid of Windows Server altogether.  I have a few apps that won't run on anything else as well as microsoft exchange. I feel as if I've no real choice.

Where is my sudo apt-get install ADreplacement!

..ah sorry this turned into kind of a little bit of a rant.  I feel like I'm banging my head up against a wall and running out of options.

Thanks for listening.

---

### Post by volkswagner on 2008-09-15
This is way beyond my skill level.  I have this book marked, but have yet to dive deep.

[http://ubuntuforums.org/showthread.php?t=640760]("http://ubuntuforums.org/showthread.php?t=640760")

---

### Post by cdenley on 2008-09-15
I believe the current stable version cannot replace an AD server. It can only do an NT4.0 style domain.

Samba4 will be able to match the functionality, but it is still in alpha status.

As far as the difficulty of upgrading all your servers, that depends what you want the server to do.

---

