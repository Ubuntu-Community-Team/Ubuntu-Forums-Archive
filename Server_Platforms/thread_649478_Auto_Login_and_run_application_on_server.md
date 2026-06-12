---
title: "Auto Login and run application on server"
date: 2007-12-25
forum: Server Platforms
---

### Post by Taransworld on 2007-12-25
Hello, 

I am not new to computers but I am new to Linux.  I have read about 20 post asking how to auto login and no one answers the question.  It seems everyone always ask why do you want to auto login and then gives a different answer. 

I am trying to have my pc at home boot ubuntu SERVER 7 and then launch NetApp 7.2.3 simulator.  I have tried other ideas such as rc.local, etc but what I really need is when I go to this server after a reboot I want it at a NetApp prompt, not a linux prompt.  

I was able to do this from the desktop version and lots of people talk about that just not how to do it from the server version. 

Any help would be great. 

Thanks!!!!

---

### Post by Taransworld on 2007-12-25
Ok, if found one way to do this.  It seems there must be an easier way but I was able to get this to work following Brandon's Blog web site.  Basically he walks you through creating a c program that you set to execute when you log in. 

Here is his web page: [http://www.imbrandon.com/2007.10.19/note-to-self-ubuntu-710-on-a-p200.html](http://www.imbrandon.com/2007.10.19/note-to-self-ubuntu-710-on-a-p200.html)

Of course to execute the NetApp sim after the login I just put it in roots .bashrc file.  

Anyone have anything better???

Thanks very much

---

### Post by mustang357 on 2007-12-25
I'm not familiar with the NetApp sim, but could you possibly try setting that as the shell for your user?

It may have unintended consequences if the user tries to log in for other things (like not getting a real shell), but it seems to me that just like switching between bash and csh that it might work.

Let us know how it works for you.

Good luck!

---

### Post by Taransworld on 2007-12-25
Hello mustang375,

Thanks for the idea.  I tried it and here are the results.  

1) This didn't help with the auto login so I had to stay with the login work around from Brandon's Blog.

2) The shell did launch once I logged in and the simulator ran fine.

3) Once in the new shell, I was never able to get back to the linux shell to do work (when it is in the .bashrc file it only runs once so I can exit out of the NetApp simulator and do linux stuff (like updates) if needed). 

4) Even when logging in with recovery mode I could never get back to the linux shell.  I had this in VMWare so I had to revert back to a snapshot I had taken. 

Thanks for the idea. (learning a lot here)

---

### Post by rsw686 on 2007-12-25
The reason you probably aren't getting any responses is that 99% of the users are not going to have their server log in automatically. The whole security aspect is gone then. NetApp should run as a service and have a client to access it. Kind of like mysqld and mysql client.

---

### Post by Taransworld on 2007-12-25
Hello rsw686,

I knew someone would say this because it has been said on every thread out there.  Note, linux desktop is for home users make it very easy to autologon, this SERVER that I am running with NetApp sim on is for HOME use.  I have no reason to run this test environment in a secure fasion.  

My only goal is to make this run as close to a real NetApp as I can. 

Thanks for any advice...

---

### Post by rsw686 on 2007-12-25
> **Taransworld said:**
> Hello rsw686,

I knew someone would say this because it has been said on every thread out there.  Note, linux desktop is for home users make it very easy to autologon, this SERVER that I am running with NetApp sim on is for HOME use.  I have no reason to run this test environment in a secure fasion.  

My only goal is to make this run as close to a real NetApp as I can. 

Thanks for any advice...

Umm you need to read my post more clearly. I just stated that the reason you are not receiving advice is due to that reason. Not that I disagree or agree with what you are trying to accomplish.

---

### Post by Taransworld on 2007-12-25
:-#  Sorry for speaking in haste. I read it right before I had to run out the door.  I should have read it more carefully.  

I really do appreciate your reply..

Merry Christmas everyone!!!!

---

