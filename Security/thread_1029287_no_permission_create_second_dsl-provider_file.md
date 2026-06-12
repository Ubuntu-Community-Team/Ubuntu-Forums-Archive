---
title: "no permission: create second dsl-provider file"
date: 2009-01-03
forum: Security
---

### Post by Nasty.Naafi on 2009-01-03
Please help me create a second dsl-provider file for my second dsl account.

Ubuntu version 8.04 hardy

I get a message saying that I don't have the right access either as a user or to the folder - despite using sudo and cp to copy an edited file into etc/ppp/Peers. I also tried using Dolphin to copy a file into the folder logged as root....

For some reason - no matter what user rights I assign - the Peers folder appears to be locked so that I cannot write to it.  Also unable to change the permission of the Peers folder with my limited skills...lol (reminds me of MSDOS 3.3!)

I want to use gpppwrap to jump between shaped and unshaped accounts - the dsl-provider is configured, I have copied this file adjusted it for the second account but cannot paste it into the Peers folder.

thanks
nasty.naafi

---

### Post by Nasty.Naafi on 2009-01-03
Solved - used super user konsole and the correct cp line...lol.

---

