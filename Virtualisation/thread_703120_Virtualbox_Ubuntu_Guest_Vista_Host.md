---
title: "Virtualbox Ubuntu Guest Vista Host"
date: 2008-02-21
forum: Virtualisation
---

### Post by nikekakkar on 2008-02-21
Hey Everyone
I know this problem has been reported in this forum a zillion times before but I cant figure out how to fix the resolution and mouse problem in the ubuntu guest installation for virtualbox. My host machine is a dell laptop running windows vista. 
I have installed guest additions, and I know it works because I can get seamless mouse working. I restarted ubuntu and then went into the recovery mode, and did the whole sudo dpkg-reconfigure -phigh xserver-xorg 
command. After doing this when I login I get the proper screen size. I even get the right screen size on the desktop - BUT now I have an invisible mouse. So I go to xorg.conf and add vboxmouse and hit ctrl-alt-backspace to restart xserver. 
This causes, the login screen to remain  the right size, but the desktop is once again back to small size. The mouse is working again.

Any changes just result in the same cycle over and over and its just really frustrating.
Can anyone give me a set of directions which are known to work or just paste a link to a solution?
Any help would be great....

---

### Post by keratos on 2008-04-06
why dont you look at one or two of the "zillions" of posts. the answer will be there. its a very common problem with a very simple fix.

clue: google is your friend (guest additions)

---

