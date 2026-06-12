---
title: "Server 10 + remote access admin"
date: 2011-02-01
forum: Server Platforms
---

### Post by nats463 on 2011-02-01
Hello everyone, 

I have an FTP server running for a client, and wish to turn over part of the user creation to him per my own boss.  The guy is kinda slack with linux so the more dumb down the better.  I currently running Server 10.10 without xwindows.  I admin the box via VNC/SSH.  I need a way for him to access the machine that only has web and ftp ports open, and will not have access to my VNC.

Any suggestions, i would prefer not to put xwindows on the machine, if possible.

---

### Post by YesWeCan on 2011-02-01
If you want another user to have a remote desktop that is different from yours, you could use TightVncServer. Unlike the built-in "vino" (which broadcasts the monitor display) this spawns individual user desktops and they can have different passwords. You view them the usual way using "vinagre". It is available in the Software Center.

---

### Post by nats463 on 2011-02-04
> **YesWeCan said:**
> If you want another user to have a remote desktop that is different from yours, you could use TightVncServer. Unlike the built-in "vino" (which broadcasts the monitor display) this spawns individual user desktops and they can have different passwords. You view them the usual way using "vinagre". It is available in the Software Center.


This can be done without having a GUI installed?  I have dumbed down adding users by creating a script.  All I need him to have is basically a shell, remotely.

---

### Post by YesWeCan on 2011-02-04
Sorry, I guess I do not understand what you are talking about. You say you do admin using vnc and ssh and you are also saying the server has no gui. You don't want your user to access your vnc. Perhaps you mean something else by vnc.

---

### Post by nats463 on 2011-02-07
> **YesWeCan said:**
> Sorry, I guess I do not understand what you are talking about. You say you do admin using vnc and ssh and you are also saying the server has no gui. You don't want your user to access your vnc. Perhaps you mean something else by vnc.

I access the machine internally via SSH,  When I am at home I have to use our VNC connection to SSH into the machine.  The VNC is my company's private VNC, and so our client would not normally have access to it.  The couple machines we are hosting/admining are on seperate domains, but can be accessed within our office.  I have to give him a way to access the machine that does not require access to our VNC, or the server to gave a gui.  My office does not want to point additional ports towards this machine other than FTP and Web.

---

