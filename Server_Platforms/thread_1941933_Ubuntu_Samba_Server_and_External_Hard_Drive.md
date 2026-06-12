---
title: "Ubuntu Samba Server and External Hard Drive"
date: 2012-03-16
forum: Server Platforms
---

### Post by salgala2000 on 2012-03-16
Hello,
My desktop has Ubuntu 11.04 installed on it, along with Samba and SSH. My goal is to be able to not use the desktop's screen and control the server from Samba and SSH. Both Samba and SSH currently work (I can control them both with my Macbook Pro). Here's my issue: I would like to be able to write files to an external hard drive I have through the network (through the desktop). So: computer > network > Desktop(Server) > External Hard drive. The external hard drive is connected through USB to the desktop. Is there a way to make (or find) a directory which i could put my files and then transfer them to the desktop? AKA, how can i access the hard drive without the GUI?

TL;DR: How can I access an external hard drive (connected through USB) through terminal or navigating the filesystem in Samba?

thank you for any and all help :)

EDIT: Nevermind, I found it. I can't believe I didn't look there before :( For anyone else who needs help with this, it's in /media/

---

