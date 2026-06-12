---
title: "Can't Edit BIND9 /etc/bind/named.conf.local"
date: 2009-11-22
forum: Server Platforms
---

### Post by TOM-J-LAEL on 2009-11-22
hey team!
 
 I'm experimenting with creating a Secondary DNS server as a backup to a windows server 2003 DNS server that we have that hosts DNS for a handful of internet domains. We want to get away from paying for the backupdns  service.
 
 I found this thread here
 
 [http://ubuntuforums.org/showthread.php?t=558960](http://ubuntuforums.org/showthread.php?t=558960)
 
 but I'm completely novice when it comes to Linux.
 
 I try to edit the named.conf.local file by typing:
 
 vi /etc/bind/named.conf.local  , and a text type file pops up in the terminal. but i can't edit it.
 
 please help.
 
 thanks,
 TOM-J-LAEL ..

---

### Post by Zeosa on 2009-11-22
Try using nano instead of vi, it's easier to wrap your brain around at first.

That said, take some time to learn vi at some point, as it's typically available on all *nix systems and you may have to use it in a pinch some day.

---

### Post by Iowan on 2009-11-22
I'm not sure - but that may be one of the files that requires **sudo** to edit.

---

### Post by fabby on 2010-09-27
Here is my advice:
- Make sure  you are root
- Use gedit instead of vi (much easier) --> gedit /etc/bind/named.conf.local
- If you insist on using vi, you need to press i (for insert) to edit text files. see the help section on that for how to save and exit because I don't remember.


On second hand, I am having difficulty with the same topic (I would like to setup BIND9 to act as a secondary DNS server to my primary (Windows Server 2008))

If anyone can help me, it would be much appreciated.
I have followed all the steps, but on step 9 I get error message from Windows saying this:
[IMG]http://bloggfiler.no/rabagast.blogg.no/images/516001-11-1285587453693.jpg[/IMG]

So what do?

---

### Post by fabby on 2010-09-27
Here is some information that can help.

- The IP of the secondary DNS server is Ubuntu on a virtual-box. I have configured it so it has its own IP adress.
- I'm testing this out because I will have to do the same thing for a Fedora server later.

---

### Post by terazen on 2010-09-27
Like iowan said... Use sudo to edit files owned by another user: "sudo nano /etc/bind/named.conf.local"

Also, it's probably best to make a backup of your files before editing as well.  "sudo cp /etc/bind/named.conf.local /etc/bind/named.conf.local.bak"

---

