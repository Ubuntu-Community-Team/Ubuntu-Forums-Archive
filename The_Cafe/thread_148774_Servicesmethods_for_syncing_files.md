---
title: "Services/methods for syncing files?"
date: 2006-03-22
forum: The Cafe
---

### Post by maruchan on 2006-03-22
I would like to set up some sort of resource for accessing some of my files remotely, regardless of what operating system I'm using. Are there free services out there that allow this? The idea is, I'd like to have certain files that I can access anywhere, preferably with a more seamless access method than FTP, i.e., you can see the files in Nautilus or Windows Explorer, etc.

Thanks for any advice.

---

### Post by s|k on 2006-03-22
[QUOTE=maruchan]I would like to set up some sort of resource for accessing some of my files remotely, regardless of what operating system I'm using. Are there free services out there that allow this? The idea is, I'd like to have certain files that I can access anywhere, preferably with a more seamless access method than FTP, i.e., you can see the files in Nautilus or Windows Explorer, etc.

Thanks for any advice.[/QUOTE]
Yahoo! Briefcase
Yahoo! Email
Gmail

come to mind right away. I use all three, because you never know when one or two will poop the same day your PC dies and your academic career dies a quick death and you end up divorced homeless and dying from typhoid.

They don't 'sync' the files or actually access your desktop obviously.

---

### Post by maruchan on 2006-03-22
Well, thanks for those. Is there a way I can have one or all of these services show up as a filesystem on my computer that I can just open up and dump files into/out of?

Thanks.

---

### Post by majikstreet on 2006-03-22
yeah gmail you can.... gmailfs anyone?

windows: [http://www.viksoe.dk/code/gmail.htm](http://www.viksoe.dk/code/gmail.htm)
linux: [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)

---

### Post by tgoose on 2006-03-22
[QUOTE=majikstreet]yeah gmail you can.... gmailfs anyone?

windows: [http://www.viksoe.dk/code/gmail.htm](http://www.viksoe.dk/code/gmail.htm)
linux: [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html)[/QUOTE]
Is it possible when this is mounted as FAT32 for both Linux and Windows computers (and OS X, i guess) to read and write to it? I can't get it working in Ubuntu and don't have any other machines to test on at the moment but it could be just what I need.

---

### Post by Iandefor on 2006-03-23
A more appropriate solution for the OP may be Samba. Windows, Linux and OS X all have SMB support.

---

### Post by s|k on 2006-03-23
You know in windows I was able to add a network folder for ftp accounts. I could use it just like any other folder on my drive except when saving within applications. Does gnome have this?

---

