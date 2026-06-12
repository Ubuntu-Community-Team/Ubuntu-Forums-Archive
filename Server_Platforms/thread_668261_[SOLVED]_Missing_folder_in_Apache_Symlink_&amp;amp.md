---
title: "[SOLVED] Missing folder in Apache Symlink &amp;amp; an SSH question.."
date: 2008-01-15
forum: Server Platforms
---

### Post by lucas4ce on 2008-01-15
Hi there, I have Apache2 running on a Ubuntu 7.10 desktop, and have a alias setup to redirect 'http://myurl/work' to a folder /home/myhomefolder/work.  This alias is password protected and it all works great from anywhere.  

At home I have a laptop running XP professional which i do my work on, I then copy (effectively overwritting) the 'otherstuff' folder on my laptop to the '/home/myhomefolder/work/otherstuff' folder on the unbuntu desktop server.  This serves two purposes...I now have a backup of my work, and it's accessible from anywhere via the internet.

To save me having to login to the server I have the /home/myhomefolder directory shared to all local hosts in a configuration similar to the standard 'allusers' setup in the samba howto.

All good so far..

My problem here is that when I update the 'otherstuff' folder as above, this folder is no longer visible online.  I can see the rest of the 'work' folder, but not the changed directory.

I'm guessing this either has something to do with permissions and/or windows/linux compatibility somehow.  But I've only just started with linux so I'm not too sure where to go next, any help would be great!

------

Also,

Ideally I would like to be able to view and change my work files from anywhere via the internet.  For example if I go to myurl/work and login using my username and password I can currently open my files, then if I change something and go to save the file I have to save it on the local computer.  Is there a way to overwrite the file on the server?  Securely of course?  I'm not sure if I'm looking at SSH or FTP or VNC maybe?

Ultimately I will get some more hard drives for the ubuntu machine, keep a master copy of my work files on that machine instead of the laptop, and use raid or something to backup the work files to another drive.

Any help would be great!!!

---

### Post by PetePete on 2008-01-15
can only asnwer your second question (although maybe your first is related to the browser caching the page?)

you want to run SSH , definatly not FTP as this is considered insecure due to sending passwords in plain text....

with ssh it will allow you to remotly control your pc from anywhere using command line, but also you can use it similar to a ftp server with SFTP (which all runs from the same SSH service with no extra setups ) .. copy files accross with a client.

VNC would be useful if you wanted to 'see' the desktop and use the computer as if it was next to you.

---

### Post by lucas4ce on 2008-01-16
Ideal thanks!

If I had SSH on my ubuntu machine up and running would I then need 'putty' or something like that on the remote computer, or could I access the server from, say, IE with a clever url.

Ok that was a wild guess:)

---

### Post by Vinno on 2008-01-16
You need a ssh client. Putty is small anyways if i remember correctly, proberly fit on a floppy disc or keychain usb storage.

---

### Post by lucas4ce on 2008-01-16
Just to help possibly answer the first question myself I found this thread [http://ubuntuforums.org/showthread.php?t=666133](http://ubuntuforums.org/showthread.php?t=666133) that may sort it out.  I'll have a go this evening and report back.

---

### Post by lucas4ce on 2008-01-17
Yep that did it...

chmod g+rws /path...

then

chown -R root:users /path..

then to be sure

chmod -R 775 /path...

and it works now.

Thanks!!

---

### Post by lucas4ce on 2008-01-17
Oh yeah had to do one last thing too as I was finding that if I copied in a folder from anywhere local I then couldn't see it online.

So in the samba.conf file I changed the following for the share that deals with my work files:

Directory mask = 0775
Create mask = 0775

Seems to work now.

Think this ones solved now:)

---

