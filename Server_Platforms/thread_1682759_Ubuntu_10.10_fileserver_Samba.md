---
title: "Ubuntu 10.10 fileserver Samba"
date: 2011-02-06
forum: Server Platforms
---

### Post by runeh76 on 2011-02-06
Hi

Im playing with 10.10 (GUI) server in Virtual-box.
I installed Samba and now when i try to open it and starting to use it, i cant. I click **System--> Administration-->Samba** and system is asking password. I give it and apply, but then nothing happens. What im doing wrong?

---

### Post by arrrghhh on 2011-02-06
The server install of Ubuntu doesn't come with a GUI...  Did you install ubuntu-desktop?  You can still run all the same services you can on a server with ubuntu-desktop... The whole point of the server distro is no GUI, lean, mean, less to update, less to worry about security-wise...

---

### Post by Morbius1 on 2011-02-06
In a terminal type the following command and see if it has any error messages:
```
gksu system-config-samba
```

---

### Post by runeh76 on 2011-02-06
Yeah sry i mean i installed gnome-desktop. 
But can u say, why samba doesnt work?


edit: umm..why this page says that if u want GUI, install gnome-desktop..isnt GUI are a Graphical user interface?
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html]("http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html")

Those terms  :)

---

### Post by arrrghhh on 2011-02-06
> **runeh76 said:**
> Yeah sry i mean i installed gnome-desktop. 
But can u say, why samba doesnt work?


edit: umm..why this page says that if u want GUI, install gnome-desktop..isnt GUI are a Graphical user interface?
[http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html]("http://www.ubuntugeek.com/install-gui-in-ubuntu-server.html")

Those terms  :)

You're missing the point of Ubuntu Server, but that's fine... Go ahead and try what was mentioned above, but the point of Ubuntu Server is that you don't need a GUI.  If you need a GUI, just use Ubuntu Desktop, there's no point in running Ubuntu Server if you want a GUI.

---

### Post by runeh76 on 2011-02-06
I know what u mean, but i installed only this:
sudo apt-get install --no-install-recommends ubuntu-desktop

becouse i dont know those terminal commands like u guys (i think u guys didnt born and know all things, right?) And i never learn server things if i dont use it as graphical..u know? Trying to learn things and now im trying to learn how to share files in server,so i can access that share from internet. One thing at time.
I have learned some basics terminal commands, but i think this server is better first to "check" as graphical, what i need to find from there  :) Just playing with it now  ;)

Cheers

---

### Post by arrrghhh on 2011-02-06
> **runeh76 said:**
> I know what u mean, but i installed only this:
sudo apt-get install --no-install-recommends ubuntu-desktop

becouse i dont know those terminal commands like u guys (i think u guys didnt born and know all things, right?) And i never learn server things if i dont use it as graphical..u know? Trying to learn things and now im trying to learn how to share files in server,so i can access that share from internet. One thing at time.
I have learned some basics terminal commands, but i think this server is better first to "check" as graphical, what i need to find from there  :) Just playing with it now  ;)

Cheers

A) you still didn't try the command above, so do you still need help with samba?  You haven't addressed your issue at all in your responses.

B) No body was born knowing terminal commands, that's outrageous for obvious reasons.  However, I found that if you use the GUI as a crutch, you'll always use the GUI as a crutch.  Honestly, I was worried going to no GUI at first - but with the forums & Google, I have figured every single thing out I needed to - and I'm now MUCH happier because the system runs great, has very little to update, and I don't have to worry about a GUI dragging on my system resources ;).

So long story short, if you start with the GUI you're probably going to stick with it and never really learn anything about the terminal.  If you force yourself to use the terminal, you'll learn a lot more about it - and in the end I've found out I can do things much faster (usually) in the terminal thru ssh than I ever could dream of in a GUI...

---

### Post by rudelgurke on 2011-02-06
> **runeh76 said:**
> Trying to learn things and now im trying to learn how to share files in server,so i can access that share from internet

I really hope your Samba server isn't connected to the internet or at least from there your Shares aren't accessible.

---

### Post by runeh76 on 2011-02-06
> **rudelgurke said:**
> I really hope your Samba server isn't connected to the internet or at least from there your Shares aren't accessible.

:lolflag:  dont worry man  ;)

---

### Post by runeh76 on 2011-02-06
> **arrrghhh said:**
> A) you still didn't try the command above, so do you still need help with samba?  You haven't addressed your issue at all in your responses.

B) No body was born knowing terminal commands, that's outrageous for obvious reasons.  However, I found that if you use the GUI as a crutch, you'll always use the GUI as a crutch.  Honestly, I was worried going to no GUI at first - but with the forums & Google, I have figured every single thing out I needed to - and I'm now MUCH happier because the system runs great, has very little to update, and I don't have to worry about a GUI dragging on my system resources ;).

So long story short, if you start with the GUI you're probably going to stick with it and never really learn anything about the terminal.  If you force yourself to use the terminal, you'll learn a lot more about it - and in the end I've found out I can do things much faster (usually) in the terminal thru ssh than I ever could dream of in a GUI...

Sry i reinstalled hole thing, so i learn how to do it right..
Yeah i tryed that command, and only what i get is that same password screen to system-config-samba. I give right password and apply, BUT nothing happens! That screen just disappear.
Dont know what the heck is problem. I did all from terminal like this:
```
sudo apt-get install samba samba-common 
```
```
sudo apt-get install  system-config-samba
```
**System--> Administration-->Samba**
(Now asking password) and HUPS! screen just close...


I wanna learn commands, and im learning all at time. And im really appreciate what u are saying, and u are right. I just dont get it, how u can learn those commands? Its different thing to learn, than just copy&paste things. I have learned some basics  and im allways writing them to the paper if its a "nice" command..like a gksudo nautilus  LOL!! ..but i dont have so good memory u know.. that i could start testing server with my knowledge of terminal.. I want but i cant  :)

---

### Post by arrrghhh on 2011-02-07
> **runeh76 said:**
> Sry i reinstalled hole thing, so i learn how to do it right..
Yeah i tryed that command, and only what i get is that same password screen to system-config-samba. I give right password and apply, BUT nothing happens! That screen just disappear.
Dont know what the heck is problem. I did all from terminal like this:
```
sudo apt-get install samba samba-common 
```
```
sudo apt-get install  system-config-samba
```
**System--> Administration-->Samba**
(Now asking password) and HUPS! screen just close...


I wanna learn commands, and im learning all at time. And im really appreciate what u are saying, and u are right. I just dont get it, how u can learn those commands? Its different thing to learn, than just copy&paste things. I have learned some basics  and im allways writing them to the paper if its a "nice" command..like a gksudo nautilus  LOL!! ..but i dont have so good memory u know.. that i could start testing server with my knowledge of terminal.. I want but i cant  :)

Well despite your adverse response to it, I still say we should do this via the command line.

So open a terminal session (alt-f2 then 'gnome-terminal') and you can copy/paste this in:```
testparm
```Please paste the output of this in [code] braces.

---

### Post by runeh76 on 2011-02-07
> **arrrghhh said:**
> Well despite your adverse response to it, I still say we should do this via the command line.


I didnt say that i dont wanna do things from terminal, did i?
I think u got wrong picture or something. Please stop that okey  :)
Lets focus this samba-thing, so guys who need this thread someday, can take benefits out from it  :)

So here is **testparm** output:

```
Program "testparm" locate in next packets:
*samba-common-bin
*samba4-common-bin
Try: sudo apt-get install <packet>
```(I had to translate output, so sry my english)


edit: By the way, synaptic package manager..same problem. Ask password when launch it, and after that doesnt open package-manager. I think problem is somewhere else..virtualbox itself?

editII: After updates i tryed from terminal:

```
samba

Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[Mon Feb  7 14:13:21 2011 EET, 0 ../smbd/server.c:374:binary_smbd_main()]
samba version 4.0.0alpha12-GIT-UNKNOWN started.
Copyright Andrew Tridgell and the Samba Team 1992-2010

```

And from terminal synaptic work.

---

### Post by runeh76 on 2011-02-07
I founded nice pages to learn terminal. Now only problem is to learn. :)
[http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/]("http://www.scottklarr.com/topic/115/linux-unix-cheat-sheets---the-ultimate-collection/")

[http://ubuntuforums.org/showthread.php?t=171507]("http://ubuntuforums.org/showthread.php?t=171507")

I need to know HOW to learn combine those commands?
Example: sudo apt-get install <package>

How i learn to know command-"statements", when i want to do something what i usually do from gnome, and that those commands are correct, so i dont harm the system? This is hard to explain, but i hope someone understand what i mean?

---

### Post by arrrghhh on 2011-02-07
> **runeh76 said:**
> I didnt say that i dont wanna do things from terminal, did i?
I think u got wrong picture or something. Please stop that okey  :)
Lets focus this samba-thing, so guys who need this thread someday, can take benefits out from it  :)

So here is **testparm** output:

```
Program "testparm" locate in next packets:
*samba-common-bin
*samba4-common-bin
Try: sudo apt-get install <packet>
```(I had to translate output, so sry my english)


edit: By the way, synaptic package manager..same problem. Ask password when launch it, and after that doesnt open package-manager. I think problem is somewhere else..virtualbox itself?

editII: After updates i tryed from terminal:

```
[Mon Feb  7 14:13:21 2011 EET, 0 ../smbd/server.c:374:binary_smbd_main()]
samba version 4.0.0alpha12-GIT-UNKNOWN started.
Copyright Andrew Tridgell and the Samba Team 1992-2010

```

And from terminal synaptic work.

It would appear that you have the alpha v4 version of samba...

Why don't you just install the 'regular' version of samba?

Please see the [Samba Ubuntu Community Doc](https://help.ubuntu.com/community/Samba).  Since testparm didn't run, you don't have the correct packages installed.

---

### Post by runeh76 on 2011-02-07
Oh okey i will try to install it another way..just was doing like this sayed:
[http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-]("http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-")

by the way..i removed GUI  ;)

Thx arrrghhh!  :)

---

### Post by arrrghhh on 2011-02-07
> **runeh76 said:**
> Oh okey i will try to install it another way..

by the way..i removed GUI  ;)

Thx arrrghhh!  :)

Heh, np.  Read that page I sent you, it's very good.  If you need more help, you know where to turn...

If you have another issue (not related to this one) feel free to search this section of the forum - there's a TON of great threads.  If you can't find what you're looking for after ***thoroughly*** searching, feel free to throw up another thread.

Thanks!

---

### Post by runeh76 on 2011-02-07
Yeah im reading it and i managed to install it correct now THX! Im configuring it now (from terminal) ;) pretty intresting and such a fun to learn :)

Its slow though, becouse i need google all at time, u know..i have to start from beginning...
```
sudo adduser username
``` 

My goal is now to connect my virtual-server fileshare, from this same computer. Is that simple? (pls dont laugh)  :)

---

### Post by arrrghhh on 2011-02-07
> **runeh76 said:**
> Yeah im reading it and i managed to install it correct now THX! Im configuring it now (from terminal) ;) pretty intresting and such a fun to learn :)

Its slow though, becouse i need google all at time, u know..i have to start from beginning...

My goal is now to connect my virtual-server fileshare, from this same computer. Is that simple? (pls dont laugh)  :)

You'll get it eventually, lots of learning at first - it does take some getting used to, but I think once you do give it a chance you'll love it.

As far as the virtual-server stuff... So you have Ubuntu as the host OS and what as the guest OS?  Assuming you're using VirtualBox, the easiest way to share files between guest & host is using Guest Additions.  [Here's](http://forums.virtualbox.org/viewtopic.php?t=15868) a good guide on how to setup file sharing using guest additions.

---

### Post by runeh76 on 2011-02-07
One computer. Both are Ubuntu 10.10
Samba-server is virtual. 

So.. is it possible to connect that share like this, if i dont install that guest additions?
I try to learn a little how to service things in server, and how to connect there to use them. 

This file-share "thing" is just one test.

by the way.. i THINK i need to connect my share from "Connect to server" and what kind of connection-method i need to use?

---

### Post by arrrghhh on 2011-02-07
> **runeh76 said:**
> One computer. Both are Ubuntu 10.10
Samba-server is virtual. 

So.. is it possible to connect that share like this, if i dont install that guest additions?
I try to learn a little how to service things in server, and how to connect there to use them. 

This file-share "thing" is just one test.

by the way.. i THINK i need to connect my share from "Connect to server" and what kind of connection-method i need to use?

I guess I don't see the point of having Ubuntu 10.10 inside of a Ubuntu 10.10 machine... Kinda redundant no?

Are you using it as a sandboxed environment, so if something does get messed up you can blow it away?  That would be the only thing that would make sense to me.

With that said, if you're sharing between Linux machines, NFS is definitely the way to go... hands down.

However, if you have a mixed environment, samba is the only way to go for Windows clients - I have both installed so I can use NFS to the Linux boxes and SMB to the Win boxes!

---

### Post by Morbius1 on 2011-02-07
I'll admit that I no longer have any idea what's going on here.

If you've installed Ubuntu Server in VBox then you need to make sure you are using "Bridged Adapter" mode in VBox. By default it will use NAT and that means that the Server can see out but nobody can see in and Servers really have no need to see out. I'm not sure if Bridged mode is available without "Guest Additions" - it may be but I'm not sure.

Do you have actual client systems in your LAN ( do you even have a LAN ? ) or is this just a stand alone PC and you are trying to simulate a Samba Server and a Linux Client? The reason I ask is that in Bridged Adapter mode the server will connect to the same router as the host. That's the only way it will be seen by the host. If you don't have a router then this ain't gonna work.

There are two other networking options in VBox but I've never used them to know how they work.

---

### Post by runeh76 on 2011-02-08
> **Morbius1 said:**
> I'll admit that I no longer have any idea what's going on here.

If you've installed Ubuntu Server in VBox then you need to make sure you are using "Bridged Adapter" mode in VBox. By default it will use NAT and that means that the Server can see out but nobody can see in and Servers really have no need to see out. I'm not sure if Bridged mode is available without "Guest Additions" - it may be but I'm not sure.

Do you have actual client systems in your LAN ( do you even have a LAN ? ) or is this just a stand alone PC and you are trying to simulate a Samba Server and a Linux Client? The reason I ask is that in Bridged Adapter mode the server will connect to the same router as the host. That's the only way it will be seen by the host. If you don't have a router then this ain't gonna work.

There are two other networking options in VBox but I've never used them to know how they work.


Yes i was looking for that "Bridged mode" and i founded it now. Havent have time to test it..testing it later. 
But u are saying it doest work? Why so, i dont have LAN, just stand alone PC and im trying to simulate like u sayed. My virtual-server has own IP-address, so isnt that possible to connect/find that server from internet? Isnt that a purpose to have virtual-machine, that u dont need LAN or another machine, so u can run server(s) from one machine?
I thought that samba works fine if guest is linux too, dont see reason why shouldnt.

```
/usr/bin/smbclient -L 192.168.1.101 -U guest
```


edit: Maybe i should try this FTP-server [http://ubuntuforums.org/showthread.php?t=841336]("http://ubuntuforums.org/showthread.php?t=841336") and forget this samba-thing, becouse first at all i was thinking to create FTP-server but i founded some links that sayed its not recommendable and its unsafe or something..but like u know im just playing and i dont have nothing unsafe in my server..just empty home-folders. I am allready friend with filezilla, so i could try this [https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html")


What u think? I think that everything is possible if u find way to do it  :)

(Also u can mark this thread SOLVED if u wish, becouse i got samba working)

---

### Post by runeh76 on 2011-02-08
I succesfully got that FTP working  :p
So i say again, if u find way to do it..u can!  :)

I did follow these links:
[http://www.howtoplaza.com/how-to-use-ftp-in-ubuntu]("http://www.howtoplaza.com/how-to-use-ftp-in-ubuntu")
[https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html")
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1421927]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1421927")
Connection "Connect to server"
```
ftp://192.168.xx.xx/home/share
```


Thank you guys

---

### Post by arrrghhh on 2011-02-08
> **runeh76 said:**
> I succesfully got that FTP working  :p
So i say again, if u find way to do it..u can!  :)

I did follow these links:
[http://www.howtoplaza.com/how-to-use-ftp-in-ubuntu]("http://www.howtoplaza.com/how-to-use-ftp-in-ubuntu")
[https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html]("https://help.ubuntu.com/10.10/serverguide/C/ftp-server.html")
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1421927]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1421927")
Connection "Connect to server"
```
ftp://192.168.xx.xx/home/share
```


Thank you guys

Heh, I guess if that works for you...

Why wouldn't you use Guest Additions and just share the folders that way?  Much easier, and much faster...  To each their own I guess.

---

### Post by runeh76 on 2011-02-08
> **arrrghhh said:**
> Heh, I guess if that works for you...

Why wouldn't you use Guest Additions and just share the folders that way?  Much easier, and much faster...  To each their own I guess.

What u mean "i guess if that works for you"?

I dont wanna use guest additions, becouse its too simple. I wanna learn things. Please read my earlier posts.

---

### Post by arrrghhh on 2011-02-08
> **runeh76 said:**
> What u mean "i guess if that works for you"?

I dont wanna use guest additions, becouse its too simple. I wanna learn things. Please read my earlier posts.

...Ok, but sharing files between a VM guest and a VM host aren't really the same as setting up a LAN.  You wouldn't want to use FTP on a LAN for example - sure you can, but why when there's NFS and samba :p.

---

### Post by runeh76 on 2011-02-08
U still dont see my point..  :confused:
Well dont get headache becouse it..

---

### Post by arrrghhh on 2011-02-08
> **runeh76 said:**
> U still dont see my point..  :confused:
Well dont get headache becouse it..

You still don't see mine, but it doesn't really matter...

Enjoy your FTP server!

---

### Post by runeh76 on 2011-02-08
Yes i see..

Thanx anyway..

---

