---
title: "Folder permissions through SSH"
date: 2009-03-06
forum: Server Platforms
---

### Post by Trekrider58 on 2009-03-06
I have just set up a Server with 8.10 and have configured Samba and SSH.

Through my windows based clients I can add folders and files and access folders created on the server or from my Ubuntu client (the later using SSH).

On my Ubuntu client I can create and modify folders and files on the server.

My problem is that if I create a folder on a windows client it shows as 'read only' on my Ubuntu client (through Nautilus).

On my Ubuntu client, if I connect to the server through a terminal using SSH I can modify folders and files no matter which client created them but when I use Nautilus and connect to the server (using SSH) any folders created on a windows client shows as 'read only' and I can't create sub-folders etc.

In smb.conf I have 'create mask = 0775' and 'directory mask = 0775'. I have added my Ubuntu server user name to the samba group.

If I 'ls -l' through the terminal on my Ubuntu client folders created on the windows clients show as 'drwxrwxr-x' which is what I would expect.

How can I get the Nautilus GUI to allow me full access to folders and files as I have through the terminal?

---

### Post by matey3 on 2009-03-06
For what I have seen you have to always create folders and set rights via Samba server (Linux) not Windows.
I once had this problem but realized samba is set up that way.
May be some one else knows the work around but I dont think it would be good thing to do.

> How can I get the Nautilus GUI to allow me full access to folders and files as I have through the terminal?
You have to be su in GUI and I cant remember the name of the program that allows you to put in root password in GUI?
But I always log in as root to my GUI so I dont remember what I used to use before. sorry ,,,

oh, I found another method in this link;

[http://ubuntuforums.org/archive/index.php/t-37737.html](http://ubuntuforums.org/archive/index.php/t-37737.html)


(I once told some 1 how to do it and the mods here, wrote me up? like what the hell? its Your machine and if you want to destroy it its no body's business) LOL :D

---

### Post by matey3 on 2009-03-06
OH OK I found the prog. I was talking about, its called gksudo
sorry for many replies...

---

### Post by Trekrider58 on 2009-03-06
> **matey3 said:**
> For what I have seen you have to always create folders and set rights via Samba server (Linux) not Windows.
I once had this problem but realized samba is set up that way.
May be some one else knows the work around but I dont think it would be good thing to do.


Thanks Matey, I understand what you are saying (and I'm not saying you are wrong) but it doesn't make sense for clients to not be able to create folders usable by all clients - isn't that the point of having a server?

I can change the folder permissions through the terminal using 'sudo chmod ogu+rwx -R share' but I don't want to have to do this every time a windows client makes a new folder.

Is there a different value to use with 'create mask' in smb.conf that sets write privileges for 'others'? I haven't been able to find a list of what the values mean.

---

### Post by Trekrider58 on 2009-03-06
OK, I have found that the value 0777 sets write access for all users and I can now create folders from a windows client and have full access from my Ubuntu client :D

---

### Post by Trekrider58 on 2010-03-13
> **Divs99 said:**
> However, the above fix will not work unless you first enable your iPhone to work with the iPhoneBrowser. Blackra1n doesn't enable the proper service to be able to use iPhoneBrowser, so you have to do it manually. This is described on the iPhoneBrowser's homepage

[]("http://code.google.com/p/iphonebrowser/") So, to summarize - if you use Blackra1n, you should make sure you iPhoneBrowser is working before you install anything. Once it is working, if you get to the point where your phone is stuck at the Apple logo, you can use iPhoneBrowser to recover.
==========
[cosmetic surgery marketing](http://fruition.net/search-engine-optimization/levels-of-service/cosmetic-dentist-orthodontist-internet-marketing/)
[Utah Search Engine Optimization Services](http://www.tavahatz.com/seo-services/)
Am I missing something here - what has the iphone got to do with this thread?

---

