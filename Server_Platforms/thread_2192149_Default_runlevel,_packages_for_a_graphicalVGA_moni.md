---
title: "Default runlevel, packages for a graphical/VGA monitor shell in Ubuntu Server"
date: 2013-12-06
forum: Server Platforms
---

### Post by helloworld1215 on 2013-12-06
I am curious how servers are generally first configured as a matter of workflow. 

  It would appear that server editions of linux operating systems  contain a set of packages for displaying a shell to a locally connected  VGA/DVI monitor.
  
[LIST=1]
[*]What is the package for said functionality? 
[*]Do you generally install the linux server, place into the rack and  then configure over the network from a base containing ssh essentially? 
[/LIST]
  [URL="http://www.youtube.com/watch?v=I_e61Cycq-k"]http://www.youtube.com/watch?v=I_e61Cycq-k
[/URL]
  1. So server hardware generally accepts VGA from USB?
2. What is the default runlevel of Ubuntu Server? Desktop  is running on 2, perhaps it is convenient to configure on runlevel for a server running entirely remotely or with a VGA shell, hence the question. 

I am configuring services but don't have a server edition installed, I apologize for the easy question regarding default runlevel, but the questions regarding server VGA functionality and workflow regarding configuration, I am soliciting input from experienced users.

---

### Post by The Cog on 2013-12-06
> What is the package for said functionality?
I'm not sure. It is in every Linux though, as it really is core functionality. You can see this console for yourself by pressing Ctrl-Alt-F1 on your desktop machine (Ctrl-Alt-F7 to get your GUI back).
> Do you generally install the linux server, place into the rack and then configure over the network from a base containing ssh essentially?I would normally do the initial install on the bench and configure up the networking, then rack the server up and do the rest remotely.
> So server hardware generally accepts VGA from USB?
Server hardware normally has a VGA output and a few USB ports (for keyboard, CD, memory stick perhaps). For a blade server like the ones in the video, there isn't much space to put the normal connectors so a small connector and an adapter cable for temporary use make a lot of sense. It's not VGA over USB, it's VGA and 2xUSB on the same custom connector by the looks of it.
> What is the default runlevel of Ubuntu Server? Desktop is running on 2, perhaps it is convenient to configure on runlevel for a server running entirely remotely or with a VGA shell, hence the question.
Ubuntu server normally goes at runlevel 2, but of course it doesn't run the GUI desktop software, only the base tty vga driver. The main difference with the server version of Ubuntu is that it doesn't install the desktop GUI, X server and so on that the desktop version installs. You can of course install ubuntu-desktop or xubuntu-desktop or any other desktop package on a server but that would be a waste of disk space and memory.

---

