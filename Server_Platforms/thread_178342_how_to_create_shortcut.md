---
title: "how to create shortcut"
date: 2006-05-17
forum: Server Platforms
---

### Post by Swiss2K on 2006-05-17
I would like to know how to make a shortcut of a folder with the command line.

I'm running a ftp-server which has all users chrooted to my /archive dir. I frequently need access to a file in /var/.../..../. right now I'm using SSH to get access to that file. I would like to access this file using FTP but without the need to give up jailing users to /archive only.
I figured that making a shortcut of the /var/..../..../. dir into /archive would do the trick. For example, the 'cdrom' shurtcut in the root of a default Ubuntu install does exactly this.

How can i make this posible?

---

### Post by mjm115 on 2006-05-17
It sounds like you just want a link created.  If that is the case, then go to a command line and type in:

> 
man ln


Let me know if this helps.

---

### Post by Swiss2K on 2006-05-18
Thanks this should do the trick. 

I did the following 'ln /archive(target) /var/.../...(source)'

Now i'm getting this message...

'hard link not allowed for directory'

any ideas?

---

### Post by breezyfox on 2006-05-19
[QUOTE=Swiss2K]I would like to know how to make a shortcut of a folder with the command line.
I[/QUOTE]

hi you can make a symboloic link with option s.

sudo  ln -s path/to/file/ Any given name to this link

if you give link for folder than folder with open in browser.

hope this helps

bz

---

### Post by Emily the strange on 2008-05-17
hi!

I'm quite new here and I have a similar problem.
I have installed matlab and I would like to make shortcut on my desktop and add it in applications menu.

(I'm tired to go in /usr/local/ and run it with ./matlab in terminal)

sorry for my english :oops:

---

### Post by gareth_005 on 2008-05-17
Go to "System"->"Preferences"->"Main menu".
Select the menu list you want your new Launcher in and click the "New Item" button.
Fill in the details and click "Ok".

You can now navigate to your menu item in the main menu, right click it and choose "Add this launcher to desktop".

You can also right click the desktop and just create a Launcher there.

---

### Post by Emily the strange on 2008-05-17
thank you for help.

---

### Post by gvpj on 2008-06-05
> **gareth_005 said:**
> Go to "System"->"Preferences"->"Main menu".
Select the menu list you want your new Launcher in and click the "New Item" button.
Fill in the details and click "Ok".

You can now navigate to your menu item in the main menu, right click it and choose "Add this launcher to desktop".

You can also right click the desktop and just create a Launcher there.

i have a similar problem. i seem to be able to create desktop shortcuts for applications quite easily, but not for places. when installing ubuntu, i created a partition called data. i can see it in the main menu places>data. but when i try to create a shortcut to it using the method above, it doesnt work. please help.

---

