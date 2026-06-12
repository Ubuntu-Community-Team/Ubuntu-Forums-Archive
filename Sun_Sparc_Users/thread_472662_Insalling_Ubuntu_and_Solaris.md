---
title: "Insalling Ubuntu and Solaris"
date: 2007-06-13
forum: Sun Sparc Users
---

### Post by manjeetchayel on 2007-06-13
[B]Hi

I have sun blade 150. 
Can have both ubuntu and solaris on the same machine.. 
If yes.. what should i install first... 

I am tryin to install Ubuntu 6.06 LTS ( Dapper Drake)

when i tried to run the ubuntu installation i get errors such as

Illegal instruction

and 

Stack underflow 

Plz help... and where shld i add the ide=nodma string

and how do i zero the hard disk.. can i zero the harddisk and install solaris first ... as i need it urgently on my machine... But when i try to install Solaris 10.. i get error
as
>Unformatted disk
>Hardware failure

(wat could be done)

Plz help soon....[/B]:)

---

### Post by Hendrixski on 2007-06-13
:-) sounds like you need to format the disk.  And the Solaris 10 install process is confusing as hell when it comes to doing all that stuff.  you can use the Ubuntu liveCD to format and partition your disk.  it's EASY.

just pop it in and click on the install icon and then it brings you to the tool called gparted (though, it may not tell you any longer that this is what it's called... I haven't installed feisty because my upgrade went just fine).  GParted can format your drive, can partition it, can install a file system even (though I don't think it does zfs).

By The way... you may want to try a distribution of OpenSolaris, like Nexenta, I think they may have an easier install process than regular Solaris.

---

### Post by manjeetchayel on 2007-06-13
can u give me the linux to download the iso image for the Ubuntu live cd which will work on sparc

---

