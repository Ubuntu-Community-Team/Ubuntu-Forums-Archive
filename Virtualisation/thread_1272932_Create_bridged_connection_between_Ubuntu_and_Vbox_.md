---
title: "Create bridged connection between Ubuntu and Vbox Win32 (guest)"
date: 2009-09-22
forum: Virtualisation
---

### Post by raptista on 2009-09-22
[SIZE=2]Hello,

Intro:

i'm using Ubuntu 9.04 wich contains Virtual Box.
Windows XP SP3 is installed on Vbox.

The probleme:

i want to make a bridged connection between the 2 OS. so i can ping successfully between Ubnutu and Win XP. i want also share files between them.(i know it's about samba but don't know how).

Conclusion:

I hope that someone helps me here plz/
and sorry for my english;i'm from Morocco.
[/SIZE]

---

### Post by scrooge_74 on 2009-09-22
To shared files, just use the share folder option that VBox has, after you enable a folder go to Network in XP and look for vboxdrv (i think is that) and mount a network drive.

You dont need samba. 


If you want to use samba then you need to configure your samba server in the host machine and configure so the host and guest have the same network name.

You also need to configure a bridge for the network card so it can have an IP from your router

---

### Post by wrathican on 2009-09-24
when you start up virtualbox after installing you guest OS, select your guest OS and where the start icon is, click the settings icon.

in the settings dialogue, you will an option called "Network". In this section you will find a dropdown menu called "attached to" It usually says "NAT", change this to "Bridged Adapter" and save. Start your VM and it should get an IP from your router, hence being pingable.

For sharing files you go to the settings again and select "shared folders". click the '+' sign and select your folder to share, then give it a name.

When in your guest OS (if its windows based) and not already viewable in my Computer, go to :open my computer, then go to tools > map network drive. the folder will be located at "\\vboxsvr\yourFolder"

Hope these help.

---

