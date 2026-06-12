---
title: "New User w\dumb question"
date: 2007-02-21
forum: Server Platforms
---

### Post by smuth10 on 2007-02-21
I am completely new to the linux\unix world. I downloaded and installed ubuntu server 6.10 today to learn something new and I understand the command line portion, but I was under the impression the is a GUI like windows that you can use as well. Is this only true of the DT version and not the server version? Is there only the command prompt interface? 

Thanks, Scott...

---

### Post by Koybe on 2007-02-21
True, ubuntu use Gnome as a desktop. If you use the server version, there is no grphical interface installed. Anyway you can do it if you want.

---

### Post by Nikron on 2007-02-21
if you want a the desktop on your server install do (only one of them)

For light weight desktop
```

sudo apt-get install xubuntu-desktop

```

For the regular desktop
```

sudo apt-get install ubuntu-desktop

```

For a different kind of desktop, more similar to widows, takes up more memory, more configurable
```

sudo apt-get install kubuntu-desktop

```

after you install one, you can either reboot or start them..

in the terminal.  If you want, you can install the components manually.

---

### Post by MystaMax on 2007-02-21
I use Dapper server with no GUI for most tasks, but I have XFCE (what xubuntu GUI is built off of) installed and ready to launch if I need it.

You can install gnome by typing:

```
sudo apt-get install ubuntu-desktop
```

I prefer: ```
sudo aptitude install ubuntu-desktop
```

```
sudo aptitude install xubuntu-desktop
```

you can use ```
sudo aptitude
``` to browse through the repositories.

I just prefer using aptitude over apt-get. for no particular reason, just do.

---

### Post by smuth10 on 2007-02-21
Thank you. I installed gnome and it worked great. Took me a while to find the command to switch to the GUI interface, but I found it. Anyway, how do I switch back to the server command screen. Is there a way to do this without rebooting? I know you can open the terminal screen, but I would like to switch back to the full server mode if I can.

Thanks, Scott...

---

### Post by Nikron on 2007-02-21
Logout, and you can hit the session options to login as terminal

---

