---
title: "cannot sudo"
date: 2007-08-10
forum: Server Platforms
---

### Post by handyguy33 on 2007-08-10
Hi all.

I've been away from my server for a couple of months and my (temp) replacement has made some changes. First of all, he's set up a new installation of server 6.10 with no gui (I know the gui isn't necessary, but it makes my life easier as I'm not terribly experienced yet). 

So I got the commands to get the gui, but when I tried to sudo it, I got the response "Administrator is not in the sudoers files. This incident will be reported." In fact that's the response I get when I try to sudo anything.

It's going to be very hard to fix or maintain anything if I can't have the access. Worse yet, there's a problem with the samba sharing. Excel files on the server open as "Read Only" on everyone's computers. This is an issue that requires immediate attention but I can't make move #1 with the server in this state.

I need some serious help. And please make your responses understandable to a newbie. Aside from some minor troubleshooting with our website, I really don't have a lot of experience with fixing things. When I left, everything just worked.

---

### Post by kast on 2007-08-10
This page should help, i would just give you the commands to add yourself and your privileges, but i'm not sure about your security practices and i wouldn't want to give that user to much. check this site out for more info.


[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

---

### Post by handyguy33 on 2007-08-10
Thanks for the link. That's definitely getting bookmarked. Unfortunately,
you have to use sudo for those commands and I can't sudo at all. Short of backing up everything and starting from scratch, I can't see how I'm supposed to change root privileges. That may take time that I don't have.

---

### Post by rickyjones on 2007-08-10
You might want to talk to your replacement and find out what he/she did and have them help you out.

-Richard

---

### Post by handyguy33 on 2007-08-10
I'm afraid he left under less than ideal circumstances. I don't think I'll get much help from him.

---

### Post by kast on 2007-08-10
did he leave disliking you? maybe you could try contacting him and appeal to him on a personal level. " hey! listen i know things didn't work out here at (blank) but now i'm totally screwed i cant even get this going on the server, what was the root password for sudo?"  

:) not a big chance it will work but not sure what else you could do.

---

