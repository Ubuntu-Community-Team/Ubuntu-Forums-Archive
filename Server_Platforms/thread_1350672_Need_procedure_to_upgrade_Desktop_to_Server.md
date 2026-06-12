---
title: "Need procedure to upgrade Desktop to Server"
date: 2009-12-09
forum: Server Platforms
---

### Post by ebayskb on 2009-12-09
Hi!
 
I installed 8.04 (Hardy Heron) desktop but now I want to upgrade it to the Server version. How do I do that? Is there a tutorial available or can someone post the commands/steps required?
 
You might ask why I am doing this....I actually wanted to install Server - long story short - the Dell (Dimension E520) I attempted to install on causes some conflict with the Server CD (the E520 only has USB ports and the installation freezes at the 'Language Choice' screen/prompt). 
 
However, the desktop version of the software was able to be installed off of the CD. So, that's how I landed up having a desktop install instead of the Server that I really wanted.
 
Any help is greatly appreciated. 
 
thanks!

---

### Post by munky99999 on 2009-12-09
I dont think there is a procedure really.

You can simply install everything you want on the desktop version. Removing the gui or removing non-essential things will be a little annoying and slow going.

Sadly afaik there is no. Sudo apt-get covert-to-server

---

### Post by holastickboy on 2009-12-09
yeah, it's true.  You just install the server components on their own.  Samba, nfs, apache, mysql, php, etc.  An easy way is to download and install Lampp, which is a good web all-in-one package.  The other stuff is just apt-get

---

### Post by HighCommander540 on 2009-12-09
Then un-install GNOME and all of the desktop applications like pidgin and Firefox.

Although, you don't need samba if you just want a web site server.

---

