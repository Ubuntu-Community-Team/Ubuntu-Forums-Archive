---
title: "Central Filestore... across the net..."
date: 2005-11-18
forum: Server Platforms
---

### Post by Buzbe on 2005-11-18
Hiya everyone,

I'm stick of M$, so I'm trying may hardest to shed the shackles of windows and move across to full flavour linux. 
One thing I've always wanted to do though, as I am often logining in to a variety of computers, some running windows, others running linux, is have a central filestore for all my documents.  When I boot up my laptop, be it in windows or ubuntu I'd want that as my home directory...

The thing is, the central filestore I would want to use would be my linux server (running centos) located in level 3 in london...

how could I achieve this??

plus are there any good alternatives to M$ exchange that are free now, and not a complete nightmare to install, plus that interface with outlook and evolution without the need for silly plugins?

Thanks 

:-)

---

### Post by spade_shark on 2005-11-18
> how could I achieve this??  Remote , secure file storage / access...try a secure ftp service.  Maybe try vsftpd for your flavor *nix.  Create secure dropboxes for you and your friends (avoid 25 mb file attachements crushing your inbox ;) ).  Access the service through any of the following methods: gFTP, ncftp, a million others, or your web browser of choice.

   > plus are there any good alternatives to M$ exchange    Yes
   
    > that are free now, and not a complete nightmare to install You are asking for the sun, moon and stars here.  Enterprise groupware solutions are a complex beast.  These programs run ontop of web services, are controlled by databases, and are linked to large file servers.  That being said no, not easy to install.  However, thankfully easy to manage and maintain if setup right.  One man's nightmares are anothers dreams. 
    
 >    plus that interface with outlook and evolution without the need for silly plugins?  No. no. no.  The silly plugins translate the information between the different systems.  Until the groupware systems of the world agree on a unified message layout to send, store and receive data, plugins are needed for the clients.  Look for a groupware solution that is web based and it will negate the use of the above clients and silly plugins.

---

