---
title: "[SOLVED] A hacker created a text file in my desktop"
date: 2019-06-04
forum: Security
---

### Post by rsplayer on 2019-06-04
I had a fight with a person on Facebook and after a while, I found a text file called "dropped text.txt" whith his name in it on my desktop. I closed internet connection and tried to find out what other things he did and thats seems the only new file he added. I guess he can't access my root my password is not easy, right? 
But how did he do that. Did he get the help of a hacker or some internet moderators relatives? Can somebody help?
And I am not joking. I am on my android phone now.

---

### Post by Frogs Hair on 2019-06-04
Moved to* security*.

---

### Post by rsplayer on 2019-06-04
I did repost on security.. but I want to know what did he exactly do?

---

### Post by TheFu on 2019-06-04
I think you are freaking out over nothing.
That filename can be created by a failed drag-n-drop attempt - according to google.  Might you have accidentally clicked on a link with the name and dragged it to the desktop?  I've seen this lots over the years on all sorts of operating systems.

Ubuntu shouldn't have any root password set, so nobody should be able to connect through root remotely.

I suspect you just need a little more security knowledge to better understand how things really work with a computer.  Basic Security: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Your android phone is 1000x less secure than your Ubuntu desktop.

---

### Post by Frogs Hair on 2019-06-04
Please don't create duplicate threads.

---

### Post by rsplayer on 2019-06-04
His name was written in the text file. Why his name? and why is it called "dropped text.txt" ? It never happned to me befor
Edit: oh it is true, I tried it and you are correct, I was so mad at what happned. But what a bad luck for me, it went wrong for me for the first time with my enemy's name. Lol

---

### Post by kpatz on 2019-06-04
Highlight any text on a web page or another application like gedit and drag it to your desktop.  It will create a file with the dragged contents within.

You probably had his name highlighted in your browser and accidentally dragged and dropped it on your desktop.  You weren't hacked... unless he was somehow able to execute script in your browser that simulated drag & drop.

---

### Post by rsplayer on 2019-06-04
This drag and drop should be removed from ubuntu, someone can accidentally drop some sensitive information and he wont notice it. Well I wish my password or anything was dropped there by accident and not that person's name. I thought he hacked me and he will wipe my computer in revenge lol

---

### Post by TheFu on 2019-06-04
> **rsplayer said:**
> This drag and drop should be removed from ubuntu, someone can accidentally drop some sensitive information and he wont notice it. Well I wish my password or anything was dropped there by accident and not that person's name. I thought he hacked me and he will wipe my computer in revenge lol

Remove something because a few people have issues while millions of others don't?
If you don't like it, then don't use it, disable it, or change the GUI (there are 20+ GUIs) to one that doesn't support files on the desktop.

Have you considered that the mouse could have a hardware fault?

Understand that X/Windows has a select/paste capability.  Not copy/paste, but just select/paste.  It is part of X/Windows and has been that way for over 40 yrs.  You'll get used to it.  Select using the left mouse button, then paste using the middle button.  No menus. No keyboard. All done with just the mouse and 2 clicks total.

Browser windows run inside a sandbox, so they can't even write outside that area (in theory) unless you do something specific. It is part of the browser security model that all the major browsers use - firefox, chromium, chrome, i.e.,  safari, whatever.  Doesn't matter which OS. OSX, Linux, Windows, ... they all do something similar.

There are many ways to lock down each application more, but that would cause confusion for someone having drag-n-drop issues.  By default, newer Ubuntu releases not only have the sandbox for each different browser tab, but the browser program runs inside a "snap" sandbox which has limited access to the rest of the file system.  Basically, files can only be "saved" to the ~/Downloads/ directory.  If you want more control than a snap provides, you can use a "firejail" where we have more control over which parts of the OS can be read and which parts can be written. Firejail allows locking down access to specific hardware too.  But all of this is a more advanced topic. Knowing it is possible is the beginning, but it is probably best to wait until more experience is gained with the OS and a little more reading is done before freaking out.  There are other programs similar to firejail which accomplish similar results.

A normal desktop user, who patches at least weekly, stays on a currently support Ubuntu release, and does weekly, versioned, backups, has almost nothing to fear, security-wise while running Ubuntu.

---

### Post by rsplayer on 2019-06-04
I understood exactly what happened now, I dropped the text from my web browser on the dock bar at the left, I tested it and it created the text file. Also I did not mean to delete the drag and drop itself, I mean the way when we drag a selected text from a web browser to the outside it creates a txt file with the containment isn't good. well I understood what happened, but It badly happened at a wrong time. I have nothing to be scared from being hacked.

EDIT: thank you everyone for your help

---

### Post by drv9977 on 2019-06-06
Hey bro...its just a highlighted dropped text you mistakenly have dropped onto your desktop...but you cannot drag and drop passwords filled inside the browsers. For security reasons browser blocks such activities.

---

