---
title: "windows to linux communication"
date: 2007-05-26
forum: Server Platforms
---

### Post by Sable_lynx on 2007-05-26
hi guys, 
i'm new in the forum, and to ubuntu too. my problem is i just cannot get any of the other windows (xp and 2003)  on our LAN (under 10 machines, no subnets) to communicate with the ubuntu box. i've installed samba (i can browse all windows shares, but cannot write to or from them), i can ping them, and they can ping the ubuntu box. what could be wrong? someone please help

---

### Post by coffeecat on 2007-05-26
I don't have too much experience of this, but I guess this is because a default install of Ubuntu has all ports closed. Configuring IPTables (the Linux firewall) by hand is a royal pain, so I suggest you install Firestarter  - it's in the Ubuntu repositories - a nice GUI frontend to IPTables. Have a look in Synaptic. If you need help configuring Firestarter I'm sure there will be plenty of people who can help.

I'm assuming here that you're using Ubuntu/Gnome. If you're using Kubuntu/KDE there's a different GUI frontend better suited to KDE, but for the life of me I can't remember its name.

---

### Post by envis on 2007-05-26
i had a similar problem when i installed a network with windows and ubuntu machines mixed togheter and it turned out that windows would not allow ubuntu to connect to its network but was able to make windows connect to the ubuntu shared folder that i created pretty easily on the ubuntu by making a folder on my desktop, right clicking on it and somehow chosing to make it shared folder... then from the windows computer, i had to go in my network places and mess a little bit in the menus to the left, to get a bit "out" of where it initially brings to something like "microsoft network" or something like that... i eventually seen my ubuntu there.. once i got it, i made a "shortcut" to that on the desktop of the windows computer... 

i hope it helps....

---

### Post by elst on 2007-05-27
> **coffeecat said:**
> I don't have too much experience of this, but I guess this is because a default install of Ubuntu has all ports closed. Configuring IPTables (the Linux firewall) by hand is a royal pain, so I suggest you install Firestarter  - it's in the Ubuntu repositories - a nice GUI frontend to IPTables. Have a look in Synaptic. If you need help configuring Firestarter I'm sure there will be plenty of people who can help.


Ubuntu doesn't actually use the Linux firewall by default. The standard installation doesn't have any open ports because all the network-accessible services are deliberately configured not to respond to remote connections. This means that the user doesn't have to jump through extra hoops with iptables if they choose to make their system a server later on.

The easiest way to figure out a Samba problem is to start with the comand-line utility (smbclient). Graphical tools don't report the exact error message, which makes it hard to figure out what's going on.

---

### Post by Alterax on 2007-05-30
When going into the Windows shares, do you get a chance to authenticate?  If so, give it a username and password from the windows machine, not for the ubuntu box.

Setting up a samba share on the Ubuntu box for the Windows machines to access isn't difficult; you'll find it in the howto section.  You'll just need to give the Windows people usernames and passwords and access rights to use it.  Piece of cake.

Sounds like that's what is going on.  No biggie.

--Alterax

---

