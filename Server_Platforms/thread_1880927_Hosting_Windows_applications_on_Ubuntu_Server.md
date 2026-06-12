---
title: "Hosting Windows applications on Ubuntu Server"
date: 2011-11-14
forum: Server Platforms
---

### Post by Punz on 2011-11-14
Hi All,

I have a Compaq Proliant ML370 with Ubuntu Server 11.10 loaded on it. I want to put a Windows based application on it and host it on my Windows network at work. All client PCs run Windows XP. 

The program is from the State of Florida. It isn't really "installed" on the system. No Registry entries at all. I can easily copy the entire Home folder, paste it to another PC and run the program with it's server in less than two minutes. 

I am a Ubuntu Server n00b. I've used the Ubuntu desktop as my main office and home OS since 2009. Any help would be appreciated.

Specs:
Windows Based-Network
Client OS: Windows XP
Main Server OS: Windows SBS 2003
Spare server - Compaq Proliant ML370 

Thanks,
Punz

---

### Post by SeijiSensei on 2011-11-14
First, try running the program over the network from a share on a Windows computer.  If that works, then you can certainly use Samba on an Ubuntu server to share the program with other machines.

You'll have to be careful if the program creates files while it works though.  If all the users share the same directory, and the program writes its files or output there, then one user's files will overwrite another's.  If you can ensure that any output will be written to the user's home directory in Windows, then you should be fine.

---

