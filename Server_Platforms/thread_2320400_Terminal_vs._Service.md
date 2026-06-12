---
title: "Terminal vs. Service?"
date: 2016-04-13
forum: Server Platforms
---

### Post by ender8 on 2016-04-13
I'm a longtime MS admin and developer, but totally new to Linux, so the concepts are not unfamiliar, but just how to do this and that are stumping me sometimes.   My friend Google has been a great help.   

So far I've: 
Installed Ubuntu 14.04 on a Dell PowerEdge T610
Installed and run two Minecraft Servers.   
Installed xrdp and xfce4 to remote desktop into the server.
Installed and fooled around with Screen.  

My questions are around the context of a terminal session.   
If use the desktop to launch terminal then launch a persistent process like Minecraft server, does it stick around if I log out?  If I log back in, how can I re-attach to that instance to see what's going on, or manipulate the program (for example, add a user to Minecraft).  
I think there is a concept similar to a Windows Service in Linux, and if so, should I (can I) launch something like Minecraft as a service?

If I use Putty to SSH to the server, can I then launch a process like Minecraft server then log out, then reconnect later to admin or manipulate the program?

Am I thinking about this all the wrong way?  :)


I might be over complicating things here, but I'm also just trying to learn how things work.  I spent some time making the remote desktop work, but I realized I really don't even care if it has a "desktop".   I just remotely log in, launch a few Minecraft servers, log out, then log in from time to time to see that they're running OK.   

BTW, none of this is high security, I'm local on my own lan and just trying to run Minecraft as  way to learn.  

Any thoughts would be appreciated.   
Ender

---

### Post by Bucky Ball on 2016-04-13
*Thread moved to **Server Platforms**.*

Welcome to the forums. Although you're a newcomer to the forums your questions may get a better response here. Good luck.

---

### Post by bab1 on 2016-04-13
> **ender8 said:**
> I'm a longtime MS admin and developer, but totally new to Linux, so the concepts are not unfamiliar, but just how to do this and that are stumping me sometimes.   My friend Google has been a great help.   

So far I've: 
Installed Ubuntu 14.04 on a Dell PowerEdge T610
Installed and run two Minecraft Servers.   
Installed xrdp and xfce4 to remote desktop into the server.
Installed and fooled around with Screen.  

My questions are around the context of a terminal session.   
If use the desktop to launch terminal then launch a persistent process like Minecraft server, does it stick around if I log out? 
No.  More on that later below.> 
If I log back in, how can I re-attach to that instance to see what's going on, or manipulate the program (for example, add a user to Minecraft).

Servers (services) are launch via a non interactive method (init (Upstart or Systemd)).  The classic definition of a server is "a process that runs in the background waiting for requests from a client.  The client comes and goes but the server is always waiting for a request (listening at a TCP port).> 

I think there is a concept similar to a Windows Service in Linux, and if so, should I (can I) launch something like Minecraft as a service?

Yep.  They are called processes or daemons with Linux.
> 
If I use Putty to SSH to the server, can I then launch a process like Minecraft server then log out, then reconnect later to admin or manipulate the program?  Am I thinking about this all the wrong way?  :)

Yes,  most likely you would reconfigure the server parameters and restart the server (no need to reboot th OS) 
> 
I might be over complicating things here, but I'm also just trying to learn how things work.  I spent some time making the remote desktop work, but I realized I really don't even care if it has a "desktop".   I just remotely log in, launch a few Minecraft servers, log out, then log in from time to time to see that they're running OK. 
  
BTW, none of this is high security, I'm local on my own lan and just trying to run Minecraft as  way to learn.  

Any thoughts would be appreciated.   
Ender
There really is no need for a GUI interface on a Linux server.  Mostly it is a newbie feel good thing.  I can administrate my Linux servers via a SSH terminal login.

---

### Post by ender8 on 2016-04-14
Thanks for your reply!  Your comments were very helpful and I got everything up and running just like I wanted, using Upstart.  I hear what you're saying about the GUI....I've been getting used to doing everything via an SSH terminal and it's starting to all make sense.   I'll admit the GUI did make me feel better when I installed it, though.  But I'm over that now.  :D

Thanks again.

---

### Post by Graham_Willis on 2016-04-14
In fact you can have GUI access to the server without installing X Server (or any other graphical server) on the server side at all. You just install WinSCP and log in to it using the same data with which you connect to SSH (it is basically the same in this case). It is sometimes really convenient. If you're just a few users on a machine it might be no such a big deal, but if you have hundreds users on a production server then it may really make a difference. GUI gives you better situational awareness. For example, if you enter into a directory you immediately see the files which are there. It saves you from typing **ls** in order to see the name of the file you don't remember exactly and it make the probability of the accidental issuing a command being in a wrong directory significantly lower.

Another nice tool is Midnight Commander. It is a GUI-alike file manager. You install it on the server side, though. But it's rather lightweight. Definitely worth trying, I'd say.

---

### Post by lukeiamyourfather on 2016-04-14
Most Linux servers are administered entirely with the terminal and secure shell (ssh). Typically services run in the background like already pointed out. If you want to run something in an interactive session and have it continue after you logout you can send it to the background with an ampersand following the command and then later retrieve it but I wouldn't recommend doing this with critical things. The screen command is another way to do it, just requires a little more software and again I wouldn't recommend doing that with critical things.

---

