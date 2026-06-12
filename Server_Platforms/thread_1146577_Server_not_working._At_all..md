---
title: "Server not working. At all."
date: 2009-05-02
forum: Server Platforms
---

### Post by GolemdX on 2009-05-02
ubuntu 8.04 Hardy Heron server edition with desktop and edubuntu installed over top of it.

I was adding something to my website when I decided to use the desktop as a transfer point for the files.

I moved the files to another folder, and then realized I forgot some hidden files on the desktop. When I tried moving what I thought were my files, I got an error so I decided to delete them and re-extract the whole thing. It turns out, that over 5GBs of files were there, but I stopped it before it deleted most of them... Ctrl-Z didn't do anything, nothing would open and the window that was open couldn't access the trash. I reset it and all it's showing is a badly sized hardy wallpaper.

Actually, the only thing working is in fact, the website itself.

What can I do?!?

---

### Post by GolemdX on 2009-05-02
OK, I'm using plain old server by pressing Ctrl-Alt-F1, but what were in those hidden folders on the desktop? How can I restore (or recreate) them?

---

### Post by GolemdX on 2009-05-02
OK, can anybody tell me what (and if) the hidden files on the ubuntu desktop are?

---

### Post by HermanAB on 2009-05-02
Howdy,

The 'Desktop' is just a subdirectory /home/username/Desktop.  There should not be anything in it, except for the odd Icon file.

---

### Post by GolemdX on 2009-05-02
OH! I think my Desktop was actually mapped to my home folder! So they were hidden files from my **home folder**, not the Desktop.

---

### Post by GolemdX on 2009-05-03
Can anybody tell me what I would need to install that was in my <home folder>? Can I just create a new user or what do I need to reinstall?

---

### Post by koenn on 2009-05-03
the hidden files in your homes are settings and preferences for programs you use. Normally they will be recreated (with default values) as needed. If that doesn't happen and a program refuses to start, you'd have to re-install that program.

---

### Post by GolemdX on 2009-05-03
Well absolutely nothing is starting. All it is showing is an offset picture of the Hardy background, and the monitor says it's the wrong frequency.

Would creating a user VIA terminal recreate the files needed to use the computer?

EDIT: Do you think I deleted system files? Seeing as how there were more than 5GB of things there...

---

### Post by GolemdX on 2009-05-05
OK, I purged ubuntu-desktop and it was less than 1MB, what package would I need to remove to revert it back to server?

---

### Post by brendan.lefoll on 2009-05-06
I think your getting confused. Ctrl+alt+F1 doesnt give you "server", its just a plain old command line instead of a gui.

If you screwed up your home directory and dont mind loosing it, just do this

sudo su
userdel user
rm -rf /home/user
useradd user
mkdir /home/user 
(if it wasnt there allready)
chown user.user /home/user
passwd user 
(enter password)

and reboot back to GDM and type everything in (you dont actually need to reboot, but its probably a better idea for less confusion)

to make ubuntu normal edition server edition you basically have to install and remove a bunch of packages, the only difference is what is installed by default!

---

### Post by GolemdX on 2009-05-06
I know Ctrl-Alt-F1 was command line (Terminal). I was just asking how to revert back to ubuntu server, without anything else installed.

I only asked that because nobody was answering my other question, I'll try that out right now, the important files in my home folder is actually just a mounted drive.

---

