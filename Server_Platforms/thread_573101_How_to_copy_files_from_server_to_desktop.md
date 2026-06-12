---
title: "How to copy files from server to desktop?"
date: 2007-10-11
forum: Server Platforms
---

### Post by chamstar on 2007-10-11
Hello, I wonder if someone can help me. I have some files on my server (Ubuntu of course) and have accidentally deleted my local copy. 

I know I can use scp to copy files from desktop to server but is there a way to copy them server to desktop. The Ubuntu server I have is very basic (no FTP).

I have root ssh access also.

Many thanks! Cham.

---

### Post by dwhitney67 on 2007-10-11
If you are familiar with scp, then you must know about the SSH-server.  Install it on the system that lacks it, or in other words on your non-server (desktop) system.

An Ubuntu server is nothing more than a lean desktop system.

---

### Post by chamstar on 2007-10-11
That would work thanks, I guess I just need to open up the correct port on my firewall, will google for more!

---

### Post by rbprogrammer on 2007-10-11
just out of curiosity.. keep us posted on what you did, because i would like to know as well... right now i just use webmin but sometimes it is a pain to try and download lots of files from my server about 300 miles away

---

### Post by Brazen on 2007-10-11
Why don't you just ssh in from the desktop to the server and then scp the files down with that?  If you already have that set up to send files up to the server, seems to only make sense to use the existing setup to pull files down from the server.

---

### Post by netlogic on 2007-10-11
Gnome had a built-in graphical sshfs for a long time now. You also got unison and rsync over ssh.

---

### Post by Xenaco on 2007-10-11
I would suggest using ***rsync***.  Type ***rsync --help*** or ***man rsync*** for usage.

**Rsync** will allow you to copy a file or files on one machine or files from one machine to another.

---

### Post by jinx099 on 2007-10-11
why would you copy files when you could use the files remotely?  Look into NFS or SAMBA if the server is on your lan, but since you mentioned a firewall it is probaly remote and you should try out sshfs.

---

