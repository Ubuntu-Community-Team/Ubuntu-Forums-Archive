---
title: "Ubuntu Server 8.1 + VirtualBox 3 + Mythbuntu"
date: 2009-09-24
forum: Virtualisation
---

### Post by Eddy Gordo from Tekken on 2009-09-24
I have ubuntu Intrepid 8.1 server running headless. I make changes via SSH connections over my home network (XP + putty) or via the interweb (android phone + connectbot).  It currently acts as:

File server (Samba)
SSH server
FTP server
a low traffic web server (LAMP)
A web based jukebox (ampache, and jinzora)
Photo gallery (galleria)
Teamspeak server

The mobo's built in video supports HDMI out, so I'd like to utilize it by attaching it directly to the HD TV and watch stored media, as well as streaming media from sites like netflix and hulu.

So I figured I'd use virtualbox to create a VM to install mythbuntu. then I'd have a remote control and wireless keyboard/mouse for control media on the TV screen.

I've been told that this will not work, because the host does not have a desktop installed.  I use SSH currently to make any changes to the server.  I figured I could use a virtual desktop to install/configure mythbuntu from my Windoze PC.  then when that was done.  I could launch the VM directly on the server, connected via HDMI to the tv (or cable box?), and that would be success. My nay saying friends say that it can't work, and that I should do it the other way around.  Meaning, the only way to do what I describe is to install mythbuntu first, then create a VM with ubuntu Intrepid Server.

question: Will what I prescribed work? or do I need to do it the way my friends have said.

---

### Post by Eddy Gordo from Tekken on 2009-09-25
Bumpdate...

I installed virtualbox 3
via ssh I configured a VM
using vrdp & Remote Desktop Connection (XP) I installed mythbuntu-9.04-desktop-i386.iso

I connected the server using HDMI to my TV as the display unit.

from a command line physically at the server, I issue this.

```
$ VBoxManage -q startvm mythbuntu
Waiting for the remote session to open...
ERROR: Virtual machine 'mythbuntu' has terminated unexpectedly during startup
Details: code NS_ERROR_FAILURE (0x80004005), component Machine, interface IMachine, callee <NULL>
```

any suggestions?

---

### Post by Eddy Gordo from Tekken on 2009-09-26
Bumpdate...

I guessed it failed because I hadn't installed X gnome and gdp so...

```
$ sudo apt-get install x-window-system-core gnome-core gdm
```

I followed that up with
```
$ startx
```

Success, a desktop on the host server displaying on the TV.  So I ctrl-alt-backspace to stop x.  and i'm back at the command line. and...

```
$ VBoxManage -q startvm mythbuntu
Waiting for the remote session to open...
ERROR: Virtual machine 'mythbuntu' has terminated unexpectedly during startup
Details: code NS_ERROR_FAILURE (0x80004005), component Machine, interface IMachine, callee <NULL>
```

I look for the error log VBox.log as I didn't know where it was off hand...

```
$ find / -name '*VBox.log*'
/pathto/.VirtualBox/Machines/mythbuntu/Logs/VBox.log
/pathto/.VirtualBox/Machines/mythbuntu/Logs/VBox.log.1
/pathto/.VirtualBox/Machines/mythbuntu/Logs/VBox.log.2
/pathto/.VirtualBox/Machines/mythbuntu/Logs/VBox.log.3
```

why do I have four logs? only one had the date I was interested in which was yesterday.  anyway...reading it doesn't seem to help unless I am missing something.  I used VI to and searched it for the strings "08x" and "ERROR" and "code" and didn't find anything enlightening.

any guidance?

---

