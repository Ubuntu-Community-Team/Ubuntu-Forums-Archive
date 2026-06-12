---
title: "Uninstalling Desktop UI"
date: 2011-06-01
forum: Server Platforms
---

### Post by DevRandom242 on 2011-06-01
Hi,

<RANT> As a new user to Ubunu (but not to Linux), I find it a little frustrating that you don't get to choose what packages are installed during installation as with other distributions.  </RANT>

Now I've got that off my chest.... ;)

I installed the latest version of Ubuntu via PXE (using a process vaguely along the lines of [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)).

The problem is that I've now got a "bells & whistles" versions with the desktop UI installed. Which I don't want or need on a server, all it does is hog disk space, RAM and CPU.

So, I would like to uninstall it (not just disable it).

However, having searched these forums, I've tried a number of "apt-get remove" combinations but none of them seem to work or have any effect.

What is the correct way to uninstall the desktop UI for the current version of Ubuntu ?  Surely I can't be the only one !

---

### Post by brettg on 2011-06-01
If you installed ubuntu from the server ISO then there is no GUI installed during the process. 

The WindowsServerNetboot process you used I am unfamiliar with but I suggest that the "server" they are referring to in that title is the server that you are installing *from* and not a "ServerOS" that you are installing.  I may be wrong of course as it's the first time I've heard of it.

However, if you do "sudo apt-get purge libgtk2.0-0" followed by "sudo apt-get autoremove" it should remove the majority of gnome and all of it's dependents, if not all of it.

---

