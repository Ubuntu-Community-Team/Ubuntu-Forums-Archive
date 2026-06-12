---
title: "server: GUI issue?"
date: 2011-03-08
forum: Server Platforms
---

### Post by netlablg on 2011-03-08
"Servers aren't meant to have GUIs because they are a serious waste of CPU clock cycles."

i encountered this line from somewhere here in ubuntu forums,
but how could i install tools like mysql wrokbench and stuff, w/c will make my life a lot easier as an administrator?

or is there such thing as remote administration?

---

### Post by BkkBonanza on 2011-03-08
I don't think that statement is entirely true. Some admins like to use a GUI but I don't. They consume a few percent cpu cycles typically. I don't like them because of all the extra processes that are hanging around and the potential for added security vulnerabilities. And on my small vps accounts they use too much memory (which costs quite a bit on hosted servers).

There are a few approaches for a GUI or GUI like admin tools. Some people use WebMin and PhpMyAdmin (for mysql). Or similar web based tools.

Another way is to use a remote GUI with X windows over SSH. There are a few tutorials around on that and it's not my normal method so I won't comment on it. But it only adds a modest X windows layer on the server and then you connect using ssh X mode to host the GUI on your "personal" system.

I just use ssh and the command line (and phpmyadmin for mysql). 

Note also that the default Nautilus file manager can manage files on your server using SSH (sftp over ssh actually) by default. So for file editing and managing that works out of the box. 

Give it a file location as sftp://mydomain.com/var/www and you can save it as a bookmark too for quick access.

---

### Post by netlablg on 2011-03-08
> **BkkBonanza said:**
> I don't think that statement is entirely true. Some admins like to use a GUI but I don't. They consume a few percent cpu cycles typically. I don't like them because of all the extra processes that are hanging around and the potential for added security vulnerabilities. And on my small vps accounts they use too much memory (which costs quite a bit on hosted servers).

There are a few approaches for a GUI or GUI like admin tools. Some people use WebMin and PhpMyAdmin (for mysql). Or similar web based tools.

Another way is to use a remote GUI with X windows over SSH. There are a few tutorials around on that and it's not my normal method so I won't comment on it. But it only adds a modest X windows layer on the server and then you connect using ssh X mode to host the GUI on your "personal" system.

I just use ssh and the command line (and phpmyadmin for mysql). 

Note also that the default Nautilus file manager can manage files on your server using SSH (sftp over ssh actually) by default. So for file editing and managing that works out of the box. 

Give it a file location as sftp://mydomain.com/var/www and you can save it as a bookmark too for quick access.


i don't think i get all what you said, but i get the idea that i can still manage it remotely (using GUI) without installing GUI on the server itself. am i right?

---

### Post by BkkBonanza on 2011-03-08
Yes.

1. Use web based tools. Google "webmin", for general server mgmt, but there are others too. PhpMyAdmin is a very popular web based mysql db manager.

2. Use X windows remotely over SSH. Google "remote x windows ssh" for a tutorial on that. It's fairly easy but more than I'd posted here. 
eg. [http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html]("http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html")

3. Nautilus can be used for file management. Some (most?) DB editors can easily access and remote manage mysql too as long as mysql is configured for remote access. Sometimes it's only configured for localhost or linux sockets but that can be changed.

---

### Post by netlablg on 2011-03-09
> **BkkBonanza said:**
> Yes.

1. Use web based tools. Google "webmin", for general server mgmt, but there are others too. PhpMyAdmin is a very popular web based mysql db manager.

2. Use X windows remotely over SSH. Google "remote x windows ssh" for a tutorial on that. It's fairly easy but more than I'd posted here. 
eg. [http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

3. Nautilus can be used for file management. Some (most?) DB editors can easily access and remote manage mysql too as long as mysql is configured for remote access. Sometimes it's only configured for localhost or linux sockets but that can be changed.


whoa, that's all i need. thanks for the help :) i'll start my server in a moment :)

---

