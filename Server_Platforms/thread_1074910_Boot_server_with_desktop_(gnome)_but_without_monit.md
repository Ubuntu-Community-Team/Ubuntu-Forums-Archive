---
title: "Boot server with desktop (gnome) but without monitor"
date: 2009-02-19
forum: Server Platforms
---

### Post by aroddo on 2009-02-19
Hi,


I'd like to maintenance my homeserver with VNC so I don't really need an attached monitor.  However, Ubuntu notices that I don't have a monitor attached and helpfully omits starting gdm and thus the VNC server.


Starting gdm manually via SSH doesn't help either, since it starts the desktop manager but expects someone to use the graphical login.


I want the server to boot up with the graphical UI and autologin without a fuss. Switch on and ready.


Any idea how to do that ? 

Thanks.


PS: Using Ubuntu 8.10

---

### Post by cariboo on 2009-02-19
I would suggest removing gdm from startup and using X forwarding to do any maintenance you need, you can also use sftp for file management.

To use X forwarding when connecting to the server type:

```
ssh -X user@server
```

This only works if you are connecting from an Ubuntu desktop, once at the prompt on the remote computer just type the name of the program you want to run.

To use sftp open Nautilus and type in the address  bar:

```
sftp://user@server
```

For X forwarding in Windows have a look [here]("http://www.math.umn.edu/systems_guide/putty_xwin32.html").

Winscp or Filezilla are two good sftp/scp programs that are free downloads.

Jim

---

### Post by aroddo on 2009-02-20
actually my clients are a Mac, Windows and Ubuntu. 
Since VNC works well with all three client systems I just figured I go for the established solution.

Is X forwarding working on a mac ? It should, since it's unix based.

---

### Post by madverb on 2009-02-20
Just do a quick search of the forums. There are HOWTO's for setting up a VNC server to access the GDM login screen.

---

