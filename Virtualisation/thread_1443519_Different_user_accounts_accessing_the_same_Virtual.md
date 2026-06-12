---
title: "Different user accounts accessing the same VirtualBox OS"
date: 2010-03-31
forum: Virtualisation
---

### Post by Asrai99 on 2010-03-31
Hello y'all,

so I've got Windows Vista running in my VirtualBox on Ubuntu. As long as I was the only user on my laptop, this wasn't a problem at all, however now I've created a second user account for Ubuntu. I'd like this user to be able to access the same Windows Vista that I can access, however when I log on to this second account, VirtualBox shows me that no operating systems are installed. That kind of makes sense, since the virtual hard drive is installed under the original home folder, which is hidden to the new second user. 

Any ideas of how I might change this? Can I share my home folder with the new user and thus make my version of Windows Vista available to them? Or will I have to install a new operating system in the VirtualBox? (Which might be tricky, seeing as my hard drive only has so much space to give...)

Any help on this would be much appreciated!

Ta,
Asrai

---

### Post by Dedoimedo on 2010-04-01
You could use a "central" location with 777 permissions for virtual machines. I've done this many times on different machines and it works well, allowing me to move virtual machines about.

Dedoimedo

---

### Post by Asrai99 on 2010-04-01
Does that mean I'll have to re-install my existing virtual OS in that central position? Or can I just, I don't know, paste it there? :D

In any case, thanks so much for your help, I'll give this a go!

---

### Post by HermanAB on 2010-04-02
A Virtual machine is simply a directory full of files.  You can change the permissions of the VM directory in situ, or you can move it. 

However, the best solution is to run the VM permanently and connect to it with RDP.

---

