---
title: "hosting my site, what permission settings?"
date: 2013-02-27
forum: Security
---

### Post by wlraider70 on 2013-02-27
I have my own site, that's mostly for internal use, but you can login from the internet. I've been setting it up for the last few weeks so my permissions are lax, now I want to tighten it up. 
Its a lmap set up. 

What should file permissions be. 
I have some that are shared through samba. Is that safe?
I have file permission at 777, obviously I don't want that.
Who should be the file owner?

---

### Post by mikaelcrocker on 2013-02-27
File permissions should be based on what you need to do.  For instance if it's a file needing to be executed by everyone and just edited by the owner, a 711 will work. If the file needs to be read and that is it except owner you would have read/write it'll be 644. TL;DR - it's all based on use.

Using Samba, I feel I don't quite have enough info to give ya too much there :(

Owning the file, again depends on who needs and is going to use it.  For instance if you're using PHP files will be owned by www-data.  

I try and keep files as restrictive as possible while allowing things to still be functional.

---

### Post by wlraider70 on 2013-02-27
My files are php. There is some mysql happening in there, does that count as an execution? I'm not really sure on the "execution" of a website. They "run" on the browser right, not on the server.

My samba sharing is just local network; I edit them on windows box. I was just wondering if there were any safety concerns there.

Also, I have a mysql DB-connection info in one of my files is there any special security concerns there?

---

### Post by CharlesA on 2013-02-27
php and mysql aren't really "executed" on a file level, they are read my their respective programs.

I have the files on my webhost set for rw-r--r--
644 for files
755 for directories

---

